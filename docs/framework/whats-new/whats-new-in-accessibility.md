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
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="18b36-102">.NET Framework'de erişilebilirlikte yenilikler</span><span class="sxs-lookup"><span data-stu-id="18b36-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="18b36-103">.NET Framework, uygulamaları kullanıcılarınız için daha erişilebilir hale getirmeyi amaçlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="18b36-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="18b36-104">Erişilebilirlik özellikleri, bir uygulamanın Yardımcı Teknoloji kullanıcıları için uygun bir deneyim sağlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b36-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="18b36-105">.NET Framework 4.7.1 ile başlayarak ,.NET Framework, geliştiricilerin erişilebilir uygulamalar oluşturmasına olanak tanıyan çok sayıda erişilebilirlik geliştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="18b36-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="18b36-106">Erişilebilirlik anahtarları</span><span class="sxs-lookup"><span data-stu-id="18b36-106">Accessibility switches</span></span>

<span data-ttu-id="18b36-107">Uygulamanızı ,NET Framework 4.7 veya daha önceki bir sürümü hedefliyorsa, ancak .NET Framework 4.7.1 veya sonraki sürümde çalışıyorsa erişilebilirlik özelliklerini seçecek şekilde yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="18b36-108">Uygulamanızı ,NET Framework 4.7.1 veya daha sonrasını hedefliyorsa eski özellikleri kullanacak (ve erişilebilirlik özelliklerinden yararlanmayacak şekilde) de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="18b36-109">.NET Framework'ün erişilebilirlik özelliklerini içeren her sürümünde, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasının bölümündeki öğeye eklediğiniz sürüme özgü erişilebilirlik anahtarı vardır.</span><span class="sxs-lookup"><span data-stu-id="18b36-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="18b36-110">Desteklenen anahtarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18b36-110">The following are the supported switches:</span></span>

|<span data-ttu-id="18b36-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="18b36-111">Version</span></span>|<span data-ttu-id="18b36-112">Anahtar</span><span class="sxs-lookup"><span data-stu-id="18b36-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="18b36-113">.NET Çerçeve 4.7.1</span><span class="sxs-lookup"><span data-stu-id="18b36-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="18b36-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="18b36-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="18b36-115"> .NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="18b36-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="18b36-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="18b36-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="18b36-117"> .NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="18b36-117">.NET Framework 4.8</span></span>|<span data-ttu-id="18b36-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="18b36-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="18b36-119">Erişilebilirlik geliştirmelerinden yararlanma</span><span class="sxs-lookup"><span data-stu-id="18b36-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="18b36-120">Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 veya sonraki lerini hedefleyen uygulamalar için varsayılan olarak etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="18b36-121">Buna ek olarak, .NET Framework'ün önceki bir sürümünü hedefleyen ancak .NET Framework 4.7.1 veya daha sonra üzerinde çalışan uygulamalar, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasının bölümündeki öğeye anahtarlar ekleyerek ve değerini `false`belirleyerek eski erişilebilirlik davranışlarını devre dışı edebilir (ve bu nedenle erişilebilirlik iyileştirmelerinden yararlanabilir).</span><span class="sxs-lookup"><span data-stu-id="18b36-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="18b36-122">Aşağıda ,NET Framework 4.7.1'de tanıtılan erişilebilirlik geliştirmelerine nasıl tercih edilebilmektedir:</span><span class="sxs-lookup"><span data-stu-id="18b36-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="18b36-123">.NET Framework'ün sonraki bir sürümünde erişilebilirlik özelliklerini seçmeyi seçerseniz, .NET Framework'ün önceki sürümlerindeki özellikleri de açıkça seçmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="18b36-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="18b36-124">Uygulamanızı hem .NET Framework 4.7.1 hem de 4.7.2'deki erişilebilirlik iyileştirmelerinden yararlanacak şekilde yapılandırmak için aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğe yi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="18b36-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="18b36-125">Uygulamanızı .NET Framework 4.7.1, 4.7.2 ve 4.8'deki erişilebilirlik iyileştirmelerinden yararlanacak [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) şekilde yapılandırmak için aşağıdaki öğe yi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="18b36-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="18b36-126">Eski davranışı geri alma</span><span class="sxs-lookup"><span data-stu-id="18b36-126">Restoring legacy behavior</span></span>

<span data-ttu-id="18b36-127">4.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) dosyasıbölümündeki elemana anahtarlar ekleyerek ve değerini 'ye `true`ayarlayarak erişilebilirlik özelliklerini devre dışı düşürebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="18b36-128">Örneğin, aşağıdaki yapılandırma .NET Framework 4.7.2'de tanıtılan erişilebilirlik özelliklerinden vazgeçer:</span><span class="sxs-lookup"><span data-stu-id="18b36-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="18b36-129">.NET Framework 4.8'de erişilebilirlikte yenilikler</span><span class="sxs-lookup"><span data-stu-id="18b36-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="18b36-130">.NET Framework 4.8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="18b36-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b36-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="18b36-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="18b36-133">Windows İş Akışı Temeli (WF) iş akışı tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="18b36-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="18b36-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b36-134">Windows Forms</span></span>

<span data-ttu-id="18b36-135">.NET Framework 4.8'de, Windows Formları sık kullanılan birçok denetime LiveRegions ve Bildirim Olayları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="18b36-136">Ayrıca, bir kullanıcı klavyeyi kullanarak denetime gittiğinde ToolTips için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="18b36-137">**Etiketlerde ve StatusStrips'te UIA LiveRegions Desteği**</span><span class="sxs-lookup"><span data-stu-id="18b36-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="18b36-138">UIA LiveRegions, uygulama geliştiricilerin, kullanıcının çalıştığı yerin dışında bulunan bir denetimdeki metin değişikliğini ekran okuyucularına bildirmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="18b36-139">Bu, örneğin, bağlantı durumunu <xref:System.Windows.Forms.StatusStrip> gösteren bir denetim için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="18b36-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="18b36-140">Bağlantı bırakılırsa ve durum değişirse, geliştirici ekran okuyucuya bildirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="18b36-141">.NET Framework 4.8 ile başlayarak, Windows Forms hem <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> denetimler hem de denetimler için UIA LiveRegions uygular.</span><span class="sxs-lookup"><span data-stu-id="18b36-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="18b36-142">Örneğin, aşağıdaki kod LiveRegion adlı <xref:System.Windows.Forms.Label> `label1`bir denetim kullanır:</span><span class="sxs-lookup"><span data-stu-id="18b36-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="18b36-143">Ekran Okuyucusu, kullanıcının uygulamayla nerede etkileşimde bulunduğuna bakılmaksızın "Hazır" bildirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="18b36-144">Ayrıca bir LiveRegion <xref:System.Windows.Forms.UserControl> olarak uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="18b36-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="18b36-145">**UIA bildirim olayları**</span><span class="sxs-lookup"><span data-stu-id="18b36-145">**UIA notification events**</span></span>

<span data-ttu-id="18b36-146">Windows 10 Fall Creators Update'te tanıtılan UIA Bildirimi etkinliği, uygulamanızın, Kullanıcı Bira'da karşılık gelen bir denetime gerek kalmadan, ekran okuyucusu yalnızca olayla ilgili olarak sağladığınız metne dayalı bir duyuru yapmasına yol açan bir Kullanıcı Durumu etkinliğini yükseltmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="18b36-147">Bazı senaryolarda bu, uygulamanızın erişilebilirliğini önemli ölçüde artırmanın basit bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="18b36-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="18b36-148">Ayrıca uzun zaman alabilir bazı sürecin ilerleme bildirmek için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="18b36-149">UIA Bildirim Etkinlikleri hakkında daha fazla bilgi için [bkz.](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need)</span><span class="sxs-lookup"><span data-stu-id="18b36-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://docs.microsoft.com/archive/blogs/winuiautomation/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need).</span></span>

<span data-ttu-id="18b36-150">Aşağıdaki örnekbildirim [olayını](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)yükseltir:</span><span class="sxs-lookup"><span data-stu-id="18b36-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="18b36-151">**Klavye erişiminde Araç İpuçları**</span><span class="sxs-lookup"><span data-stu-id="18b36-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="18b36-152">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, bir denetim [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca bir fare işaretçisini denetime taşıyarak açılır.</span><span class="sxs-lookup"><span data-stu-id="18b36-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="18b36-153">.NET Framework 4.8 ile başlayarak, klavye kullanıcısı denetime sekme tuşu veya ok tuşlarını kullanarak veya değiştirici tuşları olmadan odaklanarak bir denetimin araç ucunu tetikleyebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="18b36-154">Bu özel erişilebilirlik geliştirme ek bir [AppContext anahtarı](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)gerektirir:</span><span class="sxs-lookup"><span data-stu-id="18b36-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="18b36-155">Aşağıdaki şekilde, kullanıcı klavyeli bir düğme seçtiğinde araç ipucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="18b36-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Kullanıcı klavyeyle düğmeye gittiğinde araç ucunun ekran görüntüsü.](./media/whats-new-in-accessibility/select-tooltip-with-keyboard.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="18b36-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="18b36-158">.NET Framework 4.8 ile başlayarak WPF bir dizi erişilebilirlik iyileştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="18b36-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="18b36-159">**Ekran ekranları artık Daraltılmış veya Gizli görünürlüğe sahip öğeleri duyurmadı**</span><span class="sxs-lookup"><span data-stu-id="18b36-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="18b36-160">Daraltılmış veya gizli görünürlüğe sahip öğeler artık ekran okuyucu tarafından duyurulmadı.</span><span class="sxs-lookup"><span data-stu-id="18b36-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="18b36-161">Görünürlüğe sahip öğeler içeren <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> veya <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> kullanıcıya duyurulması durumunda ekran okuyucular tarafından yanlış tanıtılabilen kullanıcı arabirimleri.</span><span class="sxs-lookup"><span data-stu-id="18b36-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="18b36-162">.NET Framework 4.8 ile başlayarak, WPF artık UIAutomation ağacının Denetim Görünümü'nde daraltılmış veya gizli öğeleri içermez, böylece ekran okuyucular artık bu öğeleri duyuramaz.</span><span class="sxs-lookup"><span data-stu-id="18b36-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="18b36-163">**SeçimTextBrush özelliği olmayan Adorner tabanlı metin seçimi ile kullanım için**</span><span class="sxs-lookup"><span data-stu-id="18b36-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="18b36-164">.NET Framework 4.7.2'de WPF, Adorner <xref:System.Windows.Controls.PasswordBox> katmanını kullanmadan metin seçimi ve çizim <xref:System.Windows.Controls.TextBox> yapma olanağı nı ekledi.</span><span class="sxs-lookup"><span data-stu-id="18b36-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="18b36-165">Bu senaryoda <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>seçilen metnin ön plan rengi .</span><span class="sxs-lookup"><span data-stu-id="18b36-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="18b36-166">.NET Framework 4.8, `SelectionTextBrush`geliştiricilerin Adorner tabanlı olmayan metin seçimini kullanırken seçilen metin için belirli fırçayı seçmelerine olanak tanıyan yeni bir özellik ekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="18b36-167">Bu özellik yalnızca <xref:System.Windows.Controls.Primitives.TextBoxBase>-türetilmiş <xref:System.Windows.Controls.PasswordBox> denetimlerde ve Adorner tabanlı olmayan metin seçimi etkinleştirilmiş WPF uygulamalarında denetim de çalışır.</span><span class="sxs-lookup"><span data-stu-id="18b36-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="18b36-168"><xref:System.Windows.Controls.RichTextBox> Denetimde çalışmıyor.</span><span class="sxs-lookup"><span data-stu-id="18b36-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="18b36-169">Adorner tabanlı olmayan metin seçimi etkinleştirilemezse, bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="18b36-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="18b36-170">Bu özelliği kullanmak için XAML kodunuza eklemeniz ve uygun fırçayı veya bağlamayı kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="18b36-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="18b36-171">Elde edilen metin seçimi aşağıdaki gibi görünür:</span><span class="sxs-lookup"><span data-stu-id="18b36-171">The resulting text selection looks like this:</span></span>

![Merhaba Dünya kelimeleriyle çalışan uygulamanın ekran görüntüsü seçildi.](./media/whats-new-in-accessibility/selectiontextbrush-property.png)

<span data-ttu-id="18b36-173">Uygun gördüğünüz herhangi bir `SelectionBrush` `SelectionTextBrush` arka plan ve ön plan renk kombinasyonu oluşturmak için ve özelliklerinin kullanımını birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="18b36-174">**UIAutomation ControllerFor özelliği ne destek**</span><span class="sxs-lookup"><span data-stu-id="18b36-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="18b36-175">UIAutomation'ın `ControllerFor` özelliği, bu özelliği destekleyen otomasyon öğesi tarafından manipüle edilen bir dizi otomasyon öğesini döndürür.</span><span class="sxs-lookup"><span data-stu-id="18b36-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="18b36-176">Bu özellik genellikle Otomatik öner erişilebilirlik için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18b36-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="18b36-177">`ControllerFor`bir otomasyon öğesi uygulama kullanıcı larının veya masaüstünün bir veya daha fazla kesimini etkilediğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="18b36-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="18b36-178">Aksi takdirde, denetim işleminin etkisini UI öğeleriyle ilişkilendirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="18b36-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="18b36-179">Bu özellik, denetimlerin özellik için bir `ControllerFor` değer sağlama özelliğini ekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="18b36-180">.NET Framework 4.8 yeni bir <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>sanal yöntem ekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-181">`ControllerFor` Özellik için bir değer sağlamak için, bu yöntemi `List<AutomationPeer>` geçersiz kılmak ve bu <xref:System.Windows.Automation.Peers.AutomationPeer>tarafından manipüle edilen denetimler için bir döndürmeniz yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="18b36-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="18b36-182">**Klavye erişiminde araç ipuçları**</span><span class="sxs-lookup"><span data-stu-id="18b36-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="18b36-183">.NET Framework 4.7.2 ve önceki sürümlerde, araç ipuçları yalnızca kullanıcı fare imlecini bir denetimüzerinde gezindiğinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="18b36-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="18b36-184">.NET Framework 4.8'de, araç ipuçları klavye odağının yanı sıra klavye kısayolu aracılığıyla da görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="18b36-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="18b36-185">Bu özelliği etkinleştirmek için bir uygulamanın .NET Framework 4.8'i hedeflemesi veya `Switch.UseLegacyAccessibilityFeatures.3` `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlarını kullanarak kabul etmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="18b36-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="18b36-186">Örnek bir uygulama yapılandırma dosyası aşağıda veda edilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="18b36-187">Etkinleştirildiğinde, bir araç ipucu içeren tüm denetimler, denetim klavye odağı aldıktan sonra görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="18b36-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="18b36-188">Araç ipucu zaman içinde veya klavye odağı değiştiğinde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="18b36-189">Kullanıcılar ayrıca yeni bir klavye kısayolu olan Ctrl + Shift + F10'u kullanarak araç ucunu el ile kapatabilirler.</span><span class="sxs-lookup"><span data-stu-id="18b36-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="18b36-190">Araç ipucu çıkarıldıktan sonra aynı klavye kısayolu kullanılarak yeniden görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="18b36-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) Denetimlerde <xref:System.Windows.Controls.Ribbon.Ribbon> şerit araç ipuçları klavye odağında gösterilmez; yalnızca klavye kısayolu üzerinden gösterirler.</span><span class="sxs-lookup"><span data-stu-id="18b36-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="18b36-192">**SizeOfSet ve PositionInSet UIAutomation özellikleri için destek eklendi**</span><span class="sxs-lookup"><span data-stu-id="18b36-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="18b36-193">Windows 10, `SizeOfSet` `PositionInSet`bir kümedeki öğelerin sayısını açıklamak için uygulamalar tarafından kullanılan iki yeni UIAutomation özelliğini tanıttı.</span><span class="sxs-lookup"><span data-stu-id="18b36-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="18b36-194">Ekran okuyucular gibi UIAutomation istemci uygulamaları daha sonra bu özellikler için bir uygulamayı sorgulayabilir ve uygulamanın Kullanıcı Arabirimi'nin doğru bir temsilini açıklayabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="18b36-195">.NET Framework 4.8 ile başlayarak, WPF bu iki özelliği WPF uygulamalarında UIAutomation'a maruz bırakır.</span><span class="sxs-lookup"><span data-stu-id="18b36-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="18b36-196">Bu iki şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="18b36-197">Bağımlılık özelliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="18b36-197">By using dependency properties.</span></span>

  <span data-ttu-id="18b36-198">WPF iki yeni bağımlılık <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> özelliği <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>ekler ve .</span><span class="sxs-lookup"><span data-stu-id="18b36-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-199">Bir geliştirici değerlerini ayarlamak için XAML'yi kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="18b36-200">AutomationPeer sanal yöntemleri geçersiz kılarak.</span><span class="sxs-lookup"><span data-stu-id="18b36-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="18b36-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> AutomationPeer <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sınıfına sanal yöntemler eklendi.</span><span class="sxs-lookup"><span data-stu-id="18b36-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="18b36-202">Bir geliştirici, aşağıdaki `SizeOfSet` `PositionInSet` örnekte gösterildiği gibi, bu yöntemler için ve geçersiz kılınarak değerler sağlayabilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="18b36-203">Buna ek olarak, örneklerdeki <xref:System.Windows.Controls.ItemsControl> öğeler, geliştiriciden ek bir eylem olmadan bu özellikler için otomatik olarak bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b36-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="18b36-204">Bir <xref:System.Windows.Controls.ItemsControl> grupgruplu ise, grup koleksiyonu bir küme olarak temsil edilir ve her grup ayrı bir küme olarak sayılır ve bu grubun içindeki her öğe, grubun içindeki konumunu ve grubun boyutunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="18b36-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="18b36-205">Otomatik değerler sanallaştırmadan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="18b36-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="18b36-206">Bir öğe gerçekleştirilmese bile, yine de kümenin toplam boyutuna doğru sayılır ve kardeş öğeler kümesindeki konumu etkiler.</span><span class="sxs-lookup"><span data-stu-id="18b36-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="18b36-207">Otomatik değerler yalnızca uygulama .NET Framework 4.8'i hedefliyorsa sağlanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="18b36-208">.NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için, aşağıdaki App.config dosyasında gösterildiği gibi `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="18b36-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="18b36-209">Windows İş Akışı Temeli (WF) iş akışı tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="18b36-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="18b36-210">İş akışı tasarımcısı .NET Framework 4.8'de aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="18b36-211">Ekran Okuyucusu'nun kullanımı FlowSwitch servis talebi etiketlerinde iyileştirmeler görür.</span><span class="sxs-lookup"><span data-stu-id="18b36-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="18b36-212">Ekran Okuyucusu'nun kullanımı düğme açıklamalarında iyileştirmeler görür.</span><span class="sxs-lookup"><span data-stu-id="18b36-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="18b36-213">Yüksek Karşıtlık temaları seçen kullanıcılar, öğeler arasındaki daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı'nın ve denetimlerinin görünürlüğünde iyileştirmeler görür.</span><span class="sxs-lookup"><span data-stu-id="18b36-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="18b36-214">Uygulamanız .NET Framework 4.7.2 veya daha önceki bir sürümü hedefliyorsa, uygulama yapılandırma dosyanızda `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `false` ayarlayarak bu değişiklikleri tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="18b36-215">Daha fazla bilgi için, bu [makaledeki erişilebilirlik geliştirmeleri bölümünden yararlanın](#taking-advantage-of-accessibility-enhancements) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="18b36-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="18b36-216">.NET Framework 4.7.2'de erişilebilirlikte yenilikler</span><span class="sxs-lookup"><span data-stu-id="18b36-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="18b36-217">.NET Framework 4.7.2 aşağıdaki alanlarda yeni erişilebilirlik özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="18b36-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b36-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="18b36-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="18b36-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b36-220">Windows Forms</span></span>

<span data-ttu-id="18b36-221">**Yüksek Karşıtlık temalarında işletim sistemi tanımlı renkler**</span><span class="sxs-lookup"><span data-stu-id="18b36-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="18b36-222">.NET Framework 4.7.2 ile başlayarak, Windows Forms Yüksek Karşıtlık temalarında işletim sistemi tarafından tanımlanan renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="18b36-223">Bu, aşağıdaki denetimleri etkiler:</span><span class="sxs-lookup"><span data-stu-id="18b36-223">This affects the following controls:</span></span>

- <span data-ttu-id="18b36-224">Kontrolün <xref:System.Windows.Forms.ToolStripDropDownButton> açılır ok.</span><span class="sxs-lookup"><span data-stu-id="18b36-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="18b36-225"><xref:System.Windows.Forms.RadioButton> ' <xref:System.Windows.Forms.Button>ve <xref:System.Windows.Forms.CheckBox> set <xref:System.Windows.Forms.ButtonBase.FlatStyle> ile <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>kontroller veya .</span><span class="sxs-lookup"><span data-stu-id="18b36-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-226">Daha önce, seçili metin ve arka plan renkleri zıt değildi ve okunması zordu.</span><span class="sxs-lookup"><span data-stu-id="18b36-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="18b36-227">Bir içinde <xref:System.Windows.Forms.GroupBox> bulunan denetimler kendi <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ayarlanmış. `false`</span><span class="sxs-lookup"><span data-stu-id="18b36-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="18b36-228">Yüksek <xref:System.Windows.Forms.ToolStripComboBox>Kontrast <xref:System.Windows.Forms.ToolStripDropDownButton> Modunda parlaklık kontrast oranı nın arttığı , ve kontroller. <xref:System.Windows.Forms.ToolStripButton></span><span class="sxs-lookup"><span data-stu-id="18b36-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="18b36-229">Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="18b36-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="18b36-230">**Anlatıcı iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="18b36-230">**Narrator improvements**</span></span>

<span data-ttu-id="18b36-231">.NET Framework 4.7.2 ile başlayarak, Ekran Okuyucudesteği aşağıdaki gibi geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="18b36-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="18b36-232">Bir ' nin metnini <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> açıklarken özelliğin <xref:System.Windows.Forms.ToolStripMenuItem>değerini bildirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="18b36-233">Bir özelliğinin <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.Control.Enabled> ne zaman `false`ayarlı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="18b36-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="18b36-234">Özellik ' e ayarlandığında <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> onay kutusunun durumu `true`hakkında geri bildirim verir.</span><span class="sxs-lookup"><span data-stu-id="18b36-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="18b36-235">Ekran Okuyucusu'nun Scan Modu odak lama sırası, ClickOnce indir iletişim penceresindeki denetimlerin görsel sırası ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="18b36-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="18b36-236">**DataGridView geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="18b36-236">**DataGridView improvements**</span></span>

<span data-ttu-id="18b36-237">.NET Framework 4.7.2 ile <xref:System.Windows.Forms.DataGridView> başlayarak, denetim aşağıdaki erişilebilirlik iyileştirmelerini getirmiştir:</span><span class="sxs-lookup"><span data-stu-id="18b36-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="18b36-238">Satırlar klavye kullanılarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="18b36-239">Bir kullanıcı geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="18b36-240"><xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> Sütun üstbilgi, <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>kullanıcı geçerli satırdaki hücreler arasında sekerken geçerli sütunu belirtmek için renk değiştirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="18b36-241">Bir <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> özelliği <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetim döndürür.</span><span class="sxs-lookup"><span data-stu-id="18b36-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="18b36-242">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="18b36-242">**Improved visual cues**</span></span>

- <span data-ttu-id="18b36-243">Boş <xref:System.Windows.Forms.RadioButton> <xref:System.Windows.Forms.ButtonBase.Text> <xref:System.Windows.Forms.CheckBox> bir özellik ile ve denetimler, odak aldığında bir odak göstergesi görüntüler.</span><span class="sxs-lookup"><span data-stu-id="18b36-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="18b36-244">**Geliştirilmiş Özellik Grid Desteği**</span><span class="sxs-lookup"><span data-stu-id="18b36-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="18b36-245">Denetim <xref:System.Windows.Forms.PropertyGrid> alt öğeleri artık `true` yalnızca <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> bir PropertyGrid öğesi etkinleştirildiğinde özellik için a döndürür.</span><span class="sxs-lookup"><span data-stu-id="18b36-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="18b36-246">Denetim <xref:System.Windows.Forms.PropertyGrid> alt öğeleri `false` yalnızca <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> bir PropertyGrid öğesi kullanıcı tarafından değiştirildiğinde özellik için bir döndürür.</span><span class="sxs-lookup"><span data-stu-id="18b36-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="18b36-247">**Geliştirilmiş klavye gezintisi**</span><span class="sxs-lookup"><span data-stu-id="18b36-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="18b36-248">Denetim, <xref:System.Windows.Forms.ToolStripButton> özelliği ayarlanmış bir <xref:System.Windows.Forms.ToolStripPanel> içinde <xref:System.Windows.Forms.ToolStripPanel.TabStop> bulunduğunda odaklanmayı sağlar`true`</span><span class="sxs-lookup"><span data-stu-id="18b36-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="18b36-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="18b36-250">**CheckBox ve RadioButton denetimleri değişiklikleri**</span><span class="sxs-lookup"><span data-stu-id="18b36-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="18b36-251">.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimler tutarsız ve Klasik ve Yüksek Karşıtlık temalarında yanlış odak görsellerine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="18b36-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="18b36-252">Bu sorunlar, denetimlerin herhangi bir içerik kümesinin olmadığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="18b36-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="18b36-253">Bu temalar kafa karıştırıcı ve odak görsel görmek zor arasındaki geçiş yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="18b36-254">.NET Framework 4.7.2'de bu görseller artık temalar arasında daha tutarlı ve Klasik ve Yüksek Karşıtlık temalarında daha kolay görülebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="18b36-255">**WinForms denetimleri bir WPF uygulamasında barındırılan**</span><span class="sxs-lookup"><span data-stu-id="18b36-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="18b36-256">.NET Framework 4.7.1 ve önceki sürümlerde bir WPF uygulamasında barındırılan WinForms denetimi için, bu katmandaki ilk veya son <xref:System.Windows.Forms.Integration.ElementHost> denetim WPF denetimi yse, kullanıcılar WinForms katmanından çıkamaz.</span><span class="sxs-lookup"><span data-stu-id="18b36-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="18b36-257">.NET Framework 4.7.2'de kullanıcılar artık WinForms katmanını sekmeyapabiliyor.</span><span class="sxs-lookup"><span data-stu-id="18b36-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="18b36-258">Ancak, WinForms katmanından asla kaçamayan odaklara dayanan otomatik uygulamalar artık beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="18b36-259">.NET Framework 4.7.1'de erişilebilirlikte yenilikler</span><span class="sxs-lookup"><span data-stu-id="18b36-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="18b36-260">.NET Framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özelliklerini içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="18b36-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="18b36-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="18b36-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="18b36-263">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="18b36-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="18b36-264">.NET SDK Araçları</span><span class="sxs-lookup"><span data-stu-id="18b36-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="18b36-265">Windows İş Akışı Temeli (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="18b36-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="18b36-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="18b36-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="18b36-267">**Ekran okuyucu iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="18b36-267">**Screen reader improvements**</span></span>

<span data-ttu-id="18b36-268">Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucularını etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="18b36-269">.NET Framework 4.7 ve <xref:System.Windows.Controls.Expander> önceki sürümlerde denetimler ekran okuyucular tarafından düğme olarak duyuruldu.</span><span class="sxs-lookup"><span data-stu-id="18b36-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="18b36-270">.NET Framework 4.7.1 ile başlayarak, genişletilebilir/katlanabilir gruplar olarak doğru bir şekilde duyurulur.</span><span class="sxs-lookup"><span data-stu-id="18b36-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="18b36-271">.NET Framework 4.7 ve <xref:System.Windows.Controls.DataGridCell> önceki sürümlerde, denetimler ekran okuyucular tarafından "özel" olarak duyuruldu.</span><span class="sxs-lookup"><span data-stu-id="18b36-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="18b36-272">.NET Framework 4.7.1 ile başlayarak, artık doğru veri ızgara hücresi (lokalize) olarak duyurulur.</span><span class="sxs-lookup"><span data-stu-id="18b36-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="18b36-273">.NET Framework 4.7.1 ile başlayarak, ekran okuyucular <xref:System.Windows.Controls.ComboBox>bir editable adını duyurmak.</span><span class="sxs-lookup"><span data-stu-id="18b36-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="18b36-274">.NET Framework 4.7 ve <xref:System.Windows.Controls.PasswordBox> önceki sürümlerinde, denetimler "görünümde öğe yok" olarak duyurulmuş veya başka türlü yanlış davranışlara sahip.</span><span class="sxs-lookup"><span data-stu-id="18b36-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="18b36-275">Bu sorun .NET Framework 4.7.1 ile başlarken giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18b36-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="18b36-276">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="18b36-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="18b36-277">Ekran Okuyucu gibi ekran okuyucular, kullanıcıların genellikle odak noktası olan Kullanıcı Bira'sı içeriğinin metinden konuşmaya çıktısı ile bir uygulamanın Kullanıcı-ı UI içeriğini okumalarına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="18b36-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="18b36-278">Ancak, bir Kullanıcı Bira öğesi değişir ve odak yoksa, kullanıcı bilgilendirilmeyebilir ve önemli bilgileri kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="18b36-279">Canlı bölgeler bu sorunu çözmeyi amaçlamaktadır.</span><span class="sxs-lookup"><span data-stu-id="18b36-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="18b36-280">Geliştirici, bunları ekran okuyucuya veya başka bir UIAutomation istemcisine, bir UI öğesinde önemli bir değişiklik yapıldığını bildirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="18b36-281">Ekran okuyucu daha sonra bu değişikliğin kullanıcıyı nasıl ve ne zaman bilgilendireceğine karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="18b36-282">Canlı bölgeleri desteklemek için WPF'ye aşağıdaki API'ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="18b36-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="18b36-283"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> **LiveSetting** özelliğini ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> **LiveRegionChanged** olayını tanımlayan alanlar.</span><span class="sxs-lookup"><span data-stu-id="18b36-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="18b36-284">XAML kullanılarak ayarlanabilirler.</span><span class="sxs-lookup"><span data-stu-id="18b36-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="18b36-285">Kullanıcı için Kullanıcı Değişikliği'nin önemini ekran okuyucuya bildiren **AutomationProperties.LiveSetting** ekli özellik.</span><span class="sxs-lookup"><span data-stu-id="18b36-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="18b36-286"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> **AutomationProperties.LiveSetting** ekli özelliği tanımlayan özellik.</span><span class="sxs-lookup"><span data-stu-id="18b36-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="18b36-287"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> **LiveSetting** değeri sağlamak için geçersiz kılınabilen yöntem.</span><span class="sxs-lookup"><span data-stu-id="18b36-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="18b36-288"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> **LiveSetting** değerini alan ve ayarlayan yöntemler.</span><span class="sxs-lookup"><span data-stu-id="18b36-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="18b36-289"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası **LiveSetting** değerlerini tanımlayan numaralandırma:</span><span class="sxs-lookup"><span data-stu-id="18b36-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="18b36-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b36-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-291">Canlı bölgenin içeriği değiştiyse öğe bildirim göndermez.</span><span class="sxs-lookup"><span data-stu-id="18b36-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="18b36-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b36-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-293">Öğe, canlı bölgenin içeriği değiştiyse kesintisiz bildirimler gönderir.</span><span class="sxs-lookup"><span data-stu-id="18b36-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="18b36-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="18b36-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="18b36-295">Öğe, canlı bölgenin içeriği değiştiyse kesintiye uğratıcı bildirimler gönderir.</span><span class="sxs-lookup"><span data-stu-id="18b36-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="18b36-296">Aşağıdaki örnekte gösterildiği **gibi, AutomationProperties.LiveSetting** özelliğini ilgi öğesine ayarlayarak bir LiveRegion oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="18b36-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="18b36-297">Canlı bölgedeki veriler değiştiğinde ve bir ekran okuyucuyu bilgilendirmeniz gerektiğinde, aşağıdaki örnekte gösterildiği gibi açıkça bir olay yükseltirsiniz.</span><span class="sxs-lookup"><span data-stu-id="18b36-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="18b36-298">**Yüksek kontrast**</span><span class="sxs-lookup"><span data-stu-id="18b36-298">**High contrast**</span></span>

<span data-ttu-id="18b36-299">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimlerinde yüksek kontrastlı iyileştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="18b36-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="18b36-300"><xref:System.Windows.SystemParameters.HighContrast%2A> Tema ayarlandığında artık görünürler.</span><span class="sxs-lookup"><span data-stu-id="18b36-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="18b36-301">Bunlar:</span><span class="sxs-lookup"><span data-stu-id="18b36-301">These include:</span></span>

- <span data-ttu-id="18b36-302"><xref:System.Windows.Controls.Expander>Denetim</span><span class="sxs-lookup"><span data-stu-id="18b36-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="18b36-303"><xref:System.Windows.Controls.Expander> Denetim için odak görselşimdi görünür.</span><span class="sxs-lookup"><span data-stu-id="18b36-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="18b36-304">Klavye görselleri <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>ve <xref:System.Windows.Controls.RadioButton> denetimleri de görülebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="18b36-305">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-305">For example:</span></span>

  <span data-ttu-id="18b36-306">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-306">Before:</span></span>

  ![Odak ve odak görsel ile genişletici kontrolü ekran görüntüsü.](./media/whats-new-in-accessibility/expander-control-before.png)

  <span data-ttu-id="18b36-308">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-308">After:</span></span>

  ![Genişletici denetiminin ekran görüntüsü ve odak, denetimin metninin etrafında noktalı bir çizgi gösterir.](./media/whats-new-in-accessibility/expander-control-after.png)

- <span data-ttu-id="18b36-310"><xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> kontroller</span><span class="sxs-lookup"><span data-stu-id="18b36-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="18b36-311">Yüksek kontrastlı <xref:System.Windows.Controls.CheckBox> <xref:System.Windows.Controls.RadioButton> temalarda seçildiğinde ve denetimlerde bulunan metni görmek artık daha kolay.</span><span class="sxs-lookup"><span data-stu-id="18b36-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="18b36-312">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-312">For example:</span></span>

  <span data-ttu-id="18b36-313">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-313">Before:</span></span>

  ![Yüksek kontrastlı temalarda metin görünürlüğü zayıf olan radyo ve kontrol düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-before.png)

  <span data-ttu-id="18b36-315">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-315">After:</span></span>

  ![Yüksek kontrastlı temalarda daha iyi metin görünürlüğü olan radyo ve kontrol düğmelerinin ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-radio-button-after.png)

- <span data-ttu-id="18b36-317"><xref:System.Windows.Controls.ComboBox>Denetim</span><span class="sxs-lookup"><span data-stu-id="18b36-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="18b36-318">.NET Framework 4.7.1 ile başlayarak, <xref:System.Windows.Controls.ComboBox> devre dışı bırakma denetiminin sınırı devre dışı bırakılmış metinle aynı renktedir.</span><span class="sxs-lookup"><span data-stu-id="18b36-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="18b36-319">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-319">For example:</span></span>

  <span data-ttu-id="18b36-320">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-320">Before:</span></span>

  ![Kenarlık ve denetim metni farklı renklerde bir engelli ComboBox ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-before.png)

  <span data-ttu-id="18b36-322">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-322">After:</span></span>

  ![Denetim metniyle aynı renge sahip engelli bir ComboBox'ın ekran görüntüsü.](./media/whats-new-in-accessibility/combo-disabled-after.png)

  <span data-ttu-id="18b36-324">Buna ek olarak, devre dışı bırakılmış ve odaklanmış düğmeler doğru tema rengini kullanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="18b36-325">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-325">Before:</span></span>

  ![Focus Me yazan gri metinli siyah bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-before.png)

  <span data-ttu-id="18b36-327">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-327">After:</span></span>

  ![Focus Me yazan siyah metinli mavi bir düğmenin ekran görüntüsü.](./media/whats-new-in-accessibility/button-theme-colors-after.png)

  <span data-ttu-id="18b36-329">Son olarak, .NET Framework 4.7 ve <xref:System.Windows.Controls.ComboBox> önceki sürümlerinde, açılan okgörünmez olması için `Toolbar.ComboBoxStyleKey` bir denetim stili ayarlama.</span><span class="sxs-lookup"><span data-stu-id="18b36-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="18b36-330">Bu sorun .NET Framework 4.7.1 ile başlarken giderilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18b36-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="18b36-331">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-331">For example:</span></span>

  <span data-ttu-id="18b36-332">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-332">Before:</span></span>

  ![Görünmez açılır oklu ComboBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-before.png)

  <span data-ttu-id="18b36-334">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-334">After:</span></span>

  ![Açılan ok gösteren bir ComBoxBox denetiminin ekran görüntüsü.](./media/whats-new-in-accessibility/combo-box-style-key-after.png)

- <span data-ttu-id="18b36-336"><xref:System.Windows.Controls.DataGrid>Denetim</span><span class="sxs-lookup"><span data-stu-id="18b36-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="18b36-337">.NET Framework 4.7.1 ile başlayarak, <xref:System.Windows.Controls.DataGrid> denetimlerde sıralama göstergesi oku artık doğru tema renklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="18b36-338">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-338">For example:</span></span>

  <span data-ttu-id="18b36-339">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-339">Before:</span></span>

  ![Geliştirmelerden önce sıralama göstergesi okunun ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-before.png)

  <span data-ttu-id="18b36-341">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-341">After:</span></span>

  ![Geliştirmelerden sonra sıralama göstergesi ok ekran görüntüsü.](./media/whats-new-in-accessibility/sort-indicator-after.png)

  <span data-ttu-id="18b36-343">Buna ek olarak, .NET Framework 4.7 ve önceki sürümlerinde, varsayılan bağlantı stili yüksek kontrastlı modlarda fare üzerinde yanlış bir renge dönüştürüldü.</span><span class="sxs-lookup"><span data-stu-id="18b36-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="18b36-344">Bu işlem .NET Framework 4.7.1 ile başlar.</span><span class="sxs-lookup"><span data-stu-id="18b36-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="18b36-345">Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusu sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirimi için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="18b36-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="18b36-346">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-346">Before:</span></span>

  ![Bana Tıkla diyen bir bağlantının ekran görüntüsü!](./media/whats-new-in-accessibility/default-link-style-before.png)

  <span data-ttu-id="18b36-349">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-349">After:</span></span>

  ![Bana Tıkla diyen bir bağlantının ekran görüntüsü!](./media/whats-new-in-accessibility/default-link-style-after.png)

<span data-ttu-id="18b36-352">.NET Framework 4.7.1'deki WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için [WPF'deki Erişilebilirlik geliştirmelerine](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf)bakın.</span><span class="sxs-lookup"><span data-stu-id="18b36-352">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="18b36-353">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="18b36-353">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="18b36-354">.NET Framework 4.7.1'de, Windows Formları (WinForms) aşağıdaki alanlarda erişilebilirlik değişikliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="18b36-354">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="18b36-355">**Yüksek Karşıtlık modunda geliştirilmiş ekran**</span><span class="sxs-lookup"><span data-stu-id="18b36-355">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="18b36-356">.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sisteminde bulunan HighContrast modlarında gelişmiş görüntüleme sunar.</span><span class="sxs-lookup"><span data-stu-id="18b36-356">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="18b36-357">Windows 10 bazı yüksek karşıtlık sistem renklerinin değerlerini değiştirdi ve Windows Forms, Windows 10 Win32 çerçevesini temel almıştır.</span><span class="sxs-lookup"><span data-stu-id="18b36-357">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="18b36-358">En iyi deneyim için, Windows'un en son sürümünde çalıştırın ve bir test uygulamasına bir app.manifest dosyası ekleyerek en son işletim sistemi değişikliklerini tercih edin ve Windows 10 destekli işletim sistemi çizgisini aşağıdaki gibi görünerek yorum yapmayı bırakın:</span><span class="sxs-lookup"><span data-stu-id="18b36-358">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="18b36-359">Yüksek karşıtlık değişikliklerine örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-359">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="18b36-360">Öğelerdeki <xref:System.Windows.Forms.MenuStrip> onay işaretlerini görüntülemek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="18b36-360">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="18b36-361">Seçildiğinde, <xref:System.Windows.Forms.MenuStrip> devre dışı bırakılan öğeleri görüntülemek daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="18b36-361">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="18b36-362">Seçili <xref:System.Windows.Forms.Button> denetimdeki metin, seçim rengiyle tezat oluşturuyor.</span><span class="sxs-lookup"><span data-stu-id="18b36-362">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="18b36-363">Devre dışı bırakılan metnin okunması daha kolaydır.</span><span class="sxs-lookup"><span data-stu-id="18b36-363">Disabled text is easier to read.</span></span> <span data-ttu-id="18b36-364">Örnek:</span><span class="sxs-lookup"><span data-stu-id="18b36-364">For example:</span></span>

  <span data-ttu-id="18b36-365">Önce:</span><span class="sxs-lookup"><span data-stu-id="18b36-365">Before:</span></span>

  ![Erişilebilirlik geliştirmelerinden önce yüksek kontrast modunda çalışan farklı denetimler kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-before.png)

  <span data-ttu-id="18b36-367">Sonra:</span><span class="sxs-lookup"><span data-stu-id="18b36-367">After:</span></span>

  ![Erişilebilirlik geliştirmeleri sonrasında yüksek kontrast modunda çalışan farklı denetimler kullanan bir uygulamanın ekran görüntüsü.](./media/whats-new-in-accessibility/high-contrast-mode-menu-items-after.png)

- <span data-ttu-id="18b36-369">İş Parçacığı Özel Durum İletişim Kutusunda yüksek kontrastlı geliştirmeler.</span><span class="sxs-lookup"><span data-stu-id="18b36-369">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="18b36-370">**Geliştirilmiş Ekran Okuyucusu desteği**</span><span class="sxs-lookup"><span data-stu-id="18b36-370">**Improved Narrator support**</span></span>

<span data-ttu-id="18b36-371">.NET Framework 4.7.1'deki Windows Formları, Ekran Okuyucusu için aşağıdaki erişilebilirlik geliştirmelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-371">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="18b36-372">Denetime <xref:System.Windows.Forms.MonthCalendar> Anlatıcı ve diğer UI otomasyon araçları tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-372">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="18b36-373">Denetim, <xref:System.Windows.Forms.CheckedListBox> bir öğenin denetim durumu değiştiğinde Ekran Okuyucu'ya haber verirken, kullanıcıya liste öğesinin değerini değiştirdiği bildirilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-373">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="18b36-374">Denetim, <xref:System.Windows.Forms.DataGridViewCell> doğru salt okunur durumunu Ekran Okuyucusu'na bildirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-374">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="18b36-375">Ekran okuyucusu <xref:System.Windows.Forms.ToolStripMenuItem> artık devre dışı bırakılan metni okuyabilirken, daha önce devre dışı bırakılan menü öğelerini atlardı.</span><span class="sxs-lookup"><span data-stu-id="18b36-375">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="18b36-376">**UIAutomation erişilebilirlik desenleri için geliştirilmiş destek**</span><span class="sxs-lookup"><span data-stu-id="18b36-376">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="18b36-377">.NET Framework 4.7.1 ile başlayarak, erişilebilirlik teknolojisi araçlarının geliştiricileri çeşitli WinForms denetimleri için ortak API erişilebilirlik desenlerinden ve özelliklerinden yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-377">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="18b36-378">Bu erişilebilirlik geliştirmeleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18b36-378">These accessibility improvements include:</span></span>

- <span data-ttu-id="18b36-379">Ve <xref:System.Windows.Forms.ComboBox> <xref:System.Windows.Forms.ToolStripSplitButton> şimdi [genişletme /daraltma deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-379">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="18b36-380"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Şimdi geçiş [deseni](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-380">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="18b36-381">Denetim <xref:System.Windows.Forms.ToolStripItem> <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [genişletme/daraltma deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-381">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="18b36-382">Ve <xref:System.Windows.Forms.NumericUpDown> <xref:System.Windows.Forms.DomainUpDown> denetimler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği destekler.</span><span class="sxs-lookup"><span data-stu-id="18b36-382">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="18b36-383">**Geliştirilmiş özellik tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="18b36-383">**Improved property browser experience**</span></span>

<span data-ttu-id="18b36-384">.NET Framework 4.7.1 ile başlayarak, Windows Formları şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-384">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="18b36-385">Çeşitli açılır seçim pencerelerinden daha iyi klavye gezintisi.</span><span class="sxs-lookup"><span data-stu-id="18b36-385">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="18b36-386">Gereksiz sekme durakları bir azalma.</span><span class="sxs-lookup"><span data-stu-id="18b36-386">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="18b36-387">Kontrol türlerinin daha iyi raporlanması.</span><span class="sxs-lookup"><span data-stu-id="18b36-387">Better reporting of control types.</span></span>
- <span data-ttu-id="18b36-388">Geliştirilmiş anlatıcı davranışı.</span><span class="sxs-lookup"><span data-stu-id="18b36-388">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="18b36-389">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="18b36-389">ASP.NET web controls</span></span>

<span data-ttu-id="18b36-390">.NET Framework 4.7.1 ve Visual Studio 2017 sürüm 15.3 ile başlayan ASP.NET, ASP.NET web denetimlerinin Visual Studio'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-390">Starting with .NET Framework 4.7.1 and Visual Studio 2017 version 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="18b36-391">Değişiklikler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="18b36-391">Changes include the following:</span></span>

- <span data-ttu-id="18b36-392">**Ayrıntılar Görünümü** sihirbazındaki **Alan Ekle** iletişim kutusu veya **ListView** sihirbazının **Yapılandırılmış ListView** iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik desenleri uygulamak için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="18b36-392">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="18b36-393">**Veri Çağrı Alanı Alanları Düzenleyicisi**gibi Yüksek Karşıtlık modunda ekranı geliştirmek için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="18b36-393">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="18b36-394">DataPager **denetiminin** **Çağrı Cihazı Alanlarını Edit** sihirbazı, **Nesne Bağlamını Yapılandıran** iletişim kutusu veya **Yapılandır Veri Kaynağı** sihirbazının **Yapılandır Veri** Seçimi iletişim kutusu gibi denetimler için klavye gezintisi deneyimlerini geliştirmek için yapılan değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="18b36-394">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="18b36-395">.NET SDK Araçları</span><span class="sxs-lookup"><span data-stu-id="18b36-395">.NET SDK Tools</span></span>

<span data-ttu-id="18b36-396">[Configuration Editor Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve Service Trace Viewer Aracı [(SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunları giderilerek geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="18b36-396">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="18b36-397">Bunların çoğu, tanımlanmayan bir ad veya belirli Kullanıcı Arabirimi otomasyon desenleri gibi doğru uygulanamayan küçük sorunlardı.</span><span class="sxs-lookup"><span data-stu-id="18b36-397">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="18b36-398">Birçok kullanıcı bu yanlış değerlerin farkında olmasa da, ekran okuyucular gibi yardımcı teknolojileri kullanan müşteriler bu SDK araçlarını daha erişilebilir bulur.</span><span class="sxs-lookup"><span data-stu-id="18b36-398">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="18b36-399">Bu geliştirmeler, klavye odak lama sırası gibi önceki bazı davranışları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="18b36-399">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="18b36-400">Windows İş Akışı Temeli (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="18b36-400">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="18b36-401">İş Akışı Tasarımcısı'ndaki erişilebilirlik değişiklikleri aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="18b36-401">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="18b36-402">Sekme sırası bazı denetimlerde soldan sağa ve yukarıdan aşağıya değişir:</span><span class="sxs-lookup"><span data-stu-id="18b36-402">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="18b36-403"><xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinlik için korelasyon verilerini ayarlamak için başlangıç korelasyon penceresi.</span><span class="sxs-lookup"><span data-stu-id="18b36-403">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="18b36-404"><xref:System.ServiceModel.Activities.Receive>, , <xref:System.ServiceModel.Activities.Send> <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler için içerik tanım penceresi.</span><span class="sxs-lookup"><span data-stu-id="18b36-404">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="18b36-405">Klavye aracılığıyla daha fazla işlev kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-405">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="18b36-406">Bir etkinliğin özelliklerini düzenlerken, özellik grupları ilk odaklandıklarında klavye yle daraltılabilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-406">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="18b36-407">Uyarı simgelerine klavyeyle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-407">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="18b36-408">**Özellikler** penceresindeki **Daha Fazla Özellik** düğmesine klavyeyle erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-408">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="18b36-409">Klavye kullanıcıları, İş Akışı Tasarımcısı'nın **Bağımsız Değişkenler** ve **Değişkenler** bölmelerinde üstbilgi öğelerine erişebilir.</span><span class="sxs-lookup"><span data-stu-id="18b36-409">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="18b36-410">Şu anda olduğu gibi odaklanmış öğelerin daha iyi görünürlüğü:</span><span class="sxs-lookup"><span data-stu-id="18b36-410">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="18b36-411">İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri ızgaralarına satır ekleme.</span><span class="sxs-lookup"><span data-stu-id="18b36-411">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="18b36-412">Alanlarda <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinliklerde sekme.</span><span class="sxs-lookup"><span data-stu-id="18b36-412">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="18b36-413">Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="18b36-413">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="18b36-414">Ekran okuyucular artık doğru tanıyabilir:</span><span class="sxs-lookup"><span data-stu-id="18b36-414">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="18b36-415">İş akışı tasarımcısında ayarlanan kesme noktaları.</span><span class="sxs-lookup"><span data-stu-id="18b36-415">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="18b36-416">, <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision>ve <xref:System.ServiceModel.Activities.CorrelationScope> aktiviteler.</span><span class="sxs-lookup"><span data-stu-id="18b36-416">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="18b36-417"><xref:System.ServiceModel.Activities.Receive> Etkinliğin içeriği.</span><span class="sxs-lookup"><span data-stu-id="18b36-417">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="18b36-418"><xref:System.Activities.Statements.InvokeMethod> Etkinlik için Hedef Türü.</span><span class="sxs-lookup"><span data-stu-id="18b36-418">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="18b36-419">Etkinlikteki Özel Durum açılan kutusu <xref:System.Activities.Statements.TryCatch> ve Son bölümü.</span><span class="sxs-lookup"><span data-stu-id="18b36-419">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="18b36-420">İleti Türü açılan kutusu, Korelik Açla Penceresindeki ayırıcı, İçerik Tanımı penceresi ve ileti etkinliklerindeki CorrelatesOn <xref:System.ServiceModel.Activities.SendReply>Definition <xref:System.ServiceModel.Activities.ReceiveReply>penceresi (<xref:System.ServiceModel.Activities.Receive>, , <xref:System.ServiceModel.Activities.Send>, ve ).</span><span class="sxs-lookup"><span data-stu-id="18b36-420">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="18b36-421">Durum makine geçişleri ve geçişler hedefleri.</span><span class="sxs-lookup"><span data-stu-id="18b36-421">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="18b36-422">Etkinliklerle ilgili <xref:System.Activities.Statements.FlowDecision> ek açıklamalar ve bağlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="18b36-422">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="18b36-423">Etkinlikler için bağlam (sağ tıklatma) menüleri.</span><span class="sxs-lookup"><span data-stu-id="18b36-423">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="18b36-424">Özellik değeri düzenleyicileri, Aramayı Temizle düğmesi, Kategoriye Ve Alfabetik sıralama düğmelerine göre ve özellikler tablosundaki İfade Düzenleyicisi iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="18b36-424">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="18b36-425">İş Akışı Tasarımcısı'ndaki yakınlaştırma yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="18b36-425">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="18b36-426">Ayırıcı ve <xref:System.Activities.Statements.Parallel> <xref:System.Activities.Statements.Pick> faaliyetleri.</span><span class="sxs-lookup"><span data-stu-id="18b36-426">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="18b36-427">Aktivite. <xref:System.Activities.Statements.InvokeDelegate></span><span class="sxs-lookup"><span data-stu-id="18b36-427">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="18b36-428">Sözlük etkinlikleri için Türleri`Microsoft.Activities.AddToDictionary<TKey,TValue>`Seç `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`penceresi (, , vb.).</span><span class="sxs-lookup"><span data-stu-id="18b36-428">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="18b36-429">Gözat ve Seç .NET Türü penceresi.</span><span class="sxs-lookup"><span data-stu-id="18b36-429">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="18b36-430">İş Akışı Tasarımcısı'ndaki ekmek kırıntıları.</span><span class="sxs-lookup"><span data-stu-id="18b36-430">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="18b36-431">Yüksek Karşıtlık temaları seçen kullanıcılar, öğeler arasındaki daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı'nın ve denetimlerinin görünürlüğünde birçok iyileştirme görür.</span><span class="sxs-lookup"><span data-stu-id="18b36-431">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="18b36-432">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18b36-432">See also</span></span>

- [<span data-ttu-id="18b36-433">.NET Framework’teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="18b36-433">What's new in the .NET Framework</span></span>](index.md)
