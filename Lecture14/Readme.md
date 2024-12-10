Спочатку були проблеми зі встановленням mongo на vm. Підійшло таке рішення:

Vagrant.configure("2") do |config|
config.vm.box = "ubuntu/focal64"  # 20.04 LTS

config.vm.provider "virtualbox" do |vb|
vb.memory = "1024"  
vb.cpus = 2        
end

config.vm.provision "shell", inline: <<-SHELL
sudo apt update && sudo apt upgrade -y
wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | sudo apt-key add -
echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/4.4 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-4.4.list
sudo apt update
sudo apt install -y mongodb-org
sudo systemctl start mongod
sudo systemctl enable mongod
SHELL
end


1. Створення бази даних та колекцій:

use gymDatabase

db.createCollection("clients")
db.createCollection("memberships")
db.createCollection("workouts")
db.createCollection("trainers")

2. Визначення схеми документів і заповнення:

db.clients.insertMany([
{
client_id: 1,
name: "Ivan Koval",
age: 28,
email: "ivan.koval@ukr.net"
},
{
client_id: 2,
name: "Maria Ivanova",
age: 35,
email: "maria.ivanova@ukr.net"
}
])


db.memberships.insertMany([
{
membership_id: 1,
client_id: 1,
start_date: ISODate("2024-01-01T00:00:00Z"),
end_date: ISODate("2024-12-31T00:00:00Z"),
type: "Premium"
},
{
membership_id: 2,
client_id: 2,
start_date: ISODate("2024-02-01T00:00:00Z"),
end_date: ISODate("2024-11-30T00:00:00Z"),
type: "Basic"
}
])


db.workouts.insertMany([
{
workout_id: 1,
description: "Full body workout for beginners",
difficulty: "Low"
},
{
workout_id: 2,
description: "Advanced weight training",
difficulty: "High"
}
])


db.trainers.insertMany([
{
trainer_id: 1,
name: "Oleh Petrov",
specialization: "Fitness trainer"
},
{
trainer_id: 2,
name: "Anastasiya Shevchenko",
specialization: "Yoga instructor"
}
])


db.workouts.insertOne({
workout_id: 3,
description: "medium level",
difficulty: "medium"
})

Знайдіть всіх клієнтів віком понад 30 років:
db.clients.find({ age: { $gt: 30 } })
![Image1](images/age_.png)

Перелічіть тренування із середньою складністю:
db.workouts.find({ difficulty: "medium" })
![Image1](images/medium_d.png)

Покажіть інформацію про членство клієнта з певним client_id:
db.memberships.find({ client_id: 1 })
![Image1](images/infoForClient1.png)