### <a name="serialport-background-thread-exceptions"></a>Seri bağlantı noktası arka plan iş parçacığı özel durumlar

|   |   |
|---|---|
|Ayrıntılar|Arka plan iş parçacığı ile oluşturulan <xref:System.IO.Ports.SerialPort> akışları OS özel durumları oluştuğunda işlemi artık sonlandırılacak. <br/>İle oluşturulmuş bir arka plan iş parçacığı üzerinde bir işletim sistemi özel durum oluştuğunda hedef .NET Framework 4.7 ve önceki sürümleri uygulamalarda, bir işlemin sonlandırıldığından bir <xref:System.IO.Ports.SerialPort> akış. <br/>Uygulamalarda hedef .NET Framework'ü 4.7.1 veya sonraki bir sürümünü, arka plan iş parçacıkları OS olayların tamamlanmasını bekleme etkin seri bağlantı noktasına ve ilgili seri bağlantı noktası ani kaldırılması gibi bazı durumlarda kilitlenebiliyordu.|
|Öneri|.NET Framework 4.7.1 hedefleyen uygulamalar için aşağıdakileri ekleyerek arzu değilse, özel durum işleme dışında seçebilirsiniz <code>&lt;runtime&gt;</code> bölümü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Hedef uygulamalar için .NET Framework'ün önceki sürümlerini .NET Framework 4.7.1 ancak çalıştırmak veya daha sonra özel durum şu şekilde ekleyerek işleme için kabul <code>&lt;runtime&gt;</code> bölümü, <code>app.config</code> dosyası:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.7.1|
|Tür|Yeniden hedefleme|
|Etkilenen API'leri|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|

