# Hi, I'm Tobias Bonifay
_Old student in engineering school at [Polytech Nice](https://polytech.univ-cotedazur.fr)_<br>
_Specialized in Software Design_

## Who am I? 

An engineering student hailing from Nice, France. Currently, I am 23 years old and thriving to grasp every opportunity that can enhance my skills in Java.

I'm enthusiastic about any potential opportunities or projects that involve Java development.

### What I'm focusing on 

My insatiable curiosity drives me to constantly expand my knowledge base. I am particularly keen to refine my skills in software development tools such as Git, algorithms, and object-oriented programming.

```java
package io.github.tobiasbonifay;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.*;

import java.util.*;
import java.util.concurrent.CompletableFuture;
import java.util.stream.Collectors;

@SpringBootApplication
@RestController
@RequestMapping("/api/tobias")
public class TobiasProfile {

    private static final List<String> SKILLS = Arrays.asList(
        "Java", "Spring Boot", "Angular", "Vue.js", "Python", "SQL", "Git"
    );

    private static final Map<String, String> EXPERIENCES = Map.of(
        "EVIDEN SLOVAKIA", "Full-Stack Software Engineer",
        "EVIDEN FRANCE", "Java Swing Software Engineer",
        "ATOS", "Java Backend Software Engineer Intern",
        "CSI CONSOLIDATED", "System Administrator Intern"
    );

    public sealed interface ProjectStatus 
        permits InProgress, Completed, Planned {}
    public record InProgress(int percentageComplete) implements ProjectStatus {}
    public record Completed(String completionDate) implements ProjectStatus {}
    public record Planned(String plannedStartDate) implements ProjectStatus {}

    public record Project(String name, String description, ProjectStatus status) {}

    public String getProjectStatusDescription(ProjectStatus status) {
        return switch (status) {
            case InProgress p -> "In progress: " + p.percentageComplete() + "% complete";
            case Completed c -> "Completed on: " + c.completionDate();
            case Planned p -> "Planned to start on: " + p.plannedStartDate();
        };
    }

    @GetMapping("/info")
    public Map<String, Object> getProfileInfo() {
        Map<String, Object> profile = new HashMap<>();
        profile.put("name", "Tobias Bonifay");
        profile.put("role", "Junior Software Engineer with Architecture specialty");
        profile.put("location", "Nice, France");
        profile.put("skills", SKILLS);
        profile.put("experiences", EXPERIENCES);
        return profile;
    }

    @GetMapping("/projects")
    public CompletableFuture<List<Project>> getProjects() {
        return CompletableFuture.supplyAsync(() -> List.of(
            new Project("MUSIC DSL", "Domain Specific Language, Java - Midi - ANTLR", new Completed("2024-01-15")),
            new Project("CONNECT 4", "AWARD TEAM POLYTECH NICE (Angular, Node.js)", new InProgress(75)),
            new Project("ECO BIKING", "C#, SOAP", new Planned("2024-09-01"))
        ));
    }

    @PostMapping("/contact")
    public String contact(@RequestBody String message) {
        // Simulating contacting logic
        return "Thanks for reaching out! I'll get back to you soon regarding: " + message;
    }

    private static final String WELCOME_MESSAGE = """
        Welcome to Tobias Bonifay's profile!
        Here you can find information about my skills, experiences, and projects.
        Feel free to explore the API endpoints:
          - GET /api/tobias/info
          - GET /api/tobias/projects
          - POST /api/tobias/contact
        """;

    public static void main(String[] args) {
        SpringApplication.run(TobiasProfile.class, args);
        System.out.println(WELCOME_MESSAGE);
        
        var sortedSkills = SKILLS.stream()
            .sorted()
            .collect(Collectors.toList());
        
        List<String> upperCaseSkills = SKILLS.stream()
            .map(String::toUpperCase)
            .toList();

        System.out.println("Sorted skills: " + String.join(", ", sortedSkills));
        System.out.println("Uppercase skills: " + String.join(", ", upperCaseSkills));

        Optional.of("Java").ifPresentOrElse(
            lang -> System.out.println("Favorite language: " + lang),
            () -> System.out.println("No favorite language specified")
        );
    }
}

```

---

---
