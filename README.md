# ts-angular-snippets-soygeekgirl README

DESARROLLA EN ANGULAR MÁS RAPIDO CON ESTOS ATAJOS

## Features

#### **Para HTML**

\_si
\_irc
\_ircf
ngfor \_for
ngforli \_forli
\_ifs

#### **TS**

**interface**
\_cfi crear interface a partir del nombre del fichero
\_ci crear interface a partir del texto seleccionado

**enum**
\_cfe crear enum a partir del nombre del fichero
\_ce crear enum a partir del texto seleccionado

**types**
\_cft crear type a partir del nombre del fichero
\_ct crear type a partir del texto seleccionado

**private variable constructor**
\_pv crear variable privada de solo lectura

**public variables**
\_puvb crear public var boolean
\_puvs crear public var string
\_puvn crear public var number
\_puva crear public var array

**TODO**
\_td

**CONDICIONALES**
\_c|
\_c&

## Known Issues

Tienes dudas, hay problemas ¿?, escribeme al [linkedin](https://www.linkedin.com/in/alexandra-jimenez-4b6459167/)

## Release Notes

Test de creación de atajos para html y ts

### 0.0.2

Se agregaron nuevos atajos para variables públicas, creación de interface, enum y types.
Se agregó una mini guía en el README para empezar en angular.

**_¡Gracias por usar ts-angular-snippets-soygeekgirl!_**

## **MINI GUIA PARA ANGULAR TS**

# **ANGULAR GUIA DE PRACTICAS COMUNES -PARA TRABAJAR EN EQUIPO-**

Luego de cometer ciertos errores al trabajar sola o incluso en equipo, me di cuenta que la forma de llevar una estabilidad (TRANQUILIDAD) mientras desarrollas o mantienes un proyecto, es que el código mantega ciertas reglas o estructura, por lo que he decidido crear esta pequeña guia o mini guia o pasos, para asi tener un estandar al escribir código y trabajar de forma más fluida, respetando y adoptando 'practicas' que se consideran al escribir un código limpio.

## **Usar Angular CLI**

[Angular CLI](https://cli.angular.io/) **Usemos Angular CLI** para generar los nuevos componentes, directivas, módulos, servicios y pipes.

#### Comandos CLI ANGULAR

```c
// Instalar Angular CLI
npm install -g @angular/cli@aqui_nros_de_la_version

// CHECK LA VERSION
ng version

// NUEVA APP
ng new nombre_de_la_app

// GENERAR ARTEFACTOS, COSAS, PARTES, COMPONENTES CON LA CLI
ng generate component|directive|module|service|pipe|library<nombre_del_componente>

//LO MISMO DE ARRIBA PERO CON ATAJO
ng g c nombre_del_componente
ng g s nombre_del_servicio
ng g m nombre_del_modulo
ng g d nombre_del_directiva
ng g p nombre_del_pipe
ng g lib nombre_lib
ng generate guard

// LEVANTAR EL PROYECTO
ng serve

//TEST
ng test

// INSTALAR PAQUETES
npm install nombre_del_paquete

// AÑADIR PAQUETES DESDE LA CLI, así en algunos casos viene configurado para usar de una vez con el proyecto, o al menos la importación
ng add @nombre_de_la_dependencia
```

## **Operadores**

**Optional chaining (?.)**

```ts
// objeto?.propiedad
const user = {
  name: "Juan",
  age: 30,
};
const address = user?.address;
```

**Operador ternario (? : ):)**
condición ? valorVerdadero : valorFalso

```ts
const isLoggedIn = true;
const message = isLoggedIn ? "Bienvenido" : "Inicia sesión";
```

**?? nullish coalescing**
Si el valor de la izquierda, es null o undefined devuelve lo de la derecha

```ts
const foo = null ?? "default string";
```

**! operador de aserción no nula**
Indica al compilador que una variable o expresión no puede ser nula o undefined.

```ts
@Input() public misDatos!: datos;
this.form.get('name')!.setValue('pancho');
```

**Destructuring assignment**

```ts
const user = {
  name: "Pedro",
  age: 35,
};

const { name, age } = user; // nombre será "Pedro" y edad será 35

const test = [1, 2, 3];

const [firts, second] = test; //1,2
```

## **Variables, funciones, métodos**

Usemos nombres descriptivos, que al leerlos infieras lo que hacen o lo que es , por alguna parte lei lo de los 5 seg para variables, (CUANDO SE TE CAE LA COMIDA , SI LA RECOGES EN ESTE TIEMPO ESTARAS BIEN, O ESO DICEN) , si te paras y lees el nombre de tu variable o método y en 5 segundo te cuesta SABER LO QUE HACE O LO QUE ES, entonces cambialo , si no, en el futuro no sabras lo que hace y a tu compañero le haces la vida cuadritos JAJAJA (L)

**boolean , que empiecen por is y sin negación, isValid , isDisabledSaveButton**

**Métodos**

getCurrentType() o getCurrentTypeById(id:number):void
Los métodos si no devuelven nada entonces tipado void, si no, el tipado que corresponda , o su DTO , en el caso de manipular datos.

Usa public o private , segun sea el caso

por ejemplo

```ts
private getCurrentType():void{

}
public getCurrentTypeById(id:number):void{

}
```

## **Constructor**

usa: private readonly _nombre: Componente
con el _ para el nombre que usaras

por ej this.\_servicio.metodo()

## **Interface**

Define estructuras de objetos con propiedades y métodos.
Permite una mayor flexibilidad y reutilización en la definición de tipos.

```ts
export interface UserInterface {
  text: string;
  age?: number;
}
let user: UserInterface;

interface User {
  name: string;
  email: string;
  age: number;

  greet(): string;
}

let user: User = {
  name: "Soy geekgirl",
  email: "soy@geekgirl.com",
  age: 30,
  greet() {
    return `Hi, i'm ${this.name}`;
  },
};
```

## **Enum**

Usemos para conjuntos de valores finitos y relacionados, como tipos de usuario, roles, estados, etc.
Ofrece mayor seguridad de tipos y legibilidad

```ts
export enum UserRole {
  Admin,
  Moderator,
  User,
}

let currentUserRole: UserRole = UserRole.Admin;

export enum TypeUserEnum {
  ADMIN = 1,
  BASIC = 3,
}

let otherCondition: boolean = false;
const isBasicUser: boolean = TypeUserEnum.BASIC && otherCondition;
```

## **Types**

Usemos alias para tipos complejos o primitivos, simplificando la sintaxis.
Adecuado para tipos que no necesitan lógica o propiedades adicionales.

```ts
export type myType = {
  type: "basic" | "admin";
};
let currentType: myType = {
  type: "basic",
};
```

## **Models como CLASS, INTERFACE O DTO?**

Usemos interface como DTO, para manipular las peticiones de datos, ya que la interface nos permite un contrato con los tipos y lo que tendremos, o lo que nos llega de respuesta, por ejemplo en una petición get, además de esta forma podemos aprovechar herramientas que permiten de forma rápida convertir un json a interface como RapidApi o JSON to TS. Seguro hay más, sin embargo estas son las que he probado y me funcionan de forma eficiente y puedo recomendar

```ts
export interface UserModel {
  //...
}
```

## **Nombrar ficheros/archivos o directorios/carpetas**

Mantener **Reglas** se vuelve muy importante para la mantener la legibilidad de código.
Usaremos guion ("**-**") para separar palabras dentro del _nombre_ del fichero y punto ("**.**") para separar el anterior del tipo de archivo. El patrón recomendado es:

```c
<nombre-largo>.<type>.ts|.css|.html

// Ejemplo
nombre-largo.component.ts
nombre-largo.enum.ts
nombre-largo.model.ts


```

## **Barrels**

**NOTA**--> ESTO LO COPIE DE LA GUIA QUE MENCIONO ABAJO , LO HABIA USADO EN UN PROYECTO CON VUEX, PERO DESCONOCIA QUE LA TÉCNICA SE LLAMA BARRELS.

Para ayudar a la organización del proyecto podemos utilizar conceptos como _"Barrels"_. La principal idea es agregar un archivo llamado "index.ts" para cada una de las carpetas que contengan un archivo .ts. Dentro de este se exportará cada una de las variables exportables de los .ts permitiendo crear una especie de jerarquía que nos va a ayudar a acortar largas cadenas de imports.

#### **Ejemplo:**

Supongamos 3 componentes diferentes dentro de `./app/modules/home/component`:

```ts
export class SomeComponent {}
export class SomeClass {}
export class SomeService {}
```

Agregando este barrel dentro de `./app/modules/home/component`

```ts
export * from "./some.model.ts";
export * from "./some.service.ts";
export { SomeComponent } from "./some.component.ts";
```

Ahora solo tendríamos que importar lo que necesitemos de este barrel

```ts
import { SomeComponent, SomeService, SomeClass } from "../some"; // index está implicito
```

## **Lazy Loading**

Carga solo los modulos que vas usando

```ts
import ...;

const routes: Routes = [
  { path: '', redirectTo: 'home', pathMatch: 'full' },
  { path: 'home', loadChildren: () => import('./modules').then( m => m.HomeModule ) },
  { path: '**', redirectTo: 'home' }
];

@NgModule({...})
export class AppRoutingModule { }
```

## **Angular Coding Style**

Puedes revisar la guia oficial[Angular Coding Style](https://angular.io/guide/styleguide):

1. Limitar **archivos a 400 líneas de código**, si se pasa debemos considerar separar en componentes más pequeños de esta forma es más facil hacer test y mantener el código.
2. Definir **funciones pequeñas** e intentar que solo cumpla su función.
3. Mantener las **reglas al declarar componentes, variables, funciones, etc** el nombre de las **propiedades y los métodos** deben **SIEMPRE** en minúsculas y **camelCase**
4. **Siempre dejar un salto de línea entre los imports** y los módulos como así también entre las importaciones de terceros y de los módulos personalizados.
5. **Utilizar prefijos personalizados** En determinados casos esto puede ser buena practica, si el componente tiene nombre similar a otro, o a un componente nativo hace falta para prevenir que los nombres de los elementos no entren en conflicto .
6. Seguir en mayor medida el **principio de Single Responsibility**.
7. No usar **namespaces** DIRAS WTF--> revisa la guia de estilos de google

**Mis referencias**
[GUIA DE ESTILO OFICIAL DE ANGULAR](https://angular.io/guide/styleguide)
[GUIA DE ESTILO GOOGLE ANGULARJS](https://google.github.io/styleguide/angularjs-google-style.html)
[GUIA DE ESTILO GOOGLE TS](https://google.github.io/styleguide/tsguide.html)
[github.com/USpiri/angular-guideline](https://github.com/USpiri/angular-guideline/blob/main/README.md)
[GUIA DE ESTILO GOOGLE TS](https://google.github.io/styleguide/tsguide.html)

## For more information

@soygeekgirl [Linkedin](https://www.linkedin.com/in/alexandra-jimenez-4b6459167/)
**Enjoy!**
