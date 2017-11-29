---
title: "Windows Forms'ta yüksek DPI desteği"
ms.custom: 
ms.date: 05/16/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a2461c507c0d2a27f1c2bdfe85327d11318b17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="aac33-102">Windows Forms'ta yüksek DPI desteği</span><span class="sxs-lookup"><span data-stu-id="aac33-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="aac33-103">.NET Framework 4.7 ile başlayarak, Windows Forms ortak yüksek DPI ve dinamik DPI senaryoları için geliştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="aac33-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="aac33-104">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aac33-104">These include:</span></span> 

- <span data-ttu-id="aac33-105">Gibi ölçekleme ve çok sayıda Windows Forms düzeni geliştirmeler denetimleri <xref:System.Windows.Forms.MonthCalendar> denetim ve <xref:System.Windows.Forms.CheckedListBox> denetim.</span><span class="sxs-lookup"><span data-stu-id="aac33-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span> 

- <span data-ttu-id="aac33-106">Tek ölçeklendirme geçiş.</span><span class="sxs-lookup"><span data-stu-id="aac33-106">Single-pass scaling.</span></span>  <span data-ttu-id="aac33-107">.NET Framework 4.6 ve önceki sürümlerinde ölçeklendirme hangi ölçeklendirilmesi için bazı denetimler neden birden çok gerekli birden çok geçer gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="aac33-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="aac33-108">Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklikleri dinamik DPI senaryolar için destek.</span><span class="sxs-lookup"><span data-stu-id="aac33-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="aac33-109">.NET Framework 4.7 ile başlayan .NET Framework sürümlerinde, Gelişmiş yüksek DPI destek bir katılımı özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="aac33-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="aac33-110">Bunu yararlanmak için uygulamanızı yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="aac33-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="aac33-111">Windows Forms uygulamanız yüksek DPI desteği için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="aac33-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="aac33-112">Yüksek DPI tanıma desteği yeni Windows Forms özellikleri, .NET Framework 4.7 hedefleyen ve Windows 10 oluşturucuları güncelleştirmesi ile başlayarak Windows işletim sistemlerinde çalışan uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="aac33-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span> 

<span data-ttu-id="aac33-113">Ayrıca, Windows Forms uygulaması'nda yüksek DPI desteğini yapılandırmak için aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="aac33-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="aac33-114">Windows 10 ile uyumluluk bildirin.</span><span class="sxs-lookup"><span data-stu-id="aac33-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="aac33-115">Bunu yapmak için bildirim dosyanızı aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="aac33-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft.comn:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="aac33-116">İzleyici başına DPI tanıma etkinleştirmek *app.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="aac33-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="aac33-117">Yeni bir Windows Forms tanıtır [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../../../docs/framework/configure-apps/file-schema/winforms/index.md) öğesinde yeni özellikler ve .NET Framework 4.7 ile başlayan eklenen özelleştirmeleri desteklemek için.</span><span class="sxs-lookup"><span data-stu-id="aac33-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../../../docs/framework/configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="aac33-118">Yüksek DPI destekleyen yeni özelliklerden yararlanmak için aşağıdaki uygulama yapılandırma dosyasına ekleyin.</span><span class="sxs-lookup"><span data-stu-id="aac33-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>   

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>      
  ```
   
  > [!IMPORTANT]
  > <span data-ttu-id="aac33-119">.NET Framework önceki sürümlerde bildirim yüksek DPI desteği eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="aac33-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="aac33-120">App.config dosyasını tanımlanan ayarları geçersiz kılar gerektiğinden bu yaklaşım artık önerilir.</span><span class="sxs-lookup"><span data-stu-id="aac33-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>
   
- <span data-ttu-id="aac33-121">Statik çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="aac33-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>
   
  <span data-ttu-id="aac33-122">Bu uygulama giriş noktası ilk yöntem çağrısında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aac33-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="aac33-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="aac33-123">For example:</span></span>
   
  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());   
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="aac33-124">Yüksek DPI özellikleri dışında tek tek kullanmama</span><span class="sxs-lookup"><span data-stu-id="aac33-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="aac33-125">Ayarı `DpiAwareness` değeri `PerMonitorV2` ile .NET Framework 4.7 başlangıç .NET Framework sürümleri tarafından desteklenen tüm yüksek DPI tanıma özellikleri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="aac33-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="aac33-126">Genellikle, bu çoğu Windows Forms uygulamaları için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="aac33-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="aac33-127">Ancak, bir veya daha fazla tek tek özellikleri dışında opt isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aac33-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="aac33-128">Bunu yapmak için en önemli varolan uygulama kodunuz zaten bu özelliği işler nedenidir.</span><span class="sxs-lookup"><span data-stu-id="aac33-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="aac33-129">Örneğin, uygulamanız otomatik ölçeklendirme işliyorsa, otomatik yeniden boyutlandırma özelliğini aşağıdaki gibi devre dışı bırakmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aac33-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" /> 
</System.Windows.Forms.ApplicationConfigurationSection>    
```

<span data-ttu-id="aac33-130">Tek tek anahtarları ve değerleri listesi için bkz: [Windows Forms eklemek yapılandırma öğesi](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="aac33-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="aac33-131">Yeni DPI değişikliği olayları</span><span class="sxs-lookup"><span data-stu-id="aac33-131">New DPI change events</span></span>

<span data-ttu-id="aac33-132">.NET Framework 4.7 ile başlayarak, üç yeni olaylar, program aracılığıyla dinamik DPI değişiklikleri işlemeye izin ver:</span><span class="sxs-lookup"><span data-stu-id="aac33-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="aac33-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetim için DPI ayarı program aracılığıyla, üst denetim için bir DPI değişikliği olayından sonra değiştirilir veya form oluştu tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="aac33-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="aac33-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetim için DPI ayarı program aracılığıyla bir DPI değişiklik olayı, üst denetim için önce değiştirilmiş ya da form oluştu tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="aac33-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="aac33-135"><xref:System.Windows.Forms.Form.DpiChanged>, DPI ayarı formun şu anda görüntülendiği görüntü cihazında değiştiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="aac33-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="aac33-136">Yeni yardımcı yöntemler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="aac33-136">New helper methods and properties</span></span>

<span data-ttu-id="aac33-137">.NET Framework 4.7 bir dizi yeni yardımcı yöntemler ve DPI ölçeklendirme hakkında bilgi sağlar ve DPI ölçeklendirme gerçekleştirmenize olanak sağlayan özellikleri de ekler.</span><span class="sxs-lookup"><span data-stu-id="aac33-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="aac33-138">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="aac33-138">These include:</span></span>

- <span data-ttu-id="aac33-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, dönüştüren bir değerini mantıksal ağdan aygıt pikselleri.</span><span class="sxs-lookup"><span data-stu-id="aac33-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="aac33-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir cihaz için mantıksal DPI bitmap görüntüye ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="aac33-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="aac33-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, geçerli cihazınız için DPI döndürür.</span><span class="sxs-lookup"><span data-stu-id="aac33-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="aac33-142">Sürüm oluşturma konuları</span><span class="sxs-lookup"><span data-stu-id="aac33-142">Versioning considerations</span></span>

<span data-ttu-id="aac33-143">.NET Framework 4.7 ve Windows 10 oluşturucuları Update çalıştırmanın yanı sıra, uygulamanızın hangi yüksek DPI geliştirmelerle uyumlu olmayan bir ortamda de çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aac33-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="aac33-144">Bu durumda, uygulamanız için bir geri dönüş geliştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="aac33-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="aac33-145">Bunu gerçekleştirmek için yapabilirsiniz [özel çizim](./controls/user-drawn-controls.md) ölçeklendirme işlemek için.</span><span class="sxs-lookup"><span data-stu-id="aac33-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="aac33-146">Bunu yapmak için Ayrıca, uygulamanızın üzerinde çalıştığı işletim sisteminin belirlemekte gerekir.</span><span class="sxs-lookup"><span data-stu-id="aac33-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="aac33-147">Bunu aşağıdaki gibi kod ile yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aac33-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="aac33-148">Uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenen değildi uygulamanız başarıyla Windows 10 algılamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="aac33-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="aac33-149">Uygulama karşı oluşturulmuş .NET Framework sürümünü de denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="aac33-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="aac33-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aac33-150">See also</span></span>

[<span data-ttu-id="aac33-151">Windows Forms yapılandırma öğesi Ekle</span><span class="sxs-lookup"><span data-stu-id="aac33-151">Windows Forms Add Configuration Element</span></span>](../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)  
[<span data-ttu-id="aac33-152">Windows Forms ölçeğini ve boyutu ayarlama</span><span class="sxs-lookup"><span data-stu-id="aac33-152">Adjusting the Size and Scale of Windows Forms</span></span>](../../../docs/framework/winforms/adjusting-the-size-and-scale-of-windows-forms.md)
