## Setting up HttpInterceptor for angular2 for AOP like functionality.

`npm install ng-http-interceptor --save`

### app.module.ts:

`imports: [HttpInterceptorModule]`

### app.component.ts:

`export class AppComponent {`          
  `constructor(http: Http, httpInterceptor: HttpInterceptorService) {`
  
    httpInterceptor.request().addInterceptor((data, method) => {
      console.log(method, data);
      return data;
    });

    httpInterceptor.response().addInterceptor((res, method) => {
      res.subscribe(r => console.log(method, r));
      return res;
    });

    http.get('/')
      .map(r => r.text())
      .subscribe(console.log);
      }
    }
