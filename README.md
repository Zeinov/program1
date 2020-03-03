using System;


namespace Zadanie_7
{
	class Vehicles
	{
		
		protected double vehicleIsSpeedGood;
		





		public delegate void VehiclesHandler();
		public event VehiclesHandler Notify;

		protected void problemWithVechicles()
		{
			if(vehicleIsSpeedGood == 0)
			{
				Notify();

			}
			else if(vehicleIsSpeedGood < 0)
			{
				Notify();
			}
		}

	}

	class Train : Vehicles
	{

		private string Name_Train { get; set; }
		private double Speed_Train { get; set; }

		
		public Train(string name_train, double speed_train)
		{
			Name_Train = name_train;
			Speed_Train = speed_train;
		}

		
		public Train(Train previousMonitor)
		{
			Name_Train = previousMonitor.Name_Train;
			Speed_Train = previousMonitor.Speed_Train;
		}

		

		public void Write_Speed_Train()
		{
			double speed_train;
			Console.Write("Скорость поезда: ");
			speed_train = double.Parse(Console.ReadLine());
			Speed_Train = speed_train;
			
		}

		public string Details_Train()
		{
			return  "   скорость поезда: " + Speed_Train.ToString() + " km/h";
		}


		public void TrainIsGoodOrNotGood()
		{
			if (Speed_Train == 0)
			{
				
				Console.WriteLine("проблемы с поездом");
				Console.WriteLine();
				Console.WriteLine("чтобы узнать какая проблема с поездом нажми Enter");
				Console.ReadKey();
				Console.Clear();
				Speed_Train = vehicleIsSpeedGood;
				problemWithVechicles();
			}
			else if (Speed_Train < 0)
			{
				
				Console.WriteLine("у поезда есть проблемы");
				Console.WriteLine();
				Console.WriteLine("чтобы узнать какая проблема с поездом нажми Enter");
				Console.ReadKey();
				Console.Clear();
				Speed_Train = vehicleIsSpeedGood;
				problemWithVechicles();
			}
			else
			{
				
				Console.WriteLine("Нет проюлем с поездом");

			}
		}

		public void Message()
		{
			Console.WriteLine("Проблемы с двигателем!");
		}

	}




	class Plane : Vehicles
	{
		private string Name_Plane { get; set; }
		private double Speed_Plane { get; set; }

		
		public Plane(string name_plane, double speed_plane)
		{
			Name_Plane = name_plane;
			Speed_Plane = speed_plane;
		}

		
		public Plane(Plane previousMonitor)
		{
			Name_Plane = previousMonitor.Name_Plane;
			Speed_Plane = previousMonitor.Speed_Plane;
		}

		

		public void Write_Speed_Plane()
		{
			double speed_plane;
			Console.Write("Скорость самолета: ");
			speed_plane = double.Parse(Console.ReadLine());
			Speed_Plane = speed_plane;

		}

		public string Details_Plane()
		{
			return "  Скорость самолета: " + Speed_Plane.ToString() + " km/h";
		}


		public void PlaneIsGoodOrNotGood()
		{
			if (Speed_Plane == 0)
			{

				Console.WriteLine("У Самолета есть проблема:");
				Console.WriteLine();
				Console.WriteLine("чтобы узнать какая проблема с самолетом нажми Enter");
				Console.ReadKey();
				Console.Clear();
				Speed_Plane = vehicleIsSpeedGood;
				problemWithVechicles();
			}
			else if (Speed_Plane < 0)
			{

				Console.WriteLine("У самолета есть проблемы");
				Console.WriteLine();
				Console.WriteLine("чтобы узнать какая проблема с Самолетом нажми Enter");
				Console.ReadKey();
				Console.Clear();
				Speed_Plane = vehicleIsSpeedGood;
				problemWithVechicles();
			}
			else
			{

				Console.WriteLine("С самолетом все в порядке");

			}
		}

		public void Message()
		{
			Console.WriteLine("Проблемы с двигателем!");
		}
	}



	class Program
	{
		static void Main(string[] args)
		{
			int action;


			
			Console.WriteLine("1.Поезд");
			Console.WriteLine("2.Самолет");

			action = int.Parse(Console.ReadLine());

			switch (action)
			{
				case 1:
					Console.Clear();
					Train tr1 = new Train("", 1);
					tr1.Write_Speed_Train();
					Console.WriteLine();
					Console.WriteLine(tr1.Details_Train());

					tr1.Notify += tr1.Message;

					tr1.TrainIsGoodOrNotGood();
					break;
				case 2:
					Console.Clear();
					Plane pl1 = new Plane("", 1);
					pl1.Write_Speed_Plane();
					Console.WriteLine();
					Console.WriteLine(pl1.Details_Plane());

					pl1.Notify += pl1.Message;
					pl1.PlaneIsGoodOrNotGood();
					break;
				default:
					break;
			}
			Console.ReadKey();
		}
	}
}

