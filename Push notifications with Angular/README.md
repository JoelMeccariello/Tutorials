# Create push notifications with Angular
## Download the service
You can get the service at [my Github](https://github.com/JoelMeccariello/Tutorials/blob/master/Push%20notifications%20with%20Angular/push-notification.service.ts).
## Install the service
You need to create a folder called "services" in your "src/app/" directory and add the file you just downloaded in there. Before the service works, you'll have to add it to your app.module.ts.

    import { BrowserModule } from '@angular/platform-browser'
    import { NgModule } from '@angular/core'
    import { AppComponent } from './app.component'
    import { PushNotificationsService } from './push-notification.service'
    @NgModule({
	    declarations: [AppComponent],
	    imports: [
		    BrowserModule
		],
		providers: [PushNotificationsService],
		bootstrap: [AppComponent],
	})
	export class AppModule { }

## Use the service
I made it as simple as possible to use. First of all you'll have to request the notification permission.

    constructor(private notificationService: PushNotificationsService) {
	    this.notificationService.requestPermission();
    }

### Create simple notifications
Finally we're able to send our first notification.

    this.notificationService.generateNotification({
	    title: 'Test Alert',
	    alertContent: 'Hello World!'
    });

### Create advanced notifications
We're not just able to define the title and the body of the notification. We're also able to configure tons of extras that make our notification look exactly like we want it to look like.
The following parameters are configurable with the `this.notificationService.create();` method.

    export interface PushNotification {
	    body?: string;
	    icon?: string;
	    tag?: string;
	    data?: any;
	    renotify?: boolean;
	    silent?: boolean;
	    sound?: string;
	    noscreen?: boolean;
	    sticky?: boolean;
	    dir?: 'auto' | 'ltr' | 'rtl';
	    lang?: string;
	    vibrate?: number[];
    }
