---
title: Erişilebilirlik .NET Framework'teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/10/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7fe7e15e482028b9988d7e560b98be19b6c07427
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33509222"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Erişilebilirlik .NET Framework'teki yenilikler

.NET Framework uygulamaları daha erişilebilir kullanıcılarınız için kolaylaştırmayı amaçlar. Erişilebilirlik Özellikleri yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak üzere bir uygulama sağlar. .NET Framework 4.7.1 ile başlayarak, .NET Framework çok sayıda erişilebilir uygulamalar oluşturmak geliştiriciler izin erişilebilirlik geliştirmeleri içerir. 

## <a name="accessibility-switches"></a>Erişilebilirlik anahtarları

.NET Framework 4.7 veya önceki bir sürümünü hedefleyen ancak .NET Framework 4.7.1 çalıştıran erişilebilirlik özellikleri kabul etmek için uygulamanızın yapılandırabilirsiniz ya da daha sonra. .NET Framework 4.7.1 hedefliyorsa eski özellikler (ve değil faydalanan erişilebilirlik özellikleri) kullanmak için uygulamanızı de yapılandırabilirsiniz ya da daha sonra. Her sürümde eklediğiniz bir sürüme özgü erişilebilirlik anahtar erişilebilirlik özellikleri içeren .NET Framework'ün [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulama yapılandırma dosyası. Desteklenen anahtarlar şunlardır:

|Sürüm|Anahtar|
|---|---|
|.NET framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Erişilebilirlik geliştirmeleri yararlanarak

Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 hedefleyen uygulamalar için varsayılan olarak etkin veya üzeri. Ayrıca, .NET Framework'ün önceki bir sürümünü hedef ancak 4.7.1 .NET Framework üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar out eski erişilebilirlik davranışlarını (ve dolayısıyla erişilebilirlik geliştirmeleri avantajlarından yararlanmak) anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasında hem de değerlerine ayarını bölümünü `false`. .NET Framework 4.7.1 sunulan erişilebilirlik geliştirmeleri için kabul etme gösterir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

.NET Framework'ün sonraki bir sürümünü erişilebilirlik özelliklerine kabul seçerseniz, ayrıca açıkça özellikleri .NET Framework'ün önceki sürümlerden kabul gerekir. Hem .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik geliştirmeleri avantajlarından yararlanmak için uygulamanızın yapılandırma aşağıdakileri gerektirir [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğe:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Eski davranışı geri yükleme

4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar devre dışı bırakabilir erişilebilirlik özellikleri anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyasının ve bunların değeri ayarlamak `true`. Örneğin, aşağıdaki yapılandırma, .NET Framework 4.7.2 sunulan erişilebilirlik özellikleri dışında kabul eder:  

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-the-net-framework-472"></a>Erişilebilirlik 4.7.2 .NET Framework'teki yenilikler

.NET Framework 4.7.2 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>
### <a name="windows-forms"></a>Windows Forms

**Yüksek karşıtlıklı Tema renkleri işletim sistemi tarafından tanımlanan**

Windows Forms 4.7.2 .NET Framework ile başlayarak, Yüksek Karşıtlık Temaları işletim sistemi tarafından tanımlanan renkleri kullanır. Bu, aşağıdaki denetimleri etkiler:

- Aşağı açılan okunu <xref:System.Windows.Forms.ToolStripDropDownButton> denetim.

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> ile denetimleri <xref:System.Windows.Forms.ButtonBase.FlatStyle> kümesine <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> veya <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Daha önce seçilen metin ve arka plan renklerini değil çakışan ve okunması zor.

- Denetimleri içinde yer alan bir <xref:System.Windows.Forms.GroupBox> olan kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.
 
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, Ve <xref:System.Windows.Forms.ToolStripDropDownButton> artan parlaklığını Karşıtlık oranı yüksek karşıtlık modunda sahip kontrol eder.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Ekran Okuyucusu geliştirmeleri**

.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği şu şekilde geliştirilmiştir:

- Değerini bildirdi <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> metnini Duyurusu zaman özelliği bir <xref:System.Windows.Forms.ToolStripMenuItem>. 

- Ne zaman gösteren bir <xref:System.Windows.Forms.ToolStripMenuItem> sahip kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.

- Bir onay kutusu durumu hakkında geri bildirim sağlar, <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> özelliği ayarlanmış `true`.

- Ekran Okuyucusu'nın tarama modu odak ClickOnce indirme iletişim kutusu penceresinin denetimleri görsel sırasını ile tutarlı sırasıdır.

**DataGridView geliştirmeleri**

4.7.2, .NET Framework ile başlayan <xref:System.Windows.Forms.DataGridView> denetim sunulan aşağıdaki erişilebilirlik geliştirmeleri:

- Klavyeyi kullanarak satırları sıralanabilir. Bir kullanıcı, geçerli sütuna göre sıralamak için F3 tuşuna kullanabilirsiniz.

- Zaman <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, sütun başlığını geçerli sütun geçerli satır hücrelerde kullanıcı sekmelerde olarak göstermek için rengi değişir.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Özelliği bir <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimini döndürür.

**Geliştirilmiş görsel ipuçları**

- <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> boş bir denetimleriyle <xref:System.Windows.Forms.ButtonBase.Text> odağı aldığında görüntü odak göstergesi özelliği.

**Geliştirilmiş Özellik Kılavuzu desteği**

- <xref:System.Windows.Forms.PropertyGrid> Alt öğeleri artık dönüş denetim bir `true` için <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> yalnızca bir PropertyGrid öğesi etkinleştirildiğinde özelliği.

- <xref:System.Windows.Forms.PropertyGrid> Alt öğelerini dönüş denetleyen bir `false` için <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> PropertyGrid öğesi kullanıcı tarafından yalnızca değiştirilebilir zaman özelliği.

**Geliştirilmiş klavye gezinme**

- <xref:System.Windows.Forms.ToolStripButton> Denetimi içinde bulunan zaman odağı sağlar bir <xref:System.Windows.Forms.ToolStripPanel> olan <xref:System.Windows.Forms.ToolStripPanel.TabStop> özelliğini ayarlayın `true`

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Onay kutusunu ve RadioButton denetimlerini yapılan değişiklikler**

.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimleri, tutarsız ve klasik ve yüksek karşıtlıklı tema, yanlış odak görselleri sahiptir.  Bu sorunlar, denetimleri herhangi bir içerik kümesi gerek duymayacağı durumlarda oluşur.  Bu karmaşık temalar ve odak görsel arasında geçiş görmek sabit yapabilirsiniz.

.NET Framework 4.7.2'da, bu görsel temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.

**Barındırılan bir WPF uygulamasında WinForms denetimleri**

Bu katmandaki ilk veya son denetim WPF ise bir WPF uygulamasında .NET Framework 4.7.1 ve önceki sürümlerinde barındırılan WinForms denetimi için kullanıcıların dışında WinForms katman sekmesinde uygulanamadı <xref:System.Windows.Forms.Integration.ElementHost> denetim. .NET Framework 4.7.2'da, kullanıcıların artık dışında WinForms katman sekmesinde imkanınız olur.

Ancak, hiçbir zaman WinForms katman kaçış odaklanmak kullanan otomatik uygulamalar artık beklendiği gibi çalışmayabilir.

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>Erişilebilirlik 4.7.1 .NET Framework'teki yenilikler

.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET web denetimleri](#aspnet471)

- [.NET SDK Araçları](#tools471)

- [Windows Workflow Foundation (WF) iş akışı Tasarımcısı](#wf471)

<a name="wpf471"></a>
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

- <xref:System.Windows.Controls.Expander> denetimi

    Görsel için odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür. Klavye görsellerini <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de. Örneğin:

    Sonra: 
    
    ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri
 
    Metin <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri yüksek karşıtlık Temalar seçildiğinde daha kolay şimdi. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> denetimi
 
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

- <xref:System.Windows.Controls.DataGrid> denetimi

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

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a>Windows Forms erişilebilirlik geliştirmeleri

.NET Framework 4.7.1'da, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.

**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**

.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sistemi içinde kullanılabilir yüksek karşıtlık modda geliştirilmiş işleme sunar. Windows 10 bazı yüksek karşıtlık sistem renkleri değerlerini değişti ve Windows Forms Windows 10 Win32 Framework'te temel alır. En iyi deneyim için en son sürümünü çalıştırın ve en son işletim sistemi değişiklikleri aşağıdaki tanıyarak test uygulaması ve kaydını yorum Windows 10 app.manifest dosyasında OS satırını desteklenen ekleyerek kabul:

```xml
<!-- Windows 10 -->
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
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a>ASP.NET web denetimleri

.NET Framework 4.7.1 ve Visual Studio 2017 15.3 ile başlayarak, ASP.NET ASP.NET web denetimleri Erişilebilirlik teknolojisi Visual Studio ile nasıl çalıştığıyla artırır. Değişiklikler şunları içerir:

- Eksik UI erişilebilirlik desenlerini denetimlerinde gibi uygulama değişiklik **alan Ekle** iletişim kutusunda **Ayrıntılar görünümü** Sihirbazı'nı veya **yapılandırma ListView** iletişim **ListView** Sihirbazı.

- Yüksek karşıtlık modunda görüntüleme gibi iyileştirmeye yönelik değişiklikler **veri çağrı cihazı alanları Düzenleyicisi**.

- Klavye gezinti iyileştirmeye yönelik değişiklikler karşılaştığında denetimleri için olduğu gibi **alanları** iletişim kutusunda **çağrı cihazı alanları Düzenle** DataPager denetiminin Sihirbazı **ObjectContext yapılandırın**  iletişim kutusunda, veya **veri seçimini Yapılandır** iletişim **Configure Data Source** Sihirbazı.

<a name="tools471"></a>
## <a name="net-sdk-tools"></a>.NET SDK Araçları

[Yapılandırma Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunlarını giderme tarafından geliştirilmiştir. Bunların çoğu tanımlı bir ad veya doğru şekilde uygulanan değil belirli UI Otomasyon düzenleri gibi küçük sorunları oluştu. Çok sayıda kullanıcı yanlış bu değerlerden farkında olmayacaktır olsa da, ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulur. 

Bu geliştirmeler, klavye odağı sipariş gibi önceki bazı davranışları değiştirin.

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) iş akışı Tasarımcısı

İş Akışı Tasarımcısı'nda erişilebilirlik değişiklikler şunları içerir:

- Soldan sağa ve bazı denetimler de yukarıdan sekme sırasını değiştirir:

  - Bağıntı verilerini ayarlamak için Initialize bağıntı penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.

  - İçin içerik tanımı penceresi <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler.

- Klavye ek işlevler kullanılabilir:

  - Bir etkinlik özelliklerini düzenlerken odaklı ilk kez özellik grupları tarafından klavye daraltılmış olabilir.

  - Uyarı simgeleri klavye kullanılarak erişilebilir.

  - **Daha özellikleri** düğmesini **özellikleri** penceredir klavye kullanılarak erişilebilir.

  - Klavye kullanıcılar üstbilgi öğeleri erişim **bağımsız değişkenleri** ve **değişkenleri** bölmeleri iş akışı Tasarımcısı'nın.

- Geliştirilmiş görünürlük ne zaman gibi odaklanılan öğelerinin:

  - İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzları satır ekleme.

  - Alanları aracılığıyla sekme <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.

  - Değişkenleri veya bağımsız değişkenleri için varsayılan değerleri ayarlama

- Ekran okuyucular şimdi düzgün tanıyabilmesi için:

  - İş Akışı Tasarımcısı'nda kesme noktalarını ayarlayın.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikler.
  - İçeriğini <xref:System.ServiceModel.Activities.Receive> etkinlik.

  - Hedef türü <xref:System.Activities.Statements.InvokeMethod> etkinlik.

  - Özel durum birleşik giriş kutusu ve son olarak konusunun <xref:System.Activities.Statements.TryCatch> etkinlik.

  - İleti türü birleşik giriş kutusu, bağıntı başlatıcıları eklemek penceresinde, içerik tanımı penceresi ve mesajlaşma etkinlikleri CorrelatesOn tanımı penceresinde Bölümlendirici (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Durum makinesi geçişler ve hedeflere geçer.

  - Ek açıklamalar ve bağlayıcıların <xref:System.Activities.Statements.FlowDecision> etkinlikler.

  - Etkinlikler (sağ tıklatma) bağlam menülerini.

  - Özellik değeri düzenleyicileri, aramayı Temizle düğmesi, kategoriye göre ve alfabetik sıralama düğmeleri ve özellikleri ızgara ifade Düzenleyicisi iletişim.

  - Yakınlaştırma yüzdesini iş akışı Tasarımcısı'nda.

  - Ayırıcı <xref:System.Activities.Statements.Parallel> ve <xref:System.Activities.Statements.Pick> etkinlikler.

  - <xref:System.Activities.Statements.InvokeDelegate> Etkinlik.

  - Sözlük etkinlikler için türlerini Seç penceresi (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`vb..).

  - Gözat ve .NET türünü seç penceresi.

  - İş Akışı Tasarımcısı'nda içerik.

- Yüksek karşıtlıklı tema seçen kullanıcılar iş akışı Tasarımcısı ve daha iyi karşıtlık oranları öğeleri için odak öğeleri kullanılan daha belirgin seçim kutularının arasındaki gibi kendi denetimlerinin görünürlüğünü içindeki birçok geliştirmeden görürsünüz.

## <a name="see-also"></a>Ayrıca Bkz.

[.NET Framework'teki yenilikler](whats-new.md)
 
