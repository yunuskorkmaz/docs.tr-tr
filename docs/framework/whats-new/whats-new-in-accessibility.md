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
ms.openlocfilehash: e9b9d1c8a059a85f2b5137e568ec6ad562ca0eb9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680316"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>Erişilebilirlik .NET Framework'teki yenilikler

.NET Framework uygulamaları daha erişilebilir, kullanıcılarınız için duruma getirmeyi amaçlar. Yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın erişilebilirlik özellikleri sağlar. .NET Framework, .NET Framework 4.7.1 ile başlayarak, çok sayıda erişilebilir uygulamalar oluşturmaları için geliştiricileri erişilebilirlik geliştirmeleri içerir. 

## <a name="accessibility-switches"></a>Erişilebilirlik anahtarları

Uygulamanızı .NET Framework 4.7 veya önceki bir sürümünü hedefler, ancak .NET Framework 4.7.1 çalıştıran erişilebilirlik özelliklerini geri çevirmek için yapılandırabilirsiniz veya üzeri. Uygulamanızı .NET Framework 4.7.1'i hedefleyen, eski özellikleri (ve değil yararlanın erişilebilirlik özellikleri) kullanacak şekilde de yapılandırabilirsiniz veya üzeri. Erişilebilirlik özellikleri içeren .NET Framework'ün her sürümü eklediğiniz bir sürüme özgü erişilebilirlik anahtara sahip [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası. Desteklenen anahtarlar şunlardır:

|Sürüm|Anahtar|
|---|---|
|.NET framework 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
|.NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Erişilebilirlik geliştirmeleri yararlanma

.NET Framework 4.7.1'i hedefleyen uygulamalar için varsayılan olarak etkin ya da daha yeni erişilebilirlik özellikleri. Ayrıca, .NET Framework'ün önceki sürümünü hedefleyecek ancak .NET Framework 4.7.1 üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar eski erişilebilirlik davranışlarını dışarı (ve böylece erişilebilirlik iyileştirmeleri yararlanmak) anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyası ve kendi değerini bölümünü `false`. Erişilebilirlik geliştirmeleri .NET Framework 4.7.1 sunmuştur kabul etmek nasıl aşağıda gösterilmiştir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

Erişilebilirlik özellikleri sonraki bir sürümü .NET Framework'ün kabul etmek isterseniz, aynı zamanda açıkça özellikleri için .NET Framework'ün önceki sürümlerinden kabul gerekir. Hem .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik geliştirmeleri avantajlarından faydalanmak için uygulamanızı yapılandırma aşağıdakileri gerektirir [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesi:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Eski davranışı geri yükleme

.NET Framework 4.7.1 ile başlayan sürümlerini hedefleyen uygulamalar devre dışı bırakabilirsiniz erişilebilirlik özellikleri anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası ve kendi değerini `true`. Örneğin, aşağıdaki yapılandırma, .NET Framework 4.7.2 sunulan erişilebilirlik özellikleri dışında kabul eder:  

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

.NET Framework 4.7.2 ile başlayarak, Windows Forms yüksek karşıtlıklı tema işletim sistemi tarafından tanımlanan renk kullanır. Bu, aşağıdaki denetimlerini etkiler:

- Aşağı açılan okunu <xref:System.Windows.Forms.ToolStripDropDownButton> denetimi.

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> ile denetimleri <xref:System.Windows.Forms.ButtonBase.FlatStyle> kümesine <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> veya <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>. Daha önce seçilen metin ve arkaplan renklerini değil çakışan ve okunması zor.

- Denetimleri içinde yer alan bir <xref:System.Windows.Forms.GroupBox> olan kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.
 
- <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, Ve <xref:System.Windows.Forms.ToolStripDropDownButton> artan parlaklık bir Karşıtlık oranı yüksek karşıtlık modunda olan denetimler.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Ekran Okuyucusu geliştirmeleri**

.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği gibi geliştirilmiştir:

- Değerini duyuruyor <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> Duyurusu metni hareketlendiremezsiniz bir <xref:System.Windows.Forms.ToolStripMenuItem>. 

- Ne zaman gösteren bir <xref:System.Windows.Forms.ToolStripMenuItem> sahip kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.

- Onay kutusunun durumunu hakkında geri bildirim sağlar, <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> özelliği `true`.

- Okuyucu'nın tarama modu odak sipariş ClickOnce indirme iletişim kutusu penceresine denetimleri visual sırasını tutarlıdır.

**DataGridView geliştirmeleri**

4.7.2, .NET Framework ile başlayarak <xref:System.Windows.Forms.DataGridView> denetimi aşağıdaki erişilebilirlik geliştirmeleri kullanıma sunulan:

- Klavyeyi kullanarak satır sıralanabilir. Bir kullanıcı, geçerli bir sütuna göre sıralamak için F3 tuşuna kullanabilirsiniz.

- Zaman <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, sütun üst bilgisinin geçerli sütunun hücre geçerli satırda aracılığıyla kullanıcı sekmeler olarak belirtmek için rengi değişir.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Özelliği bir <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimini döndürür.

**Geliştirilmiş görsel ipuçları**

- <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> boş denetimleriyle <xref:System.Windows.Forms.ButtonBase.Text> odağı aldıklarında bir odak göstergesi görüntü özelliği.

**Gelişmiş özellik Kılavuzu desteği**

- <xref:System.Windows.Forms.PropertyGrid> Alt öğeleri artık dönüş denetleyen bir `true` için <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> PropertyGrid öğe etkinleştirildiğinde özelliği.

- <xref:System.Windows.Forms.PropertyGrid> Alt öğeleri iade denetleyen bir `false` için <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> özelliğine yalnızca bir PropertyGrid öğesi kullanıcı tarafından değiştirilebilir.

**Geliştirilmiş klavye gezintisi**

- <xref:System.Windows.Forms.ToolStripButton> Denetimi içinde bulunan zaman odağı sağlar bir <xref:System.Windows.Forms.ToolStripPanel> olan <xref:System.Windows.Forms.ToolStripPanel.TabStop> özelliği ayarlayın `true`

<a name="wpf472"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Değişiklikleri için onay kutusunu ve RadioButton denetimleri**

.NET Framework 4.7.1 ve önceki sürümlerinde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimleri, tutarsız ve klasik ve yüksek karşıtlık temalar, yanlış odak görsel sahiptir.  Bu sorunlar burada denetimleri herhangi bir içerik kümesi olmayan durumlarda oluşur.  Bu tema kafa karıştırıcı ve odak görsel arasında geçiş görmek sabit yapabilirsiniz.

.NET Framework'teki 4.7.2 Bu görsel temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.

**Barındırılan bir WPF uygulamasında WinForms denetimleri**

Bu katmandaki ilk veya son denetim WPF ise .NET Framework 4.7.1 ve önceki sürümlerinde WPF uygulamasında barındırılan WinForms denetimi için WinForms katman dışında kullanıcılar sekmesinde uygulanamadı <xref:System.Windows.Forms.Integration.ElementHost> denetimi. .NET Framework'teki 4.7.2 kullanıcılar artık dışında WinForms katman sekmesinde olanağına sahip olursunuz.

Ancak, hiçbir zaman WinForms katman kaçış odaklanmak otomatik uygulamaları artık beklendiği gibi çalışmayabilir.

## <a name="whats-new-in-accessibility-in-the-net-framework-471"></a>.NET Framework 4.7.1 erişilebilirlik yenilikleri

.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET web denetimleri](#aspnet471)

- [.NET SDK Tools](#tools471)

- [Windows Workflow Foundation (WF) iş akışı Tasarımcısı](#wf471)

<a name="wpf471"></a>
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ekran Okuyucusu geliştirmeleri**

Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucular etkileyen aşağıdaki geliştirmeleri içerir:

- .NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.Expander> denetimleri düğme olarak ekran okuyucular tarafından Duyuruldu. .NET Framework 4.7.1 ile başlayarak, bunlar Genişletilebilir/daraltılabilir gruplar olarak doğru şekilde bildirilir.

- .NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.DataGridCell> denetimleri ekran okuyucular tarafından bildirilen "özel" .NET Framework 4.7.1 ile başlayarak, yöneticiler artık doğru şekilde veri kılavuz hücresi (yerelleştirilmiş) bildirilir.
 
- .NET Framework 4.7.1 ile başlayarak, adı düzenlenebilir bir ekran okuyucular duyurmaktan <xref:System.Windows.Controls.ComboBox>.

- .NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.PasswordBox> denetimleri veya "öğesi Görünümü'nde" olarak bildirilen olduğu Aksi takdirde yanlış bir davranışı. .NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir.

**UIAutomation LiveRegion desteği**

Ekran okuyucular ekran okuyucusu Yardım kişiler gibi bir uygulama kullanıcı Arabirimi içeriği genellikle metin okuma odağa sahip kullanıcı Arabirimi içeriği çıktı tarafından okuyun. Ancak, bir kullanıcı Arabirimi öğesi değiştirir ve odağı yok, Kullanıcı bildirim değil ve önemli bilgiler eksik. Bu sorunu çözme sırasında Canlı bölge hedeflenir. Bir geliştirici, ekran okuyucu veya bir kullanıcı Arabirimi öğesi için önemli bir değişiklik yapılmadığını diğer UIAutomation istemci bildirmek için bunları kullanabilirsiniz. Ekran Okuyucu sonra nasıl ve ne zaman karar verebilirsiniz kullanıcıya bu değişikliği bildirmek için. 

Canlı bölge desteklemek için aşağıdaki API'leri için WPF eklenmiştir:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> tanımlamak alanları **LiveSetting** özelliği ve **LiveRegionChanged** olay. XAML kullanılarak ayarlanabilir.

- **AutomationProperties.LiveSetting** ekran okuyucu önem UI değişikliğinin kullanıcıya bildirir özelliğe bağlı.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Tanımlayan özellik **AutomationProperties.LiveSetting** ekli özellik.
 
- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Sağlamak için geçersiz kılınabilir bir yöntemi, bir **LiveSetting** değeri.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> almanıza ve ayarlamanıza yöntemleri bir **LiveSetting** değeri.
 
- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası tanımlayan sabit listesi **LiveSetting** değerleri:

   - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Canlı bölge içeriğini değiştiyse öğesi bildirimleri göndermez.   
   - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Canlı bölge içeriğini değiştiyse öğe interruptive olmayan bildirimleri gönderir.   

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Canlı bölge içeriğini değiştiyse öğe interruptive bildirimleri gönderir.   

Ayarlayarak bir LiveRegion oluşturabilirsiniz **AutomationProperties.LiveSetting** aşağıdaki örnekte gösterildiği gibi ilgi alanı, öğe özelliği:   

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Canlı bölge verileri değiştirir ve ekran okuyucu bildirmeniz gerekir, siz açıkça bir olay aşağıdaki örnekte gösterildiği gibi neden olmaktadır.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```
```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Yüksek Karşıtlık**

.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimleri için yüksek karşıtlık geliştirmeleri yapıldı. Bunlar artık ne zaman görülebilir <xref:System.Windows.SystemParameters.HighContrast%2A> tema ayarlanır. Bu güncelleştirmeler şunlardır:

- <xref:System.Windows.Controls.Expander> Denetimi

    Görseli odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür. Klavye görseller için <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de. Örneğin:

    Sonra: 
    
    ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri
 
    Metinde <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri, yüksek karşıtlık Temalar da seçildiğinde daha kolay sunuldu. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox> Denetimi
 
    .NET Framework 4.7.1, devre dışı kenarlık başlangıç <xref:System.Windows.Controls.ComboBox> devre dışı bırakılmış metinlerin aynı renge denetimidir. Örneğin:
    
    Sonra: 

     ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri önce devre dışı](media/combo-disabled-before.png)

    Sonra:   

     ![ComboBox kenarlık ve metin sonra erişilebilirlik iyileştirmeleri devre dışı](media/combo-disabled-after.png)

    Ayrıca, doğru bir Tema rengi devre dışı bırakılmış ve odaklanmış düğmelerini kullanın.

    Sonra:

    ![Erişilebilirlik geliştirmeleri önce düğme Tema renkleri](media/button-themes-before.png) 
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra düğme Tema renkleri](media/button-themes-after.png) 

    Son olarak, .NET Framework 4.7 ve önceki sürümleri, ayar, bir <xref:System.Windows.Controls.ComboBox> denetimin stil `Toolbar.ComboBoxStyleKey` görünmemesini açılan liste okunu neden oldu. .NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 
    
    Sonra: 

    ![Erişilebilirlik geliştirmeleri sonra Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <xref:System.Windows.Controls.DataGrid> Denetimi

    .NET Framework 4.7.1'i, sıralama göstergesi oka başlayarak <xref:System.Windows.Controls.DataGrid> Tema renkleri kullandığı düzeltmek artık denetler. Örneğin:

    Sonra: 

    ![Erişilebilirlik geliştirmeleri önce sıralama göstergesi oku](media/sort-indicator-before.png) 
    
    Sonra:   
 
    ![Erişilebilirlik geliştirmeleri sonra sıralama göstergesi oku](media/sort-indicator-after.png) 
    
    Ayrıca, .NET Framework 4.7 ve önceki sürümlerinde, varsayılan bağlantı stilini fare yanlış bir renk yüksek karşıtlık modlarında değiştirilecek. Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir. Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusu sütunları, .NET Framework 4.7.1 ile başlayarak klavye odağı geri bildirim için beklenen renkleri kullanır.

    Sonra: 

    ![DataGrid varsayılan bağlantı stilini önce erişilebilirlik geliştirmeleri](media/default-link-style-before.png) 
 
    Sonra:    
  
    ![DataGrid varsayılan bağlantı stilini sonra erişilebilirlik geliştirmeleri](media/default-link-style-after.png)  

.NET Framework 4.7.1 WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz. [erişilebilirlik geliştirmeleri ' WPF'de](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>
## <a name="windows-forms-accessibility-improvements"></a>Windows Forms erişilebilirlik geliştirmeleri

.NET Framework 4.7.1'da, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.

**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**

.NET Framework 4.7.1 ile başlayarak, işletim sistemi içinde kullanılabilir olan yüksek karşıtlık modda geliştirilmiş işleme çeşitli WinForms denetimler sunar. Windows 10 bazı yüksek karşıtlık sistem renkleri için değerleri değişti ve Windows Forms, Windows 10 Win32 altyapısını temel alır. En iyi deneyim için en son Windows sürümüne çalıştırın ve en son işletim sistemi değişiklikleri için aşağıdaki görünür, böylece bir app.manifest dosyasındaki bir test uygulaması ve Çalıştır-açıklama Windows 10 işletim sistemi satırı desteklenen ekleyerek kabul et:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```
Yüksek Karşıtlık değişiklikler bazı örnekleri şunlardır:

- Açılır menüdeki onay <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.

- Bu onay kutusu seçildiğinde, devre dışı <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.

- Seçili metinde <xref:System.Windows.Forms.Button> Denetim seçim rengi ile karşılaştırır.

- Devre dışı bırakılmış metinlerin okunmasını daha kolay olur. Örneğin:

    Sonra:

    ![Erişilebilirlik geliştirmeleri önce devre dışı bırakılmış metin](media/wf-disabled-before.png) 

    Sonra:

    ![Erişilebilirlik geliştirmeleri sonra devre dışı bırakılmış metin](media/wf-disabled-after.png) 

- İş parçacığı özel durum iletişim kutusunda yüksek karşıtlık geliştirmeleri.

**Geliştirilmiş ekran okuyucu desteği**

Windows Forms'ta .NET Framework 4.7.1 ekran okuyucu için aşağıdaki erişilebilirlik geliştirmeleri içerir:

- <xref:System.Windows.Forms.MonthCalendar> Denetim, ekran okuyucusu tarafından yanı sıra diğer UI Otomasyon araçları tarafından erişilebilir.

- <xref:System.Windows.Forms.CheckedListBox> Denetim, ekran okuyucusu bir liste öğesi değerini değiştirdiyseniz kullanıcıyı uyarır, böylece bir öğenin denetim durumu değiştiğinde bildirir.
 
- <xref:System.Windows.Forms.DataGridViewCell> Denetimi için ekran okuyucusu doğru salt okunur durumunu raporlar.
 
- Okuyucu artık devre dışı okur <xref:System.Windows.Forms.ToolStripMenuItem> metin, daha önce devre dışı bırakılmış menü öğelerinin üzerine atlarsınız ise.

**UIAutomation erişilebilirlik desenleri için gelişmiş destek**

Erişilebilirlik teknoloji Araçlar, geliştiricilerin .NET Framework 4.7.1 ile başlayarak, ortak API erişilebilirlik desenleri ve birden çok WinForms denetimi özelliklerini yararlanabilirsiniz. Bu erişilebilirlik geliştirmeleri içerir:

- <xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ToolStripSplitButton> artık destek [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).
 
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Artık destekliyor [geçiş deseni](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).
 
- <xref:System.Windows.Forms.ToolStripItem> Denetim destekler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).

- <xref:System.Windows.Forms.NumericUpDown> Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri Destek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği.

**Geliştirilmiş özelliği tarayıcı deneyimi**

.NET Framework 4.7.1 ile başlayarak, Windows Forms içerir:

- Daha iyi klavye gezintisi aracılığıyla çeşitli yanıdaki açılan seçimi windows.
- Gereksiz sekme duraklarının azaltma.
- Daha iyi denetim türlerini raporlama.
- Geliştirilmiş ekran okuyucu davranışı.
 
<a name="aspnet471"></a>
## <a name="aspnet-web-controls"></a>ASP.NET web denetimleri

ASP.NET .NET Framework 4.7.1 ve Visual Studio 2017 15.3 ile başlayarak, Visual Studio'da Erişilebilirlik teknolojisi ile ASP.NET web denetimleri nasıl artırır. Değişiklikler şunları içerir:

- Eksik kullanıcı Arabirimi erişilebilirliği desenleri gibi denetimleri içinde uygulamak için değişiklikleri **alan Ekle** iletişim kutusunda **Ayrıntılar görünümü** Sihirbazı'nı veya **yapılandırma ListView** iletişim **ListView** Sihirbazı.

- Yüksek karşıtlık modunda görüntüleme gibi iyileştirmeye yönelik değişiklikler **veri çağrı alanları Düzenleyicisi**.

- Klavye ile gezintiyi iyileştirmeye yönelik değişiklikler deneyimleri denetimler için gibi **alanları** iletişim kutusunda **çağrı alanları Düzenle** DataPager denetimi Sihirbazı **ObjectContext yapılandırın**  iletişim kutusunda veya **yapılandırma veri seçimi** iletişim **veri kaynağı yapılandırma** Sihirbazı.

<a name="tools471"></a>
## <a name="net-sdk-tools"></a>.NET SDK Tools

[Yapılandırma Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunları çözme tarafından geliştirilmiştir. Bunların çoğu tanımlanmayan bir ad veya doğru uygulanmadı belirli bir UI Otomasyon düzenleri gibi küçük problemler yoktu. Birçok kullanıcı bu yanlış değerini kullanan sunulacaktır, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulabilirsiniz. 

Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.

<a name="wf471"></a>
## <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) iş akışı Tasarımcısı

İş akışı tasarımcısında erişilebilirlik değişiklikler şunları içerir:

- Sekme sırası, soldan sağa ve yukarıdan aşağıya bazı denetimlerinde değiştirir:

  - Upravit data korelace için ayarlamak için Initialize bağıntı penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.

  - İçerik tanımı penceresi <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler.

- Daha fazla işlev klavye mevcuttur:

  - Bir etkinliğin özelliklerini düzenlerken, özellik grupları tarafından klavye odaklı ilk kez daraltılabilirler.

  - Uyarı simgeleri klavye tarafından erişilebilir.

  - **Daha özellikleri** düğmesine **özellikleri** pencere, klavye tarafından erişilebilir.

  - Klavye kullanıcılarının üstbilgi öğeleri erişebileceği **bağımsız değişkenleri** ve **değişkenleri** iş akışı Tasarımcısı bölmelerini.

- Geliştirilmiş görünürlük odaklanılan ne zaman gibi öğeleri:

  - İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzları için satırlar ekleme.

  - Alanları arasında sekmeyle gitmeyi <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.

  - Değişken veya bağımsız değişkenleri için varsayılan değerleri ayarlama

- Artık ekran okuyucular düzgün tanıyabilmesi:

  - İş Akışı Tasarımcısı'nda kesme noktalarını ayarlayın.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikler.
  - İçeriğini <xref:System.ServiceModel.Activities.Receive> etkinlik.

  - Hedef türü için <xref:System.Activities.Statements.InvokeMethod> etkinlik.

  - Özel durum birleşik giriş kutusu ve son olarak konusundaki <xref:System.Activities.Statements.TryCatch> etkinlik.

  - İleti türü açılan kutusu, bağıntı başlatıcılar Ekle penceresi, içerik tanım penceresini ve mesajlaşma etkinlikleri CorrelatesOn tanımı penceresinde ayırıcı (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>).

  - Durum makinesi geçişler ve hedeflere geçer.

  - Ek açıklamalar ve bağlayıcılarda <xref:System.Activities.Statements.FlowDecision> etkinlikler.

  - Etkinlikler için (sağ tıklama) bağlam menüleri.

  - Özellik değer düzenleyicileri, aramayı Temizle düğmesi, kategoriye göre ve alfabetik sıralama düğmeler ve Özellikler kılavuzundaki ifade Düzenleyicisi iletişim kutusu.

  - İş akışı tasarımcısında yakınlaştırma yüzdesi.

  - Ayırıcı <xref:System.Activities.Statements.Parallel> ve <xref:System.Activities.Statements.Pick> etkinlikler.

  - <xref:System.Activities.Statements.InvokeDelegate> Etkinlik.

  - Sözlük etkinlikler için seçim türlerinin penceresi (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`vb..).

  - Göz atma ve .NET türünü seç penceresi.

  - İş akışı tasarımcısında içerik haritaları.

- Yüksek karşıtlıklı tema seçen kullanıcılar, iş akışı Tasarımcısı gibi öğeleri ve odak öğeleri için kullanılan daha belirgin seçim kutuları arasında daha iyi kontrast, Denetim ve görünürlüğü içindeki birçok geliştirmeden görürsünüz.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework'teki yenilikler](whats-new.md)

