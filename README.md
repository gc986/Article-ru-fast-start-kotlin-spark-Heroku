<h1>Статья: быстный старт kotlin+spark+Heroku</h1>

<i>Изначально хотел разместить статью на Habr-е, но в итоге отказался от этогот, т. к. статейка оказалась небольшой, это скорее даже интенсивная пятиминутка.</i>

Обычно, я разрабатываю приложения для смартфонов, но недавно потребовалось написать простой REST API и разместить его на публичном хостинге Heroku. В данном материале я подробно расскажу и покажу как сделать собственное, очень простое, серверное приложение за 15 минут и разместить его.

Сначала создаём Maven проект в  IntellijIdea CE, используя шаблон kotlin-archetype-jvm
<img src="images/1.png" alt="Создание проекта в IntellijIdea">

Далее указываем имя проекта и место его расположения (я назвал проект Hellohabrahabr).

Переходим в pom.xml, чтобы внести необходимые изменения.
Во первых, чтобы проект собирался в независимый JAR файл (со всеми зависимостями), добавляем необходимый плагин, в блок \<plugins\>:
<i>
<pre>
<plugin>
    <groupId>org.apache.maven.plugins</groupId>
    <artifactId>maven-assembly-plugin</artifactId>
    <version>3.2.0</version>
    <executions>
        <execution>
            <id>make-assembly</id>
            <phase>package</phase>
            <goals> <goal>single</goal> </goals>
            <configuration>
                <archive>
                    <manifest>
                        <mainClass>ru.gc986.HelloKt</mainClass>
                    </manifest>
                </archive>
                <descriptorRefs>
                    <descriptorRef>jar-with-dependencies</descriptorRef>
                </descriptorRefs>
            </configuration>
        </execution>
    </executions>
</plugin>
</pre>
</i>