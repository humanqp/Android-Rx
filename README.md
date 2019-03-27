# Android-Rx
> ### RxAndriod
 - RxAndroid Observar Patten 일종으로 기본적으로 Obseravable과 Subscribe로 구성되어 있음.
 ```code : java
    Observable<String> simpleObservable =
           Observable.create(new Observable.OnSubscribe<String>() {
               @Override
               public void call(Subscriber<? super String> subscriber) {
                   subscriber.onNext("Hello RxAndroid !!");
                   subscriber.onCompleted();
               }
           });

   simpleObservable
           .subscribe(new Subscriber<String>() {
               @Override
               public void onCompleted() {
                   Log.d(TAG, "complete!");
               }

               @Override
               public void onError(Throwable e) {
                   Log.e(TAG, "error: " + e.getMessage());
               }

               @Override
               public void onNext(String text) {
                   ((TextView) findViewById(R.id.textView)).setText(text);
               }
           });
 ```
  - Rx Reference
