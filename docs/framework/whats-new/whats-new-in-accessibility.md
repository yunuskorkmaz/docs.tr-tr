---
title: Erişilebilirlik .NET Framework'teki yenilikler
ms.custom: updateeachrelease
ms.date: 04/18/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: da73df97524b9e394fac795daf14a3f0fb1f4e3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661379"
---
# <a name="whats-new-in-accessibility-in-the-net-framework"></a><span data-ttu-id="ef159-102">Erişilebilirlik .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="ef159-102">What's new in accessibility in the .NET Framework</span></span>

<span data-ttu-id="ef159-103">.NET Framework uygulamaları daha erişilebilir, kullanıcılarınız için duruma getirmeyi amaçlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-103">The .NET Framework aims at making applications more accessible for your users.</span></span> <span data-ttu-id="ef159-104">Yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak için uygulamanın erişilebilirlik özellikleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-104">Accessibility features allow an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="ef159-105">.NET Framework, .NET Framework 4.7.1 ile başlayarak, çok sayıda erişilebilir uygulamalar oluşturmaları için geliştiricileri erişilebilirlik geliştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef159-105">Starting with .NET Framework 4.7.1, the .NET Framework includes a large number of accessibility improvements that allow developers to create accessible applications.</span></span>

## <a name="accessibility-switches"></a><span data-ttu-id="ef159-106">Erişilebilirlik anahtarları</span><span class="sxs-lookup"><span data-stu-id="ef159-106">Accessibility switches</span></span>

<span data-ttu-id="ef159-107">Uygulamanızı .NET Framework 4.7 veya önceki bir sürümünü hedefler, ancak .NET Framework 4.7.1'i çalıştıran erişilebilirlik özelliklerini geri çevirmek için yapılandırabilirsiniz veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="ef159-107">You can configure your app to opt into accessibility features if it targets .NET Framework 4.7 or an earlier version but is running on .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="ef159-108">Uygulamanızı .NET Framework 4.7.1'i hedefleyen, eski özellikleri (ve değil yararlanın erişilebilirlik özellikleri) kullanacak şekilde de yapılandırabilirsiniz veya üzeri.</span><span class="sxs-lookup"><span data-stu-id="ef159-108">You can also configure your app to use legacy features (and not take advantage of accessibility features) if it targets .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="ef159-109">Erişilebilirlik özellikleri içeren .NET Framework'ün her sürümü eklediğiniz bir sürüme özgü erişilebilirlik anahtara sahip [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası.</span><span class="sxs-lookup"><span data-stu-id="ef159-109">Each version of the .NET Framework that includes accessibility features has a version-specific accessibility switch, which you add to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file.</span></span> <span data-ttu-id="ef159-110">Desteklenen anahtarlar şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ef159-110">The following are the supported switches:</span></span>

|<span data-ttu-id="ef159-111">Sürüm</span><span class="sxs-lookup"><span data-stu-id="ef159-111">Version</span></span>|<span data-ttu-id="ef159-112">Anahtar</span><span class="sxs-lookup"><span data-stu-id="ef159-112">Switch</span></span>|
|---|---|
|<span data-ttu-id="ef159-113">.NET framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="ef159-113">.NET Framework 4.7.1</span></span>|<span data-ttu-id="ef159-114">"Switch.UseLegacyAccessibilityFeatures"</span><span class="sxs-lookup"><span data-stu-id="ef159-114">"Switch.UseLegacyAccessibilityFeatures"</span></span>|
|<span data-ttu-id="ef159-115">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="ef159-115">.NET Framework 4.7.2</span></span>|<span data-ttu-id="ef159-116">"Switch.UseLegacyAccessibilityFeatures.2"</span><span class="sxs-lookup"><span data-stu-id="ef159-116">"Switch.UseLegacyAccessibilityFeatures.2"</span></span>|
|<span data-ttu-id="ef159-117">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="ef159-117">.NET Framework 4.8</span></span>|<span data-ttu-id="ef159-118">"Switch.UseLegacyAccessibilityFeatures.3"</span><span class="sxs-lookup"><span data-stu-id="ef159-118">"Switch.UseLegacyAccessibilityFeatures.3"</span></span>|

### <a name="taking-advantage-of-accessibility-enhancements"></a><span data-ttu-id="ef159-119">Erişilebilirlik geliştirmeleri yararlanma</span><span class="sxs-lookup"><span data-stu-id="ef159-119">Taking advantage of accessibility enhancements</span></span>

<span data-ttu-id="ef159-120">.NET Framework 4.7.1'i hedefleyen uygulamalar için varsayılan olarak etkin ya da daha yeni erişilebilirlik özellikleri.</span><span class="sxs-lookup"><span data-stu-id="ef159-120">The new accessibility features are enabled by default for applications that target .NET Framework 4.7.1 or later.</span></span> <span data-ttu-id="ef159-121">Ayrıca, .NET Framework'ün önceki sürümünü hedefleyecek ancak .NET Framework 4.7.1 üzerinde çalışmakta olan veya daha sonra seçebilirsiniz uygulamalar eski erişilebilirlik davranışlarını dışarı (ve böylece erişilebilirlik iyileştirmeleri yararlanmak) anahtarları için ekleyerek[ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) uygulamanın yapılandırma dosyası ve kendi değerini bölümünü `false`.</span><span class="sxs-lookup"><span data-stu-id="ef159-121">In addition, applications that target an earlier version of the .NET Framework but are running on .NET Framework 4.7.1 or later can opt out of legacy accessibility behaviors (and thereby take advantage of accessibility improvements) by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `false`.</span></span> <span data-ttu-id="ef159-122">Erişilebilirlik geliştirmeleri .NET Framework 4.7.1 sunmuştur kabul etmek nasıl aşağıda gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef159-122">The following shows how to opt in to accessibility enhancements introduced in .NET Framework 4.7.1:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false" />
</runtime>
```

<span data-ttu-id="ef159-123">Erişilebilirlik özellikleri sonraki bir sürümü .NET Framework'ün kabul etmek isterseniz, aynı zamanda açıkça özellikleri için .NET Framework'ün önceki sürümlerinden kabul gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef159-123">If you choose to opt in to accessibility features in a later version of the .NET Framework, you must also explicitly opt in to the features from earlier versions of the .NET Framework.</span></span> <span data-ttu-id="ef159-124">Hem .NET Framework 4.7.1 ve 4.7.2 erişilebilirlik geliştirmeleri avantajlarından faydalanmak için uygulamanızı yapılandırma aşağıdakileri gerektirir [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesi:</span><span class="sxs-lookup"><span data-stu-id="ef159-124">Configuring your app to take advantage of accessibility improvements in both .NET Framework 4.7.1 and 4.7.2 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false" />
</runtime>
```

<span data-ttu-id="ef159-125">.NET Framework 4.7.1 4.7.2 ve 4.8 erişilebilirlik geliştirmeleri avantajlarından faydalanmak için uygulamanızı yapılandırma aşağıdakileri gerektirir [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesi:</span><span class="sxs-lookup"><span data-stu-id="ef159-125">Configuring your app to take advantage of accessibility improvements in .NET Framework 4.7.1, 4.7.2, and 4.8 requires the following [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures=false;Switch.UseLegacyAccessibilityFeatures.2=false;Switch.UseLegacyAccessibilityFeatures.3=false" />
</runtime>
```

### <a name="restoring-legacy-behavior"></a><span data-ttu-id="ef159-126">Eski davranışı geri yükleme</span><span class="sxs-lookup"><span data-stu-id="ef159-126">Restoring legacy behavior</span></span>

<span data-ttu-id="ef159-127">.NET Framework 4.7.1 ile başlayan sürümlerini hedefleyen uygulamalar devre dışı bırakabilirsiniz erişilebilirlik özellikleri anahtarlara ekleyerek [ `<AppContextSwitchOverrides>` ](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) öğesinde [ `<runtime>` ](~/docs/framework/configure-apps/file-schema/runtime/index.md) bölümü Uygulamanın yapılandırma dosyası ve kendi değerini `true`.</span><span class="sxs-lookup"><span data-stu-id="ef159-127">Applications that target versions of the .NET Framework starting with 4.7.1 can disable accessibility features by adding switches to the [`<AppContextSwitchOverrides>`](~/docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) element in the [`<runtime>`](~/docs/framework/configure-apps/file-schema/runtime/index.md) section of the application's configuration file and setting their value to `true`.</span></span> <span data-ttu-id="ef159-128">Örneğin, aşağıdaki yapılandırma, .NET Framework 4.7.2 sunulan erişilebilirlik özellikleri dışında kabul eder:</span><span class="sxs-lookup"><span data-stu-id="ef159-128">For example, the following configuration opts out of accessibility features introduced in .NET Framework 4.7.2:</span></span>

```xml
<runtime>
    <!-- AppContextSwitchOverrides value attribute is in the form of 'key1=true|false;key2=true|false  -->
    <AppContextSwitchOverrides value="Switch.UseLegacyAccessibilityFeatures.2=true" />
</runtime>
```

## <a name="whats-new-in-accessibility-in-net-framework-48"></a><span data-ttu-id="ef159-129">.NET Framework 4.8 erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="ef159-129">What's new in accessibility in .NET Framework 4.8</span></span>

<span data-ttu-id="ef159-130">.NET framework 4.8 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-130">.NET Framework 4.8 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="ef159-131">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef159-131">Windows Forms</span></span>](#winforms48)

- [<span data-ttu-id="ef159-132">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-132">Windows Presentation Foundation (WPF)</span></span>](#wpf48)

- [<span data-ttu-id="ef159-133">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="ef159-133">Windows Workflow Foundation (WF) workflow designer</span></span>](#wf48)

<a name="winforms48" />

### <a name="windows-forms"></a><span data-ttu-id="ef159-134">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef159-134">Windows Forms</span></span>

<span data-ttu-id="ef159-135">.NET Framework 4.8 içinde Windows Forms için birçok yaygın olarak kullanılan denetimler LiveRegions ve bildirim olayları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="ef159-135">In .NET Framework 4.8, Windows Forms adds support for LiveRegions and Notification Events to many commonly used controls.</span></span> <span data-ttu-id="ef159-136">Klavyeyi kullanarak bir kullanıcı denetimi gittiğinde Ayrıca araç ipuçları için destek ekler.</span><span class="sxs-lookup"><span data-stu-id="ef159-136">It also adds support for ToolTips when a user navigates to a control by using the keyboard.</span></span>

<span data-ttu-id="ef159-137">**Etiketleri ve StatusStrip'leri UIA LiveRegions desteği**</span><span class="sxs-lookup"><span data-stu-id="ef159-137">**UIA LiveRegions Support in Labels and StatusStrips**</span></span>

<span data-ttu-id="ef159-138">UIA LiveRegions kullanıcı nerede çalıştığını konumu dışında bulunan bir denetimdeki metin değişikliğinin ekran okuyucular bildirmek uygulama geliştiricilerinin imkan tanır.</span><span class="sxs-lookup"><span data-stu-id="ef159-138">UIA LiveRegions allow application developers to notify screen readers of a text change in a control that is located apart from the location where the user is working.</span></span> <span data-ttu-id="ef159-139">Bu örneğin yararlı bir <xref:System.Windows.Forms.StatusStrip> bağlantı durumunu gösteren denetimdir.</span><span class="sxs-lookup"><span data-stu-id="ef159-139">This is useful, for example, for a <xref:System.Windows.Forms.StatusStrip> control that shows a connection status.</span></span> <span data-ttu-id="ef159-140">Bağlantı kesildi ve durum değişiklikleri, geliştirici ekran okuyucu bildirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-140">If the connection is dropped and the status changes, the developer might want to notify the screen reader.</span></span>

<span data-ttu-id="ef159-141">.NET Framework 4.8 ile başlayarak, Windows Forms UIA LiveRegions hem uygulayan <xref:System.Windows.Forms.Label> ve <xref:System.Windows.Forms.StatusStrip> kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ef159-141">Starting with .NET Framework 4.8, Windows Forms implements UIA LiveRegions for both the <xref:System.Windows.Forms.Label> and <xref:System.Windows.Forms.StatusStrip> controls.</span></span> <span data-ttu-id="ef159-142">Örneğin, aşağıdaki kodu içinde LiveRegion kullanan bir <xref:System.Windows.Forms.Label> adlı Denetim `label1`:</span><span class="sxs-lookup"><span data-stu-id="ef159-142">For example, the following code uses the LiveRegion in a <xref:System.Windows.Forms.Label> control named `label1`:</span></span>

```csharp
public Form1()
{
   InitializeComponent();
   label1.AutomationLiveSetting = AutomationLiveSetting.Polite;
}

…
Label1.Text = “Ready!”;
```

<span data-ttu-id="ef159-143">Ekran Okuyucusu "Hazır" kullanıcı burada uygulamayla etkileşime bağımsız olarak kullanıma sunulduğunu duyurdu.</span><span class="sxs-lookup"><span data-stu-id="ef159-143">Narrator announces “Ready” regardless of where the user is interacting with the application.</span></span>

<span data-ttu-id="ef159-144">Ayrıca uygulayabilirsiniz, <xref:System.Windows.Forms.UserControl> bir LiveRegion olarak:</span><span class="sxs-lookup"><span data-stu-id="ef159-144">You can also implement your <xref:System.Windows.Forms.UserControl> as a LiveRegion:</span></span>

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

<span data-ttu-id="ef159-145">**UIA bildirim olayları**</span><span class="sxs-lookup"><span data-stu-id="ef159-145">**UIA notification events**</span></span>

<span data-ttu-id="ef159-146">Windows 10 Fall Creators Update içinde tanıtılan UIA bildirim olayı kullanıcı Arabiriminde denetim karşılık gelen sahip gerek kalmadan olaylı sağladığınız müşteri adaylarını ekran okuyucusu yalnızca metne göre bir duyuru yapmak için bir UIA olayın tetiklenmesi uygulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-146">The UIA Notification event, introduced in Windows 10 Fall Creators Update, allows your app to raise a UIA event, which leads to Narrator simply making an announcement based on text you supply with the event, without the need to have a corresponding control in the UI.</span></span> <span data-ttu-id="ef159-147">Bazı senaryolarda, uygulamanızın erişilebilirliğini önemli ölçüde artırmak için basit bir yol budur.</span><span class="sxs-lookup"><span data-stu-id="ef159-147">In some scenarios, this is a straightforward way to dramatically improve the accessibility of your app.</span></span> <span data-ttu-id="ef159-148">Ayrıca uzun sürebilir bazı işlemin ilerlemesini bildirmek yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-148">In can also be useful to notify of the progress of some process that may take a long time.</span></span> <span data-ttu-id="ef159-149">UIA bildirim olaylar hakkında daha fazla bilgi için bkz. [Masaüstü uygulamanızın yeni bir kullanıcı Arabirimi bildirim olayı yararlanabilirsiniz?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span><span class="sxs-lookup"><span data-stu-id="ef159-149">For more information about UIA Notification Events, see [Can your desktop app leverage the new UI Notification event?](https://blogs.msdn.microsoft.com/winuiautomation/2017/11/08/can-your-desktop-app-leverage-the-new-uia-notification-event-in-order-to-have-narrator-say-exactly-what-your-customers-need/).</span></span>

<span data-ttu-id="ef159-150">Aşağıdaki örnek başlatır [bildirim olayı](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span><span class="sxs-lookup"><span data-stu-id="ef159-150">The following example raises the [Notification event](xref:System.Windows.Forms.AccessibleObject.RaiseAutomationNotification%2A):</span></span>

```csharp
MethodInfo raiseMethod = typeof(AccessibleObject).GetMethod("RaiseAutomationNotification");
if (raiseMethod != null) {
   raiseMethod.Invoke(progressBar1.AccessibilityObject, new object[3] {/*Other*/ 4, /*All*/ 2, "The progress is 50%." });
}
```

<span data-ttu-id="ef159-151">**Klavye Erişimi araç ipuçları**</span><span class="sxs-lookup"><span data-stu-id="ef159-151">**ToolTips on keyboard access**</span></span>

<span data-ttu-id="ef159-152">.NET Framework 4.7.2 ve denetim önceki sürümleri hedefleyen uygulamalarda [araç ipucu](xref:System.Windows.Forms.ToolTip) yalnızca pop'ye yukarı fare işaretçisi denetime taşıma tarafından tetiklenebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-152">In applications that target .NET Framework 4.7.2 and earlier versions, a control [tooltip](xref:System.Windows.Forms.ToolTip) can only be triggered to pop up by moving a mouse pointer into the control.</span></span> <span data-ttu-id="ef159-153">.NET Framework 4.8 ile başlayarak, bir klavye kullanıcı denetimi içeren veya içermeyen değiştirici tuşları SEKME tuşunu veya ok tuşlarını kullanarak odaklanarak bir denetimin araç ipucu tetikleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-153">Starting with .NET Framework 4.8, a keyboard user can trigger a control’s tooltip by focusing the control using a Tab key or arrow keys with or without modifier keys.</span></span> <span data-ttu-id="ef159-154">Bu belirli erişilebilirlik geliştirme ek gerektirir [AppContext anahtar](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span><span class="sxs-lookup"><span data-stu-id="ef159-154">This particular accessibility enhancement requires an additional [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md):</span></span>

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

<span data-ttu-id="ef159-155">Kullanıcının klavye ile bir düğme seçildiğinde aşağıdaki şekilde araç ipucu gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef159-155">The following figure shows the tooltip when the user has selected a button with the keyboard.</span></span>

![Kullanıcı bir düğme klavye ile gittiğinde araç ipucu](media/tooltip.png)

<a name="wpf48" />

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="ef159-157">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-157">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="ef159-158">WPF, .NET Framework 4.8 ile başlayarak, birkaç erişilebilirlik iyileştirmeleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef159-158">Starting with .NET Framework 4.8, WPF includes a number of accessibility improvements.</span></span>

<span data-ttu-id="ef159-159">**Ekran narrators öğeleri daraltılmış veya gizli görünürlük sayesinde artık bildir.**</span><span class="sxs-lookup"><span data-stu-id="ef159-159">**Screen narrators no longer announce elements with Collapsed or Hidden visibility**</span></span>

<span data-ttu-id="ef159-160">Daraltılmış ya da gizli görünürlük öğelerle artık ekran okuyucu tarafından bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-160">Elements with collapsed or hidden visibility are no longer announced by screen reader.</span></span> <span data-ttu-id="ef159-161">Bir görünürlüğünü öğelerle içeren kullanıcı arabirimleri <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> veya <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> kullanıcıya Duyuruldu ekran okuyucular tarafından adı.</span><span class="sxs-lookup"><span data-stu-id="ef159-161">User interfaces that contain elements with a Visibility of <xref:System.Windows.Visibility.Collapsed?displayProperty=nameWithType> or <xref:System.Windows.Visibility.Hidden?displayProperty=nameWithType> can be misrepresented by screen readers if they are announced to the user.</span></span> <span data-ttu-id="ef159-162">Ekran okuyucuları, artık bu öğeleri duyurmaktan, böylece .NET Framework 4.8 ile başlayarak, WPF artık daraltılmış ya da gizli öğeleri UIAutomation ağacının denetim görünümünde içerir.</span><span class="sxs-lookup"><span data-stu-id="ef159-162">Starting with .NET Framework 4.8, WPF no longer includes collapsed or hidden elements in the Control View of the UIAutomation tree, so the screen readers can no longer announce these elements.</span></span>

<span data-ttu-id="ef159-163">**Metin seçimi SelectionTextBrush özelliği olmayan donatıcı ile kullanmak için temel**</span><span class="sxs-lookup"><span data-stu-id="ef159-163">**SelectionTextBrush property for use with non-Adorner based text selection**</span></span>

<span data-ttu-id="ef159-164">.NET Framework'teki 4.7.2 WPF çizmek olanağı eklendi. <xref:System.Windows.Controls.TextBox> ve <xref:System.Windows.Controls.PasswordBox> donatıcı katmanı kullanmadan metin seçimi.</span><span class="sxs-lookup"><span data-stu-id="ef159-164">In the .NET Framework 4.7.2, WPF added the ability to draw <xref:System.Windows.Controls.TextBox> and <xref:System.Windows.Controls.PasswordBox> text selection without using the Adorner layer.</span></span> <span data-ttu-id="ef159-165">Bu senaryoda seçili metin ön plan rengi tarafından dikte <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-165">The foreground color of the selected text in this scenario was dictated by <xref:System.Windows.SystemColors.HighlightTextBrush?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ef159-166">.NET framework 4.8 yeni bir özellik ekler `SelectionTextBrush`, seçili metin için belirli fırça donatıcı olmayan kullanarak metin seçimi temel seçmek geliştiricilerin izin verir.</span><span class="sxs-lookup"><span data-stu-id="ef159-166">.NET Framework 4.8 adds a new property, `SelectionTextBrush`, that allows developers to select the specific brush for the selected text when using non-Adorner based text selection.</span></span> <span data-ttu-id="ef159-167">Bu özellik yalnızca çalışır <xref:System.Windows.Controls.Primitives.TextBoxBase>-denetimleri türetilmiş ve <xref:System.Windows.Controls.PasswordBox> etkin donatıcı tabanlı olmayan metin seçimi ile WPF uygulamalarında denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef159-167">This property works only on <xref:System.Windows.Controls.Primitives.TextBoxBase>-derived controls and the <xref:System.Windows.Controls.PasswordBox> control in WPF applications with non-Adorner-based text selection enabled.</span></span> <span data-ttu-id="ef159-168">Üzerinde çalışmaz <xref:System.Windows.Controls.RichTextBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef159-168">It does not work on the <xref:System.Windows.Controls.RichTextBox> control.</span></span> <span data-ttu-id="ef159-169">Donatıcı tabanlı olmayan metin seçimi etkin değilse, bu özellik yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="ef159-169">If non-Adorner-based text selection is not enabled, this property is ignored.</span></span>

<span data-ttu-id="ef159-170">Bu özelliği kullanmak için XAML kodunuza ekleyin ve uygun bir fırça veya bağlama kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef159-170">To use this property, simply add it to your XAML code and use the appropriate brush or binding.</span></span> <span data-ttu-id="ef159-171">Sonuçta elde edilen metin seçimi şöyle görünür:</span><span class="sxs-lookup"><span data-stu-id="ef159-171">The resulting text selection looks like this:</span></span>

![Kullanıcı bir düğme klavye ile gittiğinde araç ipucu](media/selectiontextbrush-property.png)

<span data-ttu-id="ef159-173">Kullanımını birleştirebilirsiniz `SelectionBrush` ve `SelectionTextBrush` özellikleri, herhangi bir arka plan ve ön plan oluşturmak için uygun bulduğunuz birleşimi rengi.</span><span class="sxs-lookup"><span data-stu-id="ef159-173">You can combine the use of the `SelectionBrush` and `SelectionTextBrush` properties to generate any background and foreground color combination that you deem appropriate.</span></span>

<span data-ttu-id="ef159-174">**UIAutomation ControllerFor özelliği için destek**</span><span class="sxs-lookup"><span data-stu-id="ef159-174">**Support for the UIAutomation ControllerFor property**</span></span>

<span data-ttu-id="ef159-175">UIAutomation'ın `ControllerFor` özelliği bu özelliği destekleyen Otomasyon öğe tarafından yönetilen Otomasyon öğeleri dizisi döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef159-175">UIAutomation’s `ControllerFor` property returns an array of automation elements that are manipulated by the automation element that supports this property.</span></span> <span data-ttu-id="ef159-176">Bu özellik, otomatik öneri erişilebilirlik için yaygın olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef159-176">This property is commonly used for Auto-suggest accessibility.</span></span> <span data-ttu-id="ef159-177">`ControllerFor` bir Otomasyon öğesi bir veya daha fazla parçadan uygulama kullanıcı Arabirimi veya Masaüstü etkilediğinde kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef159-177">`ControllerFor` is used when an automation element affects one or more segments of the application UI or the desktop.</span></span> <span data-ttu-id="ef159-178">Aksi takdirde, denetim işlemi etkisini UI öğeleriyle ilişkilendirmek zordur.</span><span class="sxs-lookup"><span data-stu-id="ef159-178">Otherwise, it is hard to associate the impact of the control operation with UI elements.</span></span> <span data-ttu-id="ef159-179">Bu özellik için bir değer sağlamak için denetim olanağı ekler `ControllerFor` özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef159-179">This feature adds the ability for controls to provide a value for the `ControllerFor` property.</span></span>

<span data-ttu-id="ef159-180">.NET framework 4.8 ekler yeni bir sanal yöntemle <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-180">.NET Framework 4.8 adds a new virtual method, <xref:System.Windows.Automation.Peers.AutomationPeer.GetControlledPeersCore?displayProperty=nameWithType?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-181">İçin bir değer sağlamak için `ControllerFor` özelliği, yalnızca bu yöntemi yok sayın ve dönüş bir `List<AutomationPeer>` bu tarafından değiştirildiği denetimler için <xref:System.Windows.Automation.Peers.AutomationPeer>:</span><span class="sxs-lookup"><span data-stu-id="ef159-181">To provide a value for the `ControllerFor` property, simply override this method and return a `List<AutomationPeer>` for the controls being manipulated by this <xref:System.Windows.Automation.Peers.AutomationPeer>:</span></span>

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

<span data-ttu-id="ef159-182">**Klavye Erişimi araç ipuçları**</span><span class="sxs-lookup"><span data-stu-id="ef159-182">**Tooltips on keyboard access**</span></span>

<span data-ttu-id="ef159-183">Yalnızca kullanıcı bir denetimin üzerine fare imlecini geldiğinde .NET Framework 4.7.2 ve önceki sürümlerinde, araç ipuçlarının görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ef159-183">In .NET Framework 4.7.2 and earlier versions, tooltips display only when the user hovers the mouse cursor over a control.</span></span> <span data-ttu-id="ef159-184">.NET Framework 4.8, araç ipuçlarının klavye odağı üzerinde yanı sıra bir klavye kısayolu aracılığıyla görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ef159-184">In .NET Framework 4.8, tooltips also display on keyboard focus, as well as via a keyboard shortcut.</span></span>

<span data-ttu-id="ef159-185">Bu özelliği etkinleştirmek için bir uygulama .NET Framework 4.8 hedef veya kullanarak katılımı gereken `Switch.UseLegacyAccessibilityFeatures.3` ve `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) anahtarlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-185">To enable this feature, an application needs to target .NET Framework 4.8 or opt-in by using the `Switch.UseLegacyAccessibilityFeatures.3` and `Switch.UseLegacyToolTipDisplay` [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches.</span></span> <span data-ttu-id="ef159-186">Örnek bir uygulama yapılandırma dosyası verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef159-186">The following is a sample application configuration file:</span></span>

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

<span data-ttu-id="ef159-187">Denetimin klavye odağı aldığında etkinleştirildikten sonra bir araç ipucu içeren tüm denetimleri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="ef159-187">Once enabled, all controls that contain a tooltip display it once the control receives keyboard focus.</span></span> <span data-ttu-id="ef159-188">Araç ipucu, saati veya klavye odağı değiştiğinde üzerinden kapatılabilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-188">The tooltip can be dismissed over time or when the keyboard focus changes.</span></span> <span data-ttu-id="ef159-189">Kullanıcılar ayrıca araç ipucunu el ile yeni klavye kısayolu, Ctrl + Shift + F10 kullanarak yok sayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-189">Users can also dismiss the tooltip manually by using a new keyboard shortcut, Ctrl + Shift + F10.</span></span> <span data-ttu-id="ef159-190">Araç İpucu kapatıldı sonra tekrar aynı klavye kısayolunu kullanarak görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-190">Once the tooltip has been dismissed it can be displayed again by using the same keyboard shortcut.</span></span>

> [!NOTE]
> <span data-ttu-id="ef159-191">[Şerit araç ipuçları](xref:System.Windows.Controls.Ribbon.RibbonToolTip) üzerinde <xref:System.Windows.Controls.Ribbon.Ribbon> denetimleri klavye odaklanmak Göster olmaz; bunlar yalnızca klavye kısayolunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="ef159-191">[Ribbon tooltips](xref:System.Windows.Controls.Ribbon.RibbonToolTip) on <xref:System.Windows.Controls.Ribbon.Ribbon> controls won’t show on keyboard focus; they only show via the keyboard shortcut.</span></span>

<span data-ttu-id="ef159-192">**SizeOfSet ve PositionInSet UIAutomation özellikleri için destek eklendi**</span><span class="sxs-lookup"><span data-stu-id="ef159-192">**Added Support for SizeOfSet and PositionInSet UIAutomation properties**</span></span>

<span data-ttu-id="ef159-193">Windows 10, iki yeni UIAutomation özellikleri, tanıtılan `SizeOfSet` ve `PositionInSet`, küme içindeki öğelerin sayısını tanımlamak için uygulamalar tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ef159-193">Windows 10 introduced two new UIAutomation properties, `SizeOfSet` and `PositionInSet`, which are used by applications to describe the count of items in a set.</span></span> <span data-ttu-id="ef159-194">Ekran okuyucular gibi UIAutomation istemci uygulamalarını uygulamanın bu özellikler için sorgu ve duyurmaktan uygulamanın UI doğru bir gösterimidir.</span><span class="sxs-lookup"><span data-stu-id="ef159-194">UIAutomation client applications such as screen readers can then query an application for these properties and announce an accurate representation of the application’s UI.</span></span>

<span data-ttu-id="ef159-195">WPF, .NET Framework 4.8 ile başlayarak, UIAutomation WPF uygulamalarında bu iki özelliği sunar.</span><span class="sxs-lookup"><span data-stu-id="ef159-195">Starting with .NET Framework 4.8, WPF  exposes these two properties to UIAutomation in WPF applications.</span></span> <span data-ttu-id="ef159-196">Bu iki şekilde gerçekleştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="ef159-196">This can be accomplished in two ways:</span></span>

- <span data-ttu-id="ef159-197">Bağımlılık özellikleri kullanarak.</span><span class="sxs-lookup"><span data-stu-id="ef159-197">By using dependency properties.</span></span>

  <span data-ttu-id="ef159-198">WPF iki yeni bağımlılık özellikleri ekler <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> ve <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-198">WPF adds two new dependency properties, <xref:System.Windows.Automation.AutomationProperties.SizeOfSet?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.PositionInSet?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-199">Bir geliştirici, XAML, değerleri ayarlamak için kullanabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="ef159-199">A developer can use XAML to set their values:</span></span>

  ```xaml
  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="1">Button 1</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="2">Button 2</Button>

  <Button AutomationProperties.SizeOfSet="3"
    AutomationProperties.PositionInSet="3">Button 3</Button>
  ```

- <span data-ttu-id="ef159-200">AutomationPeer sanal yöntemleri geçersiz kılarak.</span><span class="sxs-lookup"><span data-stu-id="ef159-200">By overriding AutomationPeer virtual methods.</span></span>

  <span data-ttu-id="ef159-201"><xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> Ve <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> sanal yöntemler olan AutomationPeer sınıfa eklenir.</span><span class="sxs-lookup"><span data-stu-id="ef159-201">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetSizeOfSetCore> and <xref:System.Windows.Automation.Peers.AutomationPeer.GetPositionInSetCore> virtual methods been added to the AutomationPeer class.</span></span> <span data-ttu-id="ef159-202">Bir geliştirici için değerleri sağlayabileceğinizi `SizeOfSet` ve `PositionInSet` aşağıdaki örnekte gösterildiği gibi bu yöntem geçersiz kılma tarafından:</span><span class="sxs-lookup"><span data-stu-id="ef159-202">A developer can provide values for `SizeOfSet` and `PositionInSet` by overriding these methods, as shown in the following example:</span></span>

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

<span data-ttu-id="ef159-203">Ayrıca, öğeler <xref:System.Windows.Controls.ItemsControl> örnekler bir değer geliştiriciden bu özellikleri başka bir işlem olmadan otomatik olarak sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-203">In addition, items in <xref:System.Windows.Controls.ItemsControl> instances provide a value for these properties automatically without additional action from the developer.</span></span> <span data-ttu-id="ef159-204">Varsa bir <xref:System.Windows.Controls.ItemsControl> olan gruplandırılmış, Grup koleksiyonu bir küme olarak temsil edilir ve her grup konumuna grubunun boyutunu yanı sıra o grup dahilindeki sağlama o grup içindeki her öğe ayrı bir küme olarak sayılır.</span><span class="sxs-lookup"><span data-stu-id="ef159-204">If an <xref:System.Windows.Controls.ItemsControl> is grouped, the collection of groups is represented as a set, and each group is counted as a separate set, with each item inside that group providing its position inside that group as well as the size of the group.</span></span> <span data-ttu-id="ef159-205">Otomatik değerleri sanallaştırma tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="ef159-205">Automatic values are not affected by virtualization.</span></span> <span data-ttu-id="ef159-206">Bir öğe gerçekleşen değil olsa bile, hala kümesinin toplam boyutu doğru kabul edilir ve kendi Eşdüzey öğeleri kümesini konumu etkiler.</span><span class="sxs-lookup"><span data-stu-id="ef159-206">Even if an item is not realized, it is still counted toward the total size of the set and affects the position in the set of its sibling items.</span></span>

<span data-ttu-id="ef159-207">Uygulama .NET Framework 4.8 hedefliyorsa otomatik değerleri yalnızca sağlanır.</span><span class="sxs-lookup"><span data-stu-id="ef159-207">Automatic values are only provided if the application targets .NET Framework 4.8.</span></span> <span data-ttu-id="ef159-208">.NET Framework'ün önceki bir sürümünü hedefleyen uygulamalar için ayarladığınız `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtar](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)aşağıdaki App.config dosyasında gösterildiği gibi:</span><span class="sxs-lookup"><span data-stu-id="ef159-208">For applications that target an earlier version of the .NET Framework, you can set the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md), as shown in the following App.config file:</span></span>

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

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="ef159-209">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="ef159-209">Windows Workflow Foundation (WF) workflow designer</span></span>

<span data-ttu-id="ef159-210">İş Akışı Tasarımcısı ' .NET Framework 4.8 aşağıdaki değişiklikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-210">The workflow designer includes the following changes in .NET Framework 4.8:</span></span>

- <span data-ttu-id="ef159-211">Ekran okuyucu kullanan kullanıcılar FlowSwitch durum etiketi iyileştirmeleri görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ef159-211">Users using Narrator will see improvements in FlowSwitch case labels.</span></span>

- <span data-ttu-id="ef159-212">Ekran okuyucu kullanan kullanıcılar düğmesi açıklamalarında geliştirmeleri göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-212">Users using Narrator will see improvements in button descriptions.</span></span>

- <span data-ttu-id="ef159-213">Yüksek karşıtlıklı tema seçen kullanıcılar iş akışı Tasarımcısı gibi öğeleri ve odak öğeleri için kullanılan daha belirgin seçim kutuları arasında daha iyi kontrast denetimlerini ve görünürlük geliştirmeleri göreceksiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-213">Users who choose High Contrast themes will see improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

<span data-ttu-id="ef159-214">Uygulamanızı .NET Framework 4.7.2 veya önceki bir sürümü hedefliyorsa, ayarlayarak bu değişiklikleri seçebilirsiniz `Switch.UseLegacyAccessibilityFeatures.3` [AppContext anahtar](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) için `false` , uygulama yapılandırma dosyasında.</span><span class="sxs-lookup"><span data-stu-id="ef159-214">If your application targets .NET Framework 4.7.2 or an earlier version, you can opt into these changes by setting the `Switch.UseLegacyAccessibilityFeatures.3` [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to `false` in your application configuration file.</span></span> <span data-ttu-id="ef159-215">Daha fazla bilgi için [erişilebilirlik geliştirmeleri avantajlarından yararlanmakla](#taking-advantage-of-accessibility-enhancements) bu makaledeki bir bölüm.</span><span class="sxs-lookup"><span data-stu-id="ef159-215">For more information, see the [Taking advantage of accessibility enhancements](#taking-advantage-of-accessibility-enhancements) section in this article.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-472"></a><span data-ttu-id="ef159-216">Erişilebilirlik 4.7.2 .NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="ef159-216">What's new in accessibility in .NET Framework 4.7.2</span></span>

<span data-ttu-id="ef159-217">.NET framework 4.7.2 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-217">.NET Framework 4.7.2 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="ef159-218">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef159-218">Windows Forms</span></span>](#winforms472)

- [<span data-ttu-id="ef159-219">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-219">Windows Presentation Foundation (WPF)</span></span>](#wpf472)

<a name="winforms472"></a>

### <a name="windows-forms"></a><span data-ttu-id="ef159-220">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef159-220">Windows Forms</span></span>

<span data-ttu-id="ef159-221">**Yüksek karşıtlıklı Tema renkleri işletim sistemi tarafından tanımlanan**</span><span class="sxs-lookup"><span data-stu-id="ef159-221">**OS-defined colors in High Contrast themes**</span></span>

<span data-ttu-id="ef159-222">.NET Framework 4.7.2 ile başlayarak, Windows Forms yüksek karşıtlıklı tema işletim sistemi tarafından tanımlanan renk kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef159-222">Starting with .NET Framework 4.7.2, Windows Forms uses colors defined by the operating system in High Contrast themes.</span></span> <span data-ttu-id="ef159-223">Bu, aşağıdaki denetimlerini etkiler:</span><span class="sxs-lookup"><span data-stu-id="ef159-223">This affects the following controls:</span></span>

- <span data-ttu-id="ef159-224">Aşağı açılan okunu <xref:System.Windows.Forms.ToolStripDropDownButton> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef159-224">The drop-down arrow of the <xref:System.Windows.Forms.ToolStripDropDownButton> control.</span></span>

- <span data-ttu-id="ef159-225"><xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> ile denetimleri <xref:System.Windows.Forms.ButtonBase.FlatStyle> kümesine <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> veya <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-225">The <xref:System.Windows.Forms.Button>, <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with <xref:System.Windows.Forms.ButtonBase.FlatStyle> set to <xref:System.Windows.Forms.FlatStyle.Flat?displayProperty=nameWithType> or <xref:System.Windows.Forms.FlatStyle.Popup?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-226">Daha önce seçilen metin ve arkaplan renklerini değil çakışan ve okunması zor.</span><span class="sxs-lookup"><span data-stu-id="ef159-226">Previously, selected text and background colors were not contrasting and were hard to read.</span></span>

- <span data-ttu-id="ef159-227">Denetimleri içinde yer alan bir <xref:System.Windows.Forms.GroupBox> olan kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="ef159-227">Controls contained within a <xref:System.Windows.Forms.GroupBox> that has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="ef159-228"><xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, Ve <xref:System.Windows.Forms.ToolStripDropDownButton> artan parlaklık bir Karşıtlık oranı yüksek karşıtlık modunda olan denetimler.</span><span class="sxs-lookup"><span data-stu-id="ef159-228">The <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripComboBox>, and <xref:System.Windows.Forms.ToolStripDropDownButton> controls, which have an increased luminosity contrast ratio in High Contrast Mode.</span></span>

- <span data-ttu-id="ef159-229"><xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> Özelliği <xref:System.Windows.Forms.DataGridViewLinkCell>.</span><span class="sxs-lookup"><span data-stu-id="ef159-229">The <xref:System.Windows.Forms.DataGridViewLinkCell.LinkColor> property of the <xref:System.Windows.Forms.DataGridViewLinkCell>.</span></span>

<span data-ttu-id="ef159-230">**Ekran Okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="ef159-230">**Narrator improvements**</span></span>

<span data-ttu-id="ef159-231">.NET Framework 4.7.2 ile başlayarak, ekran okuyucusu desteği gibi geliştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef159-231">Starting with .NET Framework 4.7.2, Narrator support is enhanced as follows:</span></span>

- <span data-ttu-id="ef159-232">Değerini duyuruyor <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> Duyurusu metni hareketlendiremezsiniz bir <xref:System.Windows.Forms.ToolStripMenuItem>.</span><span class="sxs-lookup"><span data-stu-id="ef159-232">It announces the value of the <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeys?displayProperty=nameWithType> property when announcing the text of a <xref:System.Windows.Forms.ToolStripMenuItem>.</span></span>

- <span data-ttu-id="ef159-233">Ne zaman gösteren bir <xref:System.Windows.Forms.ToolStripMenuItem> sahip kendi <xref:System.Windows.Forms.Control.Enabled> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="ef159-233">It indicates when a <xref:System.Windows.Forms.ToolStripMenuItem> has its <xref:System.Windows.Forms.Control.Enabled> property set to `false`.</span></span>

- <span data-ttu-id="ef159-234">Onay kutusunun durumunu hakkında geri bildirim sağlar, <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> özelliği `true`.</span><span class="sxs-lookup"><span data-stu-id="ef159-234">It gives feedback on the state of a check box when the <xref:System.Windows.Forms.ListView.CheckBoxes?displayProperty=nameWithType> property is set to `true`.</span></span>

- <span data-ttu-id="ef159-235">Okuyucu'nın tarama modu odak sipariş ClickOnce indirme iletişim kutusu penceresine denetimleri visual sırasını tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef159-235">Narrator's Scan Mode focus order is consistent with the visual order of the controls on the ClickOnce download dialog window.</span></span>

<span data-ttu-id="ef159-236">**DataGridView geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="ef159-236">**DataGridView improvements**</span></span>

<span data-ttu-id="ef159-237">4\.7.2, .NET Framework ile başlayarak <xref:System.Windows.Forms.DataGridView> denetimi aşağıdaki erişilebilirlik geliştirmeleri kullanıma sunulan:</span><span class="sxs-lookup"><span data-stu-id="ef159-237">Starting with .NET Framework 4.7.2, the <xref:System.Windows.Forms.DataGridView> control has introduced the following accessibility improvements:</span></span>

- <span data-ttu-id="ef159-238">Klavyeyi kullanarak satır sıralanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-238">Rows can be sorted using the keyboard.</span></span> <span data-ttu-id="ef159-239">Bir kullanıcı, geçerli bir sütuna göre sıralamak için F3 tuşuna kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-239">A user can use the F3 key in order to sort by the current column.</span></span>

- <span data-ttu-id="ef159-240">Zaman <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> ayarlanır <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, sütun üst bilgisinin geçerli sütunun hücre geçerli satırda aracılığıyla kullanıcı sekmeler olarak belirtmek için rengi değişir.</span><span class="sxs-lookup"><span data-stu-id="ef159-240">When the <xref:System.Windows.Forms.DataGridView.SelectionMode?displayProperty=nameWithType> is set to <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect?displayProperty=nameWithType>, the column header changes color to indicate the current column as the user tabs through the cells in the current row.</span></span>

- <span data-ttu-id="ef159-241"><xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> Özelliği bir <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> doğru üst denetimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef159-241">The <xref:System.Windows.Forms.AccessibleObject.Parent?displayProperty=nameWithType> property of a  <xref:System.Windows.Forms.DataGridViewLinkCell.DataGridViewLinkCellAccessibleObject?displayProperty=nameWithType> returns the correct parent control.</span></span>

<span data-ttu-id="ef159-242">**Geliştirilmiş görsel ipuçları**</span><span class="sxs-lookup"><span data-stu-id="ef159-242">**Improved visual cues**</span></span>

- <span data-ttu-id="ef159-243"><xref:System.Windows.Forms.RadioButton> Ve <xref:System.Windows.Forms.CheckBox> boş denetimleriyle <xref:System.Windows.Forms.ButtonBase.Text> odağı aldıklarında bir odak göstergesi görüntü özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef159-243">The <xref:System.Windows.Forms.RadioButton> and <xref:System.Windows.Forms.CheckBox> controls with an empty <xref:System.Windows.Forms.ButtonBase.Text> property  display a focus indicator when they receive the focus.</span></span>

<span data-ttu-id="ef159-244">**Gelişmiş özellik Kılavuzu desteği**</span><span class="sxs-lookup"><span data-stu-id="ef159-244">**Improved Property Grid Support**</span></span>

- <span data-ttu-id="ef159-245"><xref:System.Windows.Forms.PropertyGrid> Alt öğeleri artık dönüş denetleyen bir `true` için <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> PropertyGrid öğe etkinleştirildiğinde özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef159-245">The <xref:System.Windows.Forms.PropertyGrid> control child elements now return a `true` for the  <xref:System.Windows.Automation.ValuePattern.IsReadOnlyProperty> property only when a PropertyGrid element is enabled.</span></span>

- <span data-ttu-id="ef159-246"><xref:System.Windows.Forms.PropertyGrid> Alt öğeleri iade denetleyen bir `false` için <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> özelliğine yalnızca bir PropertyGrid öğesi kullanıcı tarafından değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-246">The <xref:System.Windows.Forms.PropertyGrid> control child elements return a `false` for the <xref:System.Windows.Automation.AutomationElement.IsEnabledProperty> property only when a PropertyGrid element can be changed by the user.</span></span>

<span data-ttu-id="ef159-247">**Geliştirilmiş klavye gezintisi**</span><span class="sxs-lookup"><span data-stu-id="ef159-247">**Improved keyboard navigation**</span></span>

- <span data-ttu-id="ef159-248"><xref:System.Windows.Forms.ToolStripButton> Denetimi içinde bulunan zaman odağı sağlar bir <xref:System.Windows.Forms.ToolStripPanel> olan <xref:System.Windows.Forms.ToolStripPanel.TabStop> özelliği ayarlayın `true`</span><span class="sxs-lookup"><span data-stu-id="ef159-248">The <xref:System.Windows.Forms.ToolStripButton> control allows focus when contained within a <xref:System.Windows.Forms.ToolStripPanel> that has the <xref:System.Windows.Forms.ToolStripPanel.TabStop> property set to `true`</span></span>

<a name="wpf472"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="ef159-249">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-249">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="ef159-250">**Değişiklikleri için onay kutusunu ve RadioButton denetimleri**</span><span class="sxs-lookup"><span data-stu-id="ef159-250">**Changes to the CheckBox and RadioButton controls**</span></span>

<span data-ttu-id="ef159-251">.NET Framework 4.7.1 ve önceki sürümlerinde, WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> ve <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> denetimleri, tutarsız ve klasik ve yüksek karşıtlık temalar, yanlış odak görsel sahiptir.</span><span class="sxs-lookup"><span data-stu-id="ef159-251">In .NET Framework 4.7.1 and earlier versions, the WPF <xref:System.Windows.Controls.CheckBox?displayProperty=nameWIthType> and <xref:System.Windows.Controls.RadioButton?displayProperty=nameWIthType> controls have inconsistent and, in Classic and High Contrast themes, incorrect focus visuals.</span></span>  <span data-ttu-id="ef159-252">Bu sorunlar burada denetimleri herhangi bir içerik kümesi olmayan durumlarda oluşur.</span><span class="sxs-lookup"><span data-stu-id="ef159-252">These issues occur in cases where the controls do not have any content set.</span></span>  <span data-ttu-id="ef159-253">Bu tema kafa karıştırıcı ve odak görsel arasında geçiş görmek sabit yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-253">This can make the transition between themes confusing and the focus visual hard to see.</span></span>

<span data-ttu-id="ef159-254">.NET Framework'teki 4.7.2, bu görsellerin temalar arasında daha tutarlı ve klasik ve yüksek karşıtlıklı tema daha kolay görünür.</span><span class="sxs-lookup"><span data-stu-id="ef159-254">In .NET Framework 4.7.2, these visuals are now more consistent across themes and more easily visible in Classic and High Contrast themes.</span></span>

<span data-ttu-id="ef159-255">**Barındırılan bir WPF uygulamasında WinForms denetimleri**</span><span class="sxs-lookup"><span data-stu-id="ef159-255">**WinForms controls hosted in a WPF application**</span></span>

<span data-ttu-id="ef159-256">Bu katmandaki ilk veya son denetim WPF ise .NET Framework 4.7.1 ve önceki sürümlerinde WPF uygulamasında barındırılan WinForms denetimi için WinForms katman dışında kullanıcılar sekmesinde uygulanamadı <xref:System.Windows.Forms.Integration.ElementHost> denetimi.</span><span class="sxs-lookup"><span data-stu-id="ef159-256">For WinForms control hosted in a WPF application in .NET Framework 4.7.1 and earlier versions, users couldn't tab out of the WinForms layer if the first or last control in that layer is the WPF <xref:System.Windows.Forms.Integration.ElementHost> control.</span></span> <span data-ttu-id="ef159-257">.NET Framework'teki 4.7.2, kullanıcılar artık dışında WinForms katman sekmesinde olanağına sahip olursunuz.</span><span class="sxs-lookup"><span data-stu-id="ef159-257">In .NET Framework 4.7.2, users are now able to tab out of the WinForms layer.</span></span>

<span data-ttu-id="ef159-258">Ancak, hiçbir zaman WinForms katman kaçış odaklanmak otomatik uygulamaları artık beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-258">However, automated applications that rely on focus never escaping the WinForms layer may no longer work as expected.</span></span>

## <a name="whats-new-in-accessibility-in-net-framework-471"></a><span data-ttu-id="ef159-259">.NET Framework 4.7.1 erişilebilirlik yenilikleri</span><span class="sxs-lookup"><span data-stu-id="ef159-259">What's new in accessibility in .NET Framework 4.7.1</span></span>

<span data-ttu-id="ef159-260">.NET framework 4.7.1 aşağıdaki alanlarda yeni erişilebilirlik özellikleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-260">.NET Framework 4.7.1 includes new accessibility features in the following areas:</span></span>

- [<span data-ttu-id="ef159-261">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-261">Windows Presentation Foundation (WPF)</span></span>](#wpf471)

- [<span data-ttu-id="ef159-262">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef159-262">Windows Forms</span></span>](#winforms471)

- [<span data-ttu-id="ef159-263">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="ef159-263">ASP.NET web controls</span></span>](#aspnet471)

- [<span data-ttu-id="ef159-264">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="ef159-264">.NET SDK Tools</span></span>](#tools471)

- [<span data-ttu-id="ef159-265">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="ef159-265">Windows Workflow Foundation (WF) Workflow Designer</span></span>](#wf471)

<a name="wpf471"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="ef159-266">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ef159-266">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="ef159-267">**Ekran Okuyucusu geliştirmeleri**</span><span class="sxs-lookup"><span data-stu-id="ef159-267">**Screen reader improvements**</span></span>

<span data-ttu-id="ef159-268">Erişilebilirlik geliştirmeleri etkinleştirilirse, .NET Framework 4.7.1 ekran okuyucular etkileyen aşağıdaki geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-268">If accessibility improvements are enabled, .NET Framework 4.7.1 includes the following enhancements that affect screen readers:</span></span>

- <span data-ttu-id="ef159-269">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.Expander> denetimleri düğme olarak ekran okuyucular tarafından Duyuruldu.</span><span class="sxs-lookup"><span data-stu-id="ef159-269">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.Expander> controls were announced by screen readers as buttons.</span></span> <span data-ttu-id="ef159-270">.NET Framework 4.7.1 ile başlayarak, bunlar Genişletilebilir/daraltılabilir gruplar olarak doğru şekilde bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-270">Starting with .NET Framework 4.7.1, they are correctly announced as expandable/collapsible groups.</span></span>

- <span data-ttu-id="ef159-271">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.DataGridCell> denetimleri ekran okuyucular tarafından bildirilen "özel"</span><span class="sxs-lookup"><span data-stu-id="ef159-271">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.DataGridCell> controls were announced by screen readers as “custom.”</span></span> <span data-ttu-id="ef159-272">.NET Framework 4.7.1 ile başlayarak, yöneticiler artık doğru şekilde veri kılavuz hücresi (yerelleştirilmiş) bildirilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-272">Starting with .NET Framework 4.7.1, they are now correctly announced as data grid cell (localized).</span></span>

- <span data-ttu-id="ef159-273">.NET Framework 4.7.1 ile başlayarak, adı düzenlenebilir bir ekran okuyucular duyurmaktan <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="ef159-273">Starting with .NET Framework 4.7.1, screen readers announce the name of an editable <xref:System.Windows.Controls.ComboBox>.</span></span>

- <span data-ttu-id="ef159-274">.NET Framework 4.7 ve önceki sürümlerinde, <xref:System.Windows.Controls.PasswordBox> denetimleri veya "öğesi Görünümü'nde" olarak bildirilen olduğu Aksi takdirde yanlış bir davranışı.</span><span class="sxs-lookup"><span data-stu-id="ef159-274">In .NET Framework 4.7 and earlier versions, <xref:System.Windows.Controls.PasswordBox> controls were announced as “no item in view” or had otherwise incorrect behavior.</span></span> <span data-ttu-id="ef159-275">.NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef159-275">This issue is fixed starting with .NET Framework 4.7.1.</span></span>

<span data-ttu-id="ef159-276">**UIAutomation LiveRegion desteği**</span><span class="sxs-lookup"><span data-stu-id="ef159-276">**UIAutomation LiveRegion support**</span></span>

<span data-ttu-id="ef159-277">Ekran okuyucular ekran okuyucusu Yardım kişiler gibi bir uygulama kullanıcı Arabirimi içeriği genellikle metin okuma odağa sahip kullanıcı Arabirimi içeriği çıktı tarafından okuyun.</span><span class="sxs-lookup"><span data-stu-id="ef159-277">Screen readers such as Narrator help people read the UI contents of an application, usually by text-to-speech output of the UI content that has the focus.</span></span> <span data-ttu-id="ef159-278">Ancak, bir kullanıcı Arabirimi öğesi değiştirir ve odağı yok, Kullanıcı bildirim değil ve önemli bilgiler eksik.</span><span class="sxs-lookup"><span data-stu-id="ef159-278">However, if a UI element changes and does not have the focus, the user may not be notified and may miss important information.</span></span> <span data-ttu-id="ef159-279">Bu sorunu çözme sırasında Canlı bölge hedeflenir.</span><span class="sxs-lookup"><span data-stu-id="ef159-279">Live regions aim at solving this problem.</span></span> <span data-ttu-id="ef159-280">Bir geliştirici, ekran okuyucu veya bir kullanıcı Arabirimi öğesi için önemli bir değişiklik yapılmadığını diğer UIAutomation istemci bildirmek için bunları kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-280">A developer can use them to inform the screen reader or any other UIAutomation client that an important change has been made to a UI element.</span></span> <span data-ttu-id="ef159-281">Ekran Okuyucu sonra nasıl ve ne zaman karar verebilirsiniz kullanıcıya bu değişikliği bildirmek için.</span><span class="sxs-lookup"><span data-stu-id="ef159-281">The screen reader can then decide how and when to inform the user of this change.</span></span>

<span data-ttu-id="ef159-282">Canlı bölge desteklemek için aşağıdaki API'leri için WPF eklenmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef159-282">To support live regions, the following APIs have been added to WPF:</span></span>

- <span data-ttu-id="ef159-283"><xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> tanımlamak alanları **LiveSetting** özelliği ve **LiveRegionChanged** olay.</span><span class="sxs-lookup"><span data-stu-id="ef159-283">The <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveSettingProperty?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationElementIdentifiers.LiveRegionChangedEvent?displayProperty=nameWithType> fields, which identify the **LiveSetting** property and the **LiveRegionChanged** event.</span></span> <span data-ttu-id="ef159-284">XAML kullanılarak ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-284">They can be set by using XAML.</span></span>

- <span data-ttu-id="ef159-285">**AutomationProperties.LiveSetting** ekran okuyucu önem UI değişikliğinin kullanıcıya bildirir özelliğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="ef159-285">The **AutomationProperties.LiveSetting** attached property, which informs the screen reader of the importance of the UI change to the user.</span></span>

- <span data-ttu-id="ef159-286"><xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> Tanımlayan özellik **AutomationProperties.LiveSetting** ekli özellik.</span><span class="sxs-lookup"><span data-stu-id="ef159-286">The <xref:System.Windows.Automation.AutomationProperties.LiveSettingProperty?displayProperty=nameWithType> property, which identifies the **AutomationProperties.LiveSetting** attached property.</span></span>

- <span data-ttu-id="ef159-287"><xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> Sağlamak için geçersiz kılınabilir bir yöntemi, bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="ef159-287">The <xref:System.Windows.Automation.Peers.AutomationPeer.GetLiveSettingCore%2A?displayProperty=nameWithType> method, which can be overridden to provide a **LiveSetting** value.</span></span>

- <span data-ttu-id="ef159-288"><xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> Ve <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> almanıza ve ayarlamanıza yöntemleri bir **LiveSetting** değeri.</span><span class="sxs-lookup"><span data-stu-id="ef159-288">The <xref:System.Windows.Automation.AutomationProperties.GetLiveSetting%2A?displayProperty=nameWithType> and <xref:System.Windows.Automation.AutomationProperties.SetLiveSetting%2A?displayProperty=nameWithType> methods, which get and set a **LiveSetting** value.</span></span>

- <span data-ttu-id="ef159-289"><xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> Aşağıdaki olası tanımlayan sabit listesi **LiveSetting** değerleri:</span><span class="sxs-lookup"><span data-stu-id="ef159-289">The <xref:System.Windows.Automation.AutomationLiveSetting?displayProperty=nameWithType> enumeration, which defines the following possible **LiveSetting** values:</span></span>

  - <span data-ttu-id="ef159-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-290"><xref:System.Windows.Automation.AutomationLiveSetting.Off?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-291">Canlı bölge içeriğini değiştiyse öğesi bildirimleri göndermez.</span><span class="sxs-lookup"><span data-stu-id="ef159-291">The element does not send notifications if the content of the live region has changed.</span></span>
  - <span data-ttu-id="ef159-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-292"><xref:System.Windows.Automation.AutomationLiveSetting.Polite?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-293">Canlı bölge içeriğini değiştiyse öğe interruptive olmayan bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="ef159-293">The element sends non-interruptive notifications if the content of the live region has changed.</span></span>

  - <span data-ttu-id="ef159-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ef159-294"><xref:System.Windows.Automation.AutomationLiveSetting.Assertive?displayProperty=nameWithType>.</span></span> <span data-ttu-id="ef159-295">Canlı bölge içeriğini değiştiyse öğe interruptive bildirimleri gönderir.</span><span class="sxs-lookup"><span data-stu-id="ef159-295">The element sends interruptive notifications if the content of the live region has changed.</span></span>

<span data-ttu-id="ef159-296">Ayarlayarak bir LiveRegion oluşturabilirsiniz **AutomationProperties.LiveSetting** aşağıdaki örnekte gösterildiği gibi ilgi alanı, öğe özelliği:</span><span class="sxs-lookup"><span data-stu-id="ef159-296">You can create a LiveRegion by setting the **AutomationProperties.LiveSetting** property on the element of interest, as shown in the following example:</span></span>

```xaml
<TextBlock Name="myTextBlock" AutomationProperties.LiveSetting="Assertive">announcement</TextBlock>
```

<span data-ttu-id="ef159-297">Canlı bölge verileri değiştirir ve ekran okuyucu bildirmeniz gerekir, siz açıkça bir olay aşağıdaki örnekte gösterildiği gibi neden olmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ef159-297">When the data in the live region changes and you need to inform a screen reader, you explicitly raise an event, as shown in the following sample.</span></span>

```csharp
var peer = FrameworkElementAutomationPeer.FromElement(myTextBlock);

peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged);
```

```vb
Dim peer = FrameworkElementAutomationPeer.FromElement(myTextBlock)
peer.RaiseAutomationEvent(AutomationEvents.LiveRegionChanged)

```

<span data-ttu-id="ef159-298">**Yüksek Karşıtlık**</span><span class="sxs-lookup"><span data-stu-id="ef159-298">**High contrast**</span></span>

<span data-ttu-id="ef159-299">.NET Framework 4.7.1 ile başlayarak, çeşitli WPF denetimleri için yüksek karşıtlık geliştirmeleri yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ef159-299">Starting with .NET Framework 4.7.1, improvements in high contrast have been made to various WPF controls.</span></span> <span data-ttu-id="ef159-300">Bunlar artık ne zaman görülebilir <xref:System.Windows.SystemParameters.HighContrast%2A> tema ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ef159-300">They are now visible when the <xref:System.Windows.SystemParameters.HighContrast%2A> theme is set.</span></span> <span data-ttu-id="ef159-301">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ef159-301">These include:</span></span>

- <span data-ttu-id="ef159-302"><xref:System.Windows.Controls.Expander> Denetimi</span><span class="sxs-lookup"><span data-stu-id="ef159-302"><xref:System.Windows.Controls.Expander> control</span></span>

  <span data-ttu-id="ef159-303">Görseli odak <xref:System.Windows.Controls.Expander> denetimidir artık görünür.</span><span class="sxs-lookup"><span data-stu-id="ef159-303">The focus visual for the  <xref:System.Windows.Controls.Expander> control is now visible.</span></span> <span data-ttu-id="ef159-304">Klavye görseller için <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, ve <xref:System.Windows.Controls.RadioButton> denetimleri görünür de.</span><span class="sxs-lookup"><span data-stu-id="ef159-304">The keyboard visuals for <xref:System.Windows.Controls.ComboBox>,<xref:System.Windows.Controls.ListBox>, and <xref:System.Windows.Controls.RadioButton> controls are visible as well.</span></span> <span data-ttu-id="ef159-305">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-305">For example:</span></span>

  <span data-ttu-id="ef159-306">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-306">Before:</span></span> 

  ![Erişilebilirlik geliştirmeleri önce odaklanılan genişletici denetimi](media/expander-before.png)

  <span data-ttu-id="ef159-308">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-308">After:</span></span> 

  ![Erişilebilirlik geliştirmeleri sonra odaklanılan genişletici denetimi](media/expander-after.png)

- <span data-ttu-id="ef159-310"><xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri</span><span class="sxs-lookup"><span data-stu-id="ef159-310"><xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls</span></span>

  <span data-ttu-id="ef159-311">Metinde <xref:System.Windows.Controls.CheckBox> ve <xref:System.Windows.Controls.RadioButton> denetimleri, yüksek karşıtlık Temalar da seçildiğinde daha kolay sunuldu.</span><span class="sxs-lookup"><span data-stu-id="ef159-311">The text in the <xref:System.Windows.Controls.CheckBox> and <xref:System.Windows.Controls.RadioButton> controls is now easier to see when selected in high contrast themes.</span></span> <span data-ttu-id="ef159-312">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-312">For example:</span></span>

  <span data-ttu-id="ef159-313">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-313">Before:</span></span> 

  ![Erişilebilirlik geliştirmeleri önce odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-before.png)

  <span data-ttu-id="ef159-315">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-315">After:</span></span> 

  ![Erişilebilirlik geliştirmeleri sonra odaklanılan yüksek karşıtlık radyo düğmesi](media/radio-button-after.png)

- <span data-ttu-id="ef159-317"><xref:System.Windows.Controls.ComboBox> Denetimi</span><span class="sxs-lookup"><span data-stu-id="ef159-317"><xref:System.Windows.Controls.ComboBox> control</span></span>

  <span data-ttu-id="ef159-318">.NET Framework 4.7.1, devre dışı kenarlık başlangıç <xref:System.Windows.Controls.ComboBox> devre dışı bırakılmış metinlerin aynı renge denetimidir.</span><span class="sxs-lookup"><span data-stu-id="ef159-318">Starting with .NET Framework 4.7.1, the border of a disabled <xref:System.Windows.Controls.ComboBox> control is the same color as disabled text.</span></span> <span data-ttu-id="ef159-319">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-319">For example:</span></span>

  <span data-ttu-id="ef159-320">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-320">Before:</span></span> 

  ![ComboBox kenarlık ve metin erişilebilirlik geliştirmeleri önce devre dışı](media/combo-disabled-before.png)

  <span data-ttu-id="ef159-322">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-322">After:</span></span>   

  ![ComboBox kenarlık ve metin sonra erişilebilirlik iyileştirmeleri devre dışı](media/combo-disabled-after.png)

  <span data-ttu-id="ef159-324">Ayrıca, doğru bir Tema rengi devre dışı bırakılmış ve odaklanmış düğmelerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="ef159-324">In addition, disabled and focused buttons use the correct theme color.</span></span>

  <span data-ttu-id="ef159-325">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-325">Before:</span></span>

  ![Erişilebilirlik geliştirmeleri önce düğme Tema renkleri](media/button-themes-before.png) 

  <span data-ttu-id="ef159-327">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-327">After:</span></span> 

  ![Erişilebilirlik geliştirmeleri sonra düğme Tema renkleri](media/button-themes-after.png) 

  <span data-ttu-id="ef159-329">Son olarak, .NET Framework 4.7 ve önceki sürümleri, ayar, bir <xref:System.Windows.Controls.ComboBox> denetimin stil `Toolbar.ComboBoxStyleKey` görünmemesini açılan liste okunu neden oldu.</span><span class="sxs-lookup"><span data-stu-id="ef159-329">Finally, in .NET Framework 4.7 and earlier versions, setting a <xref:System.Windows.Controls.ComboBox> control’s style to `Toolbar.ComboBoxStyleKey` caused the drop-down arrow to be invisible.</span></span> <span data-ttu-id="ef159-330">.NET Framework 4.7.1 ile başlayarak Bu sorun düzeltilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef159-330">This issue is fixed starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="ef159-331">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-331">For example:</span></span>

  <span data-ttu-id="ef159-332">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-332">Before:</span></span> 

  ![Erişilebilirlik geliştirmeleri önce Toolbar.ComboBoxStyleKey](media/comboboxstylekey-before.png) 

  <span data-ttu-id="ef159-334">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-334">After:</span></span> 

  ![Erişilebilirlik geliştirmeleri sonra Toolbar.ComboBoxStyleKey](media/comboboxstylekey-after.png) 

- <span data-ttu-id="ef159-336"><xref:System.Windows.Controls.DataGrid> Denetimi</span><span class="sxs-lookup"><span data-stu-id="ef159-336"><xref:System.Windows.Controls.DataGrid> control</span></span>

  <span data-ttu-id="ef159-337">.NET Framework 4.7.1, sıralama göstergesi oka başlayarak <xref:System.Windows.Controls.DataGrid> Tema renkleri kullandığı düzeltmek artık denetler.</span><span class="sxs-lookup"><span data-stu-id="ef159-337">Starting with .NET Framework 4.7.1, the sort indicator arrow in <xref:System.Windows.Controls.DataGrid> controls now uses correct theme colors.</span></span> <span data-ttu-id="ef159-338">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-338">For example:</span></span>

  <span data-ttu-id="ef159-339">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-339">Before:</span></span> 

  ![Erişilebilirlik geliştirmeleri önce sıralama göstergesi oku](media/sort-indicator-before.png) 

  <span data-ttu-id="ef159-341">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-341">After:</span></span>   

  ![Erişilebilirlik geliştirmeleri sonra sıralama göstergesi oku](media/sort-indicator-after.png) 

  <span data-ttu-id="ef159-343">Ayrıca, .NET Framework 4.7 ve önceki sürümlerinde, varsayılan bağlantı stilini fare yanlış bir renk yüksek karşıtlık modlarında değiştirilecek.</span><span class="sxs-lookup"><span data-stu-id="ef159-343">In addition, in .NET Framework 4.7 and earlier versions, the default link style changed to an incorrect color on mouse over in high contrast modes.</span></span> <span data-ttu-id="ef159-344">Bu, .NET Framework 4.7.1 ile başlayarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="ef159-344">This is resolved starting with .NET Framework 4.7.1.</span></span> <span data-ttu-id="ef159-345">Benzer şekilde, <xref:System.Windows.Controls.DataGrid> onay kutusu sütunları, .NET Framework 4.7.1 ile başlayarak klavye odağı geri bildirim için beklenen renkleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef159-345">Similarly, <xref:System.Windows.Controls.DataGrid> checkbox columns uses the expected colors for keyboard focus feedback starting with .NET Framework 4.7.1.</span></span>

  <span data-ttu-id="ef159-346">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-346">Before:</span></span> 

  ![DataGrid varsayılan bağlantı stilini önce erişilebilirlik geliştirmeleri](media/default-link-style-before.png) 

  <span data-ttu-id="ef159-348">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-348">After:</span></span>    

  ![DataGrid varsayılan bağlantı stilini sonra erişilebilirlik geliştirmeleri](media/default-link-style-after.png) 

<span data-ttu-id="ef159-350">.NET Framework 4.7.1 WPF erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz. [erişilebilirlik geliştirmeleri ' WPF'de](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span><span class="sxs-lookup"><span data-stu-id="ef159-350">For more information on WPF accessibility improvements in .NET Framework 4.7.1, see [Accessibility improvements in WPF](../migration-guide/retargeting/4.7-4.7.1.md#accessibility-improvements-in-wpf).</span></span>

<a name="winforms471"></a>

### <a name="windows-forms-accessibility-improvements"></a><span data-ttu-id="ef159-351">Windows Forms erişilebilirlik geliştirmeleri</span><span class="sxs-lookup"><span data-stu-id="ef159-351">Windows Forms accessibility improvements</span></span>

<span data-ttu-id="ef159-352">.NET Framework 4.7.1, Windows Forms (WinForms) aşağıdaki alanlarda erişilebilirlik değişiklikleri içerir.</span><span class="sxs-lookup"><span data-stu-id="ef159-352">In .NET Framework 4.7.1, Windows Forms (WinForms) includes accessibility changes in the following areas.</span></span>

<span data-ttu-id="ef159-353">**Yüksek karşıtlık modunda geliştirilmiş görüntüleme**</span><span class="sxs-lookup"><span data-stu-id="ef159-353">**Improved display in High Contrast mode**</span></span>

<span data-ttu-id="ef159-354">.NET Framework 4.7.1 ile başlayarak, işletim sistemi içinde kullanılabilir olan yüksek karşıtlık modda geliştirilmiş işleme çeşitli WinForms denetimler sunar.</span><span class="sxs-lookup"><span data-stu-id="ef159-354">Starting with .NET Framework 4.7.1, various WinForms controls offer improved rendering in the HighContrast modes available in the operating system.</span></span> <span data-ttu-id="ef159-355">Windows 10 bazı yüksek karşıtlık sistem renkleri için değerleri değişti ve Windows Forms, Windows 10 Win32 altyapısını temel alır.</span><span class="sxs-lookup"><span data-stu-id="ef159-355">Windows 10 has changed the values for some high contrast system colors, and Windows Forms is based on the Windows 10 Win32 framework.</span></span> <span data-ttu-id="ef159-356">En iyi deneyim için en son Windows sürümüne çalıştırın ve en son işletim sistemi değişiklikleri için aşağıdaki görünür, böylece bir app.manifest dosyasındaki bir test uygulaması ve Çalıştır-açıklama Windows 10 işletim sistemi satırı desteklenen ekleyerek kabul et:</span><span class="sxs-lookup"><span data-stu-id="ef159-356">For the best experience, run on the latest version of Windows and opt in to the latest OS changes by adding an app.manifest file in a test application and un-comment the Windows 10 supported OS  line so that it looks the following:</span></span>

```xml
<!-- Windows 10 -->
<supportedOS Id=”{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}” />
```

<span data-ttu-id="ef159-357">Yüksek Karşıtlık değişiklikler bazı örnekleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="ef159-357">Some examples of high contrast changes include:</span></span>

- <span data-ttu-id="ef159-358">Açılır menüdeki onay <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="ef159-358">Checkmarks in <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="ef159-359">Bu onay kutusu seçildiğinde, devre dışı <xref:System.Windows.Forms.MenuStrip> öğeleri görüntülemek daha kolay.</span><span class="sxs-lookup"><span data-stu-id="ef159-359">When selected, disabled <xref:System.Windows.Forms.MenuStrip> items are easier to view.</span></span>

- <span data-ttu-id="ef159-360">Seçili metinde <xref:System.Windows.Forms.Button> Denetim seçim rengi ile karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="ef159-360">Text in a selected <xref:System.Windows.Forms.Button> control contrasts with the selection color.</span></span>

- <span data-ttu-id="ef159-361">Devre dışı bırakılmış metinlerin okunmasını daha kolay olur.</span><span class="sxs-lookup"><span data-stu-id="ef159-361">Disabled text is easier to read.</span></span> <span data-ttu-id="ef159-362">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="ef159-362">For example:</span></span>

  <span data-ttu-id="ef159-363">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-363">Before:</span></span>

  ![Erişilebilirlik geliştirmeleri önce devre dışı bırakılmış metin](media/wf-disabled-before.png) 

  <span data-ttu-id="ef159-365">Sonra:</span><span class="sxs-lookup"><span data-stu-id="ef159-365">After:</span></span>

  ![Erişilebilirlik geliştirmeleri sonra devre dışı bırakılmış metin](media/wf-disabled-after.png) 

- <span data-ttu-id="ef159-367">İş parçacığı özel durum iletişim kutusunda yüksek karşıtlık geliştirmeleri.</span><span class="sxs-lookup"><span data-stu-id="ef159-367">High contrast improvements in the Thread Exception Dialog.</span></span>

<span data-ttu-id="ef159-368">**Geliştirilmiş ekran okuyucu desteği**</span><span class="sxs-lookup"><span data-stu-id="ef159-368">**Improved Narrator support**</span></span>

<span data-ttu-id="ef159-369">Windows Forms'ta .NET Framework 4.7.1 ekran okuyucu için aşağıdaki erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-369">Windows Forms in .NET Framework 4.7.1 includes the following accessibility improvements for the Narrator:</span></span>

- <span data-ttu-id="ef159-370"><xref:System.Windows.Forms.MonthCalendar> Denetim, ekran okuyucusu tarafından yanı sıra diğer UI Otomasyon araçları tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-370">The <xref:System.Windows.Forms.MonthCalendar> control can be accessed by the Narrator, as well as by other UI automation tools.</span></span>

- <span data-ttu-id="ef159-371"><xref:System.Windows.Forms.CheckedListBox> Denetim, ekran okuyucusu bir liste öğesi değerini değiştirdiyseniz kullanıcıyı uyarır, böylece bir öğenin denetim durumu değiştiğinde bildirir.</span><span class="sxs-lookup"><span data-stu-id="ef159-371">The <xref:System.Windows.Forms.CheckedListBox> control notifies Narrator when an item's check state has changed so the user is notified that they’ve changed the value of a list item.</span></span>

- <span data-ttu-id="ef159-372"><xref:System.Windows.Forms.DataGridViewCell> Denetimi için ekran okuyucusu doğru salt okunur durumunu raporlar.</span><span class="sxs-lookup"><span data-stu-id="ef159-372">The <xref:System.Windows.Forms.DataGridViewCell> control reports the correct read-only status to Narrator.</span></span>

- <span data-ttu-id="ef159-373">Okuyucu artık devre dışı okur <xref:System.Windows.Forms.ToolStripMenuItem> metin, daha önce devre dışı bırakılmış menü öğelerinin üzerine atlarsınız ise.</span><span class="sxs-lookup"><span data-stu-id="ef159-373">Narrator can now read disabled <xref:System.Windows.Forms.ToolStripMenuItem> text, whereas previously it would skip over disabled menu items.</span></span>

<span data-ttu-id="ef159-374">**UIAutomation erişilebilirlik desenleri için gelişmiş destek**</span><span class="sxs-lookup"><span data-stu-id="ef159-374">**Enhanced support for UIAutomation accessibility patterns**</span></span>

<span data-ttu-id="ef159-375">.NET Framework 4.7.1 ile başlayarak, Erişilebilirlik teknoloji Araçlar, geliştiricilerin ortak API erişilebilirlik desenleri ve birden çok WinForms denetimi özelliklerini yararlanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-375">Starting with .NET Framework 4.7.1, developers of accessibility technology tools can leverage common API accessibility patterns and properties for several WinForms controls.</span></span> <span data-ttu-id="ef159-376">Bu erişilebilirlik geliştirmeleri içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-376">These accessibility improvements include:</span></span>

- <span data-ttu-id="ef159-377"><xref:System.Windows.Forms.ComboBox> Ve <xref:System.Windows.Forms.ToolStripSplitButton> artık destek [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ef159-377">The <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.ToolStripSplitButton> now support the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="ef159-378"><xref:System.Windows.Forms.DataGridViewCheckBoxCell> Artık destekliyor [geçiş deseni](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ef159-378">The <xref:System.Windows.Forms.DataGridViewCheckBoxCell> now supports the [toggle pattern](../ui-automation/implementing-the-ui-automation-toggle-control-pattern.md).</span></span>

- <span data-ttu-id="ef159-379"><xref:System.Windows.Forms.ToolStripItem> Denetim destekler <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği ve [Genişlet/Daralt deseni](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="ef159-379">The <xref:System.Windows.Forms.ToolStripItem> control supports the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property and the [expand/collapse pattern](../ui-automation/implementing-the-ui-automation-expandcollapse-control-pattern.md).</span></span>

- <span data-ttu-id="ef159-380"><xref:System.Windows.Forms.NumericUpDown> Ve <xref:System.Windows.Forms.DomainUpDown> denetimleri Destek <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> özelliği.</span><span class="sxs-lookup"><span data-stu-id="ef159-380">The <xref:System.Windows.Forms.NumericUpDown> and <xref:System.Windows.Forms.DomainUpDown> controls support the <xref:System.Windows.Automation.AutomationElement.AutomationElementInformation.Name> property.</span></span>

<span data-ttu-id="ef159-381">**Geliştirilmiş özelliği tarayıcı deneyimi**</span><span class="sxs-lookup"><span data-stu-id="ef159-381">**Improved property browser experience**</span></span>

<span data-ttu-id="ef159-382">.NET Framework 4.7.1 ile başlayarak, Windows Forms içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-382">Starting with .NET Framework 4.7.1, Windows Forms includes:</span></span>

- <span data-ttu-id="ef159-383">Daha iyi klavye gezintisi aracılığıyla çeşitli yanıdaki açılan seçimi windows.</span><span class="sxs-lookup"><span data-stu-id="ef159-383">Better keyboard navigation through the various drop-down selection windows.</span></span>
- <span data-ttu-id="ef159-384">Gereksiz sekme duraklarının azaltma.</span><span class="sxs-lookup"><span data-stu-id="ef159-384">A reduction of unnecessary tab stops.</span></span>
- <span data-ttu-id="ef159-385">Daha iyi denetim türlerini raporlama.</span><span class="sxs-lookup"><span data-stu-id="ef159-385">Better reporting of control types.</span></span>
- <span data-ttu-id="ef159-386">Geliştirilmiş ekran okuyucu davranışı.</span><span class="sxs-lookup"><span data-stu-id="ef159-386">Improved narrator behavior.</span></span>

<a name="aspnet471"></a>

### <a name="aspnet-web-controls"></a><span data-ttu-id="ef159-387">ASP.NET web denetimleri</span><span class="sxs-lookup"><span data-stu-id="ef159-387">ASP.NET web controls</span></span>

<span data-ttu-id="ef159-388">.NET Framework 4.7.1 ve Visual Studio 2017 15.3 ile başlayarak, ASP.NET erişilebilirlik teknolojisinin Visual Studio ile ASP.NET web denetimleri nasıl artırır.</span><span class="sxs-lookup"><span data-stu-id="ef159-388">Starting with .NET Framework 4.7.1 and Visual Studio 2017 15.3, ASP.NET improves how ASP.NET web controls work with accessibility technology in Visual Studio.</span></span> <span data-ttu-id="ef159-389">Değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-389">Changes include the following:</span></span>

- <span data-ttu-id="ef159-390">Eksik kullanıcı Arabirimi erişilebilirliği desenleri gibi denetimleri içinde uygulamak için değişiklikleri **alan Ekle** iletişim kutusunda **Ayrıntılar görünümü** Sihirbazı'nı veya **yapılandırma ListView** iletişim **ListView** Sihirbazı.</span><span class="sxs-lookup"><span data-stu-id="ef159-390">Changes to implement missing UI accessibility patterns in controls, like the **Add Field** dialog in the **Details View** wizard, or the **Configure ListView** dialog of the **ListView** wizard.</span></span>

- <span data-ttu-id="ef159-391">Yüksek karşıtlık modunda görüntüleme gibi iyileştirmeye yönelik değişiklikler **veri çağrı alanları Düzenleyicisi**.</span><span class="sxs-lookup"><span data-stu-id="ef159-391">Changes to improve the display in High Contrast mode, like the **Data Pager Fields Editor**.</span></span>

- <span data-ttu-id="ef159-392">Klavye ile gezintiyi iyileştirmeye yönelik değişiklikler deneyimleri denetimler için gibi **alanları** iletişim kutusunda **çağrı alanları Düzenle** DataPager denetimi Sihirbazı **ObjectContext yapılandırın**  iletişim kutusunda veya **yapılandırma veri seçimi** iletişim **veri kaynağı yapılandırma** Sihirbazı.</span><span class="sxs-lookup"><span data-stu-id="ef159-392">Changes to improve the keyboard navigation experiences for controls, like the **Fields** dialog in the **Edit Pager Fields** wizard of the DataPager control, the **Configure ObjectContext** dialog, or the **Configure Data Selection** dialog of the **Configure Data Source** wizard.</span></span>

<a name="tools471"></a>

### <a name="net-sdk-tools"></a><span data-ttu-id="ef159-393">.NET SDK Tools</span><span class="sxs-lookup"><span data-stu-id="ef159-393">.NET SDK Tools</span></span>

<span data-ttu-id="ef159-394">[Yapılandırma Aracı (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) ve [hizmet izleme Görüntüleyicisi aracı (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) çeşitli erişilebilirlik sorunları çözme tarafından geliştirilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef159-394">The [Configuration Editor Tool (SvcConfigEditor.exe)](../wcf/configuration-editor-tool-svcconfigeditor-exe.md) and [Service Trace Viewer Tool (SvcTraceViewer.exe)](../wcf/service-trace-viewer-tool-svctraceviewer-exe.md) have been improved by fixing varied accessibility issues.</span></span> <span data-ttu-id="ef159-395">Bunların çoğu tanımlanmayan bir ad veya doğru uygulanmadı belirli bir UI Otomasyon düzenleri gibi küçük problemler yoktu.</span><span class="sxs-lookup"><span data-stu-id="ef159-395">Most of these were small issues, like a name not being defined or certain UI automation patterns not being implemented correctly.</span></span> <span data-ttu-id="ef159-396">Birçok kullanıcı bu yanlış değerini kullanan sunulacaktır, ancak ekran okuyucular gibi yardımcı teknolojiler kullanan müşteriler bu SDK Araçları daha erişilebilir bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef159-396">While many users won’t be aware of these incorrect values, customers who use assistive technologies like screen readers will find these SDK tools more accessible.</span></span>

<span data-ttu-id="ef159-397">Bu geliştirmeler, klavye odağı sırası gibi önceki bazı davranışları değiştirir.</span><span class="sxs-lookup"><span data-stu-id="ef159-397">These enhancements change some previous behaviors, such as keyboard focus order.</span></span>

<a name="wf471"></a>

### <a name="windows-workflow-foundation-wf-workflow-designer"></a><span data-ttu-id="ef159-398">Windows Workflow Foundation (WF) iş akışı Tasarımcısı</span><span class="sxs-lookup"><span data-stu-id="ef159-398">Windows Workflow Foundation (WF) Workflow Designer</span></span>

<span data-ttu-id="ef159-399">İş akışı tasarımcısında erişilebilirlik değişiklikler şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="ef159-399">Accessibility changes in the Workflow Designer include the following:</span></span>

- <span data-ttu-id="ef159-400">Sekme sırası, soldan sağa ve yukarıdan aşağıya bazı denetimlerinde değiştirir:</span><span class="sxs-lookup"><span data-stu-id="ef159-400">The tab order changes to left to right and top to bottom in some controls:</span></span>

  - <span data-ttu-id="ef159-401">Upravit data korelace için ayarlamak için Initialize bağıntı penceresi <xref:System.ServiceModel.Activities.InitializeCorrelation> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ef159-401">The initialize correlation window for setting correlation data for the <xref:System.ServiceModel.Activities.InitializeCorrelation> activity.</span></span>

  - <span data-ttu-id="ef159-402">İçerik tanımı penceresi <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ef159-402">The content definition window for the <xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply> activities.</span></span>

- <span data-ttu-id="ef159-403">Daha fazla işlev klavye mevcuttur:</span><span class="sxs-lookup"><span data-stu-id="ef159-403">More functions are available via the keyboard:</span></span>

  - <span data-ttu-id="ef159-404">Bir etkinliğin özelliklerini düzenlerken, özellik grupları tarafından klavye odaklı ilk kez daraltılabilirler.</span><span class="sxs-lookup"><span data-stu-id="ef159-404">When editing the properties of an activity, property groups can be collapsed by keyboard the first time they are focused.</span></span>

  - <span data-ttu-id="ef159-405">Uyarı simgeleri klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-405">Warning icons are accessible by keyboard.</span></span>

  - <span data-ttu-id="ef159-406">**Daha özellikleri** düğmesine **özellikleri** pencere, klavye tarafından erişilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef159-406">The **More Properties** button in the **Properties** window is accessible by keyboard.</span></span>

  - <span data-ttu-id="ef159-407">Klavye kullanıcılarının üstbilgi öğeleri erişebileceği **bağımsız değişkenleri** ve **değişkenleri** iş akışı Tasarımcısı bölmelerini.</span><span class="sxs-lookup"><span data-stu-id="ef159-407">Keyboard users can access the header items in the **Arguments** and **Variables** panes of the Workflow Designer.</span></span>

- <span data-ttu-id="ef159-408">Geliştirilmiş görünürlük odaklanılan ne zaman gibi öğeleri:</span><span class="sxs-lookup"><span data-stu-id="ef159-408">Improved visibility of items with focus, such as when:</span></span>

  - <span data-ttu-id="ef159-409">İş Akışı Tasarımcısı ve etkinlik tasarımcıları tarafından kullanılan veri kılavuzları için satırlar ekleme.</span><span class="sxs-lookup"><span data-stu-id="ef159-409">Adding rows to data grids used by the Workflow Designer and activity designers.</span></span>

  - <span data-ttu-id="ef159-410">Alanları arasında sekmeyle gitmeyi <xref:System.ServiceModel.Activities.ReceiveReply> ve <xref:System.ServiceModel.Activities.SendReply> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ef159-410">Tabbing through fields in the <xref:System.ServiceModel.Activities.ReceiveReply> and <xref:System.ServiceModel.Activities.SendReply> activities.</span></span>

  - <span data-ttu-id="ef159-411">Değişken veya bağımsız değişkenleri için varsayılan değerleri ayarlama</span><span class="sxs-lookup"><span data-stu-id="ef159-411">Setting default values for variables or arguments</span></span>

- <span data-ttu-id="ef159-412">Artık ekran okuyucular düzgün tanıyabilmesi:</span><span class="sxs-lookup"><span data-stu-id="ef159-412">Screen readers can now correctly recognize:</span></span>

  - <span data-ttu-id="ef159-413">İş Akışı Tasarımcısı'nda kesme noktalarını ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="ef159-413">Breakpoints set in the workflow designer.</span></span>

  - <span data-ttu-id="ef159-414"><xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, Ve <xref:System.ServiceModel.Activities.CorrelationScope> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ef159-414">The <xref:System.Activities.Statements.FlowSwitch%601>, <xref:System.Activities.Statements.FlowDecision>, and <xref:System.ServiceModel.Activities.CorrelationScope> activities.</span></span>
  - <span data-ttu-id="ef159-415">İçeriğini <xref:System.ServiceModel.Activities.Receive> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ef159-415">The contents of the <xref:System.ServiceModel.Activities.Receive> activity.</span></span>

  - <span data-ttu-id="ef159-416">Hedef türü için <xref:System.Activities.Statements.InvokeMethod> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ef159-416">The Target Type for the <xref:System.Activities.Statements.InvokeMethod> activity.</span></span>

  - <span data-ttu-id="ef159-417">Özel durum birleşik giriş kutusu ve son olarak konusundaki <xref:System.Activities.Statements.TryCatch> etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ef159-417">The Exception combo box and the Finally section in the <xref:System.Activities.Statements.TryCatch> activity.</span></span>

  - <span data-ttu-id="ef159-418">İleti türü açılan kutusu, bağıntı başlatıcılar Ekle penceresi, içerik tanım penceresini ve mesajlaşma etkinlikleri CorrelatesOn tanımı penceresinde ayırıcı (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, ve <xref:System.ServiceModel.Activities.ReceiveReply>).</span><span class="sxs-lookup"><span data-stu-id="ef159-418">The Message Type combo box, the splitter in the Add Correlation Initializers window, the Content Definition window, and the CorrelatesOn Definition window in the messaging activities (<xref:System.ServiceModel.Activities.Receive>, <xref:System.ServiceModel.Activities.Send>, <xref:System.ServiceModel.Activities.SendReply>, and <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>

  - <span data-ttu-id="ef159-419">Durum makinesi geçişler ve hedeflere geçer.</span><span class="sxs-lookup"><span data-stu-id="ef159-419">State machine transitions and transitions destinations.</span></span>

  - <span data-ttu-id="ef159-420">Ek açıklamalar ve bağlayıcılarda <xref:System.Activities.Statements.FlowDecision> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ef159-420">Annotations and connectors on <xref:System.Activities.Statements.FlowDecision> activities.</span></span>

  - <span data-ttu-id="ef159-421">Etkinlikler için (sağ tıklama) bağlam menüleri.</span><span class="sxs-lookup"><span data-stu-id="ef159-421">The context (right-click) menus for activities.</span></span>

  - <span data-ttu-id="ef159-422">Özellik değer düzenleyicileri, aramayı Temizle düğmesi, kategoriye göre ve alfabetik sıralama düğmeler ve Özellikler kılavuzundaki ifade Düzenleyicisi iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="ef159-422">The property value editors, the Clear Search button, the By Category and Alphabetical sort buttons, and the Expression Editor dialog in the properties grid.</span></span>

  - <span data-ttu-id="ef159-423">İş akışı tasarımcısında yakınlaştırma yüzdesi.</span><span class="sxs-lookup"><span data-stu-id="ef159-423">The zoom percentage in the Workflow Designer.</span></span>

  - <span data-ttu-id="ef159-424">Ayırıcı <xref:System.Activities.Statements.Parallel> ve <xref:System.Activities.Statements.Pick> etkinlikler.</span><span class="sxs-lookup"><span data-stu-id="ef159-424">The separator in <xref:System.Activities.Statements.Parallel> and <xref:System.Activities.Statements.Pick> activities.</span></span>

  - <span data-ttu-id="ef159-425"><xref:System.Activities.Statements.InvokeDelegate> Etkinlik.</span><span class="sxs-lookup"><span data-stu-id="ef159-425">The <xref:System.Activities.Statements.InvokeDelegate> activity.</span></span>

  - <span data-ttu-id="ef159-426">Sözlük etkinlikler için seçim türlerinin penceresi (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`vb..).</span><span class="sxs-lookup"><span data-stu-id="ef159-426">The Select Types window for dictionary activities (`Microsoft.Activities.AddToDictionary<TKey,TValue>`, `Microsoft.Activities.RemoveFromDictionary<TKey,TValue>`, etc.).</span></span>

  - <span data-ttu-id="ef159-427">Göz atma ve .NET türünü seç penceresi.</span><span class="sxs-lookup"><span data-stu-id="ef159-427">The Browse and Select .NET Type window.</span></span>

  - <span data-ttu-id="ef159-428">İş akışı tasarımcısında içerik haritaları.</span><span class="sxs-lookup"><span data-stu-id="ef159-428">Breadcrumbs in the Workflow Designer.</span></span>

- <span data-ttu-id="ef159-429">Yüksek karşıtlıklı tema seçen kullanıcılar, iş akışı Tasarımcısı gibi öğeleri ve odak öğeleri için kullanılan daha belirgin seçim kutuları arasında daha iyi kontrast, Denetim ve görünürlüğü içindeki birçok geliştirmeden görürsünüz.</span><span class="sxs-lookup"><span data-stu-id="ef159-429">Users who choose High Contrast themes will see many improvements in the visibility of the Workflow Designer and its controls, like better contrast ratios between elements and more noticeable selection boxes used for focus elements.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef159-430">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef159-430">See also</span></span>

- [<span data-ttu-id="ef159-431">.NET Framework'teki yenilikler</span><span class="sxs-lookup"><span data-stu-id="ef159-431">What's new in the .NET Framework</span></span>](whats-new.md)
