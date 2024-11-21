![image](https://github.com/user-attachments/assets/cee1ace6-273b-4646-aa3a-e7cac60f8b59)

# puga-fernnadez-jorge-kaled1-326-3w
class Persona:
    def __init__(self, nombre="", edad=0, direccion=""):
        self._nombre = nombre
        self._edad = edad
        self._direccion = direccion

    # Setters y Getters con validación
    @property
    def nombre(self):
        return self._nombre

    @nombre.setter
    def nombre(self, value):
        if isinstance(value, str):
            self._nombre = value
        else:
            raise ValueError("El nombre debe ser una cadena de caracteres")

    @property
    def edad(self):
        return self._edad

    @edad.setter
    def edad(self, value):
        if isinstance(value, int) and value >= 0:
            self._edad = value
        else:
            raise ValueError("La edad debe ser un número entero positivo")

    @property
    def direccion(self):
        return self._direccion

    @direccion.setter
    def direccion(self, value):
        if isinstance(value, str):
            self._direccion = value
        else:
            raise ValueError("La dirección debe ser una cadena de caracteres")

    # Método mostrar
    def mostrar(self):
        print(f"Nombre: {self._nombre}, Edad: {self._edad}, Dirección: {self._direccion}")

    # Método esMayorDeEdad
    def esMayorDeEdad(self):
        return self._edad >= 18

# Ejemplo de uso
persona = Persona()
persona.nombre = "jorge puga"
persona.edad = 16
persona.direccion = "cbtis128"
persona.mostrar()
print("Es mayor de edad:", persona.esMayorDeEdad())
