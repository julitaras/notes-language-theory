<h1 align="center">TDL - Clase I</h3>

## [Clase grabada](https://drive.google.com/file/d/1jpKg5FeMaOHDi2LlISByVO6N5mLi4K-1/view)

Objetivo:
- Entender a la programación como conceptos
- Entender a los lenguajes por los conceptos que tienen

**Como? - Analizar los lenguajes de programacion**
- A traves de su sintaxis y su semantica
	- Sintaxist
		- Como se escribe - Estructura o forma de los programas
	- Semantica:
		- Como se ejecuta

Vamos a utilizar --> lenguaje Oz

---

Modelo computacional
- Sistema formal que define **como** se ejecutan los calculos
- Se define en terminos de los conceptos que incluye.
- Definicion mas precisa de un paradigma de programacion
- Declarativo - Imperativo
	- **Declarativo:** Uno habla del QUE. --> Por ejemplo: SQL.  Algo muy fuerte es la inmutalidad.
	- **Imperativo:** Tiene que ver con las instrucciones. Uno habla del COMO. Ejemplo: Una receta, ya que se esta diciendo COMO hacerlo.

Determinismo --> Ante un mismo input tengo que tener el mismo output. --> Caracterista de programacion funcional.

**Que es un lenguaje de programacion?**
Se dice que es un lenguaje de programacion si es **turing completo**
Si puede ser procesado por la maquina que turing hizo.

- Sintaxis
- Semantica
- Pragmatica


`Mozart` --> Implementacion de `Oz`

Tarea para el hogar:
- Instalar Mozart y Oz
- Bajarse emacs

---
## Acerca del lenguaje `oz`:
### Hello world:
```oz
{Browse 'Hello world!'}
```

> Ejecuto el buffer haciendo feed.
> Oz --> Feed buffer
> Shortcut --> control (^) + `.` + `b`

### Variables
- Variables de simple asignacion, no mutan
- Una variable no es mas que un nombre de algo, representa el nombre de un valor
- La vraible siempre empieza con mayuscula
- Tipado es dinamico.
```oz
declare A B C
A = 4
B = 5 
C = A*B + 3
{Browse C}
```

 #### Scopes
 - En donde existe esa variable. En donde vive
 - Dos tipos de scopes:
	 - Globales
	 - Locales

```oz
local A B C in
	A = 4
	B = 5 
	C = A*B + 3
	{Browse C}
end 
```

> No usar `declare` nunca

- Se puede tener un local dentro de otro, puedo re declarar variables

```oz
local A B C in
	A = 4
	B = 5 
	local A in
		A = 10
		C = A*B + 3
		{Browse C}
	end
	{Browse C}
end 
```


```oz
local Uno Dos in
	Uno = 1
	2 = Dos
	{Browse Uno + Dos}
end 
```

2 $\Leftrightarrow$ Dos

### Funciones

```oz
local Mayor A B M in
	fun {Mayor X Y}
		if (X > Y) then
			X 
		else
			Y 
		end
	end 
	A=30
	B=20
	M={Mayor A B}
	{Browse M}
end
```
- Variables y funciones estan al mismo nivel
	- Funciones: Ciudadanos de primera clase. Como si fuera "un tipo mas de dato"

Otra sintaxis:
```oz
local Mayor A B M in
	Mayor = fun {$ X Y}
		if (X > Y) then
			X 
		else
			Y 
		end
	end 
	A=30
	B=20
	M={Mayor A B}
	{Browse M}
end
```
`$` en la funcion, vendria a representar una funcion $\lambda$

- La variables no necesariamente mutan
- Las funciones son variabes que tienen guardado otro tipo de valor

### Expression vs Statement
- **Statement** --> A= 30 es un statemente , M={Mayor A B} es un statemente
	- Es cualquier bloque o instreucccion que no devuelve valor
- **Expression** algo que devuelve valor. Algop que es asignable a una variable.

Las funciones no tienen return.
Las funciones devuelven a ultima expresion.

## Records
- Estructura de datos para agrupar referencias

```oz
tree(key:I value:Y left:LT right:RT)
```

`Etiqueta (label)` --> `tree`

`Caracteristica (features)` --> `key, value, left, rigth`

```oz
local Arbol in
	Arbol = tree(key: 1 value: 8 left: nil right: nil)
	
	{Browse Arbol}
	{Browse Arbol.value}
end
```

```oz
local Alumno E in
	E = 20
	Alumno = persona(nombre: 'Nombre' apellido: 'Apellido' edad: E)
	
	{Browse Alumno}
	{Browse {Label Alumno}}
	{Browse {Width Alumno}}
	{Browse {Arity Alumno}}
end
```

**arity** --> Lista de features que tiene el record. En este caso `[apellido edad nombre]`

**width** --> Cantidad de cosas que tiene. En este caso `3`

**label** --> Nombre de el record. En este caso `persona`


## Tuplas
- Es un record cuyos features son numericos comenzando por el 1.
```oz
local Alumno E in
	E = 20
	Alumno = persona('Nombre' 'Apellido' E)
	
	{Browse Alumno}
end
```

En caso de pedirle a la tupla los features va a decir que es `[1 2 3]`

## Binding
- Asignale un valor a una variable

## Lista 
- Una tupla de dos elementos
- El primer elemento es el primer
- El segundo elemento es el resto de la cola

```oz
local L1 L2 in
	L1 = [1 2 3 4 5 6]
	L2 = 1|2|3|4|5|6|
	
	{Browse L1}
	{Browse L2}
	{Browse L1.1} %Cabeza, primer elemento%
	{Browse L2.1}
	{Browse L1.2} %Resto de la cola%
	{Browse L2.2} 
	{Browse L.2.2.2.1} %Acceder a 5to elemento%
end
```

## Pattern Matching
- Trata de matchear un record por el with, label y features.
- Es una manera de acceder a los campos de una estructura de datos y obtener los valores.

Ejemplo:
```oz
local Alumno E EdadAlumno in
	EdadAlumno = fun {$ Alumno}
		case Alumno of
			persona(nombre: N apellido: A edad: E) then
			E
		else
			0
		end
	end

	Alumno = persona(nombre:'Roberto' apellido:'Apellido' edad : E)
	Alumno.edad = 78
	{Browse Alumno}

	{Browse {EdadAlumno Alumno}}
end
```
> EdadAlumno se encarga de devolver la edad del alumno en caso de que matchee el record. Es decir, en caso de que contenga esos mismos

# Ejercicios

1. Devolver el maximo de la lista de enteros
2. A partir de una lista de numeros devolver una lista de los valores absolutos