---
title: "Erişilebilirlik .NET Framework'teki yenilikler"
ms.custom: updateeachrelease
ms.date: 10/13/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e6a6759ae285f2dd101bddf71ea8e5ca792e87df
ms.sourcegitcommit: 957c696f25e39f923a827fc3ad5e8ab72768838c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2018
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Erişilebilirlik .NET Framework'teki yenilikler

.NET Framework uygulamaları, kullanıcılarınızın daha fazla accessibile kolaylaştırmayı amaçlar. Erişilebilirlik Özellikleri yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak üzere bir uygulama sağlar. .NET Framework 4.7.1 ile başlayarak, .NET Framework çok sayıda erişilebilir uygulamalar oluşturmak geliştiriciler izin erişilebilirlik geliştirmeleri içerir. 

Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 hedefleyen uygulamalar için varsayılan olarak etkin veya üzeri. Ayrıca, .NET Framework'ün önceki bir sürümünü hedef ancak 4.7.1 .NET Framework üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar out eski erişilebilirlik davranışlarını (ve dolayısıyla 4.7.1 .NET Framework'teki erişilebilirlik geliştirmeleri için kabul) tarafından Aşağıdaki anahtar ekleme [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Benzer şekilde, 4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar erişilebilirlik özellikleri aşağıdaki anahtara ekleyerek devre dışı bırakabilirsiniz [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının. 

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Erişilebilirlik 4.7.1 .NET Framework'teki yenilikler

.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Presentation Foundation (WPF)](#windows-presentation-foundation-wpf)

- [Windows Forms](#windows-forms-accessibility-improvements)

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ekran Okuyucusu geliştirmeleri**

Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucular etkileyen aşağıdaki geliştirmeleri içerir:

- .NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.Expander> denetimleri duyurdu düğmeler olarak ekran okuyucular tarafından. .NET Framework 4.7.1 ile başlayarak, bunlar Genişletilebilir/daraltılabilir grupları olarak doğru bildirilir.

- .NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.DataGridCell> denetimleri ekran okuyucular tarafından bildirilen "özel" olarak .NET Framework 4.7.1 ile başlayarak, bunlar artık doğru (yerelleştirilmiş) veri kılavuz hücresinin bildirilir.
 
- .NET Framework 4.7.1 ile başlayarak, ekran okuyucuların bir düzenlenebilir adını Duyurusu <xref:System.Windows.Controls.ComboBox>.

- .NET Framework 4.7 ve önceki sürümlerde, <xref:System.Windows.Controls.PasswordBox> denetimleri "öğesi görünüm olarak" duyurdu veya vardı Aksi takdirde yanlış bir davranış. Bu sorun .NET Framework 4.7.1 ile başlayan düzeltilmiştir.     

**UIAutomation LiveRegion desteği**

Ekran okuyucular ekran okuyucusu Yardım kişiler gibi bir uygulama kullanıcı Arabirimi içeriğini odaklanmış UI içeriği metin okuma çıktı tarafından genellikle okuyun. Ancak, bir kullanıcı Arabirimi öğesi değiştirir ve odağı yok, kullanıcı bilgilendirilmez ve önemli bilgiler eksik. Bu sorunu çözme sırasında dinamik bölgeler hedefleyin. Bir geliştirici ekran okuyucusu veya önemli bir değişiklik bir kullanıcı Arabirimi öğesine yapılan herhangi bir UIAutomation istemcisi hakkında bilgilendirmek için bunları kullanabilirsiniz. Ekran Okuyucusu sonra nasıl ve ne zaman karar verebilirsiniz bu değişikliği kullanıcıyı bilgilendirmek üzere. 

Canlı bölgeler desteklemek için aşağıdaki API'leri WPF için eklenmiştir:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> tanımlamak alanları **LiveSetting** özelliği ve **LiveRegionChanged** olay. XAML kullanılarak ayarlanabilir.

- **AutomationProperties.LiveSetting** kullanıcı için kullanıcı Arabirimi değişiklik önem ekran okuyucusu bildirir özelliği eklenmiş.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Tanımlayan özellik **AutomationProperties.LiveSetting** özelliği eklenmiş.
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Sağlamak üzere geçersiz yöntemi bir **LiveSetting** değeri.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> alma ve ayarlama yöntemleri bir **LiveSetting** değeri.
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası tanımlar numaralandırma **LiveSetting** değerler:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Canlı bölge içeriği değişirse öğesi bildirim göndermez.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Canlı bölge içeriği değişirse öğesi interruptive olmayan bildirimleri gönderir.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Canlı bölge içeriği değişirse öğesi interruptive bildirimleri gönderir.   

Bir LiveRegion ayarlayarak oluşturabileceğiniz **AutomationProperties.LiveSetting** ilgi, aşağıdaki örnekte gösterildiği gibi öğesindeki özelliği:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Canlı bölgede veri değişikliklerini ve ekran okuyucusu bildirmek gerektiğinde, açıkça bir olay aşağıdaki örnekte gösterildiği gibi yükseltin.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Yüksek Karşıtlık**

.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimleri yüksek karşıtlıklı iyileştirmeler yapılmıştır. Şimdi ne zaman görünür oldukları <xref:System.Windows.SystemParameters.HighContrast%2A> tema ayarlanır. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Controls.Expander>denetimi

    Görsel için odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür. Klavye görsellerini <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de. Örneğin:

    Sonra: 
    
    ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> denetimleri
 
    Metin <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri yüksek karşıtlık Temalar seçildiğinde daha kolay şimdi. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>denetimi
 
    .NET Framework ile 4.7.1, bir devre dışı kenarlık başlangıç <xref:System.Windows.Controls.ComboBox> denetimidir devre dışı bırakılmış metin olarak aynı rengi. Örneğin:
    
    Sonra: 

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri önce devre dışı](media/combo-disabled-before.png)

    Sonra:   

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri sonra devre dışı](media/combo-disabled-after.png)

    Ayrıca, doğru Tema rengi devre dışı bırakılmış ve odaklanmış düğmelerini kullanın.

    Sonra:

    ![Erişilebilirlik geliştirmeleri önce düğmesi Tema renkleri](media/button-themes-before.png) 
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra düğmesi Tema renkleri](media/button-themes-after.png) 

    Son olarak, .NET Framework 4.7 ve önceki sürümleri, ayarı içinde bir <xref:System.Windows.Controls.ComboBox> denetimin stiline `Toolbar.ComboBoxStyleKey` görünmez olmasını aşağı açılan okunu neden oldu. Bu sorun .NET Framework 4.7.1 ile başlayan düzeltilmiştir. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid>denetimi

    .NET Framework 4.7.1, sıralama göstergesi oku başlayarak <xref:System.Windows.Controls.DataGrid> kullandığı Tema renkleri düzeltmek artık denetler. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce sıralama göstergesi oku](media/sort-indicator-before.png) 
    
    Sonra:   
 
    ![Erişilebilirlik geliştirmeleri sonra sıralama göstergesi oku](media/sort-indicator-after.png) 
    
    Ayrıca, .NET Framework 4.7 ve önceki sürümlerinde varsayılan bağlantı stilini fare yanlış bir renk yüksek karşıtlık modunda değiştirilip. Bu .NET Framework 4.7.1 ile başlayan çözümlenir. Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusunu sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirim için beklenen renkleri kullanır.

    Sonra: 

    ![DataGrid varsayılan bağlantı stili önce erişilebilirlik geliştirmeleri](media/default-link-style-before.png) 
 
    Sonra:    
  
    ![DataGrid varsayılan bağlantı stili sonra erişilebilirlik geliştirmeleri](media/default-link-style-after.png)  

.NET Framework'teki 4.7.1 WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik geliştirmeleri WPF'de](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

## <a name="windows-forms-accessibility-improvements"></a>Windows Forms erişilebilirlik geliştirmeleri

.NET Framework 4.7.1'da, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.

**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**

.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sistemi içinde kullanılabilir yüksek karşıtlık modda geliştirilmiş işleme sunar. Windows 10 bazı yüksek karşıtlık sistem renkleri değerlerini değişti ve Windows Forms Windows 10 Win32 Framework'te temel alır. En iyi deneyim için en son sürümünü çalıştırın ve en son işletim sistemi değişiklikleri aşağıdaki tanıyarak test uygulaması ve kaydını yorum Windows 10 app.manifest dosyasında OS satırını desteklenen ekleyerek kabul:

```xml
<!– Windows 10 –>
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Yüksek Karşıtlık değişiklikler bazı örnekleri şunlardır:

- Açılır menüdeki onay <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.

- Seçili olduğunda, devre dışı <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.

- Seçili metni <xref:System.Windows.Forms.Button> Denetim seçim rengi ile çelişir.

- Devre dışı bırakılmış metin okumak daha kolay olur. Örneğin:

    Sonra:

    ![Erişilebilirlik geliştirmeleri önce devre dışı bırakılmış metin](media/wf-disabled-before.png) 

    Sonra:

    ![Devre dışı metinden sonra erişilebilirlik geliştirmeleri](media/wf-disabled-after.png) 

- İş parçacığı özel durum iletişim kutusunda yüksek karşıtlık geliştirmeleri.

**Ekran Okuyucusu için geliştirilmiş destek**

.NET Framework 4.7.1 Windows Forms'ta ekran okuyucusu için aşağıdaki erişilebilirlik geliştirmeleri içerir:

- <xref:System.Windows.Forms.MonthCalendar> Denetimi, ekran okuyucusu tarafından yanı sıra diğer UI Otomasyon araçları tarafından erişilebilir.

- <xref:System.Windows.Forms.CheckedListBox> Denetim ekran okuyucusu kullanıcıya bir liste öğesinin değeri değiştirdiyseniz bildirimde şekilde öğenin onay durumu değiştiğinde bildirir.
 
- <xref:System.Windows.Forms.DataGridViewCell> Denetim ekran okuyucusu için doğru salt okunur durumunu raporlar.
 
- Ekran Okuyucusu şimdi devre dışı okuma <xref:System.Windows.Forms.ToolStripMenuItem> metin, daha önce devre dışı bırakılmış menü öğeleri üzerindeki Atla ancak.

**UIAutomation erişilebilirlik desenler için gelişmiş destek**

4.7.1 .NET Framework ile başlayarak, geliştiricilerin erişilebilirlik teknolojisinin Araçları'nın ortak API erişilebilirlik desenleri ve birden çok WinForms denetimi özelliklerini yararlanabilirsiniz. Bu erişilebilirlik geliştirmeleri içerir:

- <xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ToolStripSplitButton> şimdi destek [Genişlet/Daralt düzeni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Artık destekliyor [değiştirme düzenini](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- <xref:System.Windows.Forms.ToolStripItem> Kontrol destekler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt düzeni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri Destek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği.

**Geliştirilmiş özellik tarayıcı deneyimi**

.NET Framework 4.7.1 ile başlayarak, Windows Forms içerir:

- Daha iyi klavye gezinmesi çeşitli aşağı açılan seçimi windows sağlar.
- Gereksiz sekme durakları azaltma.
- Daha iyi denetim türlerini raporlama.
- Gelişmiş ekran okuyucusu davranışı.
 
## <a name="see-also"></a>Ayrıca Bkz.
[.NET Framework'teki yenilikler](whats-new.md)   
 