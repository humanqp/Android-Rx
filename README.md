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
  - RxAndroid 에서 제공하는 스케줄러
   Schedulers.computation() - 이벤트 룹에서 간단한 연산이나 콜백 처리를 위해 사용됩니다.
   RxComputationThreadPool라는 별도의 스레드 풀에서 돌아갑니다. 최대 cㅔu갯수 개의 스레드 풀이 순환하면서 실행됩니다.
   Schedulers.immediate() - 현재 스레드에서 즉시 수행합니다. 
   observeOn()이 여러번 쓰였을 경우 immediate()를 선언한 바로 윗쪽의 스레드를 따라갑니다.
   Schedulers.from(executor) - 특정 executor를 스케쥴러로 사용합니다.
   Schedulers.io() - 동기 I/O를 별도로 처리시켜 비동기 효율을 얻기 위한 스케줄러입니다.자체적인 스레드 풀 CachedThreadPool을 사용합니다. API 호출 등 네트워크를 사용한 호출 시 사용됩니다.
   Schedulers.newThread() - 새로운 스레드를 만드는 스케쥴러입니다.
   Schedulers.trampoline() - 큐에 있는 일이 끝나면 이어서 현재 스레드에서 수행하는 스케쥴러. 
   AndroidSchedulers.mainThread() - 안드로이드의 UI 스레드에서 동작합니다.
   HandlerScheduler.from(handler) - 특정 핸들러 handler에 의존하여 동작합니다.
   
   
