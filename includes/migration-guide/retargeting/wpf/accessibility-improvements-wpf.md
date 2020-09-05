---
ms.openlocfilehash: 895d09e4ec39bd4a92ed1f4910da80474334d99b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89497146"
---
### <a name="accessibility-improvements-in-wpf"></a>WPF 'de erişilebilirlik geliştirmeleri

#### <a name="details"></a>Ayrıntılar

**Yüksek Karşıtlık iyileştirmeler**

- Denetim için odak <xref:System.Windows.Controls.Expander> artık görünür durumdadır. Önceki .NET Framework sürümlerinde, değildi.
- İçindeki metin <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimlerin seçildikleri zaman önceki .NET Framework sürümlerinden daha kolay görmek daha kolaydır.
- Devre dışı bırakılan sınır <xref:System.Windows.Controls.ComboBox> artık devre dışı metinle aynı renktedir. Önceki .NET Framework sürümlerinde, değildi.
- Devre dışı bırakılmış ve odaklanmış düğmeler artık doğru tema rengini kullanıyor. Önceki .NET Framework sürümlerinde, bu değildir.
- Bir <xref:System.Windows.Controls.ComboBox> denetimin stili olarak ayarlandığında açılan düğme artık görünür olur <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey?displayProperty=nameWithType> . Önceki .NET Framework sürümlerinde, değildi.
- Bir denetimdeki sıralama göstergesi oku <xref:System.Windows.Controls.DataGrid> artık Tema renklerini kullanıyor. Önceki .NET Framework sürümlerinde, değildi.
- Varsayılan köprü stili artık fare üzerinde doğru Tema rengine göre değişir. Önceki .NET Framework sürümlerinde, değildi.
- Radyo düğmelerindeki klavye odağı artık görülebilir. Önceki .NET Framework sürümlerinde, değildi.
- <xref:System.Windows.Controls.DataGrid>Denetimin CheckBox sütunu artık klavye odağı geri bildirimi için beklenen renkleri kullanıyor. Önceki .NET Framework sürümlerinde, değildi.
- Klavye odak görselleri artık <xref:System.Windows.Controls.ComboBox> ve <xref:System.Windows.Controls.ListBox> denetimlerinde görünür. Önceki .NET Framework sürümlerinde, değildi.

**Ekran okuyucu etkileşimi iyileştirmeleri**

- <xref:System.Windows.Controls.Expander> denetimler artık ekran okuyucular tarafından gruplar (genişletme/daraltma) olarak doğru duyuruldu.
- <xref:System.Windows.Controls.DataGridCell> denetimler artık ekran okuyucular tarafından veri kılavuzu hücresi (yerelleştirilmiş) olarak doğru duyuruldu.
- Ekran okuyucular artık düzenlenebilir bir adı duyuracaktır <xref:System.Windows.Controls.ComboBox> .
- <xref:System.Windows.Controls.PasswordBox> denetimler artık, ekran okuyucular tarafından "görünümde hiçbir öğe yok" olarak duyurulmaz.

**LiveRegion desteği**

Ekran okuyucular gibi ekran okuyucular, insanların bir uygulamanın kullanıcı arabirimini (UI) anlamasına yardımcı olur ve genellikle şu anda odağa sahip olan UI öğesini tanımlar. Ancak, bir kullanıcı arabirimi öğesi ekranda bir yerde değişiklik yaptığı ve odağa sahip değilse, Kullanıcı bilinçli olmayabilir ve önemli bilgileri kaçırmayabilir. Ligegions bu sorunu çözmek için tasarlanmıştır. Geliştirici, ekran okuyucuyu veya diğer [Kullanıcı Arabirimi Otomasyonu](~/docs/framework/ui-automation/ui-automation-overview.md) istemcisini, BIR kullanıcı arabirimi öğesine önemli bir değişikliğin yapıldığını bilgilendirmek için kullanabilir. Ekran okuyucu daha sonra bu değişikliğin kullanıcısına nasıl ve ne zaman bilgi verileceğine karar verebilir. LiveSetting özelliği de ekran okuyucunun Kullanıcı ARABIRIMINDE yapılan değişikliği bilgilendirmek için ne kadar önemli olduğunu bilmesini sağlar.

#### <a name="suggestion"></a>Öneri

**Bu değişiklikleri kabul etme veya devre dışı bırakma**

Uygulamanın bu değişikliklerden faydalanabilir olması için .NET Framework 4.7.1 veya üzeri bir sürümde çalışmalıdır. Uygulama, aşağıdaki yollarla bu değişikliklerden faydalanabilir:

- Hedef .NET Framework 4.7.1. Bu, önerilen yaklaşımdır. Bu erişilebilirlik değişiklikleri, .NET Framework 4.7.1 veya üstünü hedefleyen WPF uygulamalarında varsayılan olarak etkinleştirilmiştir.
- Aşağıdaki [AppContext Switch](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `<runtime>` `false` örnekte gösterildiği gibi, uygulama yapılandırma dosyasının bölümüne aşağıdaki AppContext anahtarını ekleyerek ve olarak ayarlayarak eski erişilebilirlik davranışlarını devre dışı bırakmak.

  ```xml
  <?xml version="1.0" encoding="utf-8"?>
  <configuration>
    <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.7"/>
    </startup>
    <runtime>
      <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true/false;key2=true/false'  -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
    </runtime>
  </configuration>
  ```

.NET Framework 4.7.1 veya üstünü hedefleyen ve eski erişilebilirlik davranışını korumak isteyen uygulamalar, bu AppContext anahtarını açıkça ayarlayarak eski erişilebilirlik özelliklerinin kullanımını kabul edebilir `true` .
UI Otomasyonu 'na genel bakış için bkz. [UI Automation 'A genel bakış](~/docs/framework/ui-automation/ui-automation-overview.md).

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
