# PRODUCTION RUN STEPS
# 1. Запустить dev-сервер (в одном ерминале) 
python run.py
# 2. Экспортировать данные (создаёт PORTFOLIO/ со всеми данными и скриншотами. Без него Docker нечего копировать)
python DOCKER/export_portfolio.py
# 3. Потом собрать Docker
docker compose up --build -d

# WIN DEV RUN
python run.py
python ultra_fast_builder.py
# PROD RUN
docker compose up -d
docker compose down
docker compose up -d --build
docker compose build --no-cache


winget install Bitwarden.SecretsManager
pip install -r requirements.txt

# 1. Запустите сервер
python run.py

# 2. В другом терминале проверьте порты
netstat -ano | findstr 5999
netstat -ano | findstr 35729
# (должны показать LISTENING)
 
# 3. Вернитесь в первый терминал, нажмите Ctrl+C
 
# 4. Снова проверьте
netstat -ano | findstr 5999
netstat -ano | findstr 35729
    
# RECOVERY
git log --oneline -n 5

Copy-Item .env $env:TEMP\.env.backup
git reset --hard 80f714fc
git clean -fd
Copy-Item $env:TEMP\.env.backup .env -Force
git push origin master --force
python run.py

# UPDATE
git add .
git commit -m "v0.0.1 - added screenshots"
git push

# DEV LOG
v0.0.1 - added screenshots