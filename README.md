# Apunts Sass

[Oficial Sass website](https://sass-lang.com/)

[Sass a Bootstrap](https://getbootstrap.com/docs/5.3/customize/sass/)

Sass és un preprocessador de CSS. Això significa que Sass proporciona funcionalitat de llenguatge de programació a CSS. Els fitxers amb els que treballa Sass són fitxers de tipus *.scss*.

Una vegada tenim el nostre fitxer *.scss*, el que hem de fer és compilar-lo per convertir-lo en un fitxer *.css*. Alguns dels compiladors que existeixen són *Node-sass*, *Dart Sass* i *libSass*. Més que compiladors, són *transpilers*, que transformen codi font en codi font d'un altre llenguatge.

*Sass* és un llenguatge que està basat en *Ruby*.

## Instal·lació
M'he instal·lat el paquet *libSass* en un entorn virtual amb `pip install libsass`. L'executable que em genera és `pysassc.exe`:

```bash
$ ls .venv/Scripts/
activate      Activate.ps1    pip.exe*      pip3.exe*     python.exe*
activate.bat  deactivate.bat  pip3.12.exe*  pysassc.exe*  pythonw.exe*
```

I per compilar:

```bash
$ pysassc helloworld.scss helloworld.css
```

## Customitzar Bootstrap amb Sass

### Colors a Bootstrap

Bootstrap té una paleta de colors molt àmplia però fa servir un subconjunt molt més petit d'aquesta paleta per generar els seus esquemes de colors. Aquest subconjunt de colors estan reunits en forma d'un `map` de *Sass* (`scss/_variables.scss`):

```scss
$theme-colors: (
  "primary":    $primary,
  "secondary":  $secondary,
  "success":    $success,
  "info":       $info,
  "warning":    $warning,
  "danger":     $danger,
  "light":      $light,
  "dark":       $dark
);
```

Totes les variables a Bootstrap estan definides amb el *flag* `!default` per a que sigui possible modificar-es sense modificar directament el codi font de Bootstrap:

```scss
// scss-docs-start theme-color-variables
$primary:       $blue !default;
```

#### Prova 1. Modificar els colors del *theme-color* directament, amb valors fixes

He de modificar els valors de les variables que conformen el *theme-color* al meu *custom.scss*:

```scss
// Include any default variable overrides here (though functions won't be available)

$primary: #684e9b;
$secondary: #86688f;
$success: #90cf09;
$info: #09cf72;
$warning: #c309cf;
$danger: #cf6309;
$light: #09cfc9;
$dark: #939e9d;

@import "../bootstrap/scss/bootstrap";
```

Després, compilem amb `libsass`:

```bash
$ pysassc scss/custom.scss css/customs.css
```

i fem servir `customs.css` al nostre *html*:

```html
<link rel="stylesheet" href="css/customs.css">
```

