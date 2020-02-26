---
description: Anotações feitas durante as Aulas do Bootcamp - 13 horas
---

# Angular

```text
import { Component, OnChanges } from '@angular/core';

@Component({
    selector:'app-star'
})

export class StarComponent implements OnChanges{


    
} 
```

```text
import { Component, OnInit } from '@angular/core';

@Component({
    selector:'app-star'
})

export class StarComponent implements OnInit{


    
} 
```

> Inicializar um componente com OnInit é fazer uma ação na inicialização, mas, ao consumir informações HTTP, será assíncrono. não garantindo assim que a  informação que estará passando estará disponível e carregada no HTTP. Para esses casos é  recomendado inicializar com OnChanges. Na medida q o valor for alterado no HTTP passará para o component e será identificado.

### Injeção de Dependência

```text
 Injectable({providein: 'root'})
```

> Injectable\({providein: 'root'}\)
>
> Tornar a classe elegível para injeção dependência e assim fazer com  que o providein   carregue  na root da aplicação. 
>
> quando carregar o model raiz\(app-model\) sera carregado também  essa classe de serviço

```text
@Injectable({
    providedIn: 'root'
})
export class CourseService {
    retrieveAll(): Course[] {
        return COURSES;
    }
}
```

> Um método precisa ser criado dentro do serviço para retornar os dados quando solicitado

> > Fundamental para a  organização da distribuição dos componentes

```text
let COURSES: Course[] = [
        {dados}
    ]
```

> **Não colocar códigos de alterações dentro do método para classes de serviço**

```text
export class CourseListComponent implements OnInit {

    public courses:Course[] = [] ;

    constructor(private courseService: CourseService){}
    ngOnInit(): void {
        this.courses = this.courseService.retrieveAll();
        
    }
    
}
```

> Course Service é injetado via injeção de dependência dentro do componente através do construtor

Após o carregamento, inserir esses dados na variável do componente pelo ngOnInit

