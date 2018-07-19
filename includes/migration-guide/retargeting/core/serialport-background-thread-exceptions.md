### <a name="serialport-background-thread-exceptions"></a>Çevirmek için SerialPort arka plan iş parçacığı özel durumları

|   |   |
|---|---|
|Ayrıntılar|Arka plan iş parçacığı ile oluşturulan <xref:System.IO.Ports.SerialPort> akışları işletim sistemi özel durumlar oluştuğunda işlemi artık sonlandırın. <br/>Bir işletim sistemi ile oluşturulmuş bir arka plan iş parçacığında özel durum, .NET Framework 4.7 ve önceki sürümleri hedefleyen uygulamalarda, bir işlemin sonlandırıldığından bir <xref:System.IO.Ports.SerialPort> akış. <br/>Uygulamalarda hedef .NET Framework 4.7.1 veya sonraki bir sürümünü, arka plan iş parçacığı'nın işletim sistemi olayların tamamlanmasını bekleme etkin seri bağlantı noktasına ilgili ve seri bağlantı noktası ani kaldırılması gibi bazı durumlarda kilitlenebiliyordu.|
|Öneri|.NET Framework 4.7.1'i hedefleyen uygulamalar için aşağıdaki ekleyerek arzu değil, özel durum işleme dışında seçebilirsiniz <code>&lt;runtime&gt;</code> bölümünü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedefleyen uygulamalar için .NET Framework'ün önceki sürümlerinde, ancak .NET Framework 4.7.1 çalıştırmak veya daha sonra özel durum işleme için aşağıdakileri ekleyerek kabul etmek <code>&lt;runtime&gt;</code> bölümünü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

