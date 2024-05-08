![Captura de pantalla 2024-05-07 122750](https://github.com/M-VictoriaCM/Seminario-de-Flutter/assets/70769530/9ac62563-914d-4526-a694-fb195a3e4a65)

>[!IMPORTANT]
>- Instalacion de software de desarrollo
>- Git
>- Android Studio
>- Visual Studio 2022 (Desktop development with C++) (opcional- desarrollo desktop windows)
>- Visual Studio Code
>- Flutter extension for vscode

![image](https://github.com/M-VictoriaCM/Seminario-de-Flutter/assets/70769530/9c582cc2-7efc-4f29-b021-8cd9403d57d2)

# Hola Mundo

Cada aplicación requiere la función **main()** de nivel superior, donde comienza la ejecución. Las funciones que no devuelven explícitamente un valor tienen el tipo de retorno **void**. Para mostrar texto en la consola, puede usar la función **print()**:

```dart
void main(){
    print(Hola, Mundo!);
}
```

# Variables

Incluso en el código Dart con seguridad de tipos, se pueden declarar la mayoría de las variables sin especificar explícitamente su tipo usando **var**. Gracias a la **inferencia de tipos**, los tipos de estas variables están determinados por sus valores iniciales:

```dart
String nameSinInferencia= 'Voyager I';
var name= 'Voyager I';
var year = 1977;
var antennaDiameter = 3.7;
var fybyObjets = ['Jupiter', 'Saturn', 'Uranus', 'Neptune'];
var image={
      'tags': ['saturn'],
      'url' : '//path/to/saturn.jpg'
}
```

# Declaraciones de flujo de control
## Sentencia de control:

```dart
if(year >=2001){
    print('21st century');
  }else if(year>=1901){
    print('20th century');
  }
}
```
```dart
for(final object in flybyObjects){
  print(object);
}
```
```dart
for(int month=1; month<=12; month++){
  print(month);
}
```
```dart  
while(year<2016){
  year +=1;
}
```
# Final en bucle for sobre colección:

Se prefiere final en la variable de bucle si la referencia no se reasigna.
Evita reasignaciones accidentales y permite optimizaciones.

>[!CAUTION]
>
> **Mala Práctica**
>  ```dart
>  for(var element in elements){//lint
>    print('Element: $element');
>  }
>  ```

>[!TIP]
>
> **Buena Práctica**
> ```dart
>  for(final element in elements){
>     print('Element: $element');
>  }
> ```

# Funciones

Se recomienda especificar los tipos de argumentos de cada función y el valor de retorno.

## Funcion fibonacci:

```dart
int fibonacci(int n){
  if(n ==0 || n == 1){
      return n;
  }else{
      return fibonacci(n - 1) + fibonacci(n - 2);
  }
var result = fibonacci(20);
}
```
Una sintaxis abreviada => (flecha) es útil para funciones que contienen una sola declaración.

# Funciones anónimas como argumentos:
```dart
flybyObjects.where((name)=>name.contains('turn)).forEach(print);
```

# Clases/Objetos

La clase es un molde de objetos y una fábrica para instanciar objetos. Un objeto es la mínima unidad computacional que encapsula estado y comportamiento.

## Ejemplo(1/2"):

```dart
class Spacecraft{
  String name; //propiedad no nula
  DateTime? launchDate; //propiedad nula

  int? get launchYear => launchDate?.year;
  Spacecraft(this.name,this.launchDate){
    Spacecraft.unlaunched(String name):
        this(name, null);
  }
}
```
## Ejemplo(2/2)

```dart
void describe(){
  print('Spacecraft: $name');
  var launchDate =this.launchDate;
  if(launchDate != null){
    int years = DateTime.now().difference(launchDate).inDays~/365;
    print('Launched: $launchYear ($years years ago)');
  }else{
    print('Unlaunched');
  }
}

void main(){
  var voyager = Spacecraft('Voyager I', DateTime(1997, 9, 5));
  voyager.describe();
  var voyager3 = Spacecraft.unlaunched('voyager III);
  voyager3.describe();
}
```
# Propiedades privadas

La accesibilidad de una propiedad es pública. Para que sea privada, se debe anteponer a su nombre un guión bajo(_): 

## Getters y Setters
```dart
class MyClass{
  int _aProperty =0;
  int get aProperty => _aProperty;

  set aProperty(int calue){
    if(value >= 0 ){
      _aProperty = value;
    }
  }
}
```
## Propiedad calculada:

```dart
class MyClass{
  final List<int> _value =[];

  void addValue(int value){
    _value.add(value);
  }
  int get count{
    return _values.length;
  }
}
```

# Parámetros posicionales opcionales:

Los parámetros posicionales son opcionales si en declaran entre []

## Posicionales obligatorios
```dart
int sumUp(int a, int b, int c){
  return a + b + c;
}
int total= sumUp(1, 2, 3);
```
## Posicionales opcionales con y sin valor por defecto
```dart
int sumUpToFive(int a, [int? b, int? c, int? d, int e=5]){
  int sum = a + e;
  if(b != null) sum += b;
  if(c != null) sum += c;
  if(d != null) sum += d;
    return sum;
}
int total = sumUpToFiver(1, 2);
```

# Parámetros por nombre:

```dart
void printName(String firstName, String lastName, {String? middleName}){
  print('$firstName ${middleName ?? ''} $lastName');
}

void main(){
  printName('Dash', 'Dartisan');

  printName('John', 'Smith', middleName: 'Who');
  printName('John', middleName: 'Who', 'Smith');
}



