---
ms.openlocfilehash: 47d3829748deef2c7c3610816b8941bf88da7ec6
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614926"
---
### <a name="accessibility-improvements-in-wpf"></a>WPF 'de erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

**Yüksek Karşıtlık iyileştirmeler**
<ul><li>Denetim için odak <xref:System.Windows.Controls.Expander> artık görünür durumdadır. Önceki .NET Framework sürümlerinde değildi.
-İçindeki metin <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimlerin seçildikleri zaman önceki .NET Framework sürümlerinden daha kolay görmek daha kolaydır.
-Devre dışı bırakılan sınır <xref:System.Windows.Controls.ComboBox> artık devre dışı metinle aynı renktedir. Önceki .NET Framework sürümlerinde değildi.
-Devre dışı bırakılmış ve odaklanmış düğmeler artık doğru tema rengini kullanıyor. .NET Framework önceki sürümlerinde, bu değildir.
-Bir denetimin stili olarak ayarlandığında açılan düğme artık görünür, <xref:System.Windows.Controls.ComboBox> <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> çünkü .NET Framework önceki sürümlerinde değildir.
-Bir denetimdeki sıralama göstergesi oku <xref:System.Windows.Controls.DataGrid> artık Tema renklerini kullanıyor. Önceki .NET Framework sürümlerinde, değildi.
-Varsayılan köprü stili artık fare üzerinde doğru Tema rengine göre değişir. Önceki .NET Framework sürümlerinde, değildi.
-Radyo düğmelerindeki klavye odağı artık görülebilir. Önceki .NET Framework sürümlerinde değildi.
-<xref:System.Windows.Controls.DataGrid>Denetimin CheckBox sütunu artık klavye odağı geri bildirimi için beklenen renkleri kullanıyor. Önceki .NET Framework sürümlerinde, değildi.
-Klavye odak görselleri artık <xref:System.Windows.Controls.ComboBox> ve <xref:System.Windows.Controls.ListBox> denetimlerinde görünür. Önceki .NET Framework sürümlerinde değildi.</p>
**Ekran okuyucu etkileşimi iyileştirmeleri**
<ul><li><xref:System.Windows.Controls.Expander>denetimler artık ekran okuyucular tarafından gruplar (genişletme/daraltma) olarak doğru duyuruldu.
- <xref:System.Windows.Controls.DataGridCell>denetimler artık ekran okuyucular tarafından veri kılavuzu hücresi (yerelleştirilmiş) olarak doğru duyuruldu.
-Ekran okuyucular artık düzenlenebilir bir adı duyuracaktır <xref:System.Windows.Controls.ComboBox> .
- <xref:System.Windows.Controls.PasswordBox>denetimler artık &quot; ekran okuyucular tarafından görünümde hiçbir öğe olmadığından duyurulmaz &quot; .</p>
**Liveregion desteği** Okuyucu gibi ekran okuyucular, kullanıcıların bir uygulamanın kullanıcı ARABIRIMI içeriğini bilmesini sağlar. Bu, genellikle kullanıcıya en çok ilgilendiğiniz bir öğe olduğundan, şu anda odaklanmış kullanıcı ARABIRIMI hakkında bir şeyi tanımlar. Ancak, bir kullanıcı arabirimi öğesi ekranda bir yerde değişiklik yaptığı ve odağa sahip değilse, Kullanıcı bilinçli olmayabilir ve önemli bilgileri kaçırmayabilir. Ligegions bu sorunu çözmek için tasarlanmıştır. Geliştirici, ekran okuyucuyu veya diğer [Kullanıcı Arabirimi Otomasyonu](~/docs/framework/ui-automation/ui-automation-overview.md) istemcisini, BIR kullanıcı arabirimi öğesine önemli bir değişikliğin yapıldığını bilgilendirmek için kullanabilir. Ekran okuyucu daha sonra bu değişikliğin kullanıcısına nasıl ve ne zaman bilgi verileceğine karar verebilir. LiveSetting özelliği de ekran okuyucunun Kullanıcı ARABIRIMINDE yapılan değişikliği bilgilendirmek için ne kadar önemli olduğunu bilmesini sağlar.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma** Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya sonraki bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- .NET Framework 4.7.1 hedefleyin. Bu, önerilen yaklaşımdır. Bu erişilebilirlik değişiklikleri, .NET Framework 4.7.1 veya üstünü hedefleyen WPF uygulamalarında varsayılan olarak etkinleştirilmiştir.
- Aşağıdaki [AppContext Switch](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` `false` örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve olarak ayarlayarak eski erişilebilirlik davranışlarını devre dışı bırakmak.

<pre><code class="lang-xml">&lt;?xml version=&quot;1.0&quot; encoding=&quot;utf-8&quot;?&gt;&#13;&#10;&lt;configuration&gt;&#13;&#10;&lt;startup&gt;&#13;&#10;&lt;supportedRuntime version=&quot;v4.0&quot; sku=&quot;.NETFramework,Version=v4.7&quot;/&gt;&#13;&#10;&lt;/startup&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;!-- AppContextSwitchOverrides value attribute is in the form of &#39;key1=true/false;key2=true/false  --&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.UseLegacyAccessibilityFeatures=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça olarak ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .
UI Otomasyonu 'na genel bakış için bkz. [UI Otomasyonu genel bakış](~/docs/framework/ui-automation/ui-automation-overview.md).

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Ana       |
| Sürüm | 4.7.1       |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting(System.Windows.DependencyObject,System.Windows.Automation.AutomationLiveSetting)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting(System.Windows.DependencyObject)?displayProperty=nameWithType>
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore?displayProperty=nameWithType>
