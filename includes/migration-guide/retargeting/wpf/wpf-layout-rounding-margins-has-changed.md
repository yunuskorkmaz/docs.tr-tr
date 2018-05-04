### <a name="wpf-layout-rounding-of-margins-has-changed"></a>WPF düzeni kenar boşluklarının yuvarlama değişti

|   |   |
|---|---|
|Ayrıntılar|Kenar boşlukları yuvarlanır ve Kenarlıklar ve arka plan bunları içinde değişti yolu. Bu değişikliğin sonucu olarak:<ul><li>Genişlik veya yüksekliğinden öğelerinin büyütür veya en çok bir piksel küçültür.</li><li>Bir nesne yerleşimini en çok bir piksel taşıyabilirsiniz.</li><li>Ortalanmış öğeleri dikey veya yatay olarak merkezi en çok bir piksel tarafından devre dışı olabilir.</li></ul>Varsayılan olarak, bu yeni düzen .NET Framework 4.6 hedefleyen uygulamalar için etkinleştirilir.|
|Öneri|Kırpma sağa ya da yüksek DPIs WPF denetimleri alt ortadan kaldırmak için bu değişiklik eğilimlidir olduğundan, .NET Framework'ün önceki sürümlerini hedefleyen ama .NET Framework 4.6 üzerinde çalışan uygulamalar bu yeni davranış aşağıdaki satırı ekleyerek seçebilirsiniz <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false&quot; /&gt;&#39;&#13;&#10;</code></pre>.NET Framework 4.6 hedef ancak WPF denetimleri önceki düzeni algoritmasını kullanarak oluşturmak istediğiniz uygulamalar yapabilirsiniz aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının:<pre><code class="lang-xml">&lt;AppContextSwitchOverrides value=&quot;Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=true&quot; /&gt;&#39;.&#13;&#10;</code></pre>|
|Kapsam|Küçük|
|Sürüm|4.6|
|Tür|Yeniden hedefleme|

