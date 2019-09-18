---
title: Fuslogvw.exe (Derleme Bağlaması Günlük Görüntüleyici)
ms.date: 03/30/2017
helpviewer_keywords:
- failed assembly binds
- Fuslogvw.exe
- displaying failed assembly bind details
- assemblies [.NET Framework], failed assembly binds
- locating assemblies
- Assembly Binding Log Viewer
ms.assetid: e32fa443-0778-4cc3-bf36-5c8ea297d296
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6077acab533ecb755ae42b7c4359a6c77ff33449
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044675"
---
# <a name="fuslogvwexe-assembly-binding-log-viewer"></a><span data-ttu-id="c7f45-102">Fuslogvw.exe (Derleme Bağlaması Günlük Görüntüleyici)</span><span class="sxs-lookup"><span data-stu-id="c7f45-102">Fuslogvw.exe (Assembly Binding Log Viewer)</span></span>

<span data-ttu-id="c7f45-103">Derleme Bağlama Kayıt Günlüğü Görüntüleyici derleme bağlamalar için ayrıntıları görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c7f45-103">The Assembly Binding Log Viewer displays details for assembly binds.</span></span> <span data-ttu-id="c7f45-104">Bu bilgiler .NET Framework'ün çalışma zamanında niye bir derlemeyi bulamadığını tanılamanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c7f45-104">This information helps you diagnose why the .NET Framework cannot locate an assembly at run time.</span></span> <span data-ttu-id="c7f45-105">Bu hatalar genellikle derlemenin yanlış yere yayınlanması sonucudur, geçerli olmayan yerel bir resim veya kültürlerin uyuşmayan bir sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="c7f45-105">These failures are usually the result of an assembly deployed to the wrong location, a native image that is no longer valid, or a mismatch in version numbers or cultures.</span></span> <span data-ttu-id="c7f45-106">Ortak dil çalışma zamanının bir derlemeyi bulma hatası genellikle uygulamanızda bir <xref:System.TypeLoadException> olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-106">The common language runtime's failure to locate an assembly typically shows up as a <xref:System.TypeLoadException> in your application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7f45-107">fuslogvw.exe'yi yönetici ayrıcalıklarıyla çalıştırmalısınız.</span><span class="sxs-lookup"><span data-stu-id="c7f45-107">You must run fuslogvw.exe with administrator privileges.</span></span>

<span data-ttu-id="c7f45-108">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="c7f45-109">Aracı çalıştırmak için, yönetici kimlik bilgileriyle Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-109">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7) with administrator credentials.</span></span> <span data-ttu-id="c7f45-110">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="c7f45-110">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="c7f45-111">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="c7f45-111">At the command prompt, type the following:</span></span>

```console
fuslogvw
```

<span data-ttu-id="c7f45-112">Görüntüleyici başarısız bağlanan her derleme için bir girdi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-112">The viewer displays an entry for each failed assembly bind.</span></span> <span data-ttu-id="c7f45-113">Her bir başarısızlık için, görüntüleyici bağlamayı ilklendirdiği uygulamayı açıklar; derleme isim, versiyon, kültür ve ortak anahtar dahil kördür; ve başarısızlığın tarih ve saati.</span><span class="sxs-lookup"><span data-stu-id="c7f45-113">For each failure, the viewer describes the application that initiated the bind; the assembly the bind is for, including name, version, culture and public key; and the date and time of the failure.</span></span>

### <a name="to-change-the-log-location-view"></a><span data-ttu-id="c7f45-114">Günlük konum görünümünü değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-114">To change the log location view</span></span>

1. <span data-ttu-id="c7f45-115">Tüm uygulama türleri için bağlama başarısızlıklarını görüntülemek için **varsayılan** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-115">Select the **Default** option button to view bind failures for all application types.</span></span> <span data-ttu-id="c7f45-116">Varsayılan olarak, wininet önbelleğinde disk üzerinde her kullanıcı dizini içinde günlük kayıtları depolanır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-116">By default, log entries are stored in per-user directories on disk in the wininet cache.</span></span>

2. <span data-ttu-id="c7f45-117">Belirttiğiniz özel bir dizinde bağlama başarısızlıklarını görüntülemek için **özel** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-117">Select the **Custom** option button to view bind failures in a custom directory that you specify.</span></span> <span data-ttu-id="c7f45-118">**Günlük ayarları** iletişim kutusundaki özel günlük konumunu geçerli bir dizin adına ayarlayarak, çalışma zamanının günlükleri depolamasını istediğiniz özel konumu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-118">You must specify the custom location where you want the runtime to store the logs by setting the custom log location in the **Log Settings** dialog to a valid directory name.</span></span> <span data-ttu-id="c7f45-119">Dizin temiz olmalıdır ve sadece çalışma zamanının oluşturduğu dosyaları içermelidir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-119">This directory should be clean, and only contain files that the runtime generates.</span></span> <span data-ttu-id="c7f45-120">Eğer günlüğe kaydedilecek hata üreten bir çalıştırılabilir dosya içeriyorsa, başarısızlık günlüğe kaydedilmeyecek çünkü araç çalıştırılabilir olanla aynı isimde bir dizin yaratmaya çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-120">If it contains an executable that generates a failure to be logged, the failure will not be logged because the tool tries to create a directory with the same name as the executable.</span></span> <span data-ttu-id="c7f45-121">Buna ek olarak, bir yürütülebilir çalıştırma denemesi bu günlük konumunda başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="c7f45-121">In addition, an attempt to run an executable from the log location will fail.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c7f45-122">Varsayılan bağlama konumu özel bağlama konumuna tercih edilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-122">The default bind location is preferable to the custom bind location.</span></span> <span data-ttu-id="c7f45-123">Wininet önbelleğindeki varsayılan bağlama konumu çalışma zamanını saklar ve otomatik olarak temizler. Eğer özel bir bağlama konumu belirlerseniz, onu temizlemek sizin sorumluluğunuzdadır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-123">The runtime stores the default bind location in the wininet cache, and therefore automatically cleans it out. If you specify a custom bind location, you are responsible for cleaning it out.</span></span>

### <a name="to-view-details-about-a-specific-failure"></a><span data-ttu-id="c7f45-124">Belirli bir kültür hakkında detayları görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-124">To view details about a specific failure</span></span>

1. <span data-ttu-id="c7f45-125">Görüntüleyiciden istenen uygulamanın girişini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-125">Select the application name of the desired entry in the viewer.</span></span>

2. <span data-ttu-id="c7f45-126">**Günlüğü görüntüle** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-126">Click the **View Log** button.</span></span> <span data-ttu-id="c7f45-127">Alternatif olarak, seçili girdiye çift tıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-127">Alternately, you can double-click the selected entry.</span></span>

    <span data-ttu-id="c7f45-128">Araç seçili bağlama başarısızlığı hakkında aşağıdaki ayrıntıları görüntüler:</span><span class="sxs-lookup"><span data-stu-id="c7f45-128">The tool displays the following details about the selected bind failure:</span></span>

    - <span data-ttu-id="c7f45-129">"Dosya bulunamadı" veya "sürüm uyuşmazlığı" gibi belirli nedenler bağlamayı başarısız yapabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-129">The specific reason the bind failed, such as "file not found" or "version mismatch".</span></span>

    - <span data-ttu-id="c7f45-130">Eğer varsa, adını, uygulamanın kök dizinini (AppBase) ve özel arama yolunun bir açıklamasını içeren bağlama ilklendiren uygulama hakkında bilgi.</span><span class="sxs-lookup"><span data-stu-id="c7f45-130">Information about the application that initiated the bind, including its name, the application's root directory (AppBase), and a description of the private search path, if there is one.</span></span>

    - <span data-ttu-id="c7f45-131">Derlemenin kimliğine araç tarafından bakılıyor.</span><span class="sxs-lookup"><span data-stu-id="c7f45-131">The identity of the assembly the tool is looking for.</span></span>

    - <span data-ttu-id="c7f45-132">Herhangi bir uygulama, Yayıncı veya Yönetici sürüm ilkeleri açıklamaya uygulanır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-132">A description of any Application, Publisher, or Administrator version policies that have been applied.</span></span>

    - <span data-ttu-id="c7f45-133">Derlemenin [genel derleme önbelleğinde](../app-domains/gac.md)bulunup bulunamamayacağı.</span><span class="sxs-lookup"><span data-stu-id="c7f45-133">Whether the assembly was found in the [global assembly cache](../app-domains/gac.md).</span></span>

    - <span data-ttu-id="c7f45-134">Tüm algılama URL'lerinin listesi.</span><span class="sxs-lookup"><span data-stu-id="c7f45-134">A list of all probing URLs.</span></span>

<span data-ttu-id="c7f45-135">Aşağıdaki örnek günlük girdisi başarısız bir derleme bağlama hakkında ayrıntılı bilgi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-135">The following sample log entry shows detailed information about a failed assembly bind.</span></span>

```output
*** Assembly Binder Log Entry  (3/5/2007 @ 12:54:20 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  C:\WINNT\Microsoft.NET\Framework\v2.0.50727\fusion.dll
Running under executable  C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\graphicfailtest.exe
--- A detailed error log follows.

=== Pre-bind state information ===
LOG: DisplayName = graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
 (Fully-specified)
LOG: Appbase = C:\Program Files\Microsoft.NET\FrameworkSDK\Samples\Tutorials\resourcesandlocalization\graphic\cs\
LOG: Initial PrivatePath = NULL
LOG: Dynamic Base = NULL
LOG: Cache Base = NULL
LOG: AppName = NULL
Calling assembly : graphicfailtest, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
===

LOG: Processing DEVPATH.
LOG: DEVPATH is not set. Falling through to regular bind.
LOG: Policy not being applied to reference at this time (private, custom, partial, or location-based assembly bind).
LOG: Post-policy reference: graphicfailtest.resources, Version=0.0.0.0, Culture=en-US, PublicKeyToken=null
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.DLL.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources.EXE.
LOG: Attempting download of new URL file:///C:/Program Files/Microsoft.NET/FrameworkSDK/Samples/Tutorials/resourcesandlocalization/graphic/cs/graphicfailtest.resources/graphicfailtest.resources.EXE.
LOG: All probing URLs attempted and failed.
```

### <a name="to-delete-a-single-entry-from-the-log"></a><span data-ttu-id="c7f45-136">Günlük kaydından tek bir girdiyi silmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-136">To delete a single entry from the log</span></span>

1. <span data-ttu-id="c7f45-137">Görüntüleyicide bir girdi seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-137">Select an entry in the viewer.</span></span>

2. <span data-ttu-id="c7f45-138">**Girişi Sil** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-138">Click the **Delete Entry** button.</span></span>

### <a name="to-delete-all-entries-from-the-log"></a><span data-ttu-id="c7f45-139">Günlükten bütün girdileri silmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-139">To delete all entries from the log</span></span>

- <span data-ttu-id="c7f45-140">**Tümünü Sil** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-140">Click the **Delete All** button.</span></span>

### <a name="to-refresh-the-user-interface"></a><span data-ttu-id="c7f45-141">Kullanıcı arabirimini yenilemek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-141">To refresh the user interface</span></span>

- <span data-ttu-id="c7f45-142">**Yenile** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-142">Click the **Refresh** button.</span></span> <span data-ttu-id="c7f45-143">Görüntüleyici çalışırken yeni günlük girdilerini otomatik olarak algılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-143">The viewer does not automatically detect new log entries while it is running.</span></span> <span data-ttu-id="c7f45-144">Bunları göstermek için **Yenile** düğmesini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-144">You must use the **Refresh** button to display them.</span></span>

### <a name="to-change-the-log-settings"></a><span data-ttu-id="c7f45-145">Günlük ayarlarını değiştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-145">To change the log settings</span></span>

- <span data-ttu-id="c7f45-146">**Ayarlar** düğmesine tıklayarak **günlük ayarları** iletişim kutusunu açın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-146">Click the **Settings** button to open the **Log Settings** dialog.</span></span>

### <a name="to-view-the-about-dialog"></a><span data-ttu-id="c7f45-147">Hakkında iletişim kutusunu görüntülemek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-147">To view the About dialog</span></span>

- <span data-ttu-id="c7f45-148">**Hakkında** düğmesine tıklayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-148">Click the **About** button.</span></span>

## <a name="binding-logs-for-native-images"></a><span data-ttu-id="c7f45-149">Özgün Görüntüler için Bağlama Günlükleri</span><span class="sxs-lookup"><span data-stu-id="c7f45-149">Binding Logs for Native Images</span></span>

<span data-ttu-id="c7f45-150">Varsayılan olarak, Fuslogvw.exe normal derleme bağlama isteklerini günlüğe kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c7f45-150">By default, Fuslogvw.exe logs normal assembly bind requests.</span></span> <span data-ttu-id="c7f45-151">Alternatif olarak, [Ngen. exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md)kullanılarak oluşturulan yerel görüntüler için derleme bağlamalarını günlüğe kaydedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-151">Alternatively, you can log assembly binds for native images that were created using the [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).</span></span>

#### <a name="to-log-assembly-binds-for-native-images"></a><span data-ttu-id="c7f45-152">Özgün görüntüler için derleme bağlamalarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-152">To log assembly binds for native images</span></span>

- <span data-ttu-id="c7f45-153">**Günlük kategorileri** grubunda, **Yerel görüntüler** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-153">In the **Log Categories** group, select the **Native Images** option button.</span></span>

<span data-ttu-id="c7f45-154">Aşağıdaki günlük kaydı uygulama için özgün görüntü oluştuğunda varolmayan bir bağımlılıktan kaynaklı bir başarısızlığı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-154">The following log shows a failure caused by a dependency that did not exist when the native image was created for the application.</span></span> <span data-ttu-id="c7f45-155">Eğer çalışma zamanındaki bağımlılık Ngen.exe çalışırken oluşan bağımlılıktan farklıysa, yerel bir görüntü bağlamaya izin vermez.</span><span class="sxs-lookup"><span data-stu-id="c7f45-155">If the dependencies at run time differ from the dependencies when Ngen.exe is run, binding to a native image is not allowed.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:22:07 PM) ***

The operation failed.
Bind result: hr = 0x80070002. The system cannot find the file specified.

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\App.exe
--- A detailed error log follows.

LOG: Start binding of native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\App.exe.
LOG: Start validating native image App, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency b, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
WRN: Dependency assembly was not found at ngen time, but is found at binding time. Disallow using this native image.
WRN: No matching native image found.
LOG: Bind to native image assembly did not succeed. Use IL image.
```

<span data-ttu-id="c7f45-156">Aşağıdaki günlük kaydı yerel görüntünün oluştuğu zamandaki güvenlik ayarlarından farklı bir uygulama çalıştığında bilgisayardaki güvenlik ayarlarından dolayı yerel bir görüntü bağlama başarısız olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-156">The following log shows a native image binding failure that occurred because the security settings on the computer when the application was run were different from the security settings at the time the native image was created.</span></span>

```output
*** Assembly Binder Log Entry  (12/8/2006 @ 5:29:09 PM) ***

The operation failed.
Bind result: hr = 0x80004005. Unspecified error

Assembly manager loaded from:  E:\Windows\Microsoft.NET\Framework64\v2.0.50727\mscorwks.dll
Running under executable  E:\test\Application101622.exe
--- A detailed error log follows.

LOG: Start binding of native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: IL assembly loaded from E:\test\Application101622.exe.
LOG: Start validating native image Application101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Start validating all the dependencies.
LOG: [Level 1]Start validating native image dependency mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.
LOG: Dependency evaluation succeeded.
LOG: [Level 1]Start validating IL dependency Dependency101622, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null.
LOG: Dependency evaluation succeeded.
LOG: Validation of dependencies succeeded.
LOG: Start loading all the dependencies into load context.
LOG: Loading of dependencies succeeded.
LOG: Bind to native image succeeded.
Native image has correct version information.
Attempting to use native image E:\Windows\assembly\NativeImages_v2.0.50727_64\Application101622\1ac7fadabec4f72575d807501e9fdc72\Application101622.ni.exe.
Rejecting native image because it failed the security check. The assembly's permissions must have changed since the time it was ngenned, or it is running with a different security context.
Discarding native image.
```

## <a name="the-log-settings-dialog"></a><span data-ttu-id="c7f45-157">Günlük Ayarları İletişim Kutusu</span><span class="sxs-lookup"><span data-stu-id="c7f45-157">The Log Settings Dialog</span></span>

<span data-ttu-id="c7f45-158">Aşağıdaki işlemleri gerçekleştirmek için **günlük ayarları** iletişim kutusunu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-158">You can use the **Log Settings** dialog to perform the following actions.</span></span>

#### <a name="to-disable-logging"></a><span data-ttu-id="c7f45-159">Günlüğe kaydetmeyi devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="c7f45-159">To disable logging</span></span>

- <span data-ttu-id="c7f45-160">**Devre dışı tut** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-160">Select the **Log disabled** option button.</span></span>  <span data-ttu-id="c7f45-161">Bu seçeneğin varsayılan olarak seçili geldiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-161">Note that this option is selected by default.</span></span>

#### <a name="to-log-assembly-binds-in-exceptions"></a><span data-ttu-id="c7f45-162">İstisnalar içinde derleme bağlamalarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-162">To log assembly binds in exceptions</span></span>

- <span data-ttu-id="c7f45-163">**Özel durum metni** seç seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-163">Select the **Log in exception text** option button.</span></span> <span data-ttu-id="c7f45-164">İstisna metninin içinde yalnızca füzyon günlük kaydı bilgileri kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-164">Only the least detailed fusion log information is logged in exception text.</span></span> <span data-ttu-id="c7f45-165">Tüm bilgileri görmek için diğer seçeneklerden birini kullanın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-165">To view full information, use one of the other settings.</span></span>

  <span data-ttu-id="c7f45-166">Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-166">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-assembly-bind-failures"></a><span data-ttu-id="c7f45-167">Derleme bağlama başarısızlıklarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-167">To log assembly bind failures</span></span>

- <span data-ttu-id="c7f45-168">**Disk bağlama başarısızlıklarını diske yaz** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-168">Select the **Log bind failures to disk** option button.</span></span>

  <span data-ttu-id="c7f45-169">Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-169">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

#### <a name="to-log-all-assembly-binds"></a><span data-ttu-id="c7f45-170">Tüm derleme bağlamalarını günlüğe kaydetmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-170">To log all assembly binds</span></span>

- <span data-ttu-id="c7f45-171">**Tümünü diske bağlar** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-171">Select the **Log all binds to disk** option button.</span></span>

  <span data-ttu-id="c7f45-172">Etki alanı nötr olarak yüklenen derlemelerle ilgili önemli bir not bırakın.</span><span class="sxs-lookup"><span data-stu-id="c7f45-172">See the Important note regarding assemblies that are loaded as domain neutral.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c7f45-173">Bir derleme etki alanı nötr olarak yüklendiğinde, örneğin <xref:System.AppDomainSetup.LoaderOptimization%2A> <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> özelliği veya <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>olarak ayarlandığında, günlüğü açma işlemi, bazı durumlarda bellek sızıntısına neden olur.</span><span class="sxs-lookup"><span data-stu-id="c7f45-173">When an assembly is loaded as domain neutral, for example by setting the <xref:System.AppDomainSetup.LoaderOptimization%2A> property to <xref:System.LoaderOptimization.MultiDomain?displayProperty=nameWithType> or <xref:System.LoaderOptimization.MultiDomainHost?displayProperty=nameWithType>, turning on logging might leak memory in some cases.</span></span> <span data-ttu-id="c7f45-174">Etki alanı nötr modu bir uygulama etki alanına yüklendiğinde ve uygulama etki alanı boşaltıldığında eğer günlük kaydı girişi yapılmışsa bu olur.</span><span class="sxs-lookup"><span data-stu-id="c7f45-174">This can happen if a log entry is made when a domain-neutral module is loaded into an application domain, and later the application domain is unloaded.</span></span> <span data-ttu-id="c7f45-175">Günlük girdisi işlem bitene kadar serbest bırakılmayabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-175">The log entry might not be released until the process ends.</span></span> <span data-ttu-id="c7f45-176">Bazı hata ayıklayıcılar otomatik olarak günlüğe kaydetmeyi etkinleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-176">Some debuggers automatically turn on logging.</span></span>

#### <a name="to-enable-a-custom-log-path"></a><span data-ttu-id="c7f45-177">Özel bir günlük kaydı yolunu etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-177">To enable a custom log path</span></span>

1. <span data-ttu-id="c7f45-178">**Özel günlük yolunu etkinleştir** seçenek düğmesini seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-178">Select the **Enable custom log path** option button.</span></span>

2. <span data-ttu-id="c7f45-179">Yolu **özel günlük yolu** metin kutusuna girin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-179">Enter the path into the **Custom log path** text box.</span></span>

> [!NOTE]
> <span data-ttu-id="c7f45-180">[Derleme bağlama günlük Görüntüleyicisi (Fuslogvw. exe)](fuslogvw-exe-assembly-binding-log-viewer.md) , bağlama günlüğünü depolamak Için Internet Explorer (IE) önbelleğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-180">The [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) uses the Internet Explorer (IE) cache to store its binding log.</span></span> <span data-ttu-id="c7f45-181">IE önbelleğinde zaman zaman bozulma nedeniyle, [derleme bağlama günlüğü Görüntüleyicisi (Fuslogvw. exe)](fuslogvw-exe-assembly-binding-log-viewer.md) bazen görüntüleme penceresinde yeni bağlama günlüklerini göstermeyi durdurabilir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-181">Due to occasional corruption in the IE cache, the [Assembly Binding Log Viewer (Fuslogvw.exe)](fuslogvw-exe-assembly-binding-log-viewer.md) can sometimes stop showing new binding logs in the viewing window.</span></span> <span data-ttu-id="c7f45-182">Bu bozulmanın sonucu olarak, .NET bağlama altyapısı (füzyon) bağlama günlüğüne yazamaz veya okuyamaz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-182">As a result of this corruption, the .NET binding infrastructure (fusion) cannot write to or read from the binding log.</span></span> <span data-ttu-id="c7f45-183">(Eğer özel günlük yolu kullanıyorsanız bu sorunla karşılaşmayabilirsiniz.)  Bozulmayı düzeltmek ve füzyonun bağlama günlük kayıtlarını tekrar göstermesine izin vermek için, IE Internet Seçenekleri iletişim kutusundan geçici internet dosyalarını silerek IE önbelleğini temizleyin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-183">(This issue is not encountered if you use a custom log path.)  To fix the corruption and allow fusion to show binding logs again, clear the IE cache by deleting temporary internet files from within the IE Internet Options dialog.</span></span>
>
> <span data-ttu-id="c7f45-184">Yönetilmeyen uygulamanız `IHostAssemblyManager` ve `IHostAssemblyStore` arabirimlerini uygulayarak ortak dil çalışma zamanını barındırıyorsa, günlük girişleri Wininet önbelleğinde depolanamaz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-184">If your unmanaged application hosts the common language runtime by implementing the `IHostAssemblyManager` and `IHostAssemblyStore` interfaces, log entries can't be stored in the wininet cache.</span></span>  <span data-ttu-id="c7f45-185">Bu arabirimleri uygulayan özel barındırmalar için günlük girdilerini görüntülemek için, alternatif bir günlük yolu belirtmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-185">To view log entries for custom hosts that implement these interfaces, you must specify an alternate log path.</span></span>

#### <a name="to-enable-logging-for-apps-running-in-the-windows-app-container"></a><span data-ttu-id="c7f45-186">Windows uygulama kapsayıcısı içinde çalışan uygulamalar için günlük kaydediciyi etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="c7f45-186">To enable logging for apps running in the Windows app container</span></span>

1. <span data-ttu-id="c7f45-187">Önceki prosedürde açıklandığı gibi özel bir günlük yolunu etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-187">Enable a custom log path, as described in the previous procedure.</span></span> <span data-ttu-id="c7f45-188">Varsayılan olarak, Windows uygulama kapsayıcı içinde çalışan uygulamaların hard disk erişimi sınırlıdır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-188">By default, apps that are running in the Windows app container have limited access to the hard disk.</span></span> <span data-ttu-id="c7f45-189">Uygulama kapsayıcı içerisindeki bütün uygulamalar için belirlediğiniz dizinin okuma/yazma erişim hakkı vardır.</span><span class="sxs-lookup"><span data-stu-id="c7f45-189">The directory you specify will have read/write access for all apps in the app container.</span></span>

2. <span data-ttu-id="c7f45-190">**Derinlikli günlüğü etkinleştir** onay kutusunu seçin.</span><span class="sxs-lookup"><span data-stu-id="c7f45-190">Select the **Enable immersive logging** check box.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c7f45-191">Bu kutu yalnızca Windows 8 veya sonrasında etkindir.</span><span class="sxs-lookup"><span data-stu-id="c7f45-191">This box is enabled only on Windows 8 or later.</span></span>

## <a name="see-also"></a><span data-ttu-id="c7f45-192">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7f45-192">See also</span></span>

- <xref:System.TypeLoadException>
- [<span data-ttu-id="c7f45-193">Araçlar</span><span class="sxs-lookup"><span data-stu-id="c7f45-193">Tools</span></span>](index.md)
- [<span data-ttu-id="c7f45-194">Genel Derleme Önbelleği</span><span class="sxs-lookup"><span data-stu-id="c7f45-194">Global Assembly Cache</span></span>](../app-domains/gac.md)
- [<span data-ttu-id="c7f45-195">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="c7f45-195">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="c7f45-196">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="c7f45-196">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
