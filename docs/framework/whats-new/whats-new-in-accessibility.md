---
title: .NET Framework erişilebilirlik yenilikleri
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22e1ae495276b0c474ad47f695d8410288289f83
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053731"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="d808c-102">.NET Framework erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="d808c-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="d808c-103">.NET Framework amaçlar, kullanıcılarınız için uygulamaları daha erişilebilir hale getirme.</span><span class="sxs-lookup"><span data-stu-id="d808c-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="d808c-104">Erişilebilirlik özellikleri, bir uygulamanın yardımcı teknoloji kullanıcıları için uygun bir deneyim sağlamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="d808c-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="d808c-105">.NET Framework .NET Framework başlayarak, geliştiricilerin erişilebilir uygulamalar oluşturmalarına izin veren çok sayıda erişilebilirlik geliştirmesi de vardır.</span><span class="sxs-lookup"><span data-stu-id="d808c-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="d808c-106">Erişilebilirlik anahtarları</span><span class="sxs-lookup"><span data-stu-id="d808c-106">Accessibility switches</span></span>

<span data-ttu-id="d808c-107">Uygulamanızı, .NET Framework 4,7 veya önceki bir sürümü hedefliyorsa ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışıyorsa erişilebilirlik özelliklerini kabul etmek üzere yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d808c-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="d808c-108">Ayrıca, .NET Framework 4.7.1 veya üstünü hedeflerse, uygulamanızı eski özellikleri (ve erişilebilirlik özelliklerinden faydalanmaz) kullanacak şekilde de yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d808c-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="d808c-109">Erişilebilirlik özelliklerini içeren .NET Framework her sürümü, uygulamanın yapılandırma dosyasının [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) bölümündeki öğesine eklediğiniz sürüme özgü bir erişilebilirlik anahtarına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="d808c-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="d808c-110">Aşağıdakiler desteklenen anahtarlardır:</span><span class="sxs-lookup"><span data-stu-id="d808c-110">The following are the supported switches:</span></span>

|<span data-ttu-id="d808c-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="d808c-111">Version</span></span>|<span data-ttu-id="d808c-112">Anahtar</span><span class="sxs-lookup"><span data-stu-id="d808c-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="d808c-113">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="d808c-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="d808c-114">"Switch. UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="d808c-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="d808c-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="d808c-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="d808c-116">"Switch. UseLegacyAccessibilityFeatures. 2"</span><span class="sxs-lookup"><span data-stu-id="d808c-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="d808c-117">.NET Framework 4,8</span><span class="sxs-lookup"><span data-stu-id="d808c-117">.NET Framework 4.8</span></span>|<span data-ttu-id="d808c-118">"Switch. UseLegacyAccessibilityFeatures. 3"</span><span class="sxs-lookup"><span data-stu-id="d808c-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="d808c-119">Erişilebilirlik geliştirmelerinden yararlanma</span><span class="sxs-lookup"><span data-stu-id="d808c-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="d808c-120">Yeni erişilebilirlik özellikleri, .NET Framework 4.7.1 veya üstünü hedefleyen uygulamalar için varsayılan olarak etkinleştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d808c-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="d808c-121">Ayrıca, .NET Framework önceki bir sürümünü hedefleyen, ancak .NET Framework 4.7.1 veya üzeri sürümlerde çalışan uygulamalar, ' a anahtar ekleyerek eski erişilebilirlik davranışlarını devre dışı bırakabilirsiniz (ve bu nedenle erişilebilirlik geliştirmelerinden faydalanabilir). [`<AppContextSwitchOverrides>`öğesini,](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) uygulamanın yapılandırma dosyasının `false` [bölümündekiöğesive`<runtime>`](../configure-apps/file-schema/runtime/index.md) değerini olarak ayarlama.</span><span class="sxs-lookup"><span data-stu-id="d808c-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="d808c-122">Aşağıda, .NET Framework 4.7.1 ' de sunulan erişilebilirlik geliştirmelerinin nasıl kabul edilecek gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="d808c-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="d808c-123">.NET Framework sonraki bir sürümünde erişilebilirlik özelliklerini kullanmayı tercih ederseniz, .NET Framework daha önceki sürümlerindeki özellikleri de açıkça kabul etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="d808c-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="d808c-124">Uygulamanızı .NET Framework 4.7.1 ve 4.7.2 içindeki erişilebilirlik geliştirmelerinden faydalanmak için yapılandırma aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d808c-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="d808c-125">.NET Framework 4.7.1, 4.7.2 ve 4,8 ' deki erişilebilirlik geliştirmelerinden faydalanmak için uygulamanızı yapılandırma aşağıdaki [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğeyi gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d808c-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="d808c-126">Eski davranışı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="d808c-126">Restoring legacy behavior</span></span>

<span data-ttu-id="d808c-127">4\.7.1 ile başlayan .NET Framework sürümlerini hedefleyen uygulamalar, uygulamanın yapılandırma dosyasının [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) [`<runtime>`](../configure-apps/file-schema/runtime/index.md) bölümündeki öğeye anahtar ekleyerek ve değerlerini olarak ayarlayarakerişilebilirliközelliklerinidevredışıbırakabilir `true`.</span><span class="sxs-lookup"><span data-stu-id="d808c-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](../configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="d808c-128">Örneğin, aşağıdaki yapılandırma .NET Framework 4.7.2 ' de tanıtılan erişilebilirlik özelliklerinden fazlasını giderir:</span><span class="sxs-lookup"><span data-stu-id="d808c-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="d808c-129">.NET Framework 4,8 ' de erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="d808c-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="d808c-130">.NET Framework 4,8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="d808c-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d808c-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="d808c-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="d808c-133">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d808c-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="d808c-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d808c-134">Windows Forms</span></span>

<span data-ttu-id="d808c-135">.NET Framework 4,8 ' de Windows Forms, yaygın olarak kullanılan birçok denetime Ligegions ve Notification olayları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="d808c-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="d808c-136">Ayrıca, bir Kullanıcı klavyeyi kullanarak bir denetime gittiğinde araç Ipuçları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="d808c-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="d808c-137">**Etiketler ve Durumlarlar için UııA LiveRegions desteği**</span><span class="sxs-lookup"><span data-stu-id="d808c-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="d808c-138">UIA Ligegions, uygulama geliştiricilerinin, kullanıcının çalıştığı konumdan ayrı olarak bulunan bir denetimdeki metin değişikliğini ekran okuyucularına bildirmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d808c-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="d808c-139">Bu, örneğin, bağlantı durumunu gösteren bir <xref:System.Windows.Forms.StatusStrip> denetim için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="d808c-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="d808c-140">Bağlantı bırakılır ve durum değişirse geliştirici, ekran okuyucuyu bilgilendirmek isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="d808c-141">.NET Framework 4,8 ' den başlayarak, Windows Forms hem hem de <xref:System.Windows.Forms.Label> <xref:System.Windows.Forms.StatusStrip> denetimleri için uııa liveregions uygular.</span><span class="sxs-lookup"><span data-stu-id="d808c-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="d808c-142">Örneğin, aşağıdaki kod adlı <xref:System.Windows.Forms.Label> `label1`bir denetimde liveregion kullanır:</span><span class="sxs-lookup"><span data-stu-id="d808c-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="d808c-143">Ekran okuyucusu, kullanıcının uygulamayla etkileşime geçen yere bakılmaksızın "Ready" duyurur.</span><span class="sxs-lookup"><span data-stu-id="d808c-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="d808c-144">Ayrıca, hesabınızı <xref:System.Windows.Forms.UserControl> bir liveregion olarak da uygulayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d808c-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="d808c-145">**UıA bildirim olayları**</span><span class="sxs-lookup"><span data-stu-id="d808c-145">**UIA notification events**</span></span>

<span data-ttu-id="d808c-146">Windows 10 Fall Creators Update 'te tanıtılan UıA bildirim olayı, uygulamanızın kullanıcı arabiriminde ilgili bir denetime sahip olması gerekmeden, yalnızca olayla sağladığınız metni temel alan bir duyuru oluşturmak için bir UıA olayı tetiklenmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="d808c-147">Bazı senaryolarda bu, uygulamanızın erişilebilirliğini önemli ölçüde artırmanın kolay bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="d808c-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="d808c-148">' De, uzun sürebilecek bazı işlemlerin ilerlemesini bilgilendirmek için de yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="d808c-149">UııA Notification olayları hakkında daha fazla bilgi için, bkz. [masaüstü uygulamanız yenı UI bildirimi olayından mi yararlanabilir?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="d808c-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="d808c-150">Aşağıdaki örnek [bildirim olayını](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A)oluşturur:</span><span class="sxs-lookup"><span data-stu-id="d808c-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="d808c-151">**Klavye erişiminde araç Ipuçları**</span><span class="sxs-lookup"><span data-stu-id="d808c-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="d808c-152">.NET Framework 4.7.2 ve önceki sürümleri hedefleyen uygulamalarda, bir denetim [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca bir fare işaretçisi denetime taşınarak açılan menü için tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="d808c-153">.NET Framework 4,8 ' den itibaren klavye kullanıcısı, değiştirici tuşları olan veya içermeyen bir sekme tuşu veya ok tuşlarını kullanarak Denetim araç ipucunu tetikleyebilirler.</span><span class="sxs-lookup"><span data-stu-id="d808c-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="d808c-154">Bu belirli erişilebilirlik geliştirmesi ek bir [AppContext anahtarı](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)gerektirir:</span><span class="sxs-lookup"><span data-stu-id="d808c-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="d808c-155">Aşağıdaki şekilde, Kullanıcı klavyeyle bir düğme seçtiğinde araç ipucunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d808c-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Kullanıcı klavyeyle bir düğmeye gittiğinde araç ipucu](./media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="d808c-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="d808c-158">.NET Framework 4,8 ' den başlayarak WPF bir dizi erişilebilirlik geliştirmesi içerir.</span><span class="sxs-lookup"><span data-stu-id="d808c-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="d808c-159">**Ekran anlayıcıları artık daraltılmış veya gizli görünürlüğe sahip öğeleri duyurmayacak**</span><span class="sxs-lookup"><span data-stu-id="d808c-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="d808c-160">Daraltılmış veya gizli görünürlüğe sahip öğeler artık ekran okuyucu tarafından duyurulmaz.</span><span class="sxs-lookup"><span data-stu-id="d808c-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="d808c-161"><xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> Görünürlüğü<xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> olan öğeleri içeren kullanıcı arabirimleri, kullanıcıya duyurulacak olmaları durumunda ekran okuyucular tarafından yanlış temsil edilebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="d808c-162">.NET Framework 4,8 ' den itibaren, WPF artık UIAutomation ağacının denetim görünümünde daraltılmış veya gizli öğeleri içermez, bu nedenle ekran okuyucular artık bu öğeleri duyurabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="d808c-163">**Adorner tabanlı metin seçimiyle kullanılacak SelectionTextBrush özelliği**</span><span class="sxs-lookup"><span data-stu-id="d808c-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="d808c-164">.NET Framework 4.7.2, WPF, donatıcı katmanını kullanmadan çizim <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.PasswordBox> metin seçme özelliği ekledi.</span><span class="sxs-lookup"><span data-stu-id="d808c-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="d808c-165">Bu senaryodaki seçili metnin ön plan rengi tarafından <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>dikte edildi.</span><span class="sxs-lookup"><span data-stu-id="d808c-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d808c-166">.NET Framework 4,8 yeni bir özellik `SelectionTextBrush`ekler, bu, geliştiricilerin, donatıcı olmayan tabanlı metin seçimi kullanılırken seçili metin için belirli fırçayı seçmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="d808c-167">Bu özellik yalnızca <xref:System.Windows.Controls.PasswordBox> , donatıcı <xref:System.Windows.Controls.Primitives.TextBoxBase>tabanlı olmayan metin seçimi etkin olan WPF uygulamalarında yalnızca türetilmiş denetimleri ve denetimi işe yarar.</span><span class="sxs-lookup"><span data-stu-id="d808c-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="d808c-168"><xref:System.Windows.Controls.RichTextBox> Denetim üzerinde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="d808c-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="d808c-169">Adorner tabanlı olmayan metin seçimi etkinleştirilmemişse, bu özellik yok sayılır.</span><span class="sxs-lookup"><span data-stu-id="d808c-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="d808c-170">Bu özelliği kullanmak için XAML kodunuza eklemeniz ve uygun fırçayı ya da bağlamayı kullanmanız yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="d808c-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="d808c-171">Ortaya çıkan metin seçimi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="d808c-171">The resulting text selection looks like this:</span></span>

![Kullanıcı klavyeyle bir düğmeye gittiğinde araç ipucu](./media/selectiontextbrush-property.png)

<span data-ttu-id="d808c-173">`SelectionBrush` Ve`SelectionTextBrush` özelliklerinin kullanımını, uygun olmayan bir arka plan ve ön plan renk kombinasyonu oluşturmak için birleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d808c-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="d808c-174">**Özelliği Için UIAutomation Controllersupport desteği**</span><span class="sxs-lookup"><span data-stu-id="d808c-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="d808c-175">UIAutomation `ControllerFor` özelliği, bu özelliği destekleyen Otomasyon öğesi tarafından yönetilen bir Otomasyon öğeleri dizisi döndürüyor.</span><span class="sxs-lookup"><span data-stu-id="d808c-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="d808c-176">Bu özellik genellikle otomatik öneri erişilebilirliği için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d808c-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="d808c-177">`ControllerFor`bir Otomasyon öğesi uygulama kullanıcı arabirimi veya masaüstünün bir veya daha fazla kesimini etkiliyorsa kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d808c-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="d808c-178">Aksi takdirde, denetim işleminin etkisini UI öğeleriyle ilişkilendirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="d808c-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="d808c-179">Bu özellik, denetimlerin `ControllerFor` özellik için bir değer sağlama yeteneğini ekler.</span><span class="sxs-lookup"><span data-stu-id="d808c-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="d808c-180">.NET Framework 4,8 yeni bir sanal yöntem <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>ekler.</span><span class="sxs-lookup"><span data-stu-id="d808c-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-181">`ControllerFor` Özelliği için bir değer sağlamak için, bu yöntemi geçersiz kılın ve bunun <xref:System.Windows.Automation.Peers.AutomationPeer>tarafından geçirilmekte `List<AutomationPeer>` olan denetimler için bir döndürür:</span><span class="sxs-lookup"><span data-stu-id="d808c-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="d808c-182">**Klavye erişiminde araç ipuçları**</span><span class="sxs-lookup"><span data-stu-id="d808c-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="d808c-183">.NET Framework 4.7.2 ve önceki sürümlerde araç ipuçları yalnızca Kullanıcı fare imlecini bir denetim üzerine getirdiğinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d808c-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="d808c-184">.NET Framework 4,8 ' de araç ipuçları klavye odağında ve klavye kısayoluyla de görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d808c-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="d808c-185">Bu özelliği etkinleştirmek için bir uygulamanın, `Switch.UseLegacyAccessibilityFeatures.3` ve [](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) `Switch.UseLegacyToolTipDisplay` AppContext anahtarlarını kullanarak .NET Framework 4,8 veya katılımı hedeflemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="d808c-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="d808c-186">Aşağıda örnek bir uygulama yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d808c-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="d808c-187">Etkinleştirildikten sonra, araç ipucu içeren tüm denetimler, denetim klavye odağını aldıktan sonra bunu görüntüler.</span><span class="sxs-lookup"><span data-stu-id="d808c-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="d808c-188">Araç ipucu zaman içinde veya klavye odağı değiştiğinde kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="d808c-189">Kullanıcılar araç ipucunu, CTRL + SHIFT + F10 yeni klavye kısayolunu kullanarak el ile de kapatabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="d808c-190">Araç ipucu kapatıldıktan sonra, aynı klavye kısayolu kullanılarak yeniden görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="d808c-191"><xref:System.Windows.Controls.Ribbon.Ribbon> Denetimlerde [Şerit Araç ipuçları](xref:System.Windows.Controls.Ribbon.RibbonToolTip) klavye odağında gösterilmez; yalnızca klavye kısayolu aracılığıyla gösterilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="d808c-192">**SizeOfSet ve Positionınset UIAutomation özellikleri için destek eklendi**</span><span class="sxs-lookup"><span data-stu-id="d808c-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="d808c-193">Windows 10, `SizeOfSet` iki yeni UIAutomation özelliği sunmuştur ve `PositionInSet`uygulamalar tarafından bir küme içindeki öğelerin sayısını açıklayan uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d808c-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="d808c-194">Ekran okuyucular gibi UIAutomation istemci uygulamaları, bu özellikler için bir uygulamayı sorgulayabilir ve uygulamanın kullanıcı arabiriminin doğru bir temsilini duyurur.</span><span class="sxs-lookup"><span data-stu-id="d808c-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="d808c-195">.NET Framework 4,8 ' den başlayarak WPF, WPF uygulamalarında UIAutomation için bu iki özelliği kullanıma sunar.</span><span class="sxs-lookup"><span data-stu-id="d808c-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="d808c-196">Bu, iki şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="d808c-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="d808c-197">Bağımlılık özelliklerini kullanarak.</span><span class="sxs-lookup"><span data-stu-id="d808c-197">By using dependency properties.</span></span>

  <span data-ttu-id="d808c-198">WPF iki yeni bağımlılık özelliği <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> ekler ve. <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-199">Geliştirici, değerlerini ayarlamak için XAML kullanabilir:</span><span class="sxs-lookup"><span data-stu-id="d808c-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="d808c-200">AutomationPeer sanal yöntemlerini geçersiz kılarak.</span><span class="sxs-lookup"><span data-stu-id="d808c-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="d808c-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> Ve<xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sanal yöntemleri AutomationPeer sınıfına eklenmiştir.</span><span class="sxs-lookup"><span data-stu-id="d808c-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="d808c-202">Bir geliştirici, aşağıdaki örnekte gösterildiği `SizeOfSet` gibi `PositionInSet` bu yöntemleri geçersiz kılarak ve için değerler verebilir:</span><span class="sxs-lookup"><span data-stu-id="d808c-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="d808c-203">Ayrıca, <xref:System.Windows.Controls.ItemsControl> örneklerdeki öğeler, geliştiriciden ek işlem yapılmadan bu özellikler için otomatik olarak bir değer sağlar.</span><span class="sxs-lookup"><span data-stu-id="d808c-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="d808c-204">Bir gruplandırılmışsa, gruplar koleksiyonu bir küme olarak temsil edilir ve her bir <xref:System.Windows.Controls.ItemsControl> grup içindeki her bir öğe, bu grubun içindeki konumunu ve grubun boyutunu sunan grubun içindeki her bir öğe ile ayrı bir küme olarak sayılır.</span><span class="sxs-lookup"><span data-stu-id="d808c-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="d808c-205">Otomatik değerler sanallaştırmadan etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="d808c-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="d808c-206">Bir öğe gerçekleştirilmese de, bu, denetimin toplam boyutuna doğru sayılır ve eşdüzey öğelerinin kümesindeki konumu etkiler.</span><span class="sxs-lookup"><span data-stu-id="d808c-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="d808c-207">Otomatik değerler yalnızca uygulama .NET Framework 4,8 ' i hedefliyorsa sağlanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="d808c-208">.NET Framework önceki bir sürümünü hedefleyen uygulamalar için, [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)aşağıdaki App. config `Switch.UseLegacyAccessibilityFeatures.3` dosyasında gösterildiği gibi ayarlayabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d808c-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="d808c-209">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d808c-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="d808c-210">İş akışı Tasarımcısı .NET Framework 4,8 ' de aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="d808c-211">Ekran okuyucusu kullanan kullanıcılar, FlowSwitch durum etiketlerindeki geliştirmeleri görür.</span><span class="sxs-lookup"><span data-stu-id="d808c-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="d808c-212">Ekran okuyucusu kullanan kullanıcılar, düğme açıklamalarındaki geliştirmeleri görür.</span><span class="sxs-lookup"><span data-stu-id="d808c-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="d808c-213">Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde geliştirmeler görür.</span><span class="sxs-lookup"><span data-stu-id="d808c-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="d808c-214">Uygulamanız .NET Framework 4.7.2 veya önceki bir sürümü hedefliyorsa, uygulama yapılandırma dosyanızda `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtarını](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) olarak `false` ayarlayarak bu değişiklikleri kabul edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d808c-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="d808c-215">Daha fazla bilgi için bu makaledeki [Erişilebilirlik geliştirmelerinden yararlanma](#taking-advantage-of-accessibility-enhancements) bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="d808c-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="d808c-216">.NET Framework 4.7.2 ' deki erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="d808c-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="d808c-217">.NET Framework 4.7.2, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="d808c-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d808c-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="d808c-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="d808c-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d808c-220">Windows Forms</span></span>

<span data-ttu-id="d808c-221">**Yüksek Karşıtlık temalarda işletim sistemi tanımlı renkler**</span><span class="sxs-lookup"><span data-stu-id="d808c-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="d808c-222">.NET Framework 4.7.2 ile başlayarak, Windows Forms Yüksek Karşıtlık temalarda işletim sistemi tarafından tanımlanan renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="d808c-223">Bu, aşağıdaki denetimleri etkiler:</span><span class="sxs-lookup"><span data-stu-id="d808c-223">This affects the following controls:</span></span>

- <span data-ttu-id="d808c-224"><xref:System.Windows.Forms.ToolStripDropDownButton> Denetimin aşağı açılan oku.</span><span class="sxs-lookup"><span data-stu-id="d808c-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="d808c-225"><xref:System.Windows.Forms.Button>, Ve,<xref:System.Windows.Forms.CheckBox> <xref:System.Windows.Forms.ButtonBase.FlatStyle> veya olarak ayarlanan<xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> denetimleri. <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType> <xref:System.Windows.Forms.RadioButton></span><span class="sxs-lookup"><span data-stu-id="d808c-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-226">Daha önce, seçilen metin ve arka plan renkleri çok sevmiyor ve okunması zor.</span><span class="sxs-lookup"><span data-stu-id="d808c-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="d808c-227">Öğesinin <xref:System.Windows.Forms.GroupBox> <xref:System.Windows.Forms.Control.Enabled> özelliği olarak ayarlanmışolaniçindebulunandenetimler.`false`</span><span class="sxs-lookup"><span data-stu-id="d808c-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="d808c-228">Yüksek karşıtlık modunda <xref:System.Windows.Forms.ToolStripComboBox>daha fazla <xref:System.Windows.Forms.ToolStripDropDownButton> parlaklık karşıtlığı oranına sahip ,vedenetimleri.<xref:System.Windows.Forms.ToolStripButton></span><span class="sxs-lookup"><span data-stu-id="d808c-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="d808c-229"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Öğesinin<xref:System.Windows.Forms.DataGridViewLinkCell>özelliği.</span><span class="sxs-lookup"><span data-stu-id="d808c-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="d808c-230">**Ekran okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="d808c-230">**Narrator improvements**</span></span>

<span data-ttu-id="d808c-231">.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği aşağıdaki şekilde geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="d808c-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="d808c-232"><xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> Bir<xref:System.Windows.Forms.ToolStripMenuItem>' ın metnini duyurdığınızda özelliğin değerini duyurur.</span><span class="sxs-lookup"><span data-stu-id="d808c-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="d808c-233">Bir <xref:System.Windows.Forms.ToolStripMenuItem> öğesinin<xref:System.Windows.Forms.Control.Enabled> özelliği olarak`false`ayarlandığı zaman gösterir.</span><span class="sxs-lookup"><span data-stu-id="d808c-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="d808c-234"><xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> Özelliği olarak`true`ayarlandığında onay kutusunun durumu hakkında geri bildirim sağlar.</span><span class="sxs-lookup"><span data-stu-id="d808c-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="d808c-235">Ekran okuyucusu 'nun tarama modu odak sırası, ClickOnce indirme iletişim kutusu penceresindeki denetimlerin görsel sırasıyla tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="d808c-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="d808c-236">**DataGridView geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="d808c-236">**DataGridView improvements**</span></span>

<span data-ttu-id="d808c-237">.NET Framework 4.7.2 ile başlayarak, <xref:System.Windows.Forms.DataGridView> denetim aşağıdaki erişilebilirlik geliştirmelerini sunmuştur:</span><span class="sxs-lookup"><span data-stu-id="d808c-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="d808c-238">Satırlar klavye kullanılarak sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="d808c-239">Kullanıcı, geçerli sütuna göre sıralamak için F3 tuşunu kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="d808c-240"><xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> , <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>' A ayarlandığında, sütun üst bilgisi, geçerli satırdaki hücreler aracılığıyla geçerli sütunu Kullanıcı sekmeleri olarak gösterecek şekilde renkle değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="d808c-241">Öğesinin özelliği doğru üst denetimi döndürür.<xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="d808c-242">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="d808c-242">**Improved visual cues**</span></span>

- <span data-ttu-id="d808c-243"><xref:System.Windows.Forms.CheckBox> Boş <xref:System.Windows.Forms.RadioButton> birözelliğiolanvedenetimleri,odağıalırkenbirodakgöstergesigörüntüler.<xref:System.Windows.Forms.ButtonBase.Text></span><span class="sxs-lookup"><span data-stu-id="d808c-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="d808c-244">**Geliştirilmiş özellik Kılavuzu desteği**</span><span class="sxs-lookup"><span data-stu-id="d808c-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="d808c-245">Denetim alt öğeleri artık yalnızca bir PropertyGrid `true` öğesi etkinleştirildiğinde <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> özelliği için bir döndürür. <xref:System.Windows.Forms.PropertyGrid></span><span class="sxs-lookup"><span data-stu-id="d808c-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="d808c-246">Denetim alt öğeleri, yalnızca bir `false` PropertyGrid öğesi <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> Kullanıcı tarafından değiştirilebiliyorsa özelliği için bir döndürür. <xref:System.Windows.Forms.PropertyGrid></span><span class="sxs-lookup"><span data-stu-id="d808c-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="d808c-247">**Geliştirilmiş Klavye gezintisi**</span><span class="sxs-lookup"><span data-stu-id="d808c-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="d808c-248">Denetim, <xref:System.Windows.Forms.ToolStripPanel.TabStop> özelliği, özelliği olan bir <xref:System.Windows.Forms.ToolStripPanel> öğesine dahil edildiğinde odağa izin verir <xref:System.Windows.Forms.ToolStripButton>`true`</span><span class="sxs-lookup"><span data-stu-id="d808c-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="d808c-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="d808c-250">**CheckBox ve RadioButton denetimlerinde yapılan değişiklikler**</span><span class="sxs-lookup"><span data-stu-id="d808c-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="d808c-251">.NET Framework 4.7.1 ve önceki sürümlerde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimler tutarsız ve klasik ve yüksek karşıtlık temalarında hatalı odak görselleri.</span><span class="sxs-lookup"><span data-stu-id="d808c-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="d808c-252">Bu sorunlar, denetimlerin hiçbir içerik kümesi olmadığı durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="d808c-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="d808c-253">Bu, Temalar kafa karıştırıcı ve odak görselindeki geçişleri görebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="d808c-254">.NET Framework 4.7.2 ' de, bu görseller artık Temalar arasında daha tutarlıdır ve klasik ve Yüksek Karşıtlık temalarda daha kolay görünür.</span><span class="sxs-lookup"><span data-stu-id="d808c-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="d808c-255">**WPF uygulamasında barındırılan WinForms denetimleri**</span><span class="sxs-lookup"><span data-stu-id="d808c-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="d808c-256">.NET Framework 4.7.1 ve önceki sürümlerde bulunan bir WPF uygulamasında barındırılan WinForms denetimi için, söz konusu katmandaki ilk veya son denetim WPF <xref:System.Windows.Forms.Integration.ElementHost> denetimi ise, kullanıcılar WinForms katmanının dışına sekmesine dönüştüremedik.</span><span class="sxs-lookup"><span data-stu-id="d808c-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="d808c-257">.NET Framework 4.7.2 ' de, kullanıcılar artık WinForms katmanının dışına sekme verebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="d808c-258">Ancak, odağa dayanan otomatikleştirilmiş uygulamalar artık WinForms katmanını hiçbir şekilde yok etmeyebilir ve beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="d808c-259">.NET Framework 4.7.1 ' deki erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="d808c-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="d808c-260">.NET Framework 4.7.1, aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="d808c-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="d808c-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d808c-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="d808c-263">ASP.NET Web denetimleri</span><span class="sxs-lookup"><span data-stu-id="d808c-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="d808c-264">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="d808c-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="d808c-265">Windows Workflow Foundation (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d808c-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="d808c-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="d808c-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="d808c-267">**Ekran okuyucu iyileştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="d808c-267">**Screen reader improvements**</span></span>

<span data-ttu-id="d808c-268">Erişilebilirlik iyileştirmeleri etkinleştirilmişse, .NET Framework 4.7.1, ekran okuyucularını etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="d808c-269">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.Expander> denetimler ekran okuyucular tarafından düğme olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d808c-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="d808c-270">.NET Framework 4.7.1 ile başlayarak, Genişletilebilir/daraltılabilir gruplar olarak doğru duyurulur.</span><span class="sxs-lookup"><span data-stu-id="d808c-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="d808c-271">.NET Framework 4,7 ve önceki sürümlerde, <xref:System.Windows.Controls.DataGridCell> denetimler ekran okuyucular tarafından "özel" olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d808c-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="d808c-272">.NET Framework 4.7.1 başlayarak, artık veri kılavuzu hücresi (yerelleştirilmiş) olarak doğru duyurulur.</span><span class="sxs-lookup"><span data-stu-id="d808c-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="d808c-273">.NET Framework 4.7.1 'den başlayarak ekran okuyucular düzenlenebilir <xref:System.Windows.Controls.ComboBox>bir adı duyurur.</span><span class="sxs-lookup"><span data-stu-id="d808c-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="d808c-274">.NET Framework 4,7 ve önceki sürümlerde denetimler, <xref:System.Windows.Controls.PasswordBox> "görünümde hiçbir öğe yok" veya başka türlü yanlış davranışa sahip olarak duyurulmuştur.</span><span class="sxs-lookup"><span data-stu-id="d808c-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="d808c-275">Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="d808c-276">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="d808c-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="d808c-277">Okuyucu gibi ekran okuyucular, kullanıcıların, genellikle odağa sahip kullanıcı arabirimi içeriğinin metinden konuşmaya çıkışıyla bir uygulamanın kullanıcı arabirimi içeriğini okumasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="d808c-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="d808c-278">Ancak, bir UI öğesi değişirse ve odağa sahip değilse, kullanıcıya bildirimde bulunulmayabilir ve önemli bilgileri kaçırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="d808c-279">Canlı bölgeler bu sorunu çözmeye hedeflenir.</span><span class="sxs-lookup"><span data-stu-id="d808c-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="d808c-280">Geliştirici, ekran okuyucuyu veya başka bir UIAutomation istemcisini, bir kullanıcı arabirimi öğesine önemli bir değişikliğin yapıldığını bilgilendirmek için kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="d808c-281">Ekran okuyucu daha sonra bu değişikliğin kullanıcısına nasıl ve ne zaman bilgi verileceğine karar verebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="d808c-282">Canlı bölgeleri desteklemek için WPF 'e aşağıdaki API 'Ler eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="d808c-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="d808c-283">**Livesetting** özelliğini ve **liveregionchanged** olayını tanımlayan <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> vealanları.<xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="d808c-284">XAML kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="d808c-285">Kullanıcı ARABIRIMININ önem derecesine sahip ekran okuyucuyu kullanıcıya bildiren **AutomationProperties. LiveSetting** iliştirilmiş özelliği.</span><span class="sxs-lookup"><span data-stu-id="d808c-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="d808c-286">**AutomationProperties. livesetting** ekli özelliğini tanımlayan özelliği.<xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="d808c-287">Bir **livesetting** değeri sağlamak için geçersiz kılınabilen <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="d808c-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="d808c-288">Ve, bir livesetting değeri alır ve ayarlar. <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="d808c-289">Aşağıdaki olası **livesetting** değerlerini tanımlayan sabitlistesi:<xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="d808c-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="d808c-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d808c-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-291">Canlı bölgenin içeriği değiştiyse öğe bildirim göndermez.</span><span class="sxs-lookup"><span data-stu-id="d808c-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="d808c-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d808c-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-293">Canlı bölgenin içeriği değiştiyse, öğesi interruptive olmayan bildirimler gönderir.</span><span class="sxs-lookup"><span data-stu-id="d808c-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="d808c-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d808c-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d808c-295">Canlı bölgenin içeriği değiştiyse, öğesi interruptive bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="d808c-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="d808c-296">Aşağıdaki örnekte gösterildiği gibi, ilgilendiğiniz öğe üzerinde **AutomationProperties. livesetting** özelliğini ayarlayarak bir LiveRegion oluşturabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="d808c-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="d808c-297">Canlı bölgedeki veriler değiştiğinde ve bir ekran okuyucuyu bilgilendirmeniz gerektiğinde, aşağıdaki örnekte gösterildiği gibi, açıkça bir olay oluşturursunuz.</span><span class="sxs-lookup"><span data-stu-id="d808c-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="d808c-298">**Yüksek karşıtlık**</span><span class="sxs-lookup"><span data-stu-id="d808c-298">**High contrast**</span></span>

<span data-ttu-id="d808c-299">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimlerinde yüksek karşıtlıklı geliştirmeler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="d808c-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="d808c-300">Artık <xref:System.Windows.SystemParameters.HighContrast%2A> Tema ayarlandığında görünür olur.</span><span class="sxs-lookup"><span data-stu-id="d808c-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="d808c-301">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="d808c-301">These include:</span></span>

- <span data-ttu-id="d808c-302"><xref:System.Windows.Controls.Expander>denetimle</span><span class="sxs-lookup"><span data-stu-id="d808c-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="d808c-303"><xref:System.Windows.Controls.Expander> Denetim için odak görseli artık görülebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="d808c-304"><xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>Ve denetimlerinin<xref:System.Windows.Controls.RadioButton> klavye görselleri de görünür.</span><span class="sxs-lookup"><span data-stu-id="d808c-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="d808c-305">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-305">For example:</span></span>

  <span data-ttu-id="d808c-306">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-306">Before:</span></span> 

  ![Erişilebilirlik geliştirmelerinden önce odaklı genişletici denetimi](./media/expander-before.png)

  <span data-ttu-id="d808c-308">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-308">After:</span></span> 

  ![Erişilebilirlik geliştirmelerinden sonra odak ile genişletici denetimi](./media/expander-after.png)

- <span data-ttu-id="d808c-310"><xref:System.Windows.Controls.CheckBox>ve <xref:System.Windows.Controls.RadioButton> denetimler</span><span class="sxs-lookup"><span data-stu-id="d808c-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="d808c-311"><xref:System.Windows.Controls.CheckBox> Ve<xref:System.Windows.Controls.RadioButton> denetimlerindeki metin artık yüksek karşıtlık temalarında seçildiğinde daha kolay görülebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="d808c-312">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-312">For example:</span></span>

  <span data-ttu-id="d808c-313">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-313">Before:</span></span> 

  ![Erişilebilirlik geliştirmelerinden önce odak içeren yüksek karşıtlık radyo düğmesi](./media/radio-button-before.png)

  <span data-ttu-id="d808c-315">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-315">After:</span></span> 

  ![Erişilebilirlik geliştirmelerinden sonra odak ile yüksek karşıtlık radyo düğmesi](./media/radio-button-after.png)

- <span data-ttu-id="d808c-317"><xref:System.Windows.Controls.ComboBox>denetimle</span><span class="sxs-lookup"><span data-stu-id="d808c-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="d808c-318">.NET Framework 4.7.1 ile başlayarak, devre dışı <xref:System.Windows.Controls.ComboBox> bir denetimin kenarlığı devre dışı metinle aynı renktedir.</span><span class="sxs-lookup"><span data-stu-id="d808c-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="d808c-319">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-319">For example:</span></span>

  <span data-ttu-id="d808c-320">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-320">Before:</span></span> 

  ![ComboBox, erişilebilirlik geliştirmelerinden önce kenarlık ve metin devre dışı](./media/combo-disabled-before.png)

  <span data-ttu-id="d808c-322">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-322">After:</span></span>   

  ![ComboBox, erişilebilirlik iyileştirmelerinden sonra devre dışı bırakıldı kenarlık ve metin](./media/combo-disabled-after.png)

  <span data-ttu-id="d808c-324">Ayrıca, devre dışı bırakılmış ve odaklanmış düğmeler doğru tema rengini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="d808c-325">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-325">Before:</span></span>

  ![Erişilebilirlik geliştirmelerinden önceki düğme teması renkleri](./media/button-themes-before.png) 

  <span data-ttu-id="d808c-327">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-327">After:</span></span> 

  ![Erişilebilirlik geliştirmelerinden sonra düğme teması renkleri](./media/button-themes-after.png) 

  <span data-ttu-id="d808c-329">Son olarak, .NET Framework 4,7 ve önceki sürümlerde, açılır okun <xref:System.Windows.Controls.ComboBox> görünmez olması nedeniyle bir `Toolbar.ComboBoxStyleKey` denetimin stilini ayarlama.</span><span class="sxs-lookup"><span data-stu-id="d808c-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="d808c-330">Bu sorun, .NET Framework 4.7.1 ile başlayarak düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="d808c-331">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-331">For example:</span></span>

  <span data-ttu-id="d808c-332">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-332">Before:</span></span> 

  ![Erişilebilirlik geliştirmelerinden önce Toolbar. ComboBoxStyleKey](./media/comboboxstylekey-before.png) 

  <span data-ttu-id="d808c-334">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-334">After:</span></span> 

  ![Erişilebilirlik geliştirmelerinden sonra Toolbar. ComboBoxStyleKey](./media/comboboxstylekey-after.png) 

- <span data-ttu-id="d808c-336"><xref:System.Windows.Controls.DataGrid>denetimle</span><span class="sxs-lookup"><span data-stu-id="d808c-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="d808c-337">.NET Framework 4.7.1 başlayarak, <xref:System.Windows.Controls.DataGrid> denetimlerde sıralama göstergesi oku artık doğru Tema renklerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="d808c-338">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-338">For example:</span></span>

  <span data-ttu-id="d808c-339">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-339">Before:</span></span> 

  ![Erişilebilirlik geliştirmelerinden önce sıralama göstergesi oku](./media/sort-indicator-before.png) 

  <span data-ttu-id="d808c-341">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-341">After:</span></span>   

  ![Erişilebilirlik geliştirmelerinden sonra sıralama göstergesi oku](./media/sort-indicator-after.png) 

  <span data-ttu-id="d808c-343">Ayrıca, .NET Framework 4,7 ve önceki sürümlerde, varsayılan bağlantı stili, fare üzerinde yüksek karşıtlık modlarında yanlış bir renge değiştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d808c-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="d808c-344">Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="d808c-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="d808c-345">Benzer şekilde <xref:System.Windows.Controls.DataGrid> , CheckBox sütunları .NET Framework 4.7.1 ile başlayan klavye odağı geri bildirimi için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="d808c-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="d808c-346">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-346">Before:</span></span> 

  ![Erişilebilirlik geliştirmelerinden önce DataGrid varsayılan bağlantı stili](./media/default-link-style-before.png) 

  <span data-ttu-id="d808c-348">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-348">After:</span></span>    

  ![Erişilebilirlik geliştirmelerinden sonra DataGrid varsayılan bağlantı stili](./media/default-link-style-after.png) 

<span data-ttu-id="d808c-350">.NET Framework 4.7.1 ' deki WPF Erişilebilirlik iyileştirmeleri hakkında daha fazla bilgi için bkz. [WPF 'de erişilebilirlik geliştirmeleri](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="d808c-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="d808c-351">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="d808c-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="d808c-352">.NET Framework 4.7.1, Windows Forms (WinForms), aşağıdaki alanlardaki erişilebilirlik değişikliklerini içerir.</span><span class="sxs-lookup"><span data-stu-id="d808c-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="d808c-353">**Yüksek Karşıtlık modunda iyileştirilmiş ekran**</span><span class="sxs-lookup"><span data-stu-id="d808c-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="d808c-354">.NET Framework 4.7.1 ile başlayarak, çeşitli WinForms denetimleri işletim sisteminde bulunan üst karşıtlık modlarında geliştirilmiş işleme sunar.</span><span class="sxs-lookup"><span data-stu-id="d808c-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="d808c-355">Windows 10, bazı yüksek karşıtlıklı sistem renklerinin değerlerini değiştirdi ve Windows Forms Windows 10 Win32 çerçevesini temel alır.</span><span class="sxs-lookup"><span data-stu-id="d808c-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="d808c-356">En iyi deneyim için, Windows 'un en son sürümünde çalıştırın ve bir test uygulamasına bir App. manifest dosyası ekleyerek en son işletim sistemi değişikliklerini kabul edin ve Windows 10 desteklenen işletim sistemi satırını, aşağıdakileri içerecek şekilde not edin:</span><span class="sxs-lookup"><span data-stu-id="d808c-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="d808c-357">Yüksek karşıtlıklı değişikliklere örnek olarak şunlar verilebilir:</span><span class="sxs-lookup"><span data-stu-id="d808c-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="d808c-358">Öğelerin içindeki <xref:System.Windows.Forms.MenuStrip> onay işaretlerinin görünümü daha kolay.</span><span class="sxs-lookup"><span data-stu-id="d808c-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="d808c-359">Seçildiğinde, devre dışı <xref:System.Windows.Forms.MenuStrip> bırakılan öğeler daha kolay görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d808c-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="d808c-360">Seçili <xref:System.Windows.Forms.Button> denetimdeki metin seçim rengiyle karşıttır.</span><span class="sxs-lookup"><span data-stu-id="d808c-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="d808c-361">Devre dışı bırakılan metin daha kolay okunabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-361">Disabled text is easier to read.</span></span> <span data-ttu-id="d808c-362">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="d808c-362">For example:</span></span>

  <span data-ttu-id="d808c-363">Sonra:</span><span class="sxs-lookup"><span data-stu-id="d808c-363">Before:</span></span>

  ![Erişilebilirlik geliştirmelerinden önce devre dışı metin](./media/wf-disabled-before.png) 

  <span data-ttu-id="d808c-365">Sonra</span><span class="sxs-lookup"><span data-stu-id="d808c-365">After:</span></span>

  ![Erişilebilirlik geliştirmelerinden sonra devre dışı metin](./media/wf-disabled-after.png) 

- <span data-ttu-id="d808c-367">Iş parçacığı özel durumu Iletişim kutusunda yüksek karşıtlık geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="d808c-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="d808c-368">**İyileştirilmiş ekran okuyucusu desteği**</span><span class="sxs-lookup"><span data-stu-id="d808c-368">**Improved Narrator support**</span></span>

<span data-ttu-id="d808c-369">.NET Framework 4.7.1 Windows Forms, ekran okuyucusu için aşağıdaki erişilebilirlik geliştirmelerini içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="d808c-370"><xref:System.Windows.Forms.MonthCalendar> Denetime, diğer UI Otomasyon Araçları ile birlikte ekran okuyucusu tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="d808c-371">Denetim <xref:System.Windows.Forms.CheckedListBox> , bir öğenin denetim durumu değiştiğinde kullanıcıya bir liste öğesinin değerini değiştirdikleri bildirilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="d808c-372"><xref:System.Windows.Forms.DataGridViewCell> Denetim, doğru salt okuma durumunu ekran okuyucusuna bildirir.</span><span class="sxs-lookup"><span data-stu-id="d808c-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="d808c-373">Ekran okuyucusu artık devre dışı <xref:System.Windows.Forms.ToolStripMenuItem> bırakılan metni okuyabilir, ancak daha önce devre dışı menü öğelerini atlar.</span><span class="sxs-lookup"><span data-stu-id="d808c-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="d808c-374">**UIAutomation erişilebilirlik desenleri için gelişmiş destek**</span><span class="sxs-lookup"><span data-stu-id="d808c-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="d808c-375">.NET Framework 4.7.1 ile başlayarak, erişilebilirlik teknolojisi araçları geliştiricileri, çeşitli WinForms denetimleri için ortak API erişilebilirlik desenlerinden ve özelliklerinden faydalanabilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="d808c-376">Bu erişilebilirlik geliştirmeleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="d808c-377">Ve artık genişletme [/daraltma düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekliyor. <xref:System.Windows.Forms.ToolStripSplitButton> <xref:System.Windows.Forms.ComboBox></span><span class="sxs-lookup"><span data-stu-id="d808c-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="d808c-378">Artık geçişli stili destekliyor. [](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md) <xref:System.Windows.Forms.DataGridViewCheckBoxCell></span><span class="sxs-lookup"><span data-stu-id="d808c-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="d808c-379">Denetim, <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt düzenlerini](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md)destekler. <xref:System.Windows.Forms.ToolStripItem></span><span class="sxs-lookup"><span data-stu-id="d808c-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="d808c-380"><xref:System.Windows.Forms.NumericUpDown> Ve<xref:System.Windows.Forms.DomainUpDown> denetimleri özelliği<xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> destekler.</span><span class="sxs-lookup"><span data-stu-id="d808c-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="d808c-381">**Geliştirilmiş özellik tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="d808c-381">**Improved property browser experience**</span></span>

<span data-ttu-id="d808c-382">.NET Framework 4.7.1 ile başlayarak, Windows Forms şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="d808c-383">Çeşitli açılan seçim pencereleri aracılığıyla daha iyi klavye gezintisi.</span><span class="sxs-lookup"><span data-stu-id="d808c-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="d808c-384">Gereksiz sekme duraklarının azaltılması.</span><span class="sxs-lookup"><span data-stu-id="d808c-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="d808c-385">Denetim türlerinin daha iyi raporlaması.</span><span class="sxs-lookup"><span data-stu-id="d808c-385">Better reporting of control types.</span></span>
- <span data-ttu-id="d808c-386">İyileştirilmiş ekran okuyucusu davranışı.</span><span class="sxs-lookup"><span data-stu-id="d808c-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="d808c-387">ASP.NET Web denetimleri</span><span class="sxs-lookup"><span data-stu-id="d808c-387">ASP.NET web controls</span></span>

<span data-ttu-id="d808c-388">.NET Framework 4.7.1 ve Visual Studio 2017 15,3 ' den başlayarak, ASP.NET ASP.NET Web denetimlerinin Visual Studio 'da erişilebilirlik teknolojisiyle nasıl çalıştığını geliştirir.</span><span class="sxs-lookup"><span data-stu-id="d808c-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="d808c-389">Değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-389">Changes include the following:</span></span>

- <span data-ttu-id="d808c-390">**Ayrıntılar görünümü** sihirbazındaki **alan Ekle** Iletişim kutusu ya da **ListView** sihirbazının **LISTVIEW yapılandırma** iletişim kutusu gibi denetimlerde eksik UI erişilebilirlik düzenlerini uygulamak için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="d808c-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="d808c-391">**Veri sayfalayıcı alanları Düzenleyicisi**gibi yüksek karşıtlık modunda görüntüyü geliştirmek için değişiklikler.</span><span class="sxs-lookup"><span data-stu-id="d808c-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="d808c-392">DataPager denetiminin **sayfalayıcı alanlarını düzenleme** Sihirbazı 'ndaki **alanlar** iletişim kutusu gibi denetimler için klavye gezinti deneyimlerini geliştirmek üzere yapılan değişiklikler, **ObjectContext 'ı Yapılandır** iletişim kutusu veya **veri Yapılandır seçimi** **veri kaynağını yapılandırma** sihirbazının iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d808c-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="d808c-393">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="d808c-393">.NET SDK Tools</span></span>

<span data-ttu-id="d808c-394">[Yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme Görüntüleyicisi Aracı (SvcTraceViewer. exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) , değişen erişilebilirlik sorunları düzeltilirken geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="d808c-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="d808c-395">Bunların çoğu, bir ad tanımlanmadığında veya belirli Kullanıcı Arabirimi Otomasyonu desenlerinin doğru uygulanmadığından küçük sorunlardır.</span><span class="sxs-lookup"><span data-stu-id="d808c-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="d808c-396">Birçok kullanıcı bu hatalı değerleri bilmez, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK araçlarını daha erişilebilir bulacaktır.</span><span class="sxs-lookup"><span data-stu-id="d808c-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="d808c-397">Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="d808c-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="d808c-398">Windows Workflow Foundation (WF) İş Akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="d808c-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="d808c-399">İş Akışı Tasarımcısı erişilebilirlik değişiklikleri şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="d808c-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="d808c-400">Sekme sırası, bazı denetimlerde soldan sağa ve yukarıdan aşağıya değişir:</span><span class="sxs-lookup"><span data-stu-id="d808c-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="d808c-401"><xref:System.ServiceModel.Activities.InitializeCorrelation> Etkinlik için bağıntı verileri ayarlamaya yönelik bağıntı Başlat penceresi.</span><span class="sxs-lookup"><span data-stu-id="d808c-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="d808c-402"><xref:System.ServiceModel.Activities.Receive> ,<xref:System.ServiceModel.Activities.Send>, Ve etkinlikleri<xref:System.ServiceModel.Activities.ReceiveReply> için içerik tanımı penceresi. <xref:System.ServiceModel.Activities.SendReply></span><span class="sxs-lookup"><span data-stu-id="d808c-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="d808c-403">Klavye aracılığıyla daha fazla işlev mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="d808c-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="d808c-404">Bir etkinliğin özelliklerini düzenlediğinizde, özellik grupları ilk odaklandığında klavye tarafından daraltılabilirler.</span><span class="sxs-lookup"><span data-stu-id="d808c-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="d808c-405">Uyarı simgeleri klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="d808c-406">**Özellikler** penceresindeki **daha fazla Özellikler** düğmesine klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="d808c-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="d808c-407">Klavye kullanıcıları İş Akışı Tasarımcısı **bağımsız değişkenler** ve **değişkenler** bölmelerinde üst bilgi öğelerine erişebilirler.</span><span class="sxs-lookup"><span data-stu-id="d808c-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="d808c-408">Odaklanılmış öğelerin şu durumlarda geliştirilmiş görünürlüğü:</span><span class="sxs-lookup"><span data-stu-id="d808c-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="d808c-409">İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzlarına satır ekleme.</span><span class="sxs-lookup"><span data-stu-id="d808c-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="d808c-410"><xref:System.ServiceModel.Activities.ReceiveReply> Ve<xref:System.ServiceModel.Activities.SendReply> etkinliklerindeki alanlar arasında sekme.</span><span class="sxs-lookup"><span data-stu-id="d808c-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="d808c-411">Değişkenler veya bağımsız değişkenler için varsayılan değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="d808c-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="d808c-412">Ekran okuyucular artık doğru şekilde tanıyabilir:</span><span class="sxs-lookup"><span data-stu-id="d808c-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="d808c-413">İş akışı tasarımcısında ayarlanan kesme noktaları.</span><span class="sxs-lookup"><span data-stu-id="d808c-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="d808c-414"><xref:System.Activities.Statements.FlowSwitch%601> ,<xref:System.Activities.Statements.FlowDecision>Ve etkinlikleri<xref:System.ServiceModel.Activities.CorrelationScope> .</span><span class="sxs-lookup"><span data-stu-id="d808c-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="d808c-415"><xref:System.ServiceModel.Activities.Receive> Etkinliğin içeriği.</span><span class="sxs-lookup"><span data-stu-id="d808c-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="d808c-416"><xref:System.Activities.Statements.InvokeMethod> Etkinliğin hedef türü.</span><span class="sxs-lookup"><span data-stu-id="d808c-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="d808c-417"><xref:System.Activities.Statements.TryCatch> Etkinliğin özel durum açılan kutusu ve son bölümü.</span><span class="sxs-lookup"><span data-stu-id="d808c-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="d808c-418">İleti türü açılan kutusu, bağıntı başlatıcı ekleme penceresinde, içerik tanımı penceresinde ve CorrelatesOn tanımı penceresinde, ileti<xref:System.ServiceModel.Activities.Receive>etkinliklerinin ( <xref:System.ServiceModel.Activities.SendReply>, <xref:System.ServiceModel.Activities.Send>, ve <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="d808c-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="d808c-419">Durum makinesi geçişleri ve geçiş hedefleri.</span><span class="sxs-lookup"><span data-stu-id="d808c-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="d808c-420">Etkinlikler üzerinde <xref:System.Activities.Statements.FlowDecision> ek açıklamalar ve bağlayıcılar.</span><span class="sxs-lookup"><span data-stu-id="d808c-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="d808c-421">Etkinlikler için bağlam (sağ tıklama) menüleri.</span><span class="sxs-lookup"><span data-stu-id="d808c-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="d808c-422">Özellik değeri düzenleyicileri, aramayı temizle düğmesi, kategoriye ve alfabetik sıralama düğmelerine göre ve Özellikler kılavuzundaki Ifade Düzenleyicisi iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="d808c-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="d808c-423">İş Akışı Tasarımcısı yakınlaştırma yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="d808c-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="d808c-424"><xref:System.Activities.Statements.Parallel> Ve<xref:System.Activities.Statements.Pick> etkinliklerindeki ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="d808c-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="d808c-425"><xref:System.Activities.Statements.InvokeDelegate> Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="d808c-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="d808c-426">Sözlük Etkinlikleri (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, vb.) için türleri seçin penceresi.</span><span class="sxs-lookup"><span data-stu-id="d808c-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="d808c-427">.NET tür araştır ve Seç penceresi.</span><span class="sxs-lookup"><span data-stu-id="d808c-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="d808c-428">İş Akışı Tasarımcısı içerik haritaları.</span><span class="sxs-lookup"><span data-stu-id="d808c-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="d808c-429">Yüksek Karşıtlık Temaları seçen kullanıcılar, öğeler arasında daha iyi kontrast oranları ve odak öğeleri için kullanılan daha belirgin seçim kutuları gibi İş Akışı Tasarımcısı ve denetimlerinin görünürlüğünde birçok geliştirme görür.</span><span class="sxs-lookup"><span data-stu-id="d808c-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="d808c-430">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d808c-430">See also</span></span>

- [<span data-ttu-id="d808c-431">.NET Framework yenilikler</span><span class="sxs-lookup"><span data-stu-id="d808c-431">What's new in the .NET Framework</span></span>](whats-new.md)
