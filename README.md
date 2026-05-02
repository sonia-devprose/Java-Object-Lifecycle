In Java, the **object lifecycle** has three main phases: **creation → use → destruction (garbage collection)**, and **reference variables are tightly tied to each phase** because they control how and when the object is reachable and therefore “alive.” [scientecheasy](https://www.scientecheasy.com/2020/06/life-cycle-of-object-in-java.html/)
<img width="2816" height="1536" alt="Gemini_Generated_Image_w6csjbw6csjbw6cs" src="https://github.com/user-attachments/assets/5b18350d-df05-4ff6-937b-2208e61fbae0" />


### Phases of the object lifecycle and where reference variables fit

1. **Creation (new + reference)**  
   - `new ClassName()` allocates memory for the object on the **heap**.  
   - A **reference variable** (on the stack or in an object field) stores the reference (like an address) to that heap object.  
   For example:
   ```java
   Person p = new Person("Alice");
   ```
   Here `p` is the reference variable that “starts” the object’s lifecycle by holding the key to the object. [procodebase](https://procodebase.com/article/understanding-the-java-object-lifecycle)

2. **Use (being reachable)**  
   - As long as there is at least one **strong reference** (like `p`, or a field in another object, a static variable, etc.) pointing to the object, the object is **reachable** and alive.  
   - Reference variables are the “handles” you use to call methods, access fields, or pass the object around:
     ```java
     p.getName();        // using the object via its reference
     someList.add(p);    // another reference now also points to the object
     ```  
   The object is considered “in‑use” while such references exist. [en.wikibooks](https://en.wikibooks.org/wiki/Java_Programming/Object_Lifecycle)

3. **Destruction / GC (no more references)**  
   - When all strong references to the object are gone (no variable, no field, no array slot, etc., points to it), the object becomes **unreachable**.  
   - Example:
     ```java
     Person p = new Person("Alice");
     p = null;   // or p goes out of scope
     ```
     Now there is no reference to that `Person` object, so it becomes eligible for garbage collection. [youtube](https://www.youtube.com/watch?v=fGO1GYz1irs)
   - The **reference variable** itself is destroyed when it goes out of scope (e.g., a local variable at the end of a method), and the JVM’s garbage collector can then reclaim the heap object. [stackoverflow](https://stackoverflow.com/questions/4557209/life-cycle-of-local-java-objects-created-during-a-method-call)

### Why reference variables are part of the lifecycle
<img width="970" height="530" alt="image" src="https://github.com/user-attachments/assets/c3aa6264-a5db-41c4-bde8-af07d054d562" />

- **They control reachability:** The object is only “alive” in the lifecycle while it is reachable via at least one reference. Remove all references, and the object enters the destruction phase. [kdgregory](https://www.kdgregory.com/index.php?page=java.refobj)
- **They connect stack and heap:** The tiny reference variable lives on the stack / in fields; the large object lives on the heap. The reference is the bridge that lets the program use the object during its lifecycle. [scientecheasy](https://www.scientecheasy.com/2020/06/life-cycle-of-object-in-java.html/)

In short:  
- **Object created → reference variable points to it.**  
- **Object used → at least one reference variable still points to it.**  
- **Object destroyed → no more references point to it; GC cleans it up.**  

So reference variables are not an optional side note; they are the **mechanism that defines whether the object is born, alive, or dead** in the JVM’s eyes. [dzone](https://dzone.com/articles/ocajp-7-object-lifecycle-java)
