---
title: Yüksek DPı desteği
description: Yaygın yüksek DPı ve dinamik DPı senaryolarında Windows Forms destek hakkında bilgi edinin. Ayrıca, yüksek DPı desteği için Windows Forms uygulamalarını yapılandırmayı öğrenin.
ms.date: 05/16/2017
helpviewer_keywords:
- High DPI in Windows Forms
- Dynamic rescaling in Windows Forms
- Windows Forms layout
- Windows Forms dynamic resizing
ms.assetid: 075ea4c3-900c-4f8a-9dd2-13ea6804346b
ms.openlocfilehash: a9e0766307095da447c772de5a3065c18b7b7154
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325653"
---
# <a name="high-dpi-support-in-windows-forms"></a><span data-ttu-id="2056a-104">Windows Forms yüksek DPı desteği</span><span class="sxs-lookup"><span data-stu-id="2056a-104">High DPI support in Windows Forms</span></span>

<span data-ttu-id="2056a-105">.NET Framework 4,7 ' den başlayarak, Windows Forms genel yüksek DPı ve dinamik DPı senaryolarına yönelik iyileştirmeler içerir.</span><span class="sxs-lookup"><span data-stu-id="2056a-105">Starting with the .NET Framework 4.7, Windows Forms includes enhancements for common high DPI and dynamic DPI scenarios.</span></span> <span data-ttu-id="2056a-106">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2056a-106">These include:</span></span>

- <span data-ttu-id="2056a-107">Denetim ve denetim gibi bir dizi Windows Forms denetiminin ölçeklendirilmesine ve düzenine yönelik iyileştirmeler <xref:System.Windows.Forms.MonthCalendar> <xref:System.Windows.Forms.CheckedListBox> .</span><span class="sxs-lookup"><span data-stu-id="2056a-107">Improvements in the scaling and layout of a number of Windows Forms controls, such as the <xref:System.Windows.Forms.MonthCalendar> control and the <xref:System.Windows.Forms.CheckedListBox> control.</span></span>

- <span data-ttu-id="2056a-108">Tek geçişli ölçekleme.</span><span class="sxs-lookup"><span data-stu-id="2056a-108">Single-pass scaling.</span></span>  <span data-ttu-id="2056a-109">.NET Framework 4,6 ve önceki sürümlerde ölçekleme birden çok geçiş aracılığıyla gerçekleştirildi, bu da bazı denetimlerin gerekenden daha fazla ölçeklendirilmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="2056a-109">In the .NET Framework 4.6 and earlier versions, scaling was performed through multiple passes, which caused some controls to be scaled more than was necessary.</span></span>

- <span data-ttu-id="2056a-110">Windows Forms bir uygulama başlatıldıktan sonra kullanıcının DPı veya ölçek faktörünü değiştirdiği dinamik DPı senaryoları için destek.</span><span class="sxs-lookup"><span data-stu-id="2056a-110">Support for dynamic DPI scenarios in which the user changes the DPI or scale factor after a Windows Forms application has been launched.</span></span>

<span data-ttu-id="2056a-111">.NET Framework 4,7 ' den başlayarak .NET Framework sürümlerinde, gelişmiş yüksek DPı desteği, bir katılım özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="2056a-111">In versions of the .NET Framework starting with the .NET Framework 4.7, enhanced high DPI support is an opt-in feature.</span></span> <span data-ttu-id="2056a-112">Uygulamanızı bundan faydalanmak için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2056a-112">You must configure your application to take advantage of it.</span></span>

## <a name="configuring-your-windows-forms-app-for-high-dpi-support"></a><span data-ttu-id="2056a-113">Windows Forms uygulamanızı yüksek DPı desteği için yapılandırma</span><span class="sxs-lookup"><span data-stu-id="2056a-113">Configuring your Windows Forms app for high DPI support</span></span>

<span data-ttu-id="2056a-114">Yüksek DPı tanımayı destekleyen yeni Windows Forms özellikleri yalnızca .NET Framework 4,7 ' i hedefleyen ve Windows 10 Creators Update ile başlayan Windows işletim sistemlerinde çalışan uygulamalarda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="2056a-114">The new Windows Forms features that support high DPI awareness are available only in applications that target the .NET Framework 4.7 and are running on Windows operating systems starting with the Windows 10 Creators Update.</span></span>

<span data-ttu-id="2056a-115">Ayrıca, Windows Forms uygulamanızda yüksek DPı desteğini yapılandırmak için aşağıdakileri yapmanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="2056a-115">In addition, to configure high DPI support in your Windows Forms application, you must do the following:</span></span>

- <span data-ttu-id="2056a-116">Windows 10 ile uyumluluk bildirin.</span><span class="sxs-lookup"><span data-stu-id="2056a-116">Declare compatibility with Windows 10.</span></span>

  <span data-ttu-id="2056a-117">Bunu yapmak için bildirim dosyanıza aşağıdakileri ekleyin:</span><span class="sxs-lookup"><span data-stu-id="2056a-117">To do this, add the following to your manifest file:</span></span>

  ```xml
  <compatibility xmlns="urn:schemas-microsoft-com:compatibility.v1">
    <application>
      <!-- Windows 10 compatibility -->
      <supportedOS Id="{8e0f7a12-bfb3-4fe8-b9a5-48fd50a15a9a}" />
    </application>
  </compatibility>
  ```

- <span data-ttu-id="2056a-118">*app.config* dosyasında MONITÖR başına DPI tanımayı etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="2056a-118">Enable per-monitor DPI awareness in the *app.config* file.</span></span>

  <span data-ttu-id="2056a-119">Windows Forms [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) , .NET Framework 4,7 ' den başlayarak eklenen yeni özellikleri ve özelleştirmeleri desteklemek için yeni bir öğe kullanıma sunuyor.</span><span class="sxs-lookup"><span data-stu-id="2056a-119">Windows Forms introduces a new [`<System.Windows.Forms.ApplicationConfigurationSection>`](../configure-apps/file-schema/winforms/index.md) element to support new features and customizations added starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="2056a-120">Yüksek DPı 'yi destekleyen yeni özelliklerden yararlanmak için, uygulama yapılandırma dosyanıza aşağıdakini ekleyin.</span><span class="sxs-lookup"><span data-stu-id="2056a-120">To take advantage of the new features that support high DPI, add the following to your application configuration file.</span></span>

  ```xml
  <System.Windows.Forms.ApplicationConfigurationSection>
    <add key="DpiAwareness" value="PerMonitorV2" />
  </System.Windows.Forms.ApplicationConfigurationSection>
  ```

  > [!IMPORTANT]
  > <span data-ttu-id="2056a-121">.NET Framework önceki sürümlerinde, yüksek DPı desteği eklemek için bildirimi kullandınız.</span><span class="sxs-lookup"><span data-stu-id="2056a-121">In previous versions of the .NET Framework, you used the manifest to add high DPI support.</span></span> <span data-ttu-id="2056a-122">Bu yaklaşım artık önerilmez, çünkü app.config dosyasında tanımlanan ayarları geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="2056a-122">This approach is no longer recommended, since it overrides settings defined on the app.config file.</span></span>

- <span data-ttu-id="2056a-123">Statik yöntemi çağırın <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> .</span><span class="sxs-lookup"><span data-stu-id="2056a-123">Call the static <xref:System.Windows.Forms.Application.EnableVisualStyles%2A> method.</span></span>

  <span data-ttu-id="2056a-124">Bu, uygulama giriş noktandaki ilk yöntem çağrısı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2056a-124">This should be the first method call in your application entry point.</span></span> <span data-ttu-id="2056a-125">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="2056a-125">For example:</span></span>

  ```csharp
  static void Main()
  {
      Application.EnableVisualStyles();
      Application.SetCompatibleTextRenderingDefault(false);
      Application.Run(new Form2());
  }
  ```

## <a name="opting-out-of-individual-high-dpi-features"></a><span data-ttu-id="2056a-126">Tek başına yüksek DPı özelliklerinden çıkma</span><span class="sxs-lookup"><span data-stu-id="2056a-126">Opting out of individual high DPI features</span></span>

<span data-ttu-id="2056a-127">Değeri, `DpiAwareness` `PerMonitorV2` .NET Framework sürümleri tarafından desteklenen tüm yüksek DPI tanıma özelliklerinin .NET Framework 4,7 ' den itibaren ayarlanmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="2056a-127">Setting the `DpiAwareness` value to `PerMonitorV2` enables all high DPI awareness features supported by .NET Framework versions starting with the .NET Framework 4.7.</span></span> <span data-ttu-id="2056a-128">Genellikle, bu çoğu Windows Forms uygulama için yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="2056a-128">Typically, this is adequate for most Windows Forms applications.</span></span> <span data-ttu-id="2056a-129">Ancak, bir veya daha fazla ayrı özelliği devre dışı bırakmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2056a-129">However, you may want to opt out of one or more individual features.</span></span> <span data-ttu-id="2056a-130">Bunu yapmanın en önemli nedeni, mevcut uygulama kodunuzun bu özelliği zaten işlemektir.</span><span class="sxs-lookup"><span data-stu-id="2056a-130">The most important reason for doing this is that your existing application code already handles that feature.</span></span>  <span data-ttu-id="2056a-131">Örneğin, uygulamanız otomatik ölçeklendirmeyi işlediğinde, otomatik yeniden boyutlandırma özelliğini aşağıdaki gibi devre dışı bırakmak isteyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2056a-131">For example, if your application handles auto scaling, you might want to disable the auto-resizing feature as follows:</span></span>

```xml
<System.Windows.Forms.ApplicationConfigurationSection>
  <add key="DpiAwareness" value="PerMonitorV2" />
  <add key="EnableWindowsFormsHighDpiAutoResizing" value="false" />
</System.Windows.Forms.ApplicationConfigurationSection>
```

<span data-ttu-id="2056a-132">Tek tek anahtarların ve değerlerinin listesi için bkz. [Windows Forms Configuration öğesi ekleme](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span><span class="sxs-lookup"><span data-stu-id="2056a-132">For a list of individual keys and their values, see [Windows Forms Add Configuration Element](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md).</span></span>

## <a name="new-dpi-change-events"></a><span data-ttu-id="2056a-133">Yeni DPı değişiklik olayları</span><span class="sxs-lookup"><span data-stu-id="2056a-133">New DPI change events</span></span>

<span data-ttu-id="2056a-134">4,7 .NET Framework başlayarak, üç yeni olay dinamik DPı değişikliklerini programlı bir şekilde işleyebilsin:</span><span class="sxs-lookup"><span data-stu-id="2056a-134">Starting with the .NET Framework 4.7, three new events allow you to programmatically handle dynamic DPI changes:</span></span>

- <span data-ttu-id="2056a-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, bir denetimin DPı ayarı, onun üst denetimi veya formu için bir DPı değişiklik olayından sonra program aracılığıyla değiştirildiğinde tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="2056a-135"><xref:System.Windows.Forms.Control.DpiChangedAfterParent>, which is fired when the DPI setting for a control is changed programmatically after a DPI change event for it's parent control or form has occurred.</span></span>
- <span data-ttu-id="2056a-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, bir denetimin DPı ayarı, üst denetimi veya formu için bir DPı değişiklik olayından önce programlı olarak değiştirildiğinde harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2056a-136"><xref:System.Windows.Forms.Control.DpiChangedBeforeParent>, which is fired when the DPI setting for a control is changed programmatically before a DPI change event for its parent control or form has occurred.</span></span>
- <span data-ttu-id="2056a-137"><xref:System.Windows.Forms.Form.DpiChanged>, bu, formun görüntülenmekte olan görüntü cihazında DPı ayarı değiştiğinde harekete geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2056a-137"><xref:System.Windows.Forms.Form.DpiChanged>, which is fired when the DPI setting changes on the display device where the form is currently displayed.</span></span>

## <a name="new-helper-methods-and-properties"></a><span data-ttu-id="2056a-138">Yeni yardımcı yöntemler ve Özellikler</span><span class="sxs-lookup"><span data-stu-id="2056a-138">New helper methods and properties</span></span>

<span data-ttu-id="2056a-139">.NET Framework 4,7 Ayrıca, DPı ölçeklendirme hakkında bilgi sağlayan ve DPı ölçeklendirme gerçekleştirmenize olanak tanıyan bir dizi yeni yardımcı yöntem ve özellik ekler.</span><span class="sxs-lookup"><span data-stu-id="2056a-139">The .NET Framework 4.7 also adds a number of new helper methods and properties that provide information about DPI scaling and allow you to perform DPI scaling.</span></span> <span data-ttu-id="2056a-140">Bu güncelleştirmeler şunlardır:</span><span class="sxs-lookup"><span data-stu-id="2056a-140">These include:</span></span>

- <span data-ttu-id="2056a-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, bir değeri mantıksal değerinden cihaz pikseline dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="2056a-141"><xref:System.Windows.Forms.Control.LogicalToDeviceUnits%2A>, which converts a value from logical to device pixels.</span></span>

- <span data-ttu-id="2056a-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, bir bit eşlem resmini bir cihaz için mantıksal DPı 'ye ölçeklendirir.</span><span class="sxs-lookup"><span data-stu-id="2056a-142"><xref:System.Windows.Forms.Control.ScaleBitmapLogicalToDevice%2A>, which scales a bitmap image to the logical DPI for a device.</span></span>

- <span data-ttu-id="2056a-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, geçerli cihaz için DPı 'yı döndürür.</span><span class="sxs-lookup"><span data-stu-id="2056a-143"><xref:System.Windows.Forms.Control.DeviceDpi%2A>, which returns the DPI for the current device.</span></span>

## <a name="versioning-considerations"></a><span data-ttu-id="2056a-144">Sürüm oluşturma konuları</span><span class="sxs-lookup"><span data-stu-id="2056a-144">Versioning considerations</span></span>

<span data-ttu-id="2056a-145">.NET Framework 4,7 ve Windows 10 Creators Update üzerinde çalıştırmanın yanı sıra, uygulamanız da yüksek DPı geliştirmeleri ile uyumlu olmayan bir ortamda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="2056a-145">In addition to running on .NET Framework 4.7 and Windows 10 Creators Update, your application may also run in an environment in which it isn't compatible with high DPI improvements.</span></span> <span data-ttu-id="2056a-146">Bu durumda, uygulamanız için bir geri dönüş geliştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2056a-146">In this case, you'll need to develop a fallback for your application.</span></span> <span data-ttu-id="2056a-147">Ölçeklendirmeyi işlemek için [özel çizim](./controls/user-drawn-controls.md) gerçekleştirmek üzere bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="2056a-147">You can do this to perform [custom drawing](./controls/user-drawn-controls.md) to handle scaling.</span></span>

<span data-ttu-id="2056a-148">Bunu yapmak için uygulamanızın üzerinde çalıştığı işletim sistemini de belirlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="2056a-148">To do this, you also need to determine the operating system on which your app is running.</span></span> <span data-ttu-id="2056a-149">Bunu aşağıdaki gibi kodla yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2056a-149">You can do that with code like the following:</span></span>

```csharp
// Create a reference to the OS version of Windows 10 Creators Update.
Version OsMinVersion = new Version(10, 0, 15063, 0);

// Access the platform/version of the current OS.
Console.WriteLine(Environment.OSVersion.Platform.ToString());
Console.WriteLine(Environment.OSVersion.VersionString);

// Compare the current version to the minimum required version.
Console.WriteLine(Environment.OSVersion.Version.CompareTo(OsMinVersion));
```

<span data-ttu-id="2056a-150">Uygulamanızın, uygulama bildiriminde desteklenen bir işletim sistemi olarak listelenmediyse Windows 10 ' un başarıyla algılanmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="2056a-150">Note that your application won't successfully detect Windows 10 if it wasn't listed as a supported operating system in the application manifest.</span></span>

<span data-ttu-id="2056a-151">Ayrıca, uygulamanın oluşturulduğu .NET Framework sürümünü denetleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="2056a-151">You can also check the version of the .NET Framework that the application was built against:</span></span>

```csharp
Console.WriteLine(AppDomain.CurrentDomain.SetupInformation.TargetFrameworkName);
```

## <a name="see-also"></a><span data-ttu-id="2056a-152">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2056a-152">See also</span></span>

- [<span data-ttu-id="2056a-153">Windows Forms yapılandırma öğesi Ekle</span><span class="sxs-lookup"><span data-stu-id="2056a-153">Windows Forms Add Configuration Element</span></span>](../configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md)
- [<span data-ttu-id="2056a-154">Windows Forms Boyutunu ve Ölçeğini Ayarlama</span><span class="sxs-lookup"><span data-stu-id="2056a-154">Adjusting the Size and Scale of Windows Forms</span></span>](adjusting-the-size-and-scale-of-windows-forms.md)
