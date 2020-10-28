#周四 第4题
 题目：（必做） 根据上述自己对于 1 和 2 的演示，写一段对于不同 GC 的总结，提交到 Github。
 解答：
 串行 GC:单个线程执行垃圾回收，用户线程处于等待状态。会触发全线暂停(STW)，停止所有的应用线程，CPU利用率高，暂停时间长。
 并行 GC:多条垃圾收集线程并行工作，用户线程处于等待状态。GC期间，所有CPU内核都在并行清理垃圾，所以总暂停时间更短。
 CMS GC:并发 GC,用户线程与垃圾收集线程同时或交替执行。采用标记-清除算法，并发收集、低停顿，在并发阶段，虽然不会导致用户线程停顿，但是会占用CPU资源而导致引用程序变慢，总吞吐量下降。
 G1 GC:并发 GC，采用标记-整理-复制算法，STW停顿的时间和分布，可预期且可配置。堆不再分成年轻代和老年代，而是划分为多个 小块堆区域，哪 一块的垃圾最多就优先清理它。
 
#周六 第2题
 题目：必做）写一段代码，使用 HttpClient 或 OkHttp 访问 http://localhost:8801 ，代码提交到 Github。
 解答：
 public static void main(String[] args) {
         OkHttpClient okHttpClient = new OkHttpClient();
         Response response;
         String url = "http://localhost:8801";
         Request request = new Request.Builder().url(url).get().build();
         try {
             response = okHttpClient.newCall(request).execute();
             System.out.println(response.body().string());
         } catch (IOException e) {
             e.printStackTrace();
         }
     }