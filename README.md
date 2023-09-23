# Hi, I'm Tobias Bonifay
_Student in 5th year of engineering school at [Polytech Nice](https://polytech.univ-cotedazur.fr)_<br>
_Specialized in Software Design_

## Who am I? 

An engineering student hailing from Nice, France. Currently, I am 22 years old and thriving to grasp every opportunity that can enhance my skills in Java.

I'm enthusiastic about any potential opportunities or projects that involve Java development.

### What I'm focusing on 

My insatiable curiosity drives me to constantly expand my knowledge base. I am particularly keen to refine my skills in software development tools such as Git, algorithms, and object-oriented programming.

```java
package world;

interface Human {
    void eat();
    void sleep();
}

interface CodingAbility {
    void code();
}

class Tobias implements Human, CodingAbility {

    private enum Pronoun {
        HE("he"), HIM("him");

        private final String pronoun;

        Pronoun(String pronoun) {
            this.pronoun = pronoun;
        }

        @Override
        public String toString() {
            return pronoun;
        }
    }

    private enum Language {
        JAVA("Java"), KOTLIN("Kotlin"), PYTHON("Python");

        private final String language;

        Language(String language) {
            this.language = language;
        }

        @Override
        public String toString() {
            return language;
        }
    }

    private static final String BRAIN_STATUS = "Always ready to learn and adapt";

    private final Pronoun[] pronouns = {Pronoun.HE, Pronoun.HIM};
    private final Language[] languages = {Language.JAVA, Language.KOTLIN, Language.PYTHON};

    @Override
    public void eat() {
        System.out.println("Eating healthy to stay productive!");
    }

    @Override
    public void sleep() {
        System.out.println("Getting enough sleep to stay refreshed!");
    }

    @Override
    public void code() {
        System.out.println("Coding with passion and efficiency!");
    }

    public void printDetails() {
        System.out.println("Pronouns: " + String.join(", ", (CharSequence[]) pronouns));
        System.out.println("Languages: " + String.join(", ", (CharSequence[]) languages));
        System.out.println("Brain Status: " + BRAIN_STATUS);
    }

    public static void main(String[] args) {
        Tobias tobias = new Tobias();
        tobias.eat();
        tobias.sleep();
        tobias.code();
        tobias.printDetails();
    }
}

```

---

---
