---
title: Windows Forms'ta yüksek DPI desteği
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1641702c7b1c3d3b0e83c59a96529de70f699d17
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57843615"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="8f087-102">Windows Forms'ta yüksek DPI desteği</span><span class="sxs-lookup"><span data-stu-id="8f087-102">High DPI support in Windows Forms</span></span>

<span data-ttu-id="8f087-103">.NET Framework 4.7 ile başlayarak, Windows Forms ortak yüksek DPI ve dinamik DPI senaryoları için geliştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="8f087-103">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="8f087-104">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8f087-104">These include:</span></span>

- <span data-ttu-id="8f087-105">Gibi ölçeklendirme ve düzen çok sayıda Windows Forms denetimleri <xref:System.Windows.Forms.MonthCalendar> denetimi ve <xref:System.Windows.Forms.CheckedListBox> denetimi.</span><span class="sxs-lookup"><span data-stu-id="8f087-105">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="8f087-106">Tek-geçişi ölçeklendirme.</span><span class="sxs-lookup"><span data-stu-id="8f087-106">Single-pass scaling.</span></span>  <span data-ttu-id="8f087-107">.NET Framework 4.6 ve önceki sürümlerinde, ölçeklendirme, gerekli birden ölçeklendirilmesi bazı denetimler neden birden çok geçer gerçekleştirildi.</span><span class="sxs-lookup"><span data-stu-id="8f087-107">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="8f087-108">Bir Windows Forms uygulaması başlatıldıktan sonra kullanıcı DPI veya ölçek faktörü değişiklik dinamik DPI senaryolar için destek.</span><span class="sxs-lookup"><span data-stu-id="8f087-108">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="8f087-109">.NET Framework 4.7 ile başlayan .NET Framework sürümlerinde geliştirilmiş yüksek DPI desteği bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="8f087-109">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="8f087-110">Uygulamanızı yararlanmak için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f087-110">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="8f087-111">Windows Forms uygulamanızı yüksek DPI desteği için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="8f087-111">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="8f087-112">Yüksek DPI tanıma destekleyen yeni bir Windows Forms özellikler, .NET Framework 4.7 hedefleyen ve Windows 10 Creators güncelleştirmesi ile başlayarak Windows işletim sistemleri üzerinde çalışan uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8f087-112">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="8f087-113">Ayrıca, Windows Forms uygulaması'nda yüksek DPI desteği yapılandırmak için aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="8f087-113">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="8f087-114">Windows 10 ile uyumluluğunu bildirin.</span><span class="sxs-lookup"><span data-stu-id="8f087-114">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="8f087-115">Bunu yapmak için bildirim dosyasına aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="8f087-115">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="8f087-116">İzleyici başına DPI tanıma etkinleştirme *app.config* dosya.</span><span class="sxs-lookup"><span data-stu-id="8f087-116">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="8f087-117">Yeni bir Windows Forms tanıtır [ `<System.Windows.Forms.ApplicationConfigurationSection>` ](../configure-apps/file-schema/winforms/index.md) yeni özellikler ve .NET Framework 4.7 ile başlayan eklenen özelleştirmeleri desteklemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="8f087-117">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="8f087-118">Yüksek DPI desteği yeni özelliklerden yararlanmak için uygulama yapılandırma dosyasına aşağıdakileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="8f087-118">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="8f087-119">Önceki .NET Framework sürümlerinde, bildirim yüksek DPI desteği eklemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="8f087-119">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="8f087-120">Bu app.config dosyası üzerinde tanımlanan ayarları geçersiz kıldığından bu yaklaşım artık önerilir.</span><span class="sxs-lookup"><span data-stu-id="8f087-120">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="8f087-121">Statik çağrı <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8f087-121">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="8f087-122">Bu, uygulama giriş noktası ilk yöntem çağrısında olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="8f087-122">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="8f087-123">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="8f087-123">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="8f087-124">Yüksek DPI özellikleri dışında tek tek seçim yapma</span><span class="sxs-lookup"><span data-stu-id="8f087-124">Opting out of individual high DPI features</span></span>

<span data-ttu-id="8f087-125">Ayarı `DpiAwareness` değerini `PerMonitorV2` .NET Framework 4.7 ile başlayan .NET Framework sürümleri tarafından desteklenen tüm yüksek DPI tanıma özelliklerini etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="8f087-125">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="8f087-126">Genellikle bu çoğu Windows Forms uygulamaları için yeterli olur.</span><span class="sxs-lookup"><span data-stu-id="8f087-126">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="8f087-127">Ancak, bir veya daha fazla tek tek özellikler dışında bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f087-127">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="8f087-128">Bunu yapmak için en önemli nedeni, var olan uygulama kodunuzun bu özelliği işlediğini olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="8f087-128">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="8f087-129">Örneğin, uygulamanız otomatik ölçeklendirme işliyorsa, otomatik yeniden boyutlandırma özelliği gibi devre dışı bırakmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f087-129">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="8f087-130">Tek tek anahtarları ve değerleri listesi için bkz. [Windows Forms ekleme yapılandırma öğesi](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="8f087-130">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="8f087-131">Yeni DPI değişikliği olayları</span><span class="sxs-lookup"><span data-stu-id="8f087-131">New DPI change events</span></span>

<span data-ttu-id="8f087-132">.NET Framework 4.7 ile başlayarak, üç yeni olaylar, program aracılığıyla dinamik DPI değişiklikleri işlemek izin ver:</span><span class="sxs-lookup"><span data-stu-id="8f087-132">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="8f087-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetim için DPI ayarı programlı olarak DPI değişiklik olayı için onun üst denetim sonra değiştirildi veya form oluştu tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="8f087-133"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="8f087-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetim için DPI ayarı programlı olarak DPI değişiklik olayı için üst denetim önce değiştirildi veya form oluştu tetiklendi.</span><span class="sxs-lookup"><span data-stu-id="8f087-134"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="8f087-135"><xref:System.Windows.Forms.Form.DpiChanged>, formu şu anda görüntüleyen görüntü cihazında DPI ayarını değiştirdiğinde tetiklenen.</span><span class="sxs-lookup"><span data-stu-id="8f087-135"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="8f087-136">Yeni yardımcı yöntemler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="8f087-136">New helper methods and properties</span></span>

<span data-ttu-id="8f087-137">.NET Framework 4.7, çok sayıda yeni yardımcı yöntemler ve DPI ölçeklendirme hakkında bilgi sağlar ve DPI ölçeklendirme gerçekleştirmenize olanak sağlayan özellikleri de ekler.</span><span class="sxs-lookup"><span data-stu-id="8f087-137">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="8f087-138">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="8f087-138">These include:</span></span>

- <span data-ttu-id="8f087-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, dönüştüren bir değerini mantıksal ağdan cihaz piksel.</span><span class="sxs-lookup"><span data-stu-id="8f087-139"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="8f087-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir cihaz için mantıksal DPI bir bit eşlem görüntüsüne ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="8f087-140"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="8f087-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, geçerli cihaz için DPI değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="8f087-141"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="8f087-142">Sürüm oluşturma konuları</span><span class="sxs-lookup"><span data-stu-id="8f087-142">Versioning considerations</span></span>

<span data-ttu-id="8f087-143">.NET Framework 4.7 ve Windows 10 Creators Update çalıştıran ek olarak, uygulamanızın içinde yüksek DPI geliştirmeleri ile uyumlu olmayan bir ortamda da çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8f087-143">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="8f087-144">Bu durumda, bir geri dönüş için uygulamanızı geliştirmek gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f087-144">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="8f087-145">Bunu gerçekleştirmek için yapabilirsiniz [özel çizim](./controls/user-drawn-controls.md) ölçeklendirme işlemek için.</span><span class="sxs-lookup"><span data-stu-id="8f087-145">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="8f087-146">Bunu yapmak için aynı zamanda uygulamanızın üzerinde çalıştığı işletim sistemi belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="8f087-146">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="8f087-147">Bunu aşağıdaki gibi kod ile yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f087-147">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="8f087-148">Uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenen değildi, uygulamanız başarıyla Windows 10 algılamaz unutmayın.</span><span class="sxs-lookup"><span data-stu-id="8f087-148">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="8f087-149">Ayrıca, uygulamanın derlendiği .NET Framework sürümünü kontrol edebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="8f087-149">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="8f087-150">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f087-150">See also</span></span>

- [<span data-ttu-id="8f087-151">Windows Forms yapılandırma öğesi Ekle</span><span class="sxs-lookup"><span data-stu-id="8f087-151">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="8f087-152">Windows Forms Boyutunu ve Ölçeğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="8f087-152">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
