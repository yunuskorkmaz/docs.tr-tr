### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT akış bağdaştırıcıları Hayır uzun FlushAsync otomatik olarak Kapat üzerinde çağırın

|   |   |
|---|---|
|Ayrıntılar|Windows mağazası uygulamalarında Windows çalışma zamanı akış bağdaştırıcıları FlushAsync yöntemi artık Dispose yöntemini çağırın.|
|Öneri|Bu değişiklik saydam olmalıdır. Geliştiriciler, önceki davranış aşağıdakine benzer bir kod yazarak geri yükleyebilirsiniz:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|

