# Practica1

LIDAR (Light Detection and Ranging) este o tehnologie de senzorizare care utilizează laser pentru a măsura distanțele și a crea o imagine detaliată a mediului înconjurător. Pentru a realiza acest proiect, vei avea nevoie de hardware (senzori LIDAR, platforma robotică etc.) și software (algoritmi de mapare, programare).

   SLAM este procesul de localizare și mapare simultană. În timp ce robotul se deplasează, acesta estimează poziția sa în funcție de datele de la senzorul LIDAR și actualizează harta mediului. Există diferite variații de algoritmi SLAM, precum EKF-SLAM (Extended Kalman Filter SLAM) sau algoritmi bazate pe partiții grid (grid-based).



   o schiță simplificată a modului în care ar putea arăta un astfel de algoritm în limbajul de programare Python:

```python
# Importarea bibliotecilor necesare
import numpy as np

# Inițializarea hărții
map = np.zeros((100, 100))  # O hartă goală de 100x100 celule

# Inițializarea poziției și orientării robotului
robot_position = [50, 50]  # Poziția inițială (centrul hărții)
robot_orientation = 0.0  # Orientarea inițială (0 radiani)

# Funcție pentru actualizarea hărții cu datele LIDAR
def update_map(scan_data, robot_position, robot_orientation):
    for distance, angle in scan_data:
        # Calculează poziția punctului detectat în sistemul global
        x = robot_position[0] + distance * np.cos(robot_orientation + angle)
        y = robot_position[1] + distance * np.sin(robot_orientation + angle)

        # Transformă coordonatele în coordonatele hărții
        x_map = int(x)
        y_map = int(y)

        # Actualizează harta pentru celula la care a ajuns punctul
        map[x_map, y_map] = 1  # Poate trebui să ajustezi valoarea în funcție de certitudinea măsurătorii

# Simulează date LIDAR
simulated_scan_data = [(1.0, angle) for angle in np.linspace(-np.pi/2, np.pi/2, 180)]

# Actualizează harta cu datele LIDAR simulate
update_map(simulated_scan_data, robot_position, robot_orientation)

# Vizualizează harta sau salvează-o într-un fișier
# Poți utiliza biblioteci precum matplotlib pentru vizualizare

# Continuă să deplasezi robotul și să actualizezi harta cu datele reale de la LIDAR în timp real
```
