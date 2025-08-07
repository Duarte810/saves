# INDEX
<ion-header [translucent]="true">
  <ion-toolbar color="danger">
    <ion-title>
      Game Time
    </ion-title>
  </ion-toolbar>
</ion-header>

<ion-content [fullscreen]="true">
  <div id="container">
  <p>Points: {{ points }} || Time: {{ numero }}</p>
  <div id="lil_ball" (click)="somar()" *ngIf="status"></div>
  </div>

  <ion-button (click)="parar()">Stop</ion-button>

  <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/a/a4/Flag_of_the_United_States.svg/1024px-Flag_of_the_United_States.svg.png" alt="">

</ion-content>

#CSS
#lil_ball{
  width: 225px;
  height: 225px;
  background-image: url(https://i.imgflip.com/8zplov.png);
  margin-left: auto;
  margin-right: auto;
}

p{
  text-align: center;
  font-weight: bold;
}

ion-button{
  display: flex;
  justify-content: center;
  margin-top: 13px;
}

#container{
  background-image: url(https://images.fineartamerica.com/images-medium-large-5/white-house-2001-granger.jpg);
  height: 30%;
  width: 100%;
  background-repeat: no-repeat;
  background-size: cover;
}

#TS
import { Component, OnInit } from '@angular/core';
import { IonHeader, IonToolbar, IonTitle, IonContent, IonButton } from '@ionic/angular/standalone';

import { NgIf } from '@angular/common';

@Component({
  selector: 'app-home',
  templateUrl: 'home.page.html',
  styleUrls: ['home.page.scss'],
  imports: [IonHeader, IonToolbar, IonTitle, IonContent, IonButton, NgIf],
})
export class HomePage implements OnInit {

  points: number = 0;
  numero: number = 0;
  temporizador: any;

  status: boolean = true;

  constructor() {
  }

  ngOnInit(): void {
    this.iniciar()
  }

  somar(){
    this.points += 1;
  }

  iniciar(){
    this.temporizador = setInterval(()=>{
      this.numero += 1;
      if(this.numero >= 10){ 
        this.status = false;
        this.parar()
      }
    }, 1000)
  }

  parar(){
    clearInterval(this.temporizador);
    this.numero = 0;
  }
}
