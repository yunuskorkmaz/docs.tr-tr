---
title: .NET Framework erişilebilirlik yenilikleri
description: .NET Framework 4.7.1 ile başlayarak .NET erişilebilirlik yenilikleri bölümüne bakın. Erişilebilirlik özellikleri, bir uygulamanın yardımcı teknoloji kullanıcıları için doğru deneyimi sağlamasına imkan tanır.
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.openlocfilehash: 593591ca340cc130a3a6d1daa015a849b8eca0f8
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/22/2020
ms.locfileid: "86925845"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a>.NET Framework erişilebilirlik yenilikleri

.NET Framework amaçlar, kullanıcılarınız için uygulamaları daha erişilebilir hale getirme. Erişilebilirlik özellikleri, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin verir. .NET Framework .NET Framework başlayarak, geliştiricilerin erişilebilir uygulamalar oluşturmalarına izin veren çok sayıda erişilebilirlik geliştirmesi de vardır.

## <a name="accessibility-switches"></a>Erişilebilirlik anahtarları

Uygulamanızı, .NET Framework 4,7 veya önceki bir sürümü hedefliyorsa ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışıyorsa erişilebilirlik özelliklerini kabul etmek üzere yapılandırabilirsiniz. Ayrıca, .NET Framework 4.7.1 veya üstünü hedeflerse, uygulamanızı eski özellikleri (ve erişilebilirlik özelliklerinden faydalanmaz) kullanacak şekilde de yapılandırabilirsiniz. Erişilebilirlik özelliklerini içeren .NET Framework her sürümü, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğesine eklediğiniz sürüme özgü bir erişilebilirlik anahtarına sahiptir. Aşağıdakiler desteklenen anahtarlardır:

|Sürüm|Anahtar|
|---|---|
|.NET Framework 4.7.1|"Switch. UseLegacyAccessibilityFeatures"|
| .NET Framework 4.7.2|"Switch. UseLegacyAccessibilityFeatures. 2"|
| .NET Framework 4.8|"Switch. UseLegacyAccessibilityFeatures. 3"|

### <a name="taking-advantage-of-accessibility-enhancements"></a>Erişilebilirlik geliştirmelerinden yararlanma

Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar için varsayılan olarak etkinleştirilmiştir. Ayrıca, .NET Framework önceki bir sürümünü hedefleyen, ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğeye anahtar ekleyerek ve değerlerini olarak ayarlayarak eski erişilebilirlik davranışlarını (ve dolayısıyla erişilebilirlik geliştirmelerinden faydalanabilir) devre dışı bırakabilirsiniz `false` . Aşağıda, .NET Framework 4.7.1 ' de sunulan erişilebilirlik geliştirmelerinin nasıl kabul edilecek gösterilmektedir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

.NET Framework sonraki bir sürümünde erişilebilirlik özelliklerini kullanmayı tercih ederseniz, .NET Framework daha önceki sürümlerindeki özellikleri de açıkça kabul etmeniz gerekir. Uygulamanızı .NET Framework 4.7.1 ve 4.7.2 içindeki erişilebilirlik geliştirmelerinden faydalanmak için yapılandırma aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi gerektirir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

.NET Framework 4.7.1, 4.7.2 ve 4,8 ' deki erişilebilirlik geliştirmelerinden faydalanmak için uygulamanızı yapılandırma aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi gerektirir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a>Eski davranışı geri yükleme

4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyasının bölümündeki öğesine anahtar ekleyerek ve değerlerini olarak ayarlayarak erişilebilirlik özelliklerini devre dışı bırakabilir `true` . Örneğin, aşağıdaki yapılandırma .NET Framework 4.7.2 ' de tanıtılan erişilebilirlik özelliklerinden fazlasını giderir:

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a>.NET Framework 4,8 ' de erişilebilirlik yenilikleri

.NET Framework 4,8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Forms](#winforms48)

- [Windows Presentation Foundation (WPF)](#wpf48)

- [Windows Workflow Foundation (WF) iş akışı Tasarımcısı](#wf48)

<a name="winforms48"></a>

### <a name="windows-forms"></a>Windows Forms

.NET Framework 4,8 ' de Windows Forms, yaygın olarak kullanılan birçok denetime Ligegions ve Notification olayları için destek ekler. Ayrıca, bir Kullanıcı klavyeyi kullanarak bir denetime gittiğinde araç Ipuçları için destek ekler.

**Etiketler ve Durumlarlar için UııA LiveRegions desteği**

UIA Ligegions, uygulama geliştiricilerinin, kullanıcının çalıştığı konumdan ayrı olarak bulunan bir denetimdeki metin değişikliğini ekran okuyucularına bildirmesini sağlar. Bu, örneğin, <xref:System.Windows.Forms.StatusStrip> bağlantı durumunu gösteren bir denetim için yararlıdır. Bağlantı bırakılır ve durum değişirse geliştirici, ekran okuyucuyu bilgilendirmek isteyebilir.

.NET Framework 4,8 ' den başlayarak, Windows Forms hem hem de denetimleri için UııA LiveRegions uygular <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> . Örneğin, aşağıdaki kod adlı bir denetimde LiveRegion kullanır <xref:System.Windows.Forms.Label> `label1` :

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

Ekran okuyucusu, kullanıcının uygulamayla etkileşime geçen yere bakılmaksızın "Ready" duyurur.

Ayrıca, hesabınızı <xref:System.Windows.Forms.UserControl> bir LiveRegion olarak da uygulayabilirsiniz:

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

**UıA bildirim olayları**

Windows 10 Fall Creators Update 'te tanıtılan UıA bildirim olayı, uygulamanızın kullanıcı arabiriminde ilgili bir denetime sahip olması gerekmeden, yalnızca olayla sağladığınız metni temel alan bir duyuru oluşturmak için bir UıA olayı tetiklenmesine olanak tanır. Bazı senaryolarda bu, uygulamanızın erişilebilirliğini önemli ölçüde artırmanın kolay bir yoludur. ' De, uzun sürebilecek bazı işlemlerin ilerlemesini bilgilendirmek için de yararlı olabilir. UııA Notification olayları hakkında daha fazla bilgi için, bkz. [masaüstü uygulamanız yenı UI bildirimi olayından mi yararlanabilir?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).

Aşağıdaki örnek [bildirim olayını](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)oluşturur:

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

**Klavye erişiminde araç Ipuçları**

.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, bir denetim [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca bir fare işaretçisi denetime taşınarak açılan menü için tetiklenebilir. .NET Framework 4,8 ' den itibaren klavye kullanıcısı, değiştirici tuşları olan veya içermeyen bir sekme tuşu veya ok tuşlarını kullanarak Denetim araç ipucunu tetikleyebilirler. Bu belirli erişilebilirlik geliştirmesi ek bir [AppContext anahtarı](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)gerektirir:

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

Aşağıdaki şekilde, Kullanıcı klavyeyle bir düğme seçtiğinde araç ipucunu gösterir.

![Kullanıcı klavyeden düğmeye gittiğinde araç ipucunun ekran görüntüsü.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4,8 ' den başlayarak WPF bir dizi erişilebilirlik geliştirmesi içerir.

**Ekran anlayıcıları artık daraltılmış veya gizli görünürlüğe sahip öğeleri duyurmayacak**

Daraltılmış veya gizli görünürlüğe sahip öğeler artık ekran okuyucu tarafından duyurulmaz. Görünürlüğü olan öğeleri içeren kullanıcı arabirimleri <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> , kullanıcıya duyurulacak olmaları durumunda ekran okuyucular tarafından yanlış temsil edilebilir. .NET Framework 4,8 ' den itibaren, WPF artık UIAutomation ağacının denetim görünümünde daraltılmış veya gizli öğeleri içermez, bu nedenle ekran okuyucular artık bu öğeleri duyurabilir.

**Adorner tabanlı metin seçimiyle kullanılacak SelectionTextBrush özelliği**

.NET Framework 4.7.2, WPF, <xref:System.Windows.Controls.TextBox> donatıcı katmanını kullanmadan çizim ve <xref:System.Windows.Controls.PasswordBox> metin seçme özelliği ekledi. Bu senaryodaki seçili metnin ön plan rengi tarafından dikte edildi <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType> .

.NET Framework 4,8 yeni bir özellik ekler, `SelectionTextBrush` Bu, geliştiricilerin, donatıcı olmayan tabanlı metin seçimi kullanılırken seçili metin için belirli fırçayı seçmesine olanak tanır. Bu özellik yalnızca <xref:System.Windows.Controls.Primitives.TextBoxBase> , <xref:System.Windows.Controls.PasswordBox> donatıcı tabanlı olmayan metin seçimi ETKIN olan WPF uygulamalarında yalnızca türetilmiş denetimleri ve denetimi işe yarar. Denetim üzerinde çalışmaz <xref:System.Windows.Controls.RichTextBox> . Adorner tabanlı olmayan metin seçimi etkinleştirilmemişse, bu özellik yok sayılır.

Bu özelliği kullanmak için XAML kodunuza eklemeniz ve uygun fırçayı ya da bağlamayı kullanmanız yeterlidir. Ortaya çıkan metin seçimi şöyle görünür:

![Merhaba Dünya sözcüklerle çalışan uygulamanın ekran görüntüsü seçili.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

`SelectionBrush`Ve özelliklerinin kullanımını, `SelectionTextBrush` uygun olmayan bir arka plan ve ön plan renk kombinasyonu oluşturmak için birleştirebilirsiniz.

**Özelliği Için UIAutomation Controllersupport desteği**

UIAutomation `ControllerFor` özelliği, bu özelliği destekleyen Otomasyon öğesi tarafından yönetilen bir Otomasyon öğeleri dizisi döndürüyor. Bu özellik genellikle otomatik öneri erişilebilirliği için kullanılır. `ControllerFor`bir Otomasyon öğesi uygulama kullanıcı arabirimi veya masaüstünün bir veya daha fazla kesimini etkiliyorsa kullanılır. Aksi takdirde, denetim işleminin etkisini UI öğeleriyle ilişkilendirmek zordur. Bu özellik, denetimlerin özellik için bir değer sağlama yeteneğini ekler `ControllerFor` .

.NET Framework 4,8 yeni bir sanal yöntem ekler <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType> . Özelliği için bir değer sağlamak için `ControllerFor` , bu yöntemi geçersiz kılın ve `List<AutomationPeer>` bunun tarafından geçirilmekte olan denetimler için bir döndürür <xref:System.Windows.Automation.Peers.AutomationPeer> :

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

.NET Framework 4.7.2 ve önceki sürümlerde araç ipuçları yalnızca Kullanıcı fare imlecini bir denetim üzerine getirdiğinde görüntülenir. .NET Framework 4,8 ' de araç ipuçları klavye odağında ve klavye kısayoluyla de görüntülenir.

Bu özelliği etkinleştirmek için bir uygulamanın, `Switch.UseLegacyAccessibilityFeatures.3` ve `Switch.UseLegacyToolTipDisplay` [appcontext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını kullanarak .NET Framework 4,8 veya katılımı hedeflemesi gerekir. Aşağıda örnek bir uygulama yapılandırma dosyası verilmiştir:

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

Etkinleştirildikten sonra, araç ipucu içeren tüm denetimler, denetim klavye odağını aldıktan sonra bunu görüntüler. Araç ipucu zaman içinde veya klavye odağı değiştiğinde kapatılabilir. Kullanıcılar araç ipucunu, CTRL + SHIFT + F10 yeni klavye kısayolunu kullanarak el ile de kapatabilir. Araç ipucu kapatıldıktan sonra, aynı klavye kısayolu kullanılarak yeniden görüntülenebilir.

> [!NOTE]
> Denetimlerde [Şerit Araç ipuçları](xref:System.Windows.Controls.Ribbon.RibbonToolTip) <xref:System.Windows.Controls.Ribbon.Ribbon> klavye odağında gösterilmez; yalnızca klavye kısayolu aracılığıyla gösterilir.

**SizeOfSet ve Positionınset UIAutomation özellikleri için destek eklendi**

Windows 10, iki yeni UIAutomation özelliği sunmuştur `SizeOfSet` ve `PositionInSet` uygulamalar tarafından bir küme içindeki öğelerin sayısını açıklayan uygulamalar tarafından kullanılır. Ekran okuyucular gibi UIAutomation istemci uygulamaları, bu özellikler için bir uygulamayı sorgulayabilir ve uygulamanın kullanıcı arabiriminin doğru bir temsilini duyurur.

.NET Framework 4,8 ' den başlayarak WPF, WPF uygulamalarında UIAutomation için bu iki özelliği kullanıma sunar. Bu, iki şekilde gerçekleştirilebilir:

- Bağımlılık özelliklerini kullanarak.

  WPF iki yeni bağımlılık özelliği ekler <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType> . Geliştirici, değerlerini ayarlamak için XAML kullanabilir:

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- AutomationPeer sanal yöntemlerini geçersiz kılarak.

  <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore>Ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sanal yöntemleri AutomationPeer sınıfına eklenmiştir. Bir geliştirici `SizeOfSet` `PositionInSet` , aşağıdaki örnekte gösterildiği gibi bu yöntemleri geçersiz kılarak ve için değerler verebilir:

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

Ayrıca, <xref:System.Windows.Controls.ItemsControl> örneklerdeki öğeler, geliştiriciden ek işlem yapılmadan bu özellikler için otomatik olarak bir değer sağlar. Bir <xref:System.Windows.Controls.ItemsControl> gruplandırılmışsa, gruplar koleksiyonu bir küme olarak temsil edilir ve her bir grup içindeki her bir öğe, bu grubun içindeki konumunu ve grubun boyutunu sunan grubun içindeki her bir öğe ile ayrı bir küme olarak sayılır. Otomatik değerler sanallaştırmadan etkilenmez. Bir öğe gerçekleştirilmese de, bu, denetimin toplam boyutuna doğru sayılır ve eşdüzey öğelerinin kümesindeki konumu etkiler.

Otomatik değerler yalnızca uygulama .NET Framework 4,8 ' i hedefliyorsa sağlanır. .NET Framework önceki bir sürümünü hedefleyen uygulamalar için, `Switch.UseLegacyAccessibilityFeatures.3` aşağıdaki App.config dosyasında gösterildiği gibi [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)ayarlayabilirsiniz:

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

<a name="wf48"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) iş akışı Tasarımcısı

İş akışı Tasarımcısı .NET Framework 4,8 ' de aşağıdaki değişiklikleri içerir:

- Ekran okuyucusu kullanan kullanıcılar, FlowSwitch durum etiketlerindeki geliştirmeleri görür.

- Ekran okuyucusu kullanan kullanıcılar, düğme açıklamalarındaki geliştirmeleri görür.

- Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde geliştirmeler görür.

Uygulamanız .NET Framework 4.7.2 veya önceki bir sürümü hedefliyorsa, `Switch.UseLegacyAccessibilityFeatures.3` uygulama yapılandırma dosyanızda [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) olarak ayarlayarak bu değişiklikleri kabul edebilirsiniz `false` . Daha fazla bilgi için bu makaledeki [Erişilebilirlik geliştirmelerinden yararlanma](#taking-advantage-of-accessibility-enhancements) bölümüne bakın.

## <a name="whats-new-in-accessibility-in-net-framework-472"></a>.NET Framework 4.7.2 ' deki erişilebilirlik yenilikleri

.NET Framework 4.7.2, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Forms](#winforms472)

- [Windows Presentation Foundation (WPF)](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a>Windows Forms

**Yüksek Karşıtlık temalarda işletim sistemi tanımlı renkler**

.NET Framework 4.7.2 ile başlayarak, Windows Forms Yüksek Karşıtlık temalarda işletim sistemi tarafından tanımlanan renkleri kullanır. Bu, aşağıdaki denetimleri etkiler:

- Denetimin aşağı açılan oku <xref:System.Windows.Forms.ToolStripDropDownButton> .

- <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve, <xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> veya olarak ayarlanan denetimleri <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> . Daha önce, seçilen metin ve arka plan renkleri çok sevmiyor ve okunması zor.

- Öğesinin <xref:System.Windows.Forms.GroupBox> özelliği olarak ayarlanmış olan içinde bulunan denetimler <xref:System.Windows.Forms.Control.Enabled> `false` .

- <xref:System.Windows.Forms.ToolStripButton> <xref:System.Windows.Forms.ToolStripComboBox> <xref:System.Windows.Forms.ToolStripDropDownButton> Yüksek karşıtlık modunda daha fazla parlaklık karşıtlığı oranına sahip, ve denetimleri.

- <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor>Öğesinin özelliği <xref:System.Windows.Forms.DataGridViewLinkCell> .

**Ekran okuyucusu geliştirmeleri**

.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği aşağıdaki şekilde geliştirilmiştir:

- <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType>Bir ' ın metnini duyurdığınızda özelliğin değerini duyurur <xref:System.Windows.Forms.ToolStripMenuItem> .

- Bir <xref:System.Windows.Forms.ToolStripMenuItem> öğesinin <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ayarlandığı zaman gösterir `false` .

- Özelliği olarak ayarlandığında onay kutusunun durumu hakkında geri bildirim sağlar <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> `true` .

- Ekran okuyucusu 'nun tarama modu odak sırası, ClickOnce indirme iletişim kutusu penceresindeki denetimlerin görsel sırasıyla tutarlıdır.

**DataGridView geliştirmeleri**

.NET Framework 4.7.2 ile başlayarak, <xref:System.Windows.Forms.DataGridView> Denetim aşağıdaki erişilebilirlik geliştirmelerini sunmuştur:

- Satırlar klavye kullanılarak sıralanabilir. Kullanıcı, geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.

- , <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ' A ayarlandığında <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType> , sütun üst bilgisi, geçerli satırdaki hücreler aracılığıyla geçerli sütunu Kullanıcı sekmeleri olarak gösterecek şekilde renkle değiştirilir.

- <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType>Öğesinin özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimi döndürür.

**Geliştirilmiş görsel ipuçları**

- <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.CheckBox> Boş bir özelliği olan ve denetimleri, <xref:System.Windows.Forms.ButtonBase.Text> odağı alırken bir odak göstergesi görüntüler.

**Geliştirilmiş özellik Kılavuzu desteği**

- <xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri artık `true` <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> yalnızca bir PropertyGrid öğesi etkinleştirildiğinde özelliği için bir döndürür.

- <xref:System.Windows.Forms.PropertyGrid>Denetim alt öğeleri, `false` <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> yalnızca bir PropertyGrid öğesi Kullanıcı tarafından değiştirilebiliyorsa özelliği için bir döndürür.

**Geliştirilmiş Klavye gezintisi**

- <xref:System.Windows.Forms.ToolStripButton>Denetim, özelliği, özelliği olan bir <xref:System.Windows.Forms.ToolStripPanel> öğesine dahil edildiğinde odağa izin verir <xref:System.Windows.Forms.ToolStripPanel.TabStop>`true`

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**CheckBox ve RadioButton denetimlerinde yapılan değişiklikler**

.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimler tutarsız ve klasik ve yüksek karşıtlık temalarında hatalı odak görselleri.  Bu sorunlar, denetimlerin hiçbir içerik kümesi olmadığı durumlarda oluşur.  Bu, Temalar kafa karıştırıcı ve odak görselindeki geçişleri görebilir.

.NET Framework 4.7.2 ' de, bu görseller artık Temalar arasında daha tutarlıdır ve klasik ve Yüksek Karşıtlık temalarda daha kolay görünür.

**WPF uygulamasında barındırılan WinForms denetimleri**

.NET Framework 4.7.1 ve önceki sürümlerde bulunan bir WPF uygulamasında barındırılan WinForms denetimi için, söz konusu katmandaki ilk veya son denetim WPF denetimi ise, kullanıcılar WinForms katmanının dışına sekmesine dönüştüremedik <xref:System.Windows.Forms.Integration.ElementHost> . .NET Framework 4.7.2 ' de, kullanıcılar artık WinForms katmanının dışına sekme verebilir.

Ancak, odağa dayanan otomatikleştirilmiş uygulamalar artık WinForms katmanını hiçbir şekilde yok etmeyebilir ve beklendiği gibi çalışmayabilir.

## <a name="whats-new-in-accessibility-in-net-framework-471"></a>.NET Framework 4.7.1 ' deki erişilebilirlik yenilikleri

.NET Framework 4.7.1, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:

- [Windows Presentation Foundation (WPF)](#wpf471)

- [Windows Forms](#winforms471)

- [ASP.NET Web denetimleri](#aspnet471)

- [.NET SDK Tools](#tools471)

- [Windows Workflow Foundation (WF) İş Akışı Tasarımcısı](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

**Ekran okuyucu iyileştirmeleri**

Erişilebilirlik iyileştirmeleri etkinleştirilmişse, .NET Framework 4.7.1, ekran okuyucularını etkileyen aşağıdaki geliştirmeleri içerir:

- .NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.Expander> denetimler ekran okuyucular tarafından düğme olarak duyurulmuştur. .NET Framework 4.7.1 ile başlayarak, Genişletilebilir/daraltılabilir gruplar olarak doğru duyurulur.

- .NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.DataGridCell> denetimler ekran okuyucular tarafından "özel" olarak duyurulmuştur. .NET Framework 4.7.1 başlayarak, artık veri kılavuzu hücresi (yerelleştirilmiş) olarak doğru duyurulur.

- .NET Framework 4.7.1 'den başlayarak ekran okuyucular düzenlenebilir bir adı duyurur <xref:System.Windows.Controls.ComboBox> .

- .NET Framework 4,7 ve önceki sürümlerde denetimler, <xref:System.Windows.Controls.PasswordBox> "görünümde hiçbir öğe yok" veya başka türlü yanlış davranışa sahip olarak duyurulmuştur. Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir.

**UIAutomation LiveRegion desteği**

Okuyucu gibi ekran okuyucular, kullanıcıların, genellikle odağa sahip kullanıcı arabirimi içeriğinin metinden konuşmaya çıkışıyla bir uygulamanın kullanıcı arabirimi içeriğini okumasına yardımcı olur. Ancak, bir UI öğesi değişirse ve odağa sahip değilse, kullanıcıya bildirimde bulunulmayabilir ve önemli bilgileri kaçırmayabilir. Canlı bölgeler bu sorunu çözmeye hedeflenir. Geliştirici, ekran okuyucuyu veya başka bir UIAutomation istemcisini, bir kullanıcı arabirimi öğesine önemli bir değişikliğin yapıldığını bilgilendirmek için kullanabilir. Ekran okuyucu daha sonra bu değişikliğin kullanıcısına nasıl ve ne zaman bilgi verileceğine karar verebilir.

Canlı bölgeleri desteklemek için WPF 'e aşağıdaki API 'Ler eklenmiştir:

- <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> **Livesetting** özelliğini ve **liveregionchanged** olayını tanımlayan ve alanları. XAML kullanılarak ayarlanabilir.

- Kullanıcı ARABIRIMININ önem derecesine sahip ekran okuyucuyu kullanıcıya bildiren **AutomationProperties. LiveSetting** iliştirilmiş özelliği.

- <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> **AutomationProperties. livesetting** ekli özelliğini tanımlayan özelliği.

- <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType>Bir **livesetting** değeri sağlamak için geçersiz kılınabilen yöntemi.

- <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType>Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> , bir **livesetting** değeri alır ve ayarlar.

- <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType>Aşağıdaki olası **livesetting** değerlerini tanımlayan sabit listesi:

  - <xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>. Canlı bölgenin içeriği değiştiyse öğe bildirim göndermez.
  - <xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>. Canlı bölgenin içeriği değiştiyse, öğesi interruptive olmayan bildirimler gönderir.

  - <xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>. Canlı bölgenin içeriği değiştiyse, öğesi interruptive bildirimleri gönderir.

Aşağıdaki örnekte gösterildiği gibi, ilgilendiğiniz öğe üzerinde **AutomationProperties. livesetting** özelliğini ayarlayarak bir LiveRegion oluşturabilirsiniz:

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

Canlı bölgedeki veriler değiştiğinde ve bir ekran okuyucuyu bilgilendirmeniz gerektiğinde, aşağıdaki örnekte gösterildiği gibi, açıkça bir olay oluşturursunuz.

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

**High contrast**

.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimlerinde yüksek karşıtlıklı geliştirmeler yapılmıştır. Artık <xref:System.Windows.SystemParameters.HighContrast%2A> Tema ayarlandığında görünür olur. Bunlara

- <xref:System.Windows.Controls.Expander>denetimle

  Denetim için odak görseli <xref:System.Windows.Controls.Expander> artık görülebilir. <xref:System.Windows.Controls.ComboBox>, Ve denetimlerinin klavye görselleri <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.RadioButton> de görünür. Örneğin:

  Önce:

  ![Odak içeren genişleticiye ve odak görselinle kumanda ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-before.png)

  Sonra:

  ![Odak ile denetimin metninin etrafında noktalı bir çizgi gösteren genişleticiyle ilgili ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-after.png)

- <xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> denetimler

  <xref:System.Windows.Controls.CheckBox>Ve <xref:System.Windows.Controls.RadioButton> denetimlerindeki metin artık yüksek karşıtlık temalarında seçildiğinde daha kolay görülebilir. Örneğin:

  Önce:

  ![Yüksek karşıtlık temalarda kötü metin görünürlüğüne sahip radyo ve denetim düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  Sonra:

  ![Yüksek karşıtlık temalarda daha iyi metin görünürlüğü olan radyo ve denetim düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <xref:System.Windows.Controls.ComboBox>denetimle

  .NET Framework 4.7.1 ile başlayarak, devre dışı bir denetimin kenarlığı <xref:System.Windows.Controls.ComboBox> devre dışı metinle aynı renktedir. Örneğin:

  Önce:

  ![Farklı renklerde kenarlık ve denetim metni olan devre dışı bir ComboBox 'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  Sonra:

  ![Denetim metniyle aynı renge sahip devre dışı bir ComboBox 'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  Ayrıca, devre dışı bırakılmış ve odaklanmış düğmeler doğru tema rengini kullanır.

  Önce:

  ![Renkli gri metinli siyah bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  Sonra:

  ![Siyah metin ile mavi bir düğmenin, odağı bana söyleyen ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  Son olarak, .NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.ComboBox> `Toolbar.ComboBoxStyleKey` açılır okun görünmez olması nedeniyle bir denetimin stilini ayarlama. Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir. Örneğin:

  Önce:

  ![Görünmeyen açılan oka sahip ComboBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  Sonra:

  ![Açılan oku görüntüleyen bir ComBoxBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <xref:System.Windows.Controls.DataGrid>denetimle

  .NET Framework 4.7.1 başlayarak, denetimlerde sıralama göstergesi oku <xref:System.Windows.Controls.DataGrid> artık doğru Tema renklerini kullanır. Örneğin:

  Önce:

  ![Geliştirmeden önce sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  Sonra:

  ![İyileştirmeler sonrasında sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  Ayrıca, .NET Framework 4,7 ve önceki sürümlerde, varsayılan bağlantı stili, fare üzerinde yüksek karşıtlık modlarında yanlış bir renge değiştirilmiştir. Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir. Benzer şekilde, <xref:System.Windows.Controls.DataGrid> CheckBox sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirimi için beklenen renkleri kullanır.

  Önce:

  ![Bağlantının ekran görüntüsü bana tıklayın! kırmızı olarak.](./media/whats-new-in-accessibility/default-link-style-before.png)

  Sonra:

  ![Bağlantının ekran görüntüsü bana tıklayın! sarı olarak.](./media/whats-new-in-accessibility/default-link-style-after.png)

.NET Framework 4.7.1 ' deki WPF Erişilebilirlik iyileştirmeleri hakkında daha fazla bilgi için bkz. [WPF 'de erişilebilirlik geliştirmeleri](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a>Windows Forms erişilebilirlik geliştirmeleri

.NET Framework 4.7.1, Windows Forms (WinForms), aşağıdaki alanlardaki erişilebilirlik değişikliklerini içerir.

**Yüksek Karşıtlık modunda iyileştirilmiş ekran**

.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sisteminde bulunan üst karşıtlık modlarında geliştirilmiş işleme sunar. Windows 10, bazı yüksek karşıtlıklı sistem renklerinin değerlerini değiştirdi ve Windows Forms Windows 10 Win32 çerçevesini temel alır. En iyi deneyim için, Windows 'un en son sürümünde çalıştırın ve bir test uygulamasına bir App. manifest dosyası ekleyerek en son işletim sistemi değişikliklerini kabul edin ve Windows 10 desteklenen işletim sistemi satırını, aşağıdakileri içerecek şekilde not edin:

```xml
<!-- Windows 10 -->
<supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
```

Yüksek karşıtlıklı değişikliklere örnek olarak şunlar verilebilir:

- Öğelerin içindeki onay işaretlerinin <xref:System.Windows.Forms.MenuStrip> görünümü daha kolay.

- Seçildiğinde, devre dışı bırakılan <xref:System.Windows.Forms.MenuStrip> öğeler daha kolay görüntülenir.

- Seçili <xref:System.Windows.Forms.Button> denetimdeki metin seçim rengiyle karşıttır.

- Devre dışı bırakılan metin daha kolay okunabilir. Örneğin:

  Önce:

  ![Erişilebilirlik geliştirmelerinden önce yüksek karşıtlıklı modda çalışan farklı denetimleri kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  Sonra:

  ![Erişilebilirlik iyileştirmelerinden sonra yüksek karşıtlıklı modda çalışan farklı denetimleri kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- Iş parçacığı özel durumu Iletişim kutusunda yüksek karşıtlık geliştirmeleri.

**İyileştirilmiş ekran okuyucusu desteği**

.NET Framework 4.7.1 Windows Forms, ekran okuyucusu için aşağıdaki erişilebilirlik geliştirmelerini içerir:

- <xref:System.Windows.Forms.MonthCalendar>Denetime, DIĞER UI Otomasyon Araçları ile birlikte ekran okuyucusu tarafından erişilebilir.

- Denetim, bir <xref:System.Windows.Forms.CheckedListBox> öğenin denetim durumu değiştiğinde kullanıcıya bir liste öğesinin değerini değiştirdikleri bildirilir.

- <xref:System.Windows.Forms.DataGridViewCell>Denetim, doğru salt okuma durumunu ekran okuyucusuna bildirir.

- Ekran okuyucusu artık devre dışı bırakılan <xref:System.Windows.Forms.ToolStripMenuItem> metni okuyabilir, ancak daha önce devre dışı menü öğelerini atlar.

**UIAutomation erişilebilirlik desenleri için gelişmiş destek**

.NET Framework 4.7.1 ile başlayarak, erişilebilirlik teknolojisi araçları geliştiricileri, çeşitli WinForms denetimleri için ortak API erişilebilirlik desenlerinden ve özelliklerinden faydalanabilir. Bu erişilebilirlik geliştirmeleri şunları içerir:

- <xref:System.Windows.Forms.ComboBox>Ve <xref:System.Windows.Forms.ToolStripSplitButton> artık [genişletme/daraltma düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekliyor.

- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>Artık [geçişli stili](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)destekliyor.

- <xref:System.Windows.Forms.ToolStripItem>Denetim, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.

- <xref:System.Windows.Forms.NumericUpDown>Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği destekler.

**Geliştirilmiş özellik tarayıcı deneyimi**

.NET Framework 4.7.1 ile başlayarak, Windows Forms şunları içerir:

- Çeşitli açılan seçim pencereleri aracılığıyla daha iyi klavye gezintisi.
- Gereksiz sekme duraklarının azaltılması.
- Denetim türlerinin daha iyi raporlaması.
- İyileştirilmiş ekran okuyucusu davranışı.

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a>ASP.NET Web denetimleri

.NET Framework 4.7.1 ve Visual Studio 2017 sürüm 15,3 ' den başlayarak, ASP.NET ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirir. Değişiklikler şunları içerir:

- **Ayrıntılar görünümü** sihirbazındaki **alan Ekle** Iletişim kutusu ya da **ListView** sihirbazının **LISTVIEW yapılandırma** iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.

- **Veri sayfalayıcı alanları Düzenleyicisi**gibi yüksek karşıtlık modunda görüntüyü geliştirmek için değişiklikler.

- DataPager denetiminin **sayfalayıcı alanlarını Düzenle** Sihirbazı 'ndaki **alanlar** **iletişim kutusu gibi** denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler veya **veri kaynağını yapılandırma** Sihirbazı 'Nın veri kaynağını yapılandırma Sihirbazı ' nın **veri seçimini Yapılandır** iletişim kutusu.

<a name="tools471"></a>

### <a name="net-sdk-tools"></a>.NET SDK Tools

[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme görüntüleyicisi Aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) , değişen erişilebilirlik sorunları düzeltilirken geliştirilmiştir. Bunların çoğu, bir ad tanımlanmadığında veya belirli Kullanıcı Arabirimi Otomasyonu desenlerinin doğru uygulanmadığından küçük sorunlardır. Birçok kullanıcı bu hatalı değerleri bilmez, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK araçlarını daha erişilebilir bulacaktır.

Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a>Windows Workflow Foundation (WF) İş Akışı Tasarımcısı

İş Akışı Tasarımcısı erişilebilirlik değişiklikleri şunları içerir:

- Sekme sırası, bazı denetimlerde soldan sağa ve yukarıdan aşağıya değişir:

  - Etkinlik için bağıntı verileri ayarlamaya yönelik bağıntı Başlat penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> .

  - <xref:System.ServiceModel.Activities.Receive>,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> Ve etkinlikleri için içerik tanımı penceresi <xref:System.ServiceModel.Activities.ReceiveReply> .

- Klavye aracılığıyla daha fazla işlev mevcuttur:

  - Bir etkinliğin özelliklerini düzenlediğinizde, özellik grupları ilk odaklandığında klavye tarafından daraltılabilirler.

  - Uyarı simgeleri klavye tarafından erişilebilir.

  - **Özellikler** penceresindeki **daha fazla Özellikler** düğmesine klavye tarafından erişilebilir.

  - Klavye kullanıcıları İş Akışı Tasarımcısı **bağımsız değişkenler** ve **değişkenler** bölmelerinde üst bilgi öğelerine erişebilirler.

- Odaklanılmış öğelerin şu durumlarda geliştirilmiş görünürlüğü:

  - İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzlarına satır ekleme.

  - <xref:System.ServiceModel.Activities.ReceiveReply>Ve etkinliklerindeki alanlar arasında sekme <xref:System.ServiceModel.Activities.SendReply> .

  - Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama

- Ekran okuyucular artık doğru şekilde tanıyabilir:

  - İş akışı tasarımcısında ayarlanan kesme noktaları.

  - <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision> Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikleri.
  - <xref:System.ServiceModel.Activities.Receive>Etkinliğin içeriği.

  - Etkinliğin hedef türü <xref:System.Activities.Statements.InvokeMethod> .

  - Etkinliğin özel durum açılan kutusu ve son bölümü <xref:System.Activities.Statements.TryCatch> .

  - İleti türü açılan kutusu, bağıntı başlatıcı ekleme penceresinde, içerik tanımı penceresinde ve CorrelatesOn tanımı penceresinde, ileti etkinliklerinin ( <xref:System.ServiceModel.Activities.Receive> ,, <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply> ve <xref:System.ServiceModel.Activities.ReceiveReply> ).

  - Durum makinesi geçişleri ve geçiş hedefleri.

  - Etkinlikler üzerinde ek açıklamalar ve bağlayıcılar <xref:System.Activities.Statements.FlowDecision> .

  - Etkinlikler için bağlam (sağ tıklama) menüleri.

  - Özellik değeri düzenleyicileri, aramayı temizle düğmesi, kategoriye ve alfabetik sıralama düğmelerine göre ve Özellikler kılavuzundaki Ifade Düzenleyicisi iletişim kutusu.

  - İş Akışı Tasarımcısı yakınlaştırma yüzdesi.

  - <xref:System.Activities.Statements.Parallel>Ve <xref:System.Activities.Statements.Pick> etkinliklerindeki ayırıcı.

  - <xref:System.Activities.Statements.InvokeDelegate>Etkinlik.

  - Sözlük Etkinlikleri ( `Microsoft.Activities.AddToDictionary<TKey,TValue>` , `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>` , vb.) Için türleri seçin penceresi.

  - .NET tür araştır ve Seç penceresi.

  - İş Akışı Tasarımcısı içerik haritaları.

- Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde birçok geliştirme görür.

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Framework’teki yenilikler](index.md)
