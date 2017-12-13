# ionic2
type must be one of: component, directive, page, pipe, provider, tabs (not componet)

```
sudo cnpm i cordova ionic -g
ionic start myapp --v2 //会报错--v1 --v2 has been removed,使用下面这句
ionic start myApp --type=ionic-angular  然后一路会车，如果网速不好可以ctrl+c,cd project folder then cnpm i
ionic lab
```
# table of contents
- app 根目录
- tab 根page

```
ionic g page detail //creat one page

```

## ui component
- list
```
//ts
export class HomePage {
  items:any[];
  constructor(public navCtrl: NavController) {
    this.items=[];
    for(let i=0;i<10;i++){
      this.items.push({
        item:"item"+(i+1),
        id:i
      })
    }
  }
  itemSelected(item){
    alert(item.item)
  }
}
//html
<ion-list>
  <button ion-item *ngFor="let item of items" (click)="itemSelected(item)">
    {{ item.item }}
  </button>
</ion-list>
```
## detailpage 6 步走(会用到2个函数)
在HomePage的click的函数中
```
//1
itemSelected(item){
    this.navCtrl.push(DetailPage,{
      item:item
    });
    // alert(item.id+1)
  }
//2
import {DetailPage} from '../detail/detail';
```

### DetaiPage 接收变量
```
export class DetailPage {
  item:any;
  constructor(public navCtrl: NavController, public navParams: NavParams) {
    this.item=navParams.get('item')
  }

  ionViewDidLoad() {
    console.log('ionViewDidLoad DetailPage');
  }

}

```

## app.moduls.ts
```
import { NgModule, ErrorHandler } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { IonicApp, IonicModule, IonicErrorHandler } from 'ionic-angular';
import { MyApp } from './app.component';

import { AboutPage } from '../pages/about/about';
import { ContactPage } from '../pages/contact/contact';
import { HomePage } from '../pages/home/home';
import { TabsPage } from '../pages/tabs/tabs';
import {DetailPage} from '../pages/detail/detail';

import { StatusBar } from '@ionic-native/status-bar';
import { SplashScreen } from '@ionic-native/splash-screen';

@NgModule({
  declarations: [
    MyApp,
    AboutPage,
    ContactPage,
    HomePage,
    TabsPage,
    DetailPage
  ],
  imports: [
    BrowserModule,
    IonicModule.forRoot(MyApp)
  ],
  bootstrap: [IonicApp],
  entryComponents: [
    MyApp,
    AboutPage,
    ContactPage,
    HomePage,
    TabsPage,
    DetailPage
  ],
  providers: [
    StatusBar,
    SplashScreen,
    {provide: ErrorHandler, useClass: IonicErrorHandler}
  ]
})
export class AppModule {}

```

