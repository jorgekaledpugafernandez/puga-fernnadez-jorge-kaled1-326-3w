![image](https://github.com/user-attachments/assets/883565e8-a4a2-44d1-bde4-6e08510059f0)
![image](https://github.com/user-attachments/assets/4c423b56-c367-4567-89b2-888e5728be64)
![image](https://github.com/user-attachments/assets/503d7988-c308-4017-aede-e9dbf5e134e1)

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

    @property
    def titular(self):
        return self.__titular

    @property
    def cantidad(self):
        return self.__cantidad

    def mostrar(self):
        print(f"Titular: {self.__titular.nombre}, Cantidad: {self.__cantidad}")

    def ingresar(self, cantidad):
        if cantidad > 0:
            self.__cantidad += cantidad

    def retirar(self, cantidad):
        self.__cantidad -= cantidad

class CuentaJoven(Cuenta):
    def __init__(self, titular, cantidad=0.0, bonificacion=0):
        super().__init__(titular, cantidad)
        self.__bonificacion = bonificacion

    @property
    def bonificacion(self):
        return self.__bonificacion

    @bonificacion.setter
    def bonificacion(self, value):
        if isinstance(value, (int, float)) and 0 <= value <= 100:
            self.__bonificacion = value
        else:
            raise ValueError("La bonificación debe ser un número entre 0 y 100")

    def esTitularValido(self):
        return 18 <= self.titular.edad < 25

    def mostrar(self):
        print(f"Cuenta Joven\nTitular: {self.titular.nombre}, Cantidad: {self.cantidad}, Bonificación: {self.bonificacion}%")

    def retirar(self, cantidad):
        if self.esTitularValido():
            super().retirar(cantidad)
        else:
            print("El titular no es válido para retirar dinero de la Cuenta Joven.")

# Ejemplo de uso
persona = Persona(nombre="jorge puga", edad=16, direccion="cbtis 128")
cuenta_joven = CuentaJoven(titular=persona, cantidad=500.0, bonificacion=10)
cuenta_joven.mostrar()

cuenta_joven.ingresar(200.0)
cuenta_joven.mostrar()

cuenta_joven.retirar(150.0)
cuenta_joven.mostrar()

persona2 = Persona(nombre="joreg puga", edad=16, direccion="cbtis 128")
cuenta_joven_no_valida = CuentaJoven(titular=persona2, cantidad=500.0, bonificacion=10)
cuenta_joven_no_valida.mostrar()

cuenta_joven_no_valida.retirar(150.0)
cuenta_joven_no_valida.mostrar()
