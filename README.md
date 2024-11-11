# Kafka ve Zookeeper Kurulumu ve Testi

Bu proje, Docker konteynerlerinde Kafka ve Zookeeper kurulumunu ve testini Ansible kullanarak gerçekleştirmektedir.

## Bilgisayarınız Windows ise Ansible yüklemek için bu adımları izleyebilirsiniz..
# WSL (Windows Subsystem for Linux) Kurulumu:
- Windows arama çubuğuna “Windows Features” yazın ve “Turn Windows features on or off” seçeneğini seçin.
- “Windows Subsystem for Linux” kutusunu işaretleyin ve bilgisayarınızı yeniden başlatın.
- Microsoft Store’dan Ubuntu’yu indirin ve kurun.
# Ansible Kurulumu:
- Ubuntu terminalini açın ve aşağıdaki komutları sırasıyla çalıştırın:
        - sudo apt update
        - sudo apt install ansible



## Docker konteynerlerini başlatmak için aşağıdaki komutu çalıştırın:

    docker-compose up -d

## Kafka ve Zookeeper kurulumunu gerçekleştirmek için:

    ansible-playbook -i hosts.ini kafka_setup.yml

## Test topic oluşturmak için:

    ansible-playbook -i hosts.ini create_topic.yml

## Topic’leri Test Etme
    Docker konteynerine bağlanın:

        docker exec -it ubuntu1 /bin/bash

# Topic’leri listelemek için:

    /opt/kafka/bin/kafka-topics.sh --list --bootstrap-server localhost:9092

# Topic’e mesaj göndermek için:

    echo "Hello, Kafka!" | /opt/kafka/bin/kafka-console-producer.sh --broker-list localhost:9092 --topic test-topic

# Topic’ten mesaj okumak için:

    /opt/kafka/bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic test-topic --from-beginning

## Kod hakkında daha detaylı bilgi için  --> MoreDetail_Code.ipynb
