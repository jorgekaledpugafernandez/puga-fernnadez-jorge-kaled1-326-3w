![image](https://github.com/user-attachments/assets/5df54d2f-3528-4f66-983c-edd687e826f2)
![image](https://github.com/user-attachments/assets/b6bfe0fd-ffb6-4dcb-b0ee-a937f426c311)


class Persona:
    def __init__(self, nombre="", edad=0, direccion=""):
        self.nombre = nombre
        self.edad = edad
        self.direccion = direccion

class Cuenta:
    def __init__(self, titular, cantidad=0.0):
        if not isinstance(titular, Persona):
            raise ValueError("El titular debe ser una instancia de la clase Persona")
        self.__titular = titular
        self.__cantidad = cantidad

    # Getters y Setters con validación
    @property
    def titular(self):
        return self.__titular

    @property
    def cantidad(self):
        return self.__cantidad

    # Método mostrar
    def mostrar(self):
        print(f"Titular: {self.__titular.nombre}, Cantidad: {self.__cantidad}")

    # Método ingresar
    def ingresar(self, cantidad):
        if cantidad > 0:
            self.__cantidad += cantidad

    # Método retirar
    def retirar(self, cantidad):
        self.__cantidad -= cantidad

# Ejemplo de uso
persona = Persona(nombre="jorge puga", edad=30, direccion="cbtis 128")
cuenta = Cuenta(titular=persona)
cuenta.mostrar()

cuenta.ingresar(1000.50)
cuenta.mostrar()

cuenta.retirar(200.75)
cuenta.mostrar()
