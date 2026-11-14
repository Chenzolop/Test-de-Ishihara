# Test de Ishihara: generar el APK

## Requisitos (una sola vez)
1. Node.js 20 o superior: https://nodejs.org
2. Android Studio (trae el SDK de Android y el JDK): https://developer.android.com/studio

## Pasos
En una terminal, dentro de esta carpeta:

    npm install
    npx cap add android
    npx cap sync android
    npx cap open android

En Android Studio espera a que termine de sincronizar (Gradle) y ve a:
Build > Build Bundle(s) / APK(s) > Build APK(s)

El archivo queda en:
android/app/build/outputs/apk/debug/app-debug.apk

## Alternativa por línea de comandos
(con ANDROID_HOME configurado y JDK 21)

    npm install
    npx cap add android
    npm run apk

## Instalar en el celular
Copia el .apk al teléfono y ábrelo (hay que permitir «instalar apps de origen desconocido»),
o conecta el teléfono con depuración USB y ejecuta: adb install app-debug.apk

## Cambios futuros
Edita www/index.html y ejecuta de nuevo: npx cap sync android

## Compilar con GitHub (sin instalar Android Studio)
1. Crea un repositorio nuevo en github.com (vacío, sin README).
2. En una terminal dentro de esta carpeta:

       git init
       git add .
       git commit -m "Test de Ishihara"
       git branch -M main
       git remote add origin https://github.com/TU_USUARIO/TU_REPO.git
       git push -u origin main

3. En GitHub abre la pestaña Actions: el flujo «Build APK» arranca solo (tarda unos 5 min).
4. Cuando termine, entra a la ejecución y descarga «test-ishihara-apk» en la sección Artifacts.
   Dentro del zip está app-debug.apk.

Para recompilar después de un cambio, haz push de nuevo o pulsa «Run workflow» en Actions.
