# Saldob
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp10
{
    internal class Program
    {
        static void Main(string[] args)
        {
            double i, conto;

            ContoBancario c = new ContoBancario("Alberto", 1000);
            Console.WriteLine("il saldo iniziale è " +c.saldo);


            Console.WriteLine("quanto vuoi depositare ? ");
            i = double.Parse(Console.ReadLine());
            c.deposito(i);
            Console.WriteLine("il saldo aggiornato, dopo il deposito, è " + c.saldo);
 

            Console.WriteLine("quanto vuoi prelevare ? ");
            i = double.Parse(Console.ReadLine());


            conto = c.prelievo(i);

            if(conto == -1)
            {
                Console.WriteLine("prelievo andato male, il tuo saldo è di " + c.saldo);
            }
            else
            {
                Console.WriteLine("il saldo dopo il prelievo è uguale a " + conto);
            }

            Console.WriteLine(c);
                
                Console.ReadLine();

        }
    }
}
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp10
{
    internal class ContoBancario
    {
        public string intestatario {8  get; set; }
        public double saldo { get; set; }
        public override string ToString()
        {
            return string.Format("{0} ha un saldo di {1} euro", intestatario, saldo);
        }

        public ContoBancario(string nomec)
        {
            saldo = 0;
            intestatario = nomec;
        }

        public ContoBancario(string nomec, double saldoi)
        {
            saldo = saldoi;
            intestatario = nomec;
        }

        public double prelievo(double saldoprel)
        {
            if(saldoprel <= saldo)
            {
                saldo = saldo - saldoprel;
                return saldo;
            }
            else
            {
                return -1;
            }
        }

        public double deposito(double saldoagg)
        {
            saldo = saldo + saldoagg;
            return saldo;
        }

        public string stampa()
        {
            return string.Format("{0} ha un saldo di {1} euro", intestatario, saldo);
        }
       
    }
}
