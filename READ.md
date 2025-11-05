# UT0201 – Prácticas DI

# Guía git

Colócate en el repo Si te dice not a git repository, no es un repo (clónalo o haz git init).

cd C:\ruta\al\repo
git status

Ver ramas y en cuál estás

git branch # ramas locales (el \* indica la activa)
git branch -vv # ramas locales + tracking
git branch -a # locales + remotas

Crear y cambiar a una rama nueva
git switch -c tema2_01

# (equivalente clásico: git checkout -b tema2_01)

Si la rama ya existe y sólo quieres cambiarte:
git switch tema2_01

Añadir cambios y hacer commit
git status # ver cambios
git add . # añadir todo (o: git add ruta\archivo)
git commit -m "feat: mensaje corto y claro"

Si te pide user/email:
git config --global user.name "Tu Nombre"
git config --global user.email "tu@correo.com"

Subir la rama al remoto (GitHub)

Primera vez que subes esa rama:

git push -u origin tema2_01

Siguientes veces (ya tiene upstream):

git push

5. Actualizar tu rama con lo último del remoto

(útil antes de mergear)

git fetch origin # trae refs nuevas
git pull --rebase origin main # rebasea tu rama sobre main (opcional)

Alternativa simple: git pull (merge), pero el rebase deja un historial más limpio.

6. Unir tu rama en main (merge)

Cambia a main y actualízala:

git switch main
git pull # baja lo último del remoto

Merge de tu rama (desde main):

git merge tema2_01

# si hay conflictos: edita archivos, marca como resueltos y:

git add .
git commit # completa el merge

Sube main actualizado:

git push

7. Borrar la rama de feature (opcional)

Local:

git branch -d tema2_01 # -D si Git no te deja (forzado)

Remoto:

git push origin --delete tema2_01

8. Renombrar una rama (local y remoto)
   git branch -m nombre_nuevo # renombra la rama actual
   git push -u origin nombre_nuevo # publica con el nuevo nombre

# (opcional) borra la vieja en remoto si existía

git push origin --delete nombre_viejo

9. Ver historial y cambios
   git log --oneline --graph --decorate --all # historial compacto
   git show HEAD # último commit
   git diff # diff sin stage
   git diff --staged # diff staged

10. Deshacer rápido (por si te lías)

Quitar un archivo del stage (antes del commit):

git restore --staged ruta\archivo

Volver un archivo a como estaba en el último commit:

git restore ruta\archivo

Deshacer el último commit (manteniendo cambios en working dir):

git reset --soft HEAD~1

Guardar cambios “en el bolsillo” temporalmente:

git stash
git stash pop
