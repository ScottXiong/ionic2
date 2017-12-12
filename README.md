# ionic2
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
