---
title: .NET Framework'de erişilebilirlikte yenilikler
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 4dbc2024aa2e956b23030ae6eab987e65e006d12
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400185"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework'de erişilebilirlikte yenilikler

.NET Framework, uygulamaları kullanıcılarınız için daha erişilebilir hale getirmeyi amaçlamaktadır. Erişilebilirlik özellikleri, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak sağlar. .NET Framework 4.7.1 ile başlayarak ,.NET Framework, geliştiricilerin erişilebilir uygulamalar oluşturmasına olanak tanıyan çok sayıda erişilebilirlik geliştirmesi içerir.

## <a name="accessibility-switches"></a>Erişilebilirlik anahtarları

Uygulamanızı ,NET Framework 4.7 veya daha önceki bir sürümü hedefliyorsa, ancak .NET Framework 4.7.1 veya sonraki sürümde çalışıyorsa erişilebilirlik özelliklerini seçecek şekilde yapılandırabilirsiniz. Uygulamanızı ,NET Framework 4.7.1 veya daha sonrasını hedefliyorsa eski özellikleri kullanacak (ve erişilebilirlik özelliklerinden yararlanmayacak şekilde) de yapılandırabilirsiniz. .NET Framework'ün erişilebilirlik özelliklerini içeren her sürümünde, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasının bölümündeki öğeye eklediğiniz sürüme özgü erişilebilirlik anahtarı vardır. Desteklenen anahtarlar şunlardır:

|Sürüm|Anahtar|
|---|---|
|.NET Çerçeve 4.7.1|"Switch.UseLegacyAccessibilityFeatures"|
| .NET Framework 4.7.2|"Switch.UseLegacyAccessibilityFeatures.2"|
| .NET Framework 4.8|"Switch.UseLegacyAccessibilityFeatures.3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Erişilebilirlik geliştirmelerinden yararlanma

Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 veya sonraki lerini hedefleyen uygulamalar için varsayılan olarak etkinleştirilir. Buna ek olarak, .NET Framework'ün önceki bir sürümünü hedefleyen ancak .NET Framework 4.7.1 veya daha sonra üzerinde çalışan uygulamalar, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasının bölümündeki öğeye anahtarlar ekleyerek ve değerini `false`belirleyerek eski erişilebilirlik davranışlarını devre dışı edebilir (ve bu nedenle erişilebilirlik iyileştirmelerinden yararlanabilir). Aşağıda ,NET Framework 4.7.1'de tanıtılan erişilebilirlik geliştirmelerine nasıl tercih edilebilmektedir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

.NET Framework'ün sonraki bir sürümünde erişilebilirlik özelliklerini seçmeyi seçerseniz, .NET Framework'ün önceki sürümlerindeki özellikleri de açıkça seçmeniz gerekir. Uygulamanızı hem .NET Framework 4.7.1 hem de 4.7.2'deki erişilebilirlik iyileştirmelerinden yararlanacak şekilde yapılandırmak için aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğe yi gerektirir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

Uygulamanızı .NET Framework 4.7.1, 4.7.2 ve 4.8'deki erişilebilirlik iyileştirmelerinden yararlanacak [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) şekilde yapılandırmak için aşağıdaki öğe yi gerektirir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Eski davranışı geri alma

4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasıbölümündeki elemana anahtarlar ekleyerek ve değerini 'ye `true`ayarlayarak erişilebilirlik özelliklerini devre dışı düşürebilir. Örneğin, aşağıdaki yapılandırma .NET Framework 4.7.2'de tanıtılan erişilebilirlik özelliklerinden vazgeçer:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>.NET Framework 4.8'de erişilebilirlikte yenilikler

.NET Framework 4.8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Windows İş Akışı Temeli (WF) iş akışı tasarımcısı](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a>Windows Forms

.NET Framework 4.8'de, Windows Formları sık kullanılan birçok denetime LiveRegions ve Bildirim Olayları için destek ekler. Ayrıca, bir kullanıcı klavyeyi kullanarak denetime gittiğinde ToolTips için destek ekler.

**Etiketlerde ve StatusStrips'te UIA LiveRegions Desteği**

UIA LiveRegions, uygulama geliştiricilerin, kullanıcının çalıştığı yerin dışında bulunan bir denetimdeki metin değişikliğini ekran okuyucularına bildirmesine olanak tanır. Bu, örneğin, bağlantı durumunu <xref:System.Windows.Forms.StatusStrip> gösteren bir denetim için yararlıdır. Bağlantı bırakılırsa ve durum değişirse, geliştirici ekran okuyucuya bildirmek isteyebilir.

.NET Framework 4.8 ile başlayarak, Windows Forms hem <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> denetimler hem de denetimler için UIA LiveRegions uygular. Örneğin, aşağıdaki kod LiveRegion adlı <xref:System.Windows.Forms.Label> `label1`bir denetim kullanır:

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Ekran Okuyucusu, kullanıcının uygulamayla nerede etkileşimde bulunduğuna bakılmaksızın "Hazır" bildirir.

Ayrıca bir LiveRegion <xref:System.Windows.Forms.UserControl> olarak uygulayabilirsiniz:

```csharp
using System;
using System.Windows.Forms;
using System.Windows.Forms.Automation;

namespace WindowsFormsApplication
{
   public partial class UserControl1 : UserControl, IAutomationLiveRegion
   {
      public UserControl1()
      {
         InitializeComponent();
      }

      public AutomationLiveSetting AutomationLiveSetting { get; set; }
      private AutomationLiveSetting IAutomationLiveRegion.GetLiveSetting()
      {
         return this.AutomationLiveSetting;
      }

      protected override void OnTextChanged(EventArgs e)
      {
         base.OnTextChanged(e);
         AutomationNotifications.UiaRaiseLiveRegionChangedEvent(this.AccessibilityObject);
      }
   }
}
```

**UIA bildirim olayları**

Windows 10 Fall Creators Update'te tanıtılan UIA Bildirimi etkinliği, uygulamanızın, Kullanıcı Bira'da karşılık gelen bir denetime gerek kalmadan, ekran okuyucusu yalnızca olayla ilgili olarak sağladığınız metne dayalı bir duyuru yapmasına yol açan bir Kullanıcı Durumu etkinliğini yükseltmesine olanak tanır. Bazı senaryolarda bu, uygulamanızın erişilebilirliğini önemli ölçüde artırmanın basit bir yoludur. Ayrıca uzun zaman alabilir bazı sürecin ilerleme bildirmek için yararlı olabilir. UIA Bildirim Etkinlikleri hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need)

Aşağıdaki örnekbildirim [olayını](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)yükseltir:

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Klavye erişiminde Araç İpuçları**

.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, bir denetim [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca bir fare işaretçisini denetime taşıyarak açılır. .NET Framework 4.8 ile başlayarak, klavye kullanıcısı denetime sekme tuşu veya ok tuşlarını kullanarak veya değiştirici tuşları olmadan odaklanarak bir denetimin araç ucunu tetikleyebilir. Bu özel erişilebilirlik geliştirme ek bir [AppContext anahtarı](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)gerektirir:

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6.1"/>
   </startup>
   <runtime>
      <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false  -->
      <!-- Please note that disabling Switch.UseLegacyAccessibilityFeatures, Switch.UseLegacyAccessibilityFeatures.2 and Switch.UseLegacyAccessibilityFeatures.3 is required to disable Switch.System.Windows.Forms.UseLegacyToolTipDisplay -->
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.System.Windows.Forms.UseLegacyToolTipDisplay=false"/>
   </runtime>
</configuration>
```

Aşağıdaki şekilde, kullanıcı klavyeli bir düğme seçtiğinde araç ipucunu gösterir.

![Kullanıcı klavyeyle düğmeye gittiğinde araç ucunun ekran görüntüsü.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.8 ile başlayarak WPF bir dizi erişilebilirlik iyileştirmesi içerir.

**Ekran ekranları artık Daraltılmış veya Gizli görünürlüğe sahip öğeleri duyurmadı**

Daraltılmış veya gizli görünürlüğe sahip öğeler artık ekran okuyucu tarafından duyurulmadı. Görünürlüğe sahip öğeler içeren <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> veya <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> kullanıcıya duyurulması durumunda ekran okuyucular tarafından yanlış tanıtılabilen kullanıcı arabirimleri. .NET Framework 4.8 ile başlayarak, WPF artık UIAutomation ağacının Denetim Görünümü'nde daraltılmış veya gizli öğeleri içermez, böylece ekran okuyucular artık bu öğeleri duyuramaz.

**SeçimTextBrush özelliği olmayan Adorner tabanlı metin seçimi ile kullanım için**

.NET Framework 4.7.2'de WPF, Adorner <xref:System.Windows.Controls.PasswordBox> katmanını kullanmadan metin seçimi ve çizim <xref:System.Windows.Controls.TextBox> yapma olanağı nı ekledi. Bu senaryoda <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>seçilen metnin ön plan rengi .

.NET Framework 4.8, `SelectionTextBrush`geliştiricilerin Adorner tabanlı olmayan metin seçimini kullanırken seçilen metin için belirli fırçayı seçmelerine olanak tanıyan yeni bir özellik ekler. Bu özellik yalnızca <xref:System.Windows.Controls.Primitives.TextBoxBase>-türetilmiş <xref:System.Windows.Controls.PasswordBox> denetimlerde ve Adorner tabanlı olmayan metin seçimi etkinleştirilmiş WPF uygulamalarında denetim de çalışır. <xref:System.Windows.Controls.RichTextBox> Denetimde çalışmıyor. Adorner tabanlı olmayan metin seçimi etkinleştirilemezse, bu özellik yoksayılır.

Bu özelliği kullanmak için XAML kodunuza eklemeniz ve uygun fırçayı veya bağlamayı kullanmanız yeterlidir. Elde edilen metin seçimi aşağıdaki gibi görünür:

![Merhaba Dünya kelimeleriyle çalışan uygulamanın ekran görüntüsü seçildi.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

Uygun gördüğünüz herhangi bir `SelectionBrush` `SelectionTextBrush` arka plan ve ön plan renk kombinasyonu oluşturmak için ve özelliklerinin kullanımını birleştirebilirsiniz.

**UIAutomation ControllerFor özelliği ne destek**

UIAutomation'ın `ControllerFor` özelliği, bu özelliği destekleyen otomasyon öğesi tarafından manipüle edilen bir dizi otomasyon öğesini döndürür. Bu özellik genellikle Otomatik öner erişilebilirlik için kullanılır. `ControllerFor`bir otomasyon öğesi uygulama kullanıcı larının veya masaüstünün bir veya daha fazla kesimini etkilediğinde kullanılır. Aksi takdirde, denetim işleminin etkisini UI öğeleriyle ilişkilendirmek zordur. Bu özellik, denetimlerin özellik için bir `ControllerFor` değer sağlama özelliğini ekler.

.NET Framework 4.8 yeni bir <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>sanal yöntem ekler. `ControllerFor` Özellik için bir değer sağlamak için, bu yöntemi `List<AutomationPeer>` geçersiz kılmak ve bu <xref:System.Windows.Automation.Peers.AutomationPeer>tarafından manipüle edilen denetimler için bir döndürmeniz yeterlidir:

```csharp
public class AutoSuggestTextBox: TextBox
{
   protected override AutomationPeer OnCreateAutomationPeer()
   {
      return new AutoSuggestTextBoxAutomationPeer(this);
   }

   public ListBox SuggestionListBox;
}

internal class AutoSuggestTextBoxAutomationPeer : TextBoxAutomationPeer
{
   public AutoSuggestTextBoxAutomationPeer(AutoSuggestTextBox owner) : base(owner)
   {
   }

   protected override List<AutomationPeer> GetControlledPeersCore()
   {
      List<AutomationPeer> controlledPeers = new List<AutomationPeer>();
      AutoSuggestTextBox owner = Owner as AutoSuggestTextBox;
      controlledPeers.Add(UIElementAutomationPeer.CreatePeerForElement(owner.SuggestionListBox));
      return controlledPeers;
   }
}
```

**Klavye erişiminde araç ipuçları**

.NET Framework 4.7.2 ve önceki sürümlerde, araç ipuçları yalnızca kullanıcı fare imlecini bir denetimüzerinde gezindiğinde görüntülenir. .NET Framework 4.8'de, araç ipuçları klavye odağının yanı sıra klavye kısayolu aracılığıyla da görüntülenir.

Bu özelliği etkinleştirmek için bir uygulamanın .NET Framework 4.8'i hedeflemesi veya `Switch.UseLegacyAccessibilityFeatures.3` `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını kullanarak kabul etmesi gerekir. Örnek bir uygulama yapılandırma dosyası aşağıda veda edilir:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false;Switch.UseLegacyToolTipDisplay=false" />
   </runtime>
</configuration>
```

Etkinleştirildiğinde, bir araç ipucu içeren tüm denetimler, denetim klavye odağı aldıktan sonra görüntülenir. Araç ipucu zaman içinde veya klavye odağı değiştiğinde kapatılabilir. Kullanıcılar ayrıca yeni bir klavye kısayolu olan Ctrl + Shift + F10'u kullanarak araç ucunu el ile kapatabilirler. Araç ipucu çıkarıldıktan sonra aynı klavye kısayolu kullanılarak yeniden görüntülenebilir.

> [!NOTE]
> [Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) Denetimlerde <xref:System.Windows.Controls.Ribbon.Ribbon> şerit araç ipuçları klavye odağında gösterilmez; yalnızca klavye kısayolu üzerinden gösterirler.

**SizeOfSet ve PositionInSet UIAutomation özellikleri için destek eklendi**

Windows 10, `SizeOfSet` `PositionInSet`bir kümedeki öğelerin sayısını açıklamak için uygulamalar tarafından kullanılan iki yeni UIAutomation özelliğini tanıttı. Ekran okuyucular gibi UIAutomation istemci uygulamaları daha sonra bu özellikler için bir uygulamayı sorgulayabilir ve uygulamanın Kullanıcı Arabirimi'nin doğru bir temsilini açıklayabilir.

.NET Framework 4.8 ile başlayarak, WPF bu iki özelliği WPF uygulamalarında UIAutomation'a maruz bırakır. Bu iki şekilde gerçekleştirilebilir:

- Bağımlılık özelliklerini kullanarak.

  WPF iki yeni bağımlılık <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> özelliği <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>ekler ve . Bir geliştirici değerlerini ayarlamak için XAML'yi kullanabilir:

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- AutomationPeer sanal yöntemleri geçersiz kılarak.

  <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> AutomationPeer <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sınıfına sanal yöntemler eklendi. Bir geliştirici, aşağıdaki `SizeOfSet` `PositionInSet` örnekte gösterildiği gibi, bu yöntemler için ve geçersiz kılınarak değerler sağlayabilir:

  ```csharp
  public class MyButtonAutomationPeer : ButtonAutomationPeer
  {
    protected override int GetSizeOfSetCore()
    {
        // Call into your own logic to provide a value for SizeOfSet
        return CalculateSizeOfSet();
    }

    protected override int GetPositionInSetCore()
    {
        // Call into your own logic to provide a value for PositionInSet
        return CalculatePositionInSet();
    }
  }
  ```

Buna ek olarak, örneklerdeki <xref:System.Windows.Controls.ItemsControl> öğeler, geliştiriciden ek bir eylem olmadan bu özellikler için otomatik olarak bir değer sağlar. Bir <xref:System.Windows.Controls.ItemsControl> grupgruplu ise, grup koleksiyonu bir küme olarak temsil edilir ve her grup ayrı bir küme olarak sayılır ve bu grubun içindeki her öğe, grubun içindeki konumunu ve grubun boyutunu sağlar. Otomatik değerler sanallaştırmadan etkilenmez. Bir öğe gerçekleştirilmese bile, yine de kümenin toplam boyutuna doğru sayılır ve kardeş öğeler kümesindeki konumu etkiler.

Otomatik değerler yalnızca uygulama .NET Framework 4.8'i hedefliyorsa sağlanır. .NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için, aşağıdaki App.config dosyasında gösterildiği gibi `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)ayarlayabilirsiniz:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
   <startup>
      <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />
   </startup>
   <runtime>
      <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
   </runtime>
</configuration>
```

<a name="wf48" />

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows İş Akışı Temeli (WF) iş akışı tasarımcısı

İş akışı tasarımcısı .NET Framework 4.8'de aşağıdaki değişiklikleri içerir:

- Ekran Okuyucusu'nun kullanımı FlowSwitch servis talebi etiketlerinde iyileştirmeler görür.

- Ekran Okuyucusu'nun kullanımı düğme açıklamalarında iyileştirmeler görür.

- Yüksek Karşıtlık temaları seçen kullanıcılar, öğeler arasındaki daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı'nın ve denetimlerinin görünürlüğünde iyileştirmeler görür.

Uygulamanız .NET Framework 4.7.2 veya daha önceki bir sürümü hedefliyorsa, uygulama yapılandırma dosyanızda `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `false` ayarlayarak bu değişiklikleri tercih edebilirsiniz. Daha fazla bilgi için, bu [makaledeki erişilebilirlik geliştirmeleri bölümünden yararlanın](#taking-advantage-of-accessibility-enhancements) bölümüne bakın.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>.NET Framework 4.7.2'de erişilebilirlikte yenilikler

.NET Framework 4.7.2 aşağıdaki alanlarda yeni erişilebilirlik özelliklerini içerir:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Yüksek Karşıtlık temalarında işletim sistemi tanımlı renkler**

.NET Framework 4.7.2 ile başlayarak, Windows Forms Yüksek Karşıtlık temalarında işletim sistemi tarafından tanımlanan renkleri kullanır. Bu, aşağıdaki denetimleri etkiler:

- Kontrolün <xref:System.Windows.Forms.ToolStripDropDownButton> açılır ok.

- <xref:System.Windows.Forms.RadioButton> ' <xref:System.Windows.Forms.Button>ve <xref:System.Windows.Forms.CheckBox> set <xref:System.Windows.Forms.ButtonBase.FlatStyle> ile <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>kontroller veya . Daha önce, seçili metin ve arka plan renkleri zıt değildi ve okunması zordu.

- Bir içinde <xref:System.Windows.Forms.GroupBox> bulunan denetimler kendi <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ayarlanmış. `false`

- Yüksek <xref:System.Windows.Forms.ToolStripComboBox>Kontrast <xref:System.Windows.Forms.ToolStripDropDownButton> Modunda parlaklık kontrast oranı nın arttığı , ve kontroller. <xref:System.Windows.Forms.ToolStripButton>

- Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell>.

**Anlatıcı iyileştirmeleri**

.NET Framework 4.7.2 ile başlayarak, Ekran Okuyucudesteği aşağıdaki gibi geliştirilmiştir:

- Bir ' nin metnini <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> açıklarken özelliğin <xref:System.Windows.Forms.ToolStripMenuItem>değerini bildirir.

- Bir özelliğinin <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.Control.Enabled> ne zaman `false`ayarlı olduğunu gösterir.

- Özellik ' e ayarlandığında <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> onay kutusunun durumu `true`hakkında geri bildirim verir.

- Ekran Okuyucusu'nun Scan Modu odak lama sırası, ClickOnce indir iletişim penceresindeki denetimlerin görsel sırası ile tutarlıdır.

**DataGridView geliştirmeleri**

.NET Framework 4.7.2 ile <xref:System.Windows.Forms.DataGridView> başlayarak, denetim aşağıdaki erişilebilirlik iyileştirmelerini getirmiştir:

- Satırlar klavye kullanılarak sıralanabilir. Bir kullanıcı geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.

- <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> Sütun üstbilgi, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>kullanıcı geçerli satırdaki hücreler arasında sekerken geçerli sütunu belirtmek için renk değiştirir.

- Bir <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetim döndürür.

**Geliştirilmiş görsel ipuçları**

- Boş <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.ButtonBase.Text> <xref:System.Windows.Forms.CheckBox> bir özellik ile ve denetimler, odak aldığında bir odak göstergesi görüntüler.

**Geliştirilmiş Özellik Grid Desteği**

- Denetim <xref:System.Windows.Forms.PropertyGrid> alt öğeleri artık `true` yalnızca <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> bir PropertyGrid öğesi etkinleştirildiğinde özellik için a döndürür.

- Denetim <xref:System.Windows.Forms.PropertyGrid> alt öğeleri `false` yalnızca <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> bir PropertyGrid öğesi kullanıcı tarafından değiştirildiğinde özellik için bir döndürür.

**Geliştirilmiş klavye gezintisi**

- Denetim, <xref:System.Windows.Forms.ToolStripButton> özelliği ayarlanmış bir <xref:System.Windows.Forms.ToolStripPanel> içinde <xref:System.Windows.Forms.ToolStripPanel.TabStop> bulunduğunda odaklanmayı sağlar`true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**CheckBox ve RadioButton denetimleri değişiklikleri**

.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimler tutarsız ve Klasik ve Yüksek Karşıtlık temalarında yanlış odak görsellerine sahiptir.  Bu sorunlar, denetimlerin herhangi bir içerik kümesinin olmadığı durumlarda oluşur.  Bu temalar kafa karıştırıcı ve odak görsel görmek zor arasındaki geçiş yapabilirsiniz.

.NET Framework 4.7.2'de bu görseller artık temalar arasında daha tutarlı ve Klasik ve Yüksek Karşıtlık temalarında daha kolay görülebilir.

**WinForms denetimleri bir WPF uygulamasında barındırılan**

.NET Framework 4.7.1 ve önceki sürümlerde bir WPF uygulamasında barındırılan WinForms denetimi için, bu katmandaki ilk veya son <xref:System.Windows.Forms.Integration.ElementHost> denetim WPF denetimi yse, kullanıcılar WinForms katmanından çıkamaz. .NET Framework 4.7.2'de kullanıcılar artık WinForms katmanını sekmeyapabiliyor.

Ancak, WinForms katmanından asla kaçamayan odaklara dayanan otomatik uygulamalar artık beklendiği gibi çalışmayabilir.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>.NET Framework 4.7.1'de erişilebilirlikte yenilikler

.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özelliklerini içerir:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET web denetimleri](#aspnet471)

- [.NET SDK Araçları](#tools471)

- [Windows İş Akışı Temeli (WF) İş Akışı Tasarımcısı](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ekran okuyucu iyileştirmeleri**

Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucularını etkileyen aşağıdaki geliştirmeleri içerir:

- .NET Framework 4.7 ve <xref:System.Windows.Controls.Expander> önceki sürümlerde denetimler ekran okuyucular tarafından düğme olarak duyuruldu. .NET Framework 4.7.1 ile başlayarak, genişletilebilir/katlanabilir gruplar olarak doğru bir şekilde duyurulur.

- .NET Framework 4.7 ve <xref:System.Windows.Controls.DataGridCell> önceki sürümlerde, denetimler ekran okuyucular tarafından "özel" olarak duyuruldu. .NET Framework 4.7.1 ile başlayarak, artık doğru veri ızgara hücresi (lokalize) olarak duyurulur.

- .NET Framework 4.7.1 ile başlayarak, ekran okuyucular <xref:System.Windows.Controls.ComboBox>bir editable adını duyurmak.

- .NET Framework 4.7 ve <xref:System.Windows.Controls.PasswordBox> önceki sürümlerinde, denetimler "görünümde öğe yok" olarak duyurulmuş veya başka türlü yanlış davranışlara sahip. Bu sorun .NET Framework 4.7.1 ile başlarken giderilmiştir.

**UIAutomation LiveRegion desteği**

Ekran Okuyucu gibi ekran okuyucular, kullanıcıların genellikle odak noktası olan Kullanıcı Bira'sı içeriğinin metinden konuşmaya çıktısı ile bir uygulamanın Kullanıcı-ı UI içeriğini okumalarına yardımcı olur. Ancak, bir Kullanıcı Bira öğesi değişir ve odak yoksa, kullanıcı bilgilendirilmeyebilir ve önemli bilgileri kaçırabilir. Canlı bölgeler bu sorunu çözmeyi amaçlamaktadır. Geliştirici, bunları ekran okuyucuya veya başka bir UIAutomation istemcisine, bir UI öğesinde önemli bir değişiklik yapıldığını bildirmek için kullanabilir. Ekran okuyucu daha sonra bu değişikliğin kullanıcıyı nasıl ve ne zaman bilgilendireceğine karar verebilir.

Canlı bölgeleri desteklemek için WPF'ye aşağıdaki API'ler eklenmiştir:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> **LiveSetting** özelliğini ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> **LiveRegionChanged** olayını tanımlayan alanlar. XAML kullanılarak ayarlanabilirler.

- Kullanıcı için Kullanıcı Değişikliği'nin önemini ekran okuyucuya bildiren **AutomationProperties.LiveSetting** ekli özellik.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> **AutomationProperties.LiveSetting** ekli özelliği tanımlayan özellik.

- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> **LiveSetting** değeri sağlamak için geçersiz kılınabilen yöntem.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> **LiveSetting** değerini alan ve ayarlayan yöntemler.

- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası **LiveSetting** değerlerini tanımlayan numaralandırma:

  - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Canlı bölgenin içeriği değiştiyse öğe bildirim göndermez.
  - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Öğe, canlı bölgenin içeriği değiştiyse kesintisiz bildirimler gönderir.

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Öğe, canlı bölgenin içeriği değiştiyse kesintiye uğratıcı bildirimler gönderir.

Aşağıdaki örnekte gösterildiği **gibi, AutomationProperties.LiveSetting** özelliğini ilgi öğesine ayarlayarak bir LiveRegion oluşturabilirsiniz:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Canlı bölgedeki veriler değiştiğinde ve bir ekran okuyucuyu bilgilendirmeniz gerektiğinde, aşağıdaki örnekte gösterildiği gibi açıkça bir olay yükseltirsiniz.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**Yüksek kontrast**

.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimlerinde yüksek kontrastlı iyileştirmeler yapılmıştır. <xref:System.Windows.SystemParameters.HighContrast%2A> Tema ayarlandığında artık görünürler. Bunlar:

- <xref:System.Windows.Controls.Expander>Denetim

  <xref:System.Windows.Controls.Expander> Denetim için odak görselşimdi görünür. Klavye görselleri <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>ve <xref:System.Windows.Controls.RadioButton> denetimleri de görülebilir. Örnek:

  Önce:

  ![Odak ve odak görsel ile genişletici kontrolü ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-before.png)

  Sonra:

  ![Genişletici denetiminin ekran görüntüsü ve odak, denetimin metninin etrafında noktalı bir çizgi gösterir.](./media/whats-new-in-accessibility/expander-control-after.png)

- <xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> kontroller

  Yüksek kontrastlı <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> temalarda seçildiğinde ve denetimlerde bulunan metni görmek artık daha kolay. Örnek:

  Önce:

  ![Yüksek kontrastlı temalarda metin görünürlüğü zayıf olan radyo ve kontrol düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  Sonra:

  ![Yüksek kontrastlı temalarda daha iyi metin görünürlüğü olan radyo ve kontrol düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>Denetim

  .NET Framework 4.7.1 ile başlayarak, <xref:System.Windows.Controls.ComboBox> devre dışı bırakma denetiminin sınırı devre dışı bırakılmış metinle aynı renktedir. Örnek:

  Önce:

  ![Kenarlık ve denetim metni farklı renklerde bir engelli ComboBox ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  Sonra:

  ![Denetim metniyle aynı renge sahip engelli bir ComboBox'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  Buna ek olarak, devre dışı bırakılmış ve odaklanmış düğmeler doğru tema rengini kullanır.

  Önce:

  ![Focus Me yazan gri metinli siyah bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  Sonra:

  ![Focus Me yazan siyah metinli mavi bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  Son olarak, .NET Framework 4.7 ve <xref:System.Windows.Controls.ComboBox> önceki sürümlerinde, açılan okgörünmez olması için `Toolbar.ComboBoxStyleKey` bir denetim stili ayarlama. Bu sorun .NET Framework 4.7.1 ile başlarken giderilmiştir. Örnek:

  Önce:

  ![Görünmez açılır oklu ComboBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  Sonra:

  ![Açılan ok gösteren bir ComBoxBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <xref:System.Windows.Controls.DataGrid>Denetim

  .NET Framework 4.7.1 ile başlayarak, <xref:System.Windows.Controls.DataGrid> denetimlerde sıralama göstergesi oku artık doğru tema renklerini kullanır. Örnek:

  Önce:

  ![Geliştirmelerden önce sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  Sonra:

  ![Geliştirmelerden sonra sıralama göstergesi ok ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  Buna ek olarak, .NET Framework 4.7 ve önceki sürümlerinde, varsayılan bağlantı stili yüksek kontrastlı modlarda fare üzerinde yanlış bir renge dönüştürüldü. Bu işlem .NET Framework 4.7.1 ile başlar. Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusu sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirimi için beklenen renkleri kullanır.

  Önce:

  ![Bana Tıkla diyen bir bağlantının ekran görüntüsü! kırmızı.](./media/whats-new-in-accessibility/default-link-style-before.png)

  Sonra:

  ![Bana Tıkla diyen bir bağlantının ekran görüntüsü! sarı.](./media/whats-new-in-accessibility/default-link-style-after.png)

.NET Framework 4.7.1'deki WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için [WPF'deki Erişilebilirlik geliştirmelerine](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)bakın.

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Windows Forms erişilebilirlik geliştirmeleri

.NET Framework 4.7.1'de, Windows Formları (WinForms) aşağıdaki alanlarda erişilebilirlik değişikliklerini içerir.

**Yüksek Karşıtlık modunda geliştirilmiş ekran**

.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sisteminde bulunan HighContrast modlarında gelişmiş görüntüleme sunar. Windows 10 bazı yüksek karşıtlık sistem renklerinin değerlerini değiştirdi ve Windows Forms, Windows 10 Win32 çerçevesini temel almıştır. En iyi deneyim için, Windows'un en son sürümünde çalıştırın ve bir test uygulamasına bir app.manifest dosyası ekleyerek en son işletim sistemi değişikliklerini tercih edin ve Windows 10 destekli işletim sistemi çizgisini aşağıdaki gibi görünerek yorum yapmayı bırakın:

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

Yüksek karşıtlık değişikliklerine örnek olarak şunlar verilebilir:

- Öğelerdeki <xref:System.Windows.Forms.MenuStrip> onay işaretlerini görüntülemek daha kolaydır.

- Seçildiğinde, <xref:System.Windows.Forms.MenuStrip> devre dışı bırakılan öğeleri görüntülemek daha kolaydır.

- Seçili <xref:System.Windows.Forms.Button> denetimdeki metin, seçim rengiyle tezat oluşturuyor.

- Devre dışı bırakılan metnin okunması daha kolaydır. Örnek:

  Önce:

  ![Erişilebilirlik geliştirmelerinden önce yüksek kontrast modunda çalışan farklı denetimler kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  Sonra:

  ![Erişilebilirlik geliştirmeleri sonrasında yüksek kontrast modunda çalışan farklı denetimler kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- İş Parçacığı Özel Durum İletişim Kutusunda yüksek kontrastlı geliştirmeler.

**Geliştirilmiş Ekran Okuyucusu desteği**

.NET Framework 4.7.1'deki Windows Formları, Ekran Okuyucusu için aşağıdaki erişilebilirlik geliştirmelerini içerir:

- Denetime <xref:System.Windows.Forms.MonthCalendar> Anlatıcı ve diğer UI otomasyon araçları tarafından erişilebilir.

- Denetim, <xref:System.Windows.Forms.CheckedListBox> bir öğenin denetim durumu değiştiğinde Ekran Okuyucu'ya haber verirken, kullanıcıya liste öğesinin değerini değiştirdiği bildirilir.

- Denetim, <xref:System.Windows.Forms.DataGridViewCell> doğru salt okunur durumunu Ekran Okuyucusu'na bildirir.

- Ekran okuyucusu <xref:System.Windows.Forms.ToolStripMenuItem> artık devre dışı bırakılan metni okuyabilirken, daha önce devre dışı bırakılan menü öğelerini atlardı.

**UIAutomation erişilebilirlik desenleri için geliştirilmiş destek**

.NET Framework 4.7.1 ile başlayarak, erişilebilirlik teknolojisi araçlarının geliştiricileri çeşitli WinForms denetimleri için ortak API erişilebilirlik desenlerinden ve özelliklerinden yararlanabilir. Bu erişilebilirlik geliştirmeleri şunlardır:

- Ve <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> şimdi [genişletme /daraltma deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.

- <xref:System.Windows.Forms.DataGridViewCheckBoxCell> Şimdi geçiş [deseni](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)destekler.

- Denetim <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [genişletme/daraltma deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.

- Ve <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> denetimler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği destekler.

**Geliştirilmiş özellik tarayıcı deneyimi**

.NET Framework 4.7.1 ile başlayarak, Windows Formları şunları içerir:

- Çeşitli açılır seçim pencerelerinden daha iyi klavye gezintisi.
- Gereksiz sekme durakları bir azalma.
- Kontrol türlerinin daha iyi raporlanması.
- Geliştirilmiş anlatıcı davranışı.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>ASP.NET web denetimleri

.NET Framework 4.7.1 ve Visual Studio 2017 sürüm 15.3 ile başlayan ASP.NET, ASP.NET web denetimlerinin Visual Studio'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirir. Değişiklikler şunlardır:

- **Ayrıntılar Görünümü** sihirbazındaki **Alan Ekle** iletişim kutusu veya **ListView** sihirbazının **Yapılandırılmış ListView** iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik desenleri uygulamak için değişiklikler.

- **Veri Çağrı Alanı Alanları Düzenleyicisi**gibi Yüksek Karşıtlık modunda ekranı geliştirmek için değişiklikler.

- DataPager **denetiminin** **Çağrı Cihazı Alanlarını Edit** sihirbazı, **Nesne Bağlamını Yapılandıran** iletişim kutusu veya **Yapılandır Veri Kaynağı** sihirbazının **Yapılandır Veri** Seçimi iletişim kutusu gibi denetimler için klavye gezintisi deneyimlerini geliştirmek için yapılan değişiklikler.

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>.NET SDK Araçları

[Configuration Editor Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve Service Trace Viewer Aracı [(SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunları giderilerek geliştirilmiştir. Bunların çoğu, tanımlanmayan bir ad veya belirli Kullanıcı Arabirimi otomasyon desenleri gibi doğru uygulanamayan küçük sorunlardı. Birçok kullanıcı bu yanlış değerlerin farkında olmasa da, ekran okuyucular gibi yardımcı teknolojileri kullanan müşteriler bu SDK araçlarını daha erişilebilir bulur.

Bu geliştirmeler, klavye odak lama sırası gibi önceki bazı davranışları değiştirir.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows İş Akışı Temeli (WF) İş Akışı Tasarımcısı

İş Akışı Tasarımcısı'ndaki erişilebilirlik değişiklikleri aşağıdakileri içerir:

- Sekme sırası bazı denetimlerde soldan sağa ve yukarıdan aşağıya değişir:

  - <xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinlik için korelasyon verilerini ayarlamak için başlangıç korelasyon penceresi.

  - <xref:System.ServiceModel.Activities.Receive>, , <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler için içerik tanım penceresi.

- Klavye aracılığıyla daha fazla işlev kullanılabilir:

  - Bir etkinliğin özelliklerini düzenlerken, özellik grupları ilk odaklandıklarında klavye yle daraltılabilir.

  - Uyarı simgelerine klavyeyle erişilebilir.

  - **Özellikler** penceresindeki **Daha Fazla Özellik** düğmesine klavyeyle erişilebilir.

  - Klavye kullanıcıları, İş Akışı Tasarımcısı'nın **Bağımsız Değişkenler** ve **Değişkenler** bölmelerinde üstbilgi öğelerine erişebilir.

- Şu anda olduğu gibi odaklanmış öğelerin daha iyi görünürlüğü:

  - İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri ızgaralarına satır ekleme.

  - Alanlarda <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerde sekme.

  - Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama

- Ekran okuyucular artık doğru tanıyabilir:

  - İş akışı tasarımcısında ayarlanan kesme noktaları.

  - , <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>ve <xref:System.ServiceModel.Activities.CorrelationScope> aktiviteler.
  - <xref:System.ServiceModel.Activities.Receive> Etkinliğin içeriği.

  - <xref:System.Activities.Statements.InvokeMethod> Etkinlik için Hedef Türü.

  - Etkinlikteki Özel Durum açılan kutusu <xref:System.Activities.Statements.TryCatch> ve Son bölümü.

  - İleti Türü açılan kutusu, Korelik Açla Penceresindeki ayırıcı, İçerik Tanımı penceresi ve ileti etkinliklerindeki CorrelatesOn <xref:System.ServiceModel.Activities.SendReply>Definition <xref:System.ServiceModel.Activities.ReceiveReply>penceresi (<xref:System.ServiceModel.Activities.Receive>, , <xref:System.ServiceModel.Activities.Send>, ve ).

  - Durum makine geçişleri ve geçişler hedefleri.

  - Etkinliklerle ilgili <xref:System.Activities.Statements.FlowDecision> ek açıklamalar ve bağlayıcılar.

  - Etkinlikler için bağlam (sağ tıklatma) menüleri.

  - Özellik değeri düzenleyicileri, Aramayı Temizle düğmesi, Kategoriye Ve Alfabetik sıralama düğmelerine göre ve özellikler tablosundaki İfade Düzenleyicisi iletişim kutusu.

  - İş Akışı Tasarımcısı'ndaki yakınlaştırma yüzdesi.

  - Ayırıcı ve <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Pick> faaliyetleri.

  - Aktivite. <xref:System.Activities.Statements.InvokeDelegate>

  - Sözlük etkinlikleri için Türleri`Microsoft.Activities.AddToDictionary<TKey,TValue>`Seç `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`penceresi (, , vb.).

  - Gözat ve Seç .NET Türü penceresi.

  - İş Akışı Tasarımcısı'ndaki ekmek kırıntıları.

- Yüksek Karşıtlık temaları seçen kullanıcılar, öğeler arasındaki daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı'nın ve denetimlerinin görünürlüğünde birçok iyileştirme görür.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework’teki yenilikler](index.md)
