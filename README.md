# -_-_juego_de_consola-_adivina_la_pregunta_- :. 
# 🎮 Juego de Consola – Adivina la Pregunta.

========================================
     ADIVINA LA PREGUNTA
========================================
          ❓  ¿PIENSAS?
        💡  RESPONDES.
          🎯  ACIERTAS.
========================================
     
<img width="2546" height="1032" alt="image" src="https://github.com/user-attachments/assets/22100250-f849-4d47-9ec2-bfd886aa0d22" />     
          
A continuación se presenta una **solución completa, clara y ejecutable** de un juego de consola en **C#** para **Visual Studio 2022**, llamado **“Adivina la Pregunta”**.

---

## 📌 Descripción General

El juego funciona de la siguiente manera:

- El sistema elige una pregunta al azar  
- Muestra **la respuesta**
- El jugador debe **adivinar cuál es la pregunta correcta** entre varias opciones
- Se valida la selección
- Se acumulan puntos
- El jugador puede volver a jugar

---

## 🛠️ Tecnologías Utilizadas

- **Lenguaje:** C#  
- **Tipo:** Console Application  
- **IDE:** Visual Studio 2022  
- **Nivel:** Básico – Intermedio  

---

## 📋 Reglas del Juego

En cada ronda se muestran:

- ✅ Una **respuesta**
- ✅ **4 preguntas posibles**
- ✅ El jugador elige la pregunta correcta
- ✅ El sistema valida la respuesta
- ✅ Se muestran los puntos acumulados
- ✅ Opción de volver a jugar

---

## 🧠 Ejemplo de Juego

RESPUESTA:
👉 París

¿Cuál es la pregunta correcta?

¿Cuál es la capital de Francia?

¿Qué país tiene más habitantes?

¿Cuál es el río más largo?

¿Qué planeta es el más grande?

Selecciona una opción (1-4):

---

## 📂 Estructura del Proyecto
```
AdivinaLaPregunta/
│
├── Program.cs
```
---

## 🧩 Código Completo (Program.cs)

```csharp
using System;
using System.Collections.Generic;

namespace AdivinaLaPregunta
{
    class Program
    {
        static void Main(string[] args)
        {
            Console.Title = "🎮 Adivina la Pregunta";
            int puntuacion = 0;
            bool jugar = true;

            List<Pregunta> preguntas = new List<Pregunta>()
            {
                new Pregunta(
                    "París",
                    new string[]
                    {
                        "¿Cuál es la capital de Francia?",
                        "¿Qué país tiene más habitantes?",
                        "¿Cuál es el océano más grande?",
                        "¿Cuál es el planeta más cercano al sol?"
                    },
                    0
                ),
                new Pregunta(
                    "8",
                    new string[]
                    {
                        "¿Cuántos continentes hay?",
                        "¿Cuántos planetas hay en el sistema solar?",
                        "¿Cuántos lados tiene un triángulo?",
                        "¿Cuántas horas tiene un día?"
                    },
                    1
                ),
                new Pregunta(
                    "Amazonas",
                    new string[]
                    {
                        "¿Cuál es el río más largo del mundo?",
                        "¿Cuál es el desierto más grande?",
                        "¿Cuál es la montaña más alta?",
                        "¿Cuál es el lago más profundo?"
                    },
                    0
                )
            };

            Random random = new Random();

            while (jugar)
            {
                Console.Clear();
                Pregunta actual = preguntas[random.Next(preguntas.Count)];

                Console.WriteLine("=================================");
                Console.WriteLine("     🎯 ADIVINA LA PREGUNTA");
                Console.WriteLine("=================================\n");

                Console.WriteLine("RESPUESTA:");
                Console.WriteLine($"👉 {actual.Respuesta}\n");

                Console.WriteLine("¿Cuál es la pregunta correcta?\n");

                for (int i = 0; i < actual.Opciones.Length; i++)
                {
                    Console.WriteLine($"{i + 1}) {actual.Opciones[i]}");
                }

                Console.Write("\nSelecciona una opción (1-4): ");
                int opcion;

                if (int.TryParse(Console.ReadLine(), out opcion) &&
                    opcion >= 1 && opcion <= 4)
                {
                    if (opcion - 1 == actual.RespuestaCorrecta)
                    {
                        Console.ForegroundColor = ConsoleColor.Green;
                        Console.WriteLine("\n✅ ¡Correcto!");
                        puntuacion++;
                    }
                    else
                    {
                        Console.ForegroundColor = ConsoleColor.Red;
                        Console.WriteLine("\n❌ Incorrecto.");
                        Console.WriteLine("La respuesta correcta era:");
                        Console.WriteLine($"👉 {actual.Opciones[actual.RespuestaCorrecta]}");
                    }
                }
                else
                {
                    Console.WriteLine("\n⚠️ Opción inválida.");
                }

                Console.ResetColor();
                Console.WriteLine($"\n🏆 Puntuación actual: {puntuacion}");

                Console.Write("\n¿Deseas jugar otra ronda? (S/N): ");
                jugar = Console.ReadLine().Trim().ToUpper() == "S";
            }

            Console.WriteLine("\n🎉 Gracias por jugar.");
            Console.WriteLine($"Puntuación final: {puntuacion}");
            Console.ReadKey();
        }
    }

    class Pregunta
    {
        public string Respuesta { get; set; }
        public string[] Opciones { get; set; }
        public int RespuestaCorrecta { get; set; }

        public Pregunta(string respuesta, string[] opciones, int respuestaCorrecta)
        {
            Respuesta = respuesta;
            Opciones = opciones;
            RespuestaCorrecta = respuestaCorrecta;
        }
    }
}

▶️ Cómo Ejecutar en Visual Studio 2022
- Abrir Visual Studio 2022
- Crear Nuevo Proyecto
- Seleccionar Aplicación de Consola
- Lenguaje: C#
- Nombre del proyecto: AdivinaLaPregunta
- Reemplazar el archivo Program.cs con el código anterior
- Ejecutar con F5

🚀 Posibles Mejoras
⏱️ Temporizador por pregunta
🎚️ Dificultades (fácil / medio / difícil)
📄 Preguntas cargadas desde archivo JSON
🏆 Ranking de jugadores
🔊 Sonidos y animaciones ASCII / .
