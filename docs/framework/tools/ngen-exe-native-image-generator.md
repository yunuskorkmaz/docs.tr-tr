---
title: Ngen.exe (Yerel Görüntü Oluşturucu)
description: Yerel görüntü oluşturucuyu Ngen.exe gözden geçirin. Yerel görüntüler oluşturarak ve yerel yerel görüntü önbelleğine yükleyerek yönetilen uygulama performansını geliştirebilirsiniz.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Native Image Generator
- images [.NET Framework], native
- side-by-side execution, native images
- assemblies [.NET Framework], native image
- Ngen.exe
- native image generation
- native image cache
- publisher policy applied for native images
- invalid images
- BypassNGenAttribute
- System.Runtime.BypassNGenAttribute
ms.assetid: 44bf97aa-a9a4-4eba-9a0d-cfaa6fc53a66
ms.openlocfilehash: ae86aed773a9a13f102b1ad111cac5a3ee563508
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517275"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="e96ef-104">Ngen.exe (Yerel Görüntü Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="e96ef-104">Ngen.exe (Native Image Generator)</span></span>

<span data-ttu-id="e96ef-105">Yerel Görüntü Oluşturucusu (Ngen.exe), yönetilen uygulamaların performansını artıran bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-105">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="e96ef-106">Ngen.exe, işlemciye özel derlenmiş makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarın yerel görüntü önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-106">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="e96ef-107">Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-107">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-108">Ngen.exe, yalnızca .NET Framework hedefleyen derlemeler için yerel görüntüleri derler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-108">Ngen.exe compiles native images for assemblies that target the .NET Framework only.</span></span> <span data-ttu-id="e96ef-109">.NET Core için eşdeğer yerel görüntü Oluşturucu, [çapraz genel](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md)' tir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-109">The equivalent native image generator for .NET Core is [CrossGen](https://github.com/dotnet/runtime/blob/master/docs/workflow/building/coreclr/crossgen.md).</span></span>

<span data-ttu-id="e96ef-110">.NET Framework 4 ' te Ngen.exe değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="e96ef-110">Changes to Ngen.exe in the .NET Framework 4:</span></span>

- <span data-ttu-id="e96ef-111">Ngen.exe artık derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-111">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

- <span data-ttu-id="e96ef-112">Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-112">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>

<span data-ttu-id="e96ef-113">Ngen.exe'ye .NET Framework 2.0 içinde yapılan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="e96ef-113">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>

- <span data-ttu-id="e96ef-114">Bir derlemeyi yüklemek ayrıca bağımlılıklarını da yükleyerek Ngen.exe'nin sözdizimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-114">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>

- <span data-ttu-id="e96ef-115">Yerel görüntüler artık uygulama etki alanları arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-115">Native images can now be shared across application domains.</span></span>

- <span data-ttu-id="e96ef-116">Yeni bir eylem, `update` geçersiz kılınan görüntüleri yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-116">A new action, `update`, re-creates images that have been invalidated.</span></span>

- <span data-ttu-id="e96ef-117">Eylemler, görüntüleri oluşturmak ve yüklemek için bilgisayardaki boşta kalma süresini kullanan bir servis tarafından ertelenebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-117">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>

- <span data-ttu-id="e96ef-118">Görüntü geçersiz kılmanın bazı nedenleri kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="e96ef-118">Some causes of image invalidation have been eliminated.</span></span>

<span data-ttu-id="e96ef-119">Windows 8 ' de, [yerel görüntü görevi](#native-image-task)' ne bakın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-119">On Windows 8, see [Native Image Task](#native-image-task).</span></span>

<span data-ttu-id="e96ef-120">Ngen.exe ve yerel görüntü hizmetini kullanma hakkında daha fazla bilgi için bkz. [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="e96ef-120">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-121">.NET Framework 1,0 ve 1,1 sürümleri için Ngen.exe sözdizimi, [Yerel Görüntü Oluşturucu (Ngen.exe) eski sözdiziminde](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100))bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-121">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>

<span data-ttu-id="e96ef-122">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-122">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="e96ef-123">Aracı çalıştırmak için, Visual Studio için Geliştirici Komut İstemi (veya Windows 7 ' de Visual Studio komut Istemi) kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-123">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="e96ef-124">Daha fazla bilgi için bkz. [komut istemleri](developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="e96ef-124">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).</span></span>

<span data-ttu-id="e96ef-125">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="e96ef-125">At the command prompt, type the following:</span></span>

## <a name="syntax"></a><span data-ttu-id="e96ef-126">Syntax</span><span class="sxs-lookup"><span data-stu-id="e96ef-126">Syntax</span></span>

```console
ngen action [options]
```

```console
ngen /? | /help
```

## <a name="actions"></a><span data-ttu-id="e96ef-127">Eylemler</span><span class="sxs-lookup"><span data-stu-id="e96ef-127">Actions</span></span>

<span data-ttu-id="e96ef-128">Aşağıdaki tabloda, her birinin sözdizimi gösterilmektedir `action` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-128">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="e96ef-129">Tek tek bölümlerinin açıklamaları için `action` bkz. [bağımsız değişkenler](#ArgumentTable), [Öncelik düzeyleri](#PriorityTable), [senaryolar](#ScenarioTable)ve [yapılandırma](#ConfigTable) tabloları.</span><span class="sxs-lookup"><span data-stu-id="e96ef-129">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="e96ef-130">[Seçenekler](#OptionTable) tablosu `options` ve yardım anahtarlarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-130">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>

|<span data-ttu-id="e96ef-131">Eylem</span><span class="sxs-lookup"><span data-stu-id="e96ef-131">Action</span></span>|<span data-ttu-id="e96ef-132">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-132">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="e96ef-133">`install`[ `assemblyName` &#124; `assemblyPath` ] [ `scenarios` ] [ `config` ] [ `/queue` [ `:` { `1`&#124;`2`&#124;`3` }]]</span><span class="sxs-lookup"><span data-stu-id="e96ef-133">`install` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="e96ef-134">Bir derleme ve bağımlılıkları için yerel görüntüler oluştur ve görüntüleri yerel görüntü önbelleğine yükle.</span><span class="sxs-lookup"><span data-stu-id="e96ef-134">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="e96ef-135">`/queue`Belirtilmişse, eylem yerel görüntü hizmeti için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-135">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="e96ef-136">Varsayılan öncelik 3'tür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-136">The default priority is 3.</span></span> <span data-ttu-id="e96ef-137">[Öncelik düzeyleri](#PriorityTable) tablosuna bakın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-137">See the [Priority Levels](#PriorityTable) table.</span></span>|
|<span data-ttu-id="e96ef-138">`uninstall`[ `assemblyName` &#124; `assemblyPath` ] [ `scenarios` ] [ `config` ]</span><span class="sxs-lookup"><span data-stu-id="e96ef-138">`uninstall` [`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="e96ef-139">Bir derleme ve bağımlılıklarının yerel görüntülerini yerel görüntü önbelleğinden sil.</span><span class="sxs-lookup"><span data-stu-id="e96ef-139">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="e96ef-140">Tek bir görüntüyü ve bağımlılıklarını kaldırmak için, görüntüyü yüklemek için kullanılan aynı komut satırı bağımsız değişkenlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-140">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="e96ef-141">**Note:**  .NET Framework 4 ' te başlayarak, eylem `uninstall` \* artık desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-141">**Note:**  Starting with the .NET Framework 4, the action `uninstall` \* is no longer supported.</span></span>|
|<span data-ttu-id="e96ef-142">`update` [`/queue`]</span><span class="sxs-lookup"><span data-stu-id="e96ef-142">`update` [`/queue`]</span></span>|<span data-ttu-id="e96ef-143">Geçersiz olan yerel görüntüleri güncelleştir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-143">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="e96ef-144">`/queue`Belirtilmişse, güncelleştirmeler yerel görüntü hizmeti için sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-144">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="e96ef-145">Güncelleştirmeler her zaman 3 önceliğindedir ve bilgisayar boşta olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-145">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|
|<span data-ttu-id="e96ef-146">`display`[ `assemblyName` &#124; `assemblyPath` ]</span><span class="sxs-lookup"><span data-stu-id="e96ef-146">`display` [`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="e96ef-147">Bir derleme ve bağımlılıkları için yerel görüntülerin durumunu görüntüle.</span><span class="sxs-lookup"><span data-stu-id="e96ef-147">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="e96ef-148">Eğer bağımsız değişken sağlanmazsa, yerel görüntü önbelleğindeki her şey görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-148">If no argument is supplied, everything in the native image cache is displayed.</span></span>|
|<span data-ttu-id="e96ef-149">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="e96ef-149">`executeQueuedItems` [<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="e96ef-150">-veya-</span><span class="sxs-lookup"><span data-stu-id="e96ef-150">-or-</span></span><br /><br /> <span data-ttu-id="e96ef-151">`eqi`[1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="e96ef-151">`eqi` [1&#124;2&#124;3]</span></span>|<span data-ttu-id="e96ef-152">Sıraya alınan derleme işlerini yürüt.</span><span class="sxs-lookup"><span data-stu-id="e96ef-152">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="e96ef-153">Eğer bir öncelik belirtilirse, ona eşit veya daha büyük önceliğe sahip derleme işleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-153">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="e96ef-154">Eğer öncelik belirtilmezse, sıraya alınan tüm derleme işleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-154">If no priority is specified, all queued compilation jobs are executed.</span></span>|
|<span data-ttu-id="e96ef-155">`queue`{ `pause` &#124; `continue` &#124; `status` }</span><span class="sxs-lookup"><span data-stu-id="e96ef-155">`queue` {`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="e96ef-156">Yerel görüntü hizmetini duraklat, duraklatılan hizmetin devam etmesine izin ver veya hizmetin durumunu sorgula.</span><span class="sxs-lookup"><span data-stu-id="e96ef-156">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|

<a name="ArgumentTable"></a>

## <a name="arguments"></a><span data-ttu-id="e96ef-157">Arguments</span><span class="sxs-lookup"><span data-stu-id="e96ef-157">Arguments</span></span>

|<span data-ttu-id="e96ef-158">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="e96ef-158">Argument</span></span>|<span data-ttu-id="e96ef-159">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-159">Description</span></span>|
|--------------|-----------------|
|`assemblyName`|<span data-ttu-id="e96ef-160">Derlemenin tam görünen adı.</span><span class="sxs-lookup"><span data-stu-id="e96ef-160">The full display name of the assembly.</span></span> <span data-ttu-id="e96ef-161">Örneğin, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span><span class="sxs-lookup"><span data-stu-id="e96ef-161">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="e96ef-162">**Note:**  `myAssembly`Ve eylemleri için gibi kısmi bir derleme adı sağlayabilirsiniz `display` `uninstall` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-162">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="e96ef-163">Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|
|`assemblyPath`|<span data-ttu-id="e96ef-164">Derlemenin açık yolu.</span><span class="sxs-lookup"><span data-stu-id="e96ef-164">The explicit path of the assembly.</span></span> <span data-ttu-id="e96ef-165">Tam veya göreli bir yol belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-165">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="e96ef-166">Eğer bir yol belirtmeden dosya adı belirtilseniz, derleme geçerli dizinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-166">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="e96ef-167">Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-167">Only one assembly can be specified per Ngen.exe command line.</span></span>|

<a name="PriorityTable"></a>

## <a name="priority-levels"></a><span data-ttu-id="e96ef-168">Öncelik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="e96ef-168">Priority Levels</span></span>

|<span data-ttu-id="e96ef-169">Öncelik</span><span class="sxs-lookup"><span data-stu-id="e96ef-169">Priority</span></span>|<span data-ttu-id="e96ef-170">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-170">Description</span></span>|
|--------------|-----------------|
|`1`|<span data-ttu-id="e96ef-171">Yerel görüntüler, boşta kalma süresi beklenmeden hemen oluşturulur ve yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-171">Native images are generated and installed immediately, without waiting for idle time.</span></span>|
|`2`|<span data-ttu-id="e96ef-172">Yerel görüntüler boşta kalma süresi beklenmeden, ancak tüm 1 öncelikli eylemler (ve bağımlılıkları) tamamlandıktan sonra yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-172">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|
|`3`|<span data-ttu-id="e96ef-173">Yerel görüntüler, yerel görüntü hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-173">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="e96ef-174">Bkz. [yerel görüntü hizmeti](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="e96ef-174">See [Native Image Service](#native-image-service).</span></span>|

<a name="ScenarioTable"></a>

## <a name="scenarios"></a><span data-ttu-id="e96ef-175">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="e96ef-175">Scenarios</span></span>

|<span data-ttu-id="e96ef-176">Senaryo</span><span class="sxs-lookup"><span data-stu-id="e96ef-176">Scenario</span></span>|<span data-ttu-id="e96ef-177">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-177">Description</span></span>|
|--------------|-----------------|
|`/Debug`|<span data-ttu-id="e96ef-178">Bir hata ayıklayıcı altında kullanılabilen yerel görüntüler oluştur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-178">Generate native images that can be used under a debugger.</span></span>|
|`/Profile`|<span data-ttu-id="e96ef-179">Bir profil oluşturucu altında kullanılabilen yerel görüntüler oluştur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-179">Generate native images that can be used under a profiler.</span></span>|
|`/NoDependencies`|<span data-ttu-id="e96ef-180">Belirli senaryo seçeneklerinin gerektirdiği en az sayıda yerel görüntü oluştur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-180">Generate the minimum number of native images required by the specified scenario options.</span></span>|

<a name="ConfigTable"></a>

## <a name="config"></a><span data-ttu-id="e96ef-181">Config</span><span class="sxs-lookup"><span data-stu-id="e96ef-181">Config</span></span>

|<span data-ttu-id="e96ef-182">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e96ef-182">Configuration</span></span>|<span data-ttu-id="e96ef-183">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-183">Description</span></span>|
|-------------------|-----------------|
|<span data-ttu-id="e96ef-184">`/ExeConfig:` `exePath`</span><span class="sxs-lookup"><span data-stu-id="e96ef-184">`/ExeConfig:` `exePath`</span></span>|<span data-ttu-id="e96ef-185">Belirtilen çalıştırılabilir derlemesinin yapılandırmasını kullan.</span><span class="sxs-lookup"><span data-stu-id="e96ef-185">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="e96ef-186">Ngen.exe, bağımlılıklara bağlarken yükleyici ile aynı kararları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-186">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="e96ef-187">Çalışma zamanında paylaşılan bir bileşen yüklendiğinde, yöntemi kullanılarak, <xref:System.Reflection.Assembly.Load%2A> uygulamanın yapılandırma dosyası paylaşılan bileşen için yüklenen bağımlılıkları belirler — örneğin, yüklenen bir bağımlılığın sürümü.</span><span class="sxs-lookup"><span data-stu-id="e96ef-187">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="e96ef-188">`/ExeConfig`Anahtar, çalışma zamanında hangi bağımlılıkların yüklenebileceğine ilişkin Ngen.exe rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-188">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|
|<span data-ttu-id="e96ef-189">`/AppBase:` `directoryPath`</span><span class="sxs-lookup"><span data-stu-id="e96ef-189">`/AppBase:` `directoryPath`</span></span>|<span data-ttu-id="e96ef-190">Bağımlılıkları bulurken, uygulama tabanı olarak belirtilen dizini kullan.</span><span class="sxs-lookup"><span data-stu-id="e96ef-190">When locating dependencies, use the specified directory as the application base.</span></span>|

<a name="OptionTable"></a>

## <a name="options"></a><span data-ttu-id="e96ef-191">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="e96ef-191">Options</span></span>

|<span data-ttu-id="e96ef-192">Seçenek</span><span class="sxs-lookup"><span data-stu-id="e96ef-192">Option</span></span>|<span data-ttu-id="e96ef-193">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e96ef-193">Description</span></span>|
|------------|-----------------|
|`/nologo`|<span data-ttu-id="e96ef-194">Microsoft başlangıç başlığını bastır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-194">Suppress the Microsoft startup banner display.</span></span>|
|`/silent`|<span data-ttu-id="e96ef-195">Başarı iletilerinin görüntülenmesini bastır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-195">Suppress the display of success messages.</span></span>|
|`/verbose`|<span data-ttu-id="e96ef-196">Hata ayıklama için ayrıntılı bilgi görüntüle.</span><span class="sxs-lookup"><span data-stu-id="e96ef-196">Display detailed information for debugging.</span></span> <span data-ttu-id="e96ef-197">**Note:**  İşletim sistemi sınırlamaları nedeniyle, bu seçenek Windows 98 ve Windows Millennium Edition hakkında daha fazla bilgi göstermez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-197">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|
|<span data-ttu-id="e96ef-198">`/help`, `/?`</span><span class="sxs-lookup"><span data-stu-id="e96ef-198">`/help`, `/?`</span></span>|<span data-ttu-id="e96ef-199">Geçerli yayın için komut sözdizimi ve seçenekleri görüntüle.</span><span class="sxs-lookup"><span data-stu-id="e96ef-199">Display command syntax and options for the current release.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e96ef-200">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e96ef-200">Remarks</span></span>

<span data-ttu-id="e96ef-201">Ngen.exe'yi çalıştırabilmek için yönetici ayrıcalıklarınızın olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-201">To run Ngen.exe, you must have administrative privileges.</span></span>

> [!CAUTION]
> <span data-ttu-id="e96ef-202">Ngen.exe'yi tam güvenilir olmayan derlemeler üzerinde çalıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-202">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="e96ef-203">.NET Framework 4 ' den başlayarak Ngen.exe, derlemeleri tam güvenle derler ve kod erişim güvenliği (CAS) ilkesi artık değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-203">Starting with the .NET Framework 4, Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>

<span data-ttu-id="e96ef-204">.NET Framework 4 ' te başlayarak, Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamalara yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-204">Starting with the .NET Framework 4, the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="e96ef-205">Bunun yerine anlık (JIT) derleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-205">Instead, the just-in-time (JIT) compiler is invoked.</span></span>

<span data-ttu-id="e96ef-206">Ngen.exe, `assemblyname` `install` eylem ve tüm bağımlılıkları için bağımsız değişken tarafından belirtilen derleme için yerel görüntüler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-206">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="e96ef-207">Bağlılıklar derleme bildirisindeki referanslar ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-207">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="e96ef-208">Bir bağımlılığı ayrı olarak yüklemeniz gereken tek senaryo, uygulamanın, örneğin metodunu çağırarak, yansıma kullanarak yüklediğinde <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e96ef-208">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e96ef-209"><xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>Yöntemini yerel görüntülerle kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-209">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="e96ef-210">Bu metotla yüklenen bir görüntü, yürütme bağlamındaki diğer derlemeler tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-210">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>

<span data-ttu-id="e96ef-211">Ngen.exe bağımlılıklar için bir sayaç tutar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-211">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="e96ef-212">Örneğin, `MyAssembly.exe` `YourAssembly.exe` hem yerel görüntü önbelleğinde hem de ' nin her ikisinin de ' de yüklü olduğunu varsayalım `OurDependency.dll` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-212">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="e96ef-213">`MyAssembly.exe`Kaldırılırsa, `OurDependency.dll` kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-213">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="e96ef-214">Yalnızca Ayrıca kaldırıldığında kaldırılır `YourAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-214">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>

<span data-ttu-id="e96ef-215">Eğer genel derleme önbelleğindeki bir derleme için doğal görüntü üretiyorsanız, onun görünür ismini belirtiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-215">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="e96ef-216">Bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e96ef-216">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e96ef-217">Ngen.exe'nin ürettiği doğal görüntüler uygulama alanı içerisinde paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-217">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="e96ef-218">Bu, Ngen.exe'yi derlemelerin uygulama etki alanları arasında paylaşılması gerektiği senaryolarda kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-218">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="e96ef-219">Alan bağımsızlığını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="e96ef-219">To specify domain neutrality:</span></span>

- <span data-ttu-id="e96ef-220"><xref:System.LoaderOptimizationAttribute>Özniteliği uygulamanıza uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-220">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>

- <span data-ttu-id="e96ef-221"><xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType>Yeni bir uygulama etki alanı için kurulum bilgilerini oluştururken özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-221">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>

<span data-ttu-id="e96ef-222">Birden çok uygulama alanına aynı derleme yüklediğiniz zaman mutlaka alan-bağımsız kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-222">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="e96ef-223">Eğer bir doğal görüntü paylaşılmış alana yüklendikten sonra paylaşılmamış alana yüklenirse, görüntü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-223">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-224">Alan-bağımsız kod yüklemesi geri alınamaz (geri döndürülemez) ve performans, özellikle statik elemanlara erişildiği zaman, çok az daha yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-224">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>

<span data-ttu-id="e96ef-225">Bu açıklamalar bölümünde:</span><span class="sxs-lookup"><span data-stu-id="e96ef-225">In this Remarks section:</span></span>

- [<span data-ttu-id="e96ef-226">Farklı senaryolar için görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e96ef-226">Generating images for different scenarios</span></span>](#Scenarios)

- [<span data-ttu-id="e96ef-227">Yerel görüntülerin ne zaman kullanılacağını belirleme</span><span class="sxs-lookup"><span data-stu-id="e96ef-227">Determining when to Use native images</span></span>](#WhenToUse)

  - [<span data-ttu-id="e96ef-228">İyileştirilmiş bellek kullanımı</span><span class="sxs-lookup"><span data-stu-id="e96ef-228">Improved memory use</span></span>](#Memory)

  - [<span data-ttu-id="e96ef-229">Daha hızlı uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="e96ef-229">Faster application startup</span></span>](#Startup)

  - [<span data-ttu-id="e96ef-230">Kullanım konularının Özeti</span><span class="sxs-lookup"><span data-stu-id="e96ef-230">Summary of usage considerations</span></span>](#UsageSummary)

- [<span data-ttu-id="e96ef-231">Derleme temel adreslerinin önemi</span><span class="sxs-lookup"><span data-stu-id="e96ef-231">Importance of assembly base addresses</span></span>](#BaseAddresses)

- [<span data-ttu-id="e96ef-232">Sabit bağlama</span><span class="sxs-lookup"><span data-stu-id="e96ef-232">Hard binding</span></span>](#HardBinding)

  - [<span data-ttu-id="e96ef-233">Bağımlılık için bağlama ipucu belirtme</span><span class="sxs-lookup"><span data-stu-id="e96ef-233">Specifying a binding hint for a dependency</span></span>](#DependencyHint)

  - [<span data-ttu-id="e96ef-234">Derleme için varsayılan bağlama ipucu belirtme</span><span class="sxs-lookup"><span data-stu-id="e96ef-234">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)

- [<span data-ttu-id="e96ef-235">Ertelenmiş işleme</span><span class="sxs-lookup"><span data-stu-id="e96ef-235">Deferred processing</span></span>](#Deferred)

- [<span data-ttu-id="e96ef-236">Yerel görüntüler ve JıT derlemesi</span><span class="sxs-lookup"><span data-stu-id="e96ef-236">Native images and JIT compilation</span></span>](#JITCompilation)

  - [<span data-ttu-id="e96ef-237">Geçersiz görüntüler</span><span class="sxs-lookup"><span data-stu-id="e96ef-237">Invalid images</span></span>](#InvalidImages)

- [<span data-ttu-id="e96ef-238">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e96ef-238">Troubleshooting</span></span>](#Troubleshooting)

  - [<span data-ttu-id="e96ef-239">Derleme Bağlaması Günlük Görüntüleyici</span><span class="sxs-lookup"><span data-stu-id="e96ef-239">Assembly Binding Log Viewer</span></span>](#Fusion)

  - [<span data-ttu-id="e96ef-240">Jıtcompilationstart yönetilen hata ayıklama Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="e96ef-240">The JITCompilationStart managed debugging assistant</span></span>](#MDA)

  - [<span data-ttu-id="e96ef-241">Yerel görüntü oluşturmayı geri alma</span><span class="sxs-lookup"><span data-stu-id="e96ef-241">Opting out of native image generation</span></span>](#OptOut)

<a name="Scenarios"></a>

## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="e96ef-242">Farklı senaryolar için görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="e96ef-242">Generating images for     different scenarios</span></span>

<span data-ttu-id="e96ef-243">Bir derleme için yerel görüntü oluşturduktan sonra, çalışma zamanı derlemeyi her çalıştırdığında otomatik olarak bu yerel görüntüyü bulmayı ve kullanmayı dener.</span><span class="sxs-lookup"><span data-stu-id="e96ef-243">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="e96ef-244">Kullanım senaryolarına göre, birden fazla görüntüler oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-244">Multiple images can be generated, depending on usage scenarios.</span></span>

<span data-ttu-id="e96ef-245">Örneğin, bir derlemeyi hata ayıklama veya profil oluşturma senaryosunda çalıştırırsanız, çalışma zamanı veya seçenekleriyle oluşturulan yerel bir görüntüyü arar `/Debug` `/Profile` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-245">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="e96ef-246">Eğer eşleşen bir doğal görüntü bulamazsa, çalışma zamanı standart JIT derlemesine geri döner.</span><span class="sxs-lookup"><span data-stu-id="e96ef-246">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="e96ef-247">Yerel görüntülerde hata ayıklamanın tek yolu, seçeneğiyle yerel bir görüntü oluşturmaktır `/Debug` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-247">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>

<span data-ttu-id="e96ef-248">`uninstall`Eylem Ayrıca senaryoları tanır, bu sayede tüm senaryoları veya yalnızca seçili senaryoları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-248">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>

<a name="WhenToUse"></a>

## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="e96ef-249">Yerel görüntülerin ne zaman kullanılacağını belirleme</span><span class="sxs-lookup"><span data-stu-id="e96ef-249">Determining when to Use native images</span></span>

<span data-ttu-id="e96ef-250">Yerel görüntüler iki alanda performans iyileştirmesi sağlayabilir: daha iyi bellek kullanımı ve daha az başlangıç zamanı.</span><span class="sxs-lookup"><span data-stu-id="e96ef-250">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-251">Yerel görüntülerin performansı; kod ve veri erişim desenleri, modül sınırları dışına yapılan çağrı sayısı ve diğer uygulamalar tarafından şimdiye kadar yüklenmiş olan bağımlılık sayısı gibi analizi zorlaştıran çeşitli etkenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-251">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="e96ef-252">Yerel görüntülerin uygulamanıza yararlı olup olmadığını belirlemenin tek yolu, anahtar dağıtım senaryolarınızda yapacağını dikkatli performans ölçümleridir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-252">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>

<a name="Memory"></a>

### <a name="improved-memory-use"></a><span data-ttu-id="e96ef-253">İyileştirilmiş bellek kullanımı</span><span class="sxs-lookup"><span data-stu-id="e96ef-253">Improved memory use</span></span>

<span data-ttu-id="e96ef-254">Yerel görüntüler kod işlemler arasında paylaşıldığında bellek kullanımını önemli ölçüde iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-254">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="e96ef-255">Yerel görüntüler Windows PE dosyalarıdır, yani bir .dll dosyasının tek kopyası birden çok işlem tarafından paylaşılabilir; buna karşılık, JIT derleyicisi tarafından üretilen yerel kod özel bellekte tutulur ve paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-255">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>

<span data-ttu-id="e96ef-256">Terminal hizmetleri altında çalışan uygulamalar da paylaşılan kod sayfalarından yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-256">Applications that are run under terminal services can also benefit from shared code pages.</span></span>

<span data-ttu-id="e96ef-257">Ek olarak, JIT derleyicisini yüklememek her uygulama örneği için sabit bir miktarda bellek kazandırır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-257">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>

<a name="Startup"></a>

### <a name="faster-application-startup"></a><span data-ttu-id="e96ef-258">Daha hızlı uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="e96ef-258">Faster application startup</span></span>

<span data-ttu-id="e96ef-259">Derlemeleri Ngen.exe ile ön derlemek bazı uygulamalar için başlangıç süresini iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-259">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="e96ef-260">Genel olarak, uygulamalar bileşen derlemelerini paylaştığında kazanç olabilir, çünkü ilk uygulama başladıktan sonra paylaşılan bileşenler sonraki uygulamalar için zaten yüklü olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-260">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="e96ef-261">Uygulamadaki tüm derlemelerin sabit diskten yüklenmesini gerektiren soğuk başlangıç yerel görüntülerden pek fayda kazanmaz, çünkü sabit disk erişim süresi baskın olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-261">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>

<span data-ttu-id="e96ef-262">Sabit bağlama başlatma süresini etkileyebilir, çünkü ana uygulama derlemesine sabit bağlı olan tüm resimler aynı anda yüklenmelidirler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-262">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-263">.NET Framework 3,5 hizmet paketi 1 ' den önce, yükleyici genel derleme önbelleğinde olmayan, paylaşılan ve tanımlayıcı adlandırılmış bir bileşen yerleştirmelisiniz, çünkü yükleyici, genel derleme önbelleğinde olmayan, kesin adlandırılmış derlemelerde daha fazla doğrulama gerçekleştirerek, yerel görüntüler kullanarak elde edilen başlatma sırasında tüm gelişmeleri etkin bir şekilde ortadan kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-263">Before the .NET Framework 3.5 Service Pack 1, you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="e96ef-264">.NET Framework 3,5 SP1'DE tanıtılan iyileştirmeler, ek doğrulamayı kaldırdı.</span><span class="sxs-lookup"><span data-stu-id="e96ef-264">Optimizations that were introduced in the .NET Framework 3.5 SP1 removed the extra validation.</span></span>

<a name="UsageSummary"></a>

### <a name="summary-of-usage-considerations"></a><span data-ttu-id="e96ef-265">Kullanım konularının Özeti</span><span class="sxs-lookup"><span data-stu-id="e96ef-265">Summary of usage considerations</span></span>

<span data-ttu-id="e96ef-266">Aşağıdaki genel önemli noktalar ve uygulama önemli noktaları uygulamanız için yerel görüntüleri değerlendirmek üzere çaba harcayıp harcamamaya karar vermenize yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-266">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>

- <span data-ttu-id="e96ef-267">Yerel görüntüler MSIL'den daha hızlı yüklenir çünkü JIT derlemesi ve tür güvenliği doğrulaması gibi pek çok başlangıç aktivitesine gereksinimi ortadan kaldırırlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-267">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>

- <span data-ttu-id="e96ef-268">Yerel görüntüler daha küçük ilk çalışma kümesi gerektirirler çünkü JIT derleyicisine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-268">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>

- <span data-ttu-id="e96ef-269">Yerel görüntüler işlemler arasında kod paylaşımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-269">Native images enable code sharing between processes.</span></span>

- <span data-ttu-id="e96ef-270">Yerel görüntüler MSIL derlemelerinden daha fazla sabit disk alanı gerektirir ve üretmek için büyük miktarda zaman gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-270">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>

- <span data-ttu-id="e96ef-271">Yerel görüntüler bakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-271">Native images must be maintained.</span></span>

  - <span data-ttu-id="e96ef-272">Orijinal derleme veya bağımlılıklarından biri değiştiğinde görüntüler yeniden oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-272">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>

  - <span data-ttu-id="e96ef-273">Tek bir derleme farklı uygulamalarda ya da farklı senaryolarda kullanılması için birden çok yerel görüntüye ihtiyaç duyabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-273">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="e96ef-274">Örneğin, iki uygulamadaki yapılandırma bilgileri aynı bağımlı derleme için farklı bağlama kararlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-274">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>

  - <span data-ttu-id="e96ef-275">Yerel görüntüler bir yönetici, yani Yöneticiler grubu içindeki bir Windows hesabı, tarafından üretilmelidir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-275">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>

<span data-ttu-id="e96ef-276">Bu genel önemli noktalara ek olarak, yerel görüntülerin bir performans kazancı sağlayıp sağlamayacağını belirlerken uygulamanızın doğası da göz önüne alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="e96ef-276">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>

- <span data-ttu-id="e96ef-277">Eğer uygulamanız pek çok paylaşılan bileşen kullanan bir ortamda çalışıyorsa, yerel görüntüler bileşenlerin birden çok işlem tarafından paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-277">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>

- <span data-ttu-id="e96ef-278">Eğer uygulamanız birden çok uygulama alanı kullanıyorsa, yerel görüntüler alanlar arasında kod sayfalarının paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-278">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>

    > [!NOTE]
    > <span data-ttu-id="e96ef-279">.NET Framework 1.0 ve 1.1 sürümlerinde, yerel görüntüler uygulama etki alanları arasında paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-279">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="e96ef-280">Bu, sürüm 2.0 ve sonrasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-280">This is not the case in version 2.0 or later.</span></span>

- <span data-ttu-id="e96ef-281">Eğer uygulamanız Terminal Server altında çalışacaksa, yerel görüntüler kod sayfalarının paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-281">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>

- <span data-ttu-id="e96ef-282">Büyük uygulamalar yerel görüntülere derlemekten genellikle yarar görür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-282">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="e96ef-283">Küçük uygulamalar genellikle yarar görmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-283">Small applications generally do not benefit.</span></span>

- <span data-ttu-id="e96ef-284">Uzun süre çalışan uygulamalarda, çalışma zamanı JIT derlemesi yerel görüntülerden biraz daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-284">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="e96ef-285">(Sabit bağlama bu performans farkını belirli bir ölçüde azaltabilir.)</span><span class="sxs-lookup"><span data-stu-id="e96ef-285">(Hard binding can mitigate this performance difference to some degree.)</span></span>

<a name="BaseAddresses"></a>

## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="e96ef-286">Derleme temel adreslerinin önemi</span><span class="sxs-lookup"><span data-stu-id="e96ef-286">Importance of assembly base addresses</span></span>

<span data-ttu-id="e96ef-287">Yerel görüntüler Windows PE dosyaları olduğu için, diğer çalıştırılabilir dosyalardaki aynı yeniden temellendirme sorunlarıyla karşılaşırlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-287">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="e96ef-288">Eğer sıkı bağlama kullanılırsa, yeniden konumlandırmanın performans maliyeti daha da belirgin olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-288">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>

<span data-ttu-id="e96ef-289">Bir yerel görüntü için temel adresi ayarlamak için, derlemenin temel adresini ayarlama amacıyla derleyicinizin uygun seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-289">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="e96ef-290">Ngen.exe yerel görüntü için bu temel adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-290">Ngen.exe uses this base address for the native image.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-291">Yerel görüntüler, oluşturuldukları yönetilen derlemelerden daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-291">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="e96ef-292">Bu daha büyük boyutlara izin vermek için temel adresler hesaplanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-292">Base addresses must be calculated to allow for these larger sizes.</span></span>

<span data-ttu-id="e96ef-293">Bir yerel görüntünün tercih edilen temel adresini görüntülemek için dumpbin.exe gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-293">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>

<a name="HardBinding"></a>

## <a name="hard-binding"></a><span data-ttu-id="e96ef-294">Sabit bağlama</span><span class="sxs-lookup"><span data-stu-id="e96ef-294">Hard binding</span></span>

<span data-ttu-id="e96ef-295">Sıkı bağlama doğal görüntüler için birim zamanda yapılan işi artırır ve çalışma seti alanını azaltır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-295">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="e96ef-296">Sıkı bağlamanın dezavantajı, bir derleme yüklendiğinde o derlemeye sıkı bağlı olan tüm görüntülerin de yüklenmesinin gerekmesidir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-296">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="e96ef-297">Bu büyük bir uygulama için başlatma zamanını önemli derecede artırabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-297">This can significantly increase startup time for a large application.</span></span>

<span data-ttu-id="e96ef-298">Sıkı bağlama, uygulamanızın performansının kritik olduğu senaryolarda yüklenen bağımlılıklar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-298">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="e96ef-299">Herhangi bir doğal görüntü kullanımında, sıkı bağlanmanın uygulamanızın performansını arttırıp arttırmadığını öğrenmenin tek yolu dikkatli(hassas) performans ölçümleridir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-299">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>

<span data-ttu-id="e96ef-300"><xref:System.Runtime.CompilerServices.DependencyAttribute>Ve <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> öznitelikleri, Ngen.exe için sabit bağlama ipuçları sağlamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-300">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-301">Bu değerler Ngen.exe'ye teknik/tavsiyelerdir, komutlar değillerdir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-301">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="e96ef-302">Bunları kullanmak sıkı bağlamayı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-302">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="e96ef-303">Bu değerlerin anlamları ileri yayınlarda değişebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-303">The meaning of these attributes may change in future releases.</span></span>

<a name="DependencyHint"></a>

### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="e96ef-304">Bağımlılık için bağlama ipucu belirtme</span><span class="sxs-lookup"><span data-stu-id="e96ef-304">Specifying a binding hint for a dependency</span></span>

<span data-ttu-id="e96ef-305"><xref:System.Runtime.CompilerServices.DependencyAttribute>Belirtilen bağımlılığın yükleneolasılığını belirtmek için bir derlemeye uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-305">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <span data-ttu-id="e96ef-306"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType>Sabit bağlamanın uygun olduğunu gösterir, <xref:System.Runtime.CompilerServices.LoadHint.Default> bağımlılığın varsayılan olarak kullanılması gerektiğini belirtir ve <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> sabit bağlamanın uygun olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-306"><xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>

<span data-ttu-id="e96ef-307">Aşağıdaki kod, iki bağlılığı olan bir derlemenin özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-307">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="e96ef-308">İlk bağımlılık (Assembly1) sıkı bağlama için uygun bir adaydır ve ikinci bağımlılık (Assembly2) değildir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-308">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>

```vb
Imports System.Runtime.CompilerServices
<Assembly:DependencyAttribute("Assembly1", LoadHint.Always)>
<Assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)>
```

```csharp
using System.Runtime.CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)]
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)]
```

```cpp
using namespace System::Runtime::CompilerServices;
[assembly:DependencyAttribute("Assembly1", LoadHint.Always)];
[assembly:DependencyAttribute("Assembly2", LoadHint.Sometimes)];
```

<span data-ttu-id="e96ef-309">Derleme ismi dosya ismi uzantısını içermez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-309">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="e96ef-310">Görünür isim kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-310">Display names can be used.</span></span>

<a name="AssemblyHint"></a>

### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="e96ef-311">Derleme için varsayılan bağlama ipucu belirtme</span><span class="sxs-lookup"><span data-stu-id="e96ef-311">Specifying a default binding hint for an assembly</span></span>

<span data-ttu-id="e96ef-312">Varsayılan bağlama ipuçları, yalnızca onlara bağlılığı olan herhangi bir uygulama tarafından anında ve sıkça kullanılacak olan derlemeler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-312">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="e96ef-313"><xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> Sabit bağlamanın kullanılması gerektiğini belirtmek için ile ilgili bütünleştirilmiş kodlara uygulayın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-313">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-314"><xref:System.Runtime.CompilerServices.DefaultDependencyAttribute>Bu kategoriye uymayan. dll Derlemeleriyle ilgili hiçbir neden yoktur, çünkü özniteliği dışında herhangi bir değere sahip olan özniteliği <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> özniteliği uygulamakla aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-314">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>

<span data-ttu-id="e96ef-315">Microsoft, <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> .NET Framework mscorlib.dll gibi çok az sayıda derleme için varsayılan değer olan sabit bağlamanın varsayılan olduğunu belirtmek için öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-315">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>

<a name="Deferred"></a>

## <a name="deferred-processing"></a><span data-ttu-id="e96ef-316">Ertelenmiş işleme</span><span class="sxs-lookup"><span data-stu-id="e96ef-316">Deferred processing</span></span>

<span data-ttu-id="e96ef-317">Çok büyük bir uygulama için yerel görüntü oluşturmak uzun bir süre alabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-317">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="e96ef-318">Benzer şekilde, paylaşılan bir bileşene veya bilgisayar seçeneklerine yapılan değişiklikler pek çok yerel görüntünün güncellenmesini gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-318">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="e96ef-319">`install`Ve `update` eylemleri, `/queue` yerel görüntü hizmeti tarafından ertelenmiş yürütme işlemini sıraya alan bir seçeneğe sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-319">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="e96ef-320">Ayrıca, Ngen.exe, `queue` ve `executeQueuedItems` hizmet üzerinde bazı denetimler sağlayan eylemlerdir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-320">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="e96ef-321">Daha fazla bilgi için bkz. [yerel görüntü hizmeti](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="e96ef-321">For more information, see [Native Image Service](#native-image-service).</span></span>

<a name="JITCompilation"></a>

## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="e96ef-322">Yerel görüntüler ve JıT derlemesi</span><span class="sxs-lookup"><span data-stu-id="e96ef-322">Native images and JIT compilation</span></span>

<span data-ttu-id="e96ef-323">Eğer Ngen.exe assembly içerisinde oluşturamayacağı herhangi bir metotla karşılaşırsa, onları doğal görüntü (özgün görüntü) içerisine dahil etmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-323">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="e96ef-324">Çalışma zamanı bu derlemeyi çalıştırdığı zaman, doğal görüntünün içerisine dahil edilmeyen metotlar için JIT derleme işlemine döner</span><span class="sxs-lookup"><span data-stu-id="e96ef-324">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>

<span data-ttu-id="e96ef-325">Ek olarak, derleme yükseltildiyse veya görüntü herhangi bir sebeple geçersiz kılındıysa yerel görüntüler kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-325">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>

<a name="InvalidImages"></a>

### <a name="invalid-images"></a><span data-ttu-id="e96ef-326">Geçersiz görüntüler</span><span class="sxs-lookup"><span data-stu-id="e96ef-326">Invalid images</span></span>

<span data-ttu-id="e96ef-327">Ngen.exe'yi bir derlemenin yerel görüntüsünü oluşturmak için kullandığınızda; çıktı, belirlediğin komut satırı seçeneklerine ve bilgisayarınızdaki belirli ayarlara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-327">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="e96ef-328">Bu ayarlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-328">These settings include the following:</span></span>

- <span data-ttu-id="e96ef-329">.NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="e96ef-329">The version of the .NET Framework.</span></span>

- <span data-ttu-id="e96ef-330">Değişiklik, Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="e96ef-330">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

- <span data-ttu-id="e96ef-331">Derlemenin tam kimliği (yeniden derleme kimliği değiştirir).</span><span class="sxs-lookup"><span data-stu-id="e96ef-331">The exact identity of the assembly (recompilation changes identity).</span></span>

- <span data-ttu-id="e96ef-332">Derlemenin başvurduğu tüm derlemelerin tam kimliği (yeniden derleme kimliği değiştirir).</span><span class="sxs-lookup"><span data-stu-id="e96ef-332">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>

- <span data-ttu-id="e96ef-333">Güvenlik etkenleri.</span><span class="sxs-lookup"><span data-stu-id="e96ef-333">Security factors.</span></span>

<span data-ttu-id="e96ef-334">Ngen.exe bir doğal görüntü oluşturduğu zaman bu bilgiyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e96ef-334">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="e96ef-335">Bir derlemeyi çalıştırdığınız zaman, çalışma zamanı bilgisayarın o anki çevresine uyan seçenekler ve ayarlarla oluşturulmuş olan doğal görüntüyü arar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-335">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="e96ef-336">Çalışma zamanı eğer eşleşen bir doğal görüntü bulamazsa, derlemeyi JIT ile derleme yoluna gider.</span><span class="sxs-lookup"><span data-stu-id="e96ef-336">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="e96ef-337">Bilgisayarın ayarlarına ve çevresine uygulanan aşağıdaki değişiklikler doğal görüntünün geçersiz olmasına sebep olur:</span><span class="sxs-lookup"><span data-stu-id="e96ef-337">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>

- <span data-ttu-id="e96ef-338">.NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="e96ef-338">The version of the .NET Framework.</span></span>

     <span data-ttu-id="e96ef-339">Eğer .NET framework'e güncelleme uygularsanız, Ngen.exe kullanarak oluşturduğunuz bütün imajlar geçersiz sayılır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-339">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="e96ef-340">Bu nedenle, `Ngen Update` tüm yerel görüntülerin yeniden üretildiğinden emin olmak için .NET Framework tüm güncelleştirmeleri komutu yürütür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-340">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="e96ef-341">.NET framework kuracağı .Net framework kütüphaneleri için yeni görüntüleri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-341">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>

- <span data-ttu-id="e96ef-342">Değişiklik, Windows 9x ailesinden Windows NT ailesine ise işletim sisteminin sürümü.</span><span class="sxs-lookup"><span data-stu-id="e96ef-342">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>

     <span data-ttu-id="e96ef-343">Örneğin, bir bilgisayarda çalışan işletim sisteminin sürümü Windows 98 ' den Windows XP 'ye değişirse, yerel görüntü önbelleğinde depolanan tüm yerel görüntüler geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-343">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="e96ef-344">Ancak, işletim sistemi Windows 2000 ' den Windows XP 'ye değişirse, görüntüler geçersiz kılınmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-344">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>

- <span data-ttu-id="e96ef-345">Derlemenin kesin kimliği.</span><span class="sxs-lookup"><span data-stu-id="e96ef-345">The exact identity of the assembly.</span></span>

     <span data-ttu-id="e96ef-346">Eğer derlemeyi yeniden derlerseniz, derlemeye karşılık gelen doğal görüntü geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-346">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>

- <span data-ttu-id="e96ef-347">Derlemenin referans ettiği bütün derlemelerin tam kimliği.</span><span class="sxs-lookup"><span data-stu-id="e96ef-347">The exact identity of any assemblies the assembly references.</span></span>

     <span data-ttu-id="e96ef-348">Eğer yönetilmiş bir derlemeyi güncellerseniz, o derlemeye direk ya da dolaylı yoldan bağlı olan bütün doğal görüntüler geçersiz olur ve yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-348">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="e96ef-349">Bu hem normal tercihleri/ayarları hem de sıkı-bağlama bağlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-349">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="e96ef-350">Her bir yazılım güncelleştirmesi uygulandığında, yükleme programının `Ngen Update` tüm bağımlı yerel görüntülerin yeniden oluşturulmasını sağlamak için bir komut yürütmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-350">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>

- <span data-ttu-id="e96ef-351">Güvenlik etkenleri.</span><span class="sxs-lookup"><span data-stu-id="e96ef-351">Security factors.</span></span>

     <span data-ttu-id="e96ef-352">Önceden yetkilendirilmiş bir derlemenin izinlerini kısıtlamak için makina güvenlik politikasında değişiklik yapmak, o derleme için önceden derlenmiş olan doğal imajın geçersiz olmasına sebep olabilir</span><span class="sxs-lookup"><span data-stu-id="e96ef-352">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>

     <span data-ttu-id="e96ef-353">Ortak dil çalışma zamanının kod erişim güvenliğini nasıl yönettiği ve izinlerin nasıl kullanılacağı hakkında ayrıntılı bilgi için bkz. [kod erişim güvenliği](../misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="e96ef-353">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../misc/code-access-security.md).</span></span>

<a name="Troubleshooting"></a>

## <a name="troubleshooting"></a><span data-ttu-id="e96ef-354">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="e96ef-354">Troubleshooting</span></span>

<span data-ttu-id="e96ef-355">Aşağıdaki sorun giderme konuları, hangi yerel görüntülerin kullanıldığını ve uygulamanız tarafından kullanılamayacağını görmenizi, JıT derleyicisinin bir yöntemi derlemeye ne zaman başlayacağını belirlemenizi ve belirtilen yöntemlerin yerel görüntü derlemesini nasıl devre dışı yapılacağını görmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-355">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>

<a name="Fusion"></a>

### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="e96ef-356">Derleme Bağlaması Günlük Görüntüleyici</span><span class="sxs-lookup"><span data-stu-id="e96ef-356">Assembly Binding Log Viewer</span></span>

<span data-ttu-id="e96ef-357">Yerel görüntülerin uygulamanız tarafından kullanıldığını onaylamak için [Fuslogvw.exe (derleme bağlama günlük Görüntüleyici)](fuslogvw-exe-assembly-binding-log-viewer.md)kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-357">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="e96ef-358">Bağlama günlüğü Görüntüleyicisi penceresindeki **günlük kategorileri** kutusunda **Yerel görüntüler** ' i seçin.</span><span class="sxs-lookup"><span data-stu-id="e96ef-358">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="e96ef-359">Fuslogvw.exe bir doğal imajın neden reddedildiği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-359">Fuslogvw.exe provides information about why a native image was rejected.</span></span>

<a name="MDA"></a>

### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="e96ef-360">Jıtcompilationstart yönetilen hata ayıklama Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="e96ef-360">The JITCompilationStart managed debugging assistant</span></span>

<span data-ttu-id="e96ef-361">JıT derleyicisinin bir işlevi derlemeye ne zaman başlayacağını anlamak için, [Jıtcompilationstart](../debug-trace-profile/jitcompilationstart-mda.md) Managed hata ayıklama Yardımcısı 'Nı (MDA) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-361">You can use the [jitCompilationStart](../debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>

<a name="OptOut"></a>

### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="e96ef-362">Yerel görüntü oluşturmayı geri alma</span><span class="sxs-lookup"><span data-stu-id="e96ef-362">Opting out of native image generation</span></span>

<span data-ttu-id="e96ef-363">Bazı durumlarda, NGen.exe belirli bir yöntem için yerel görüntü üretmekte güçlük açabilir veya metodun yerel bir görüntüye derlenmek yerine JıT olarak derlenmesine de tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-363">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="e96ef-364">Bu durumda, `System.Runtime.BypassNGenAttribute` NGen.exe belirli bir yöntem için yerel görüntü oluşturmasını engellemek için özniteliğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-364">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="e96ef-365">Özniteliği, kodu yerel görüntüye eklemek istemediğiniz her bir yönteme ayrı ayrı uygulanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-365">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="e96ef-366">NGen.exe özniteliği tanır ve ilgili yöntem için yerel görüntüde kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-366">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>

<span data-ttu-id="e96ef-367">Ancak, `BypassNGenAttribute` .NET Framework sınıf kitaplığındaki bir tür olarak tanımlanmayan Not.</span><span class="sxs-lookup"><span data-stu-id="e96ef-367">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="e96ef-368">Kodunuzda özniteliği tüketmek için, önce bunu aşağıdaki gibi tanımlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-368">In order to consume the attribute in your code, you must first define it as follows:</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
[!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]

<span data-ttu-id="e96ef-369">Sonra özniteliği yöntem başına temelinde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-369">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="e96ef-370">Aşağıdaki örnek, yerel görüntü oluşturucuya yöntemi için yerel görüntü oluşturmaması gerektiğini söyler `ExampleClass.ToJITCompile` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-370">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>

[!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
[!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]

## <a name="examples"></a><span data-ttu-id="e96ef-371">Örnekler</span><span class="sxs-lookup"><span data-stu-id="e96ef-371">Examples</span></span>

<span data-ttu-id="e96ef-372">Aşağıdaki komut, geçerli dizinde bulunan için yerel bir görüntü oluşturur `ClientApp.exe` ve görüntüyü yerel görüntü önbelleğine yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-372">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="e96ef-373">Derleme için bir yapılandırma dosyası varsa, onu Ngen.exe kullanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-373">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="e96ef-374">Bunlara ek olarak, başvuruda bulunan tüm. dll dosyaları için yerel görüntüler oluşturulur `ClientApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-374">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>

```console
ngen install ClientApp.exe
```

<span data-ttu-id="e96ef-375">Ngen.exe ile yüklenmiş bir resim, bir kök olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-375">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="e96ef-376">Kök, bir uygulama veya paylaşılan bir bileşen olabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-376">A root can be an application or a shared component.</span></span>

<span data-ttu-id="e96ef-377">Aşağıdaki komut, belirtilen yol ile için yerel bir görüntü oluşturur `MyAssembly.exe` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-377">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>

```console
ngen install c:\myfiles\MyAssembly.exe
```

<span data-ttu-id="e96ef-378">Derlemeler ve bağımlılıklarını belirlerken Ngen.exe ortak dil çalışma zamanı tarafından kullanılan aynı algılama mantığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-378">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="e96ef-379">Varsayılan olarak, içeren dizin, `ClientApp.exe` uygulama temel dizini olarak kullanılır ve tüm derleme yoklama bu dizinde başlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-379">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="e96ef-380">Seçeneğini kullanarak bu davranışı geçersiz kılabilirsiniz `/AppBase` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-380">You can override this behavior by using the `/AppBase` option.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-381">Bu, uygulama temel dizininin geçerli dizin olarak ayarlandığı .NET Framework 1.0 ve 1.1 sürümlerindeki Ngen.exe davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-381">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>

<span data-ttu-id="e96ef-382">Bir derlemeye başvuru olmadan bağımlılık olabilir, örneğin, yöntemini kullanarak bir. dll dosyası yüklerse. <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="e96ef-382">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e96ef-383">Bu tür bir. dll dosyası için, seçeneğiyle birlikte uygulama derlemesi için yapılandırma bilgilerini kullanarak yerel bir görüntü oluşturabilirsiniz `/ExeConfig` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-383">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="e96ef-384">Aşağıdaki komut, ' `MyLib.dll,` den yapılandırma bilgilerini kullanmak için yerel bir görüntü oluşturur `MyApp.exe` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-384">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>

```console
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="e96ef-385">Uygulamayı kaldırdığınızda, bu şekilde yüklenen derlemeler kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-385">Assemblies installed in this way are not removed when the application is removed.</span></span>

<span data-ttu-id="e96ef-386">Bir bağımlılık kaldırmak için yüklemek için kullanılan aynı komut satırı seçeneklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-386">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="e96ef-387">Aşağıdaki komut, `MyLib.dll` önceki örnekteki öğesini kaldırır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-387">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>

```console
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe
```

<span data-ttu-id="e96ef-388">Genel bütünleştirilmiş kod önbelleğindeki bir derleme için yerel görüntü oluşturmak için, derlemenin görünen adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-388">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="e96ef-389">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="e96ef-389">For example:</span></span>

```console
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
```

<span data-ttu-id="e96ef-390">NGen.exe yüklediğiniz her senaryo için ayrı bir görüntü kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-390">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="e96ef-391">Örneğin, aşağıdaki komutlar normal işlemler için tamamen yerel görüntü kümesi, hata ayıklama için farklı bir küme ve belirleme için üçüncüyü yükler:</span><span class="sxs-lookup"><span data-stu-id="e96ef-391">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>

```console
ngen install MyApp.exe
ngen install MyApp.exe /debug
ngen install MyApp.exe /profile
```

### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="e96ef-392">Yerel Görüntü Önbelleğini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="e96ef-392">Displaying the Native Image Cache</span></span>

<span data-ttu-id="e96ef-393">Yerel görüntüler önbelleğe yüklendikten sonra, Ngen.exe kullanılarak görüntülenebilirler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-393">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="e96ef-394">Aşağıdaki komut yerel görüntü belleğindeki tüm yerel görüntüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-394">The following command displays all native images in the native image cache.</span></span>

```console
ngen display
```

<span data-ttu-id="e96ef-395">`display`Eylem önce tüm kök derlemeleri, ardından bilgisayardaki tüm yerel görüntülerin listesini listeler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-395">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>

<span data-ttu-id="e96ef-396">Yalnızca bir derlemenin bilgilerini görüntülemek için o derlemenin basit adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-396">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="e96ef-397">Aşağıdaki komut, yerel görüntü önbelleğindeki tüm yerel görüntüleri, kısmen adı `MyAssembly` , bağımlılıklarıyla ve bağımlılığı olan tüm köklerle eşleşen bir şekilde görüntüler `MyAssembly` :</span><span class="sxs-lookup"><span data-stu-id="e96ef-397">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>

```console
ngen display MyAssembly
```

<span data-ttu-id="e96ef-398">Paylaşılan bileşen derlemesine hangi köklerin bağımlı olduğunu bilmek, `update` paylaşılan bileşen yükseltildikten sonra bir eylemin etkisinin ölçmek içinde yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-398">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>

<span data-ttu-id="e96ef-399">Eğer bir derlemenin dosya uzantısını belirtirseniz, ya yolu belirtmeniz ya da Ngen.exe'yi derlemeyi içeren dizinden yürütmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-399">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>

```console
ngen display c:\myApps\MyAssembly.exe
```

<span data-ttu-id="e96ef-400">Aşağıdaki komut yerel görüntü önbelleğindeki tüm yerel görüntüleri, ad `MyAssembly` ve sürüm 1.0.0.0 ile görüntüler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-400">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>

```console
ngen display "myAssembly, version=1.0.0.0"
```

### <a name="updating-images"></a><span data-ttu-id="e96ef-401">Görüntüleri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="e96ef-401">Updating Images</span></span>

<span data-ttu-id="e96ef-402">Görüntüler genellikle paylaşılan bir bileşen yükseltildikten sonra güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-402">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="e96ef-403">Değiştirilen veya bağımlılıkları değişmiş olan tüm yerel görüntüleri güncelleştirmek için, bu `update` eylemi bağımsız değişken olmadan kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-403">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>

```console
ngen update
```

<span data-ttu-id="e96ef-404">Tüm görüntüleri güncelleştirmek uzun süren bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-404">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="e96ef-405">Seçeneğini kullanarak, yerel görüntü hizmeti tarafından yürütme için güncelleştirmeleri sıraya alabilirsiniz `/queue` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-405">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="e96ef-406">Seçenek ve yükleme öncelikleri hakkında daha fazla bilgi için `/queue` bkz. [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="e96ef-406">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>

```console
ngen update /queue
```

### <a name="uninstalling-images"></a><span data-ttu-id="e96ef-407">Görüntüleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="e96ef-407">Uninstalling Images</span></span>

<span data-ttu-id="e96ef-408">Ngen.exe bağımlılıkların bir listesini tutar, yani paylaşılan bileşenler yalnızca onlara bağlı olan tüm derlemeler kaldırıldığında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-408">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="e96ef-409">Ek olarak kök olarak yüklenmiş ortak bileşenler silinmez.</span><span class="sxs-lookup"><span data-stu-id="e96ef-409">In addition, a shared component is not removed if it has been installed as a root.</span></span>

<span data-ttu-id="e96ef-410">Aşağıdaki komut, kök için tüm senaryoları kaldırır `ClientApp.exe` :</span><span class="sxs-lookup"><span data-stu-id="e96ef-410">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp
```

<span data-ttu-id="e96ef-411">`uninstall`Eylem, belirli senaryoları kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-411">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="e96ef-412">Aşağıdaki komut, için tüm hata ayıklama senaryolarını kaldırır `ClientApp.exe` :</span><span class="sxs-lookup"><span data-stu-id="e96ef-412">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>

```console
ngen uninstall ClientApp /debug
```

> [!NOTE]
> <span data-ttu-id="e96ef-413">`/debug`Senaryoları kaldırmak, hem hem de içeren bir senaryoyu kaldırmaz `/profile``/debug.`</span><span class="sxs-lookup"><span data-stu-id="e96ef-413">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and `/debug.`</span></span>

<span data-ttu-id="e96ef-414">Aşağıdaki komut belirli bir sürümü için tüm senaryoları kaldırır `ClientApp.exe` :</span><span class="sxs-lookup"><span data-stu-id="e96ef-414">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0"
```

<span data-ttu-id="e96ef-415">Aşağıdaki komutlar, bu derleme için tüm senaryoları `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` veya yalnızca hata ayıklama senaryosunu kaldırır:</span><span class="sxs-lookup"><span data-stu-id="e96ef-415">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>

```console
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug
```

<span data-ttu-id="e96ef-416">Eylemde olduğu gibi `install` , bir uzantı sağlamak, derlemeyi içeren dizinden Ngen.exe yürütmeyi ya da tam yol belirtmeyi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-416">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>

<span data-ttu-id="e96ef-417">Yerel görüntü hizmetiyle ilgili örnekler için bkz. [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="e96ef-417">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>

## <a name="native-image-task"></a><span data-ttu-id="e96ef-418">Yerel Görüntü Görevi</span><span class="sxs-lookup"><span data-stu-id="e96ef-418">Native Image Task</span></span>

<span data-ttu-id="e96ef-419">Yerel görüntü görevi, yerel görüntüler üreten ve tutan bir Windows görevidir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-419">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="e96ef-420">Yerel görüntü görevi, desteklenen senaryolar için otomatik olarak yerel görüntüler oluşturur ve geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-420">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="e96ef-421">Ayrıca, yükleyicilerin yerel görüntüleri bir ertelenen zamanda oluşturmak ve güncelleştirmek için [Ngen.exe (yerel görüntü Oluşturucu)](ngen-exe-native-image-generator.md) kullanmasına de olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-421">It also enables installers to use [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>

<span data-ttu-id="e96ef-422">Yerel görüntü görevi, her bir mimariyi hedefleyen uygulamalar için derlemeye izin vermek üzere bir bilgisayarda desteklenen her CPU mimarisi için bir kez kaydedilir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-422">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>

|<span data-ttu-id="e96ef-423">Görev adı</span><span class="sxs-lookup"><span data-stu-id="e96ef-423">Task name</span></span>|<span data-ttu-id="e96ef-424">32 bit bilgisayar</span><span class="sxs-lookup"><span data-stu-id="e96ef-424">32-bit computer</span></span>|<span data-ttu-id="e96ef-425">64 bit bilgisayar</span><span class="sxs-lookup"><span data-stu-id="e96ef-425">64-bit computer</span></span>|
|---------------|----------------------|----------------------|
|<span data-ttu-id="e96ef-426">NET Framework NGEN v 4.0.30319</span><span class="sxs-lookup"><span data-stu-id="e96ef-426">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="e96ef-427">Yes</span><span class="sxs-lookup"><span data-stu-id="e96ef-427">Yes</span></span>|<span data-ttu-id="e96ef-428">Yes</span><span class="sxs-lookup"><span data-stu-id="e96ef-428">Yes</span></span>|
|<span data-ttu-id="e96ef-429">NET Framework NGEN v 4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="e96ef-429">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="e96ef-430">Hayır</span><span class="sxs-lookup"><span data-stu-id="e96ef-430">No</span></span>|<span data-ttu-id="e96ef-431">Evet</span><span class="sxs-lookup"><span data-stu-id="e96ef-431">Yes</span></span>|

<span data-ttu-id="e96ef-432">Yerel görüntü görevi, Windows 8 veya sonraki sürümlerde çalışırken .NET Framework 4,5 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-432">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="e96ef-433">Windows 'un önceki sürümlerinde, .NET Framework [yerel görüntü hizmetini](#native-image-service)kullanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-433">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>

### <a name="task-lifetime"></a><span data-ttu-id="e96ef-434">Görev ömrü</span><span class="sxs-lookup"><span data-stu-id="e96ef-434">Task Lifetime</span></span>

<span data-ttu-id="e96ef-435">Genellikle, Windows Görev Zamanlayıcı bilgisayar boştayken her gece yerel görüntü görevini başlatır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-435">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="e96ef-436">Görev, uygulama yükleyicileri tarafından kuyruğa alınan ertelenmiş işleri, ertelenmiş yerel görüntü güncelleştirme isteklerini ve herhangi bir otomatik görüntü oluşturmayı denetler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-436">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="e96ef-437">Görev, bekleyen iş öğelerini tamamlar ve sonra kapatır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-437">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="e96ef-438">Görev çalışırken bilgisayar boşta çalışmayı durduktan sonra görev durmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-438">If the computer stops being idle while the task is running, the task stops.</span></span>

<span data-ttu-id="e96ef-439">Yerel görüntü görevini Görev Zamanlayıcı kullanıcı arabiriminden el ile veya NGen.exe el ile yapılan çağrılar aracılığıyla da başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-439">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="e96ef-440">Görev bu yöntemlerden birini kullanarak başlatılırsa, bilgisayar artık boşta olmadığında çalışmaya devam eder.</span><span class="sxs-lookup"><span data-stu-id="e96ef-440">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="e96ef-441">NGen.exe kullanılarak el ile oluşturulan görüntüler, uygulama yükleyicilerine yönelik öngörülebilir davranışı etkinleştirmek için önceliklendirilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-441">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>

## <a name="native-image-service"></a><span data-ttu-id="e96ef-442">Yerel Görüntü Hizmeti</span><span class="sxs-lookup"><span data-stu-id="e96ef-442">Native Image Service</span></span>

<span data-ttu-id="e96ef-443">Yerel görüntü hizmeti, yerel görüntüleri üreten ve tutan bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-443">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="e96ef-444">Yerel görüntü hizmeti, geliştiricinin yerel görüntülerin yükleme ve güncelleştirme işlemini bilgisayar boştayken dönemlere erteetmesine olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-444">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>

<span data-ttu-id="e96ef-445">Normal olarak, yerel görüntü hizmeti bir uygulama veya güncelleştirme için yükleme programı (Yükleyici) tarafından başlatılır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-445">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="e96ef-446">Öncelik 3 işlemleri için, hizmet bilgisayarda boşta kalma süresi boyunca yürütülür.</span><span class="sxs-lookup"><span data-stu-id="e96ef-446">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="e96ef-447">Hizmet, durumunu kaydeder ve gerekirse birden çok yeniden başlatma işlemi için devam etme yeteneğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-447">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="e96ef-448">Birden çok görüntü derlemesi kuyruğa alınabilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-448">Multiple image compilations can be queued.</span></span>

<span data-ttu-id="e96ef-449">Hizmet el ile Ngen.exe komutuyla da etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="e96ef-449">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="e96ef-450">El ile gerçekleştirilen komutların arka plan etkinliğine göre önceliği vardır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-450">Manual commands take precedence over background activity.</span></span>

> [!NOTE]
> <span data-ttu-id="e96ef-451">Windows Vista 'da, yerel görüntü hizmeti için görünen ad "Microsoft.NET Framework NGEN v 2.0.50727_X86" veya "Microsoft.NET Framework NGEN v 2.0.50727_X64" olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-451">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="e96ef-452">Microsoft Windows 'un önceki tüm sürümlerinde, ad ".NET Runtime Optimization Service v 2.0.50727_X86" veya ".NET Runtime Optimizasyon hizmeti v 2.0.50727_X64" olur.</span><span class="sxs-lookup"><span data-stu-id="e96ef-452">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>

### <a name="launching-deferred-operations"></a><span data-ttu-id="e96ef-453">Ertelenmiş Işlemler başlatılıyor</span><span class="sxs-lookup"><span data-stu-id="e96ef-453">Launching Deferred Operations</span></span>

<span data-ttu-id="e96ef-454">Yükleme veya yükseltmeye başlamadan önce, hizmeti duraklatma önerilir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-454">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="e96ef-455">Bu, yükleyici dosyaları kopyalarken veya derlemeleri genel bütünleştirilmiş kod önbelleğine yerleştirirken hizmetin yürütülmemesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="e96ef-455">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="e96ef-456">Aşağıdaki Ngen.exe komut satırı Hizmeti duraklatır:</span><span class="sxs-lookup"><span data-stu-id="e96ef-456">The following Ngen.exe command line pauses the service:</span></span>

```console
ngen queue pause
```

<span data-ttu-id="e96ef-457">Tüm ertelenmiş işlemler sıraya alınmışsa aşağıdaki komut hizmetin sürdürülmesine izin verir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-457">When all deferred operations have been queued, the following command allows the service to resume:</span></span>

```console
ngen queue continue
```

<span data-ttu-id="e96ef-458">Yeni bir uygulama yüklerken veya paylaşılan bir bileşeni güncelleştirirken yerel görüntü üretimini ertelemek için `/queue` seçeneğini `install` veya `update` eylemleriyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-458">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="e96ef-459">Aşağıdaki Ngen.exe komut satırları paylaşılan bir bileşen için yerel bir görüntü yükler ve etkilenen tüm köklerin güncelleştirilmesini gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="e96ef-459">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>

```console
ngen install MyComponent /queue
ngen update /queue
```

<span data-ttu-id="e96ef-460">`update`Eylem, yalnızca kullananlarla değil, geçersiz kılınan tüm yerel görüntüleri yeniden oluşturur `MyComponent` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-460">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>

<span data-ttu-id="e96ef-461">Uygulamanız birçok kökten oluşuyorsa, ertelenmiş eylemlerin önceliğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-461">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="e96ef-462">Aşağıdaki komutlar, üç kök yüklemeyi sıraya alma.</span><span class="sxs-lookup"><span data-stu-id="e96ef-462">The following commands queue the installation of three roots.</span></span> <span data-ttu-id="e96ef-463">`Assembly1`, boşta kalma süresi beklememeden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-463">`Assembly1` is installed first, without waiting for idle time.</span></span> <span data-ttu-id="e96ef-464">`Assembly2`, boşta kalma süresi beklememeden da yüklenir, ancak tüm öncelik 1 eylemleri tamamlandıktan sonra.</span><span class="sxs-lookup"><span data-stu-id="e96ef-464">`Assembly2` is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> <span data-ttu-id="e96ef-465">`Assembly3`, hizmet bilgisayarın boşta olduğunu algıladığında yüklenir.</span><span class="sxs-lookup"><span data-stu-id="e96ef-465">`Assembly3` is installed when the service detects that the computer is idle.</span></span>

```console
ngen install Assembly1 /queue:1
ngen install Assembly2 /queue:2
ngen install Assembly3 /queue:3
```

<span data-ttu-id="e96ef-466">Eylemi kullanarak sıraya alınan eylemleri zaman uyumlu olarak gerçekleşecek şekilde zorlayabilirsiniz `executeQueuedItems` .</span><span class="sxs-lookup"><span data-stu-id="e96ef-466">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="e96ef-467">İsteğe bağlı öncelik sağlarsanız, bu eylem yalnızca eşit veya daha düşük önceliğe sahip olan sıraya alınmış eylemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="e96ef-467">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="e96ef-468">Varsayılan öncelik 3 ' dir, bu nedenle aşağıdaki Ngen.exe komutu sıraya alınan tüm eylemleri hemen işler ve tamamlanana kadar döndürmez:</span><span class="sxs-lookup"><span data-stu-id="e96ef-468">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>

```console
ngen executeQueuedItems
```

<span data-ttu-id="e96ef-469">Zaman uyumlu komutlar Ngen.exe tarafından yürütülür ve yerel görüntü hizmetini kullanmaz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-469">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="e96ef-470">Yerel görüntü hizmeti çalışırken Ngen.exe kullanarak eylemleri çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-470">You can execute actions using Ngen.exe while the native image service is running.</span></span>

### <a name="service-shutdown"></a><span data-ttu-id="e96ef-471">Hizmet kapatılıyor</span><span class="sxs-lookup"><span data-stu-id="e96ef-471">Service Shutdown</span></span>

<span data-ttu-id="e96ef-472">Seçeneğini içeren bir Ngen.exe komutunun yürütülmesi tarafından başlatıldıktan sonra `/queue` , hizmet tüm eylemler tamamlanana kadar arka planda çalışır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-472">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="e96ef-473">Hizmet, gerektiğinde birden çok yeniden başlatma işleminin devam edebilmesi için durumunu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="e96ef-473">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="e96ef-474">Hizmet sıraya alınmış daha fazla eylem olmadığını algıladığında, bilgisayarın bir sonraki önyüklenilişinde yeniden başlatmaması için durumunu sıfırlar ve sonra kendisini kapatır.</span><span class="sxs-lookup"><span data-stu-id="e96ef-474">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>

### <a name="service-interaction-with-clients"></a><span data-ttu-id="e96ef-475">Istemcilerle hizmet etkileşimi</span><span class="sxs-lookup"><span data-stu-id="e96ef-475">Service Interaction with Clients</span></span>

<span data-ttu-id="e96ef-476">.NET Framework sürüm 2,0 ' de, yerel görüntü hizmeti ile tek etkileşim, komut satırı aracı Ngen.exe.</span><span class="sxs-lookup"><span data-stu-id="e96ef-476">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="e96ef-477">Yerel görüntü hizmeti için eylemleri sıraya almak ve hizmetle etkileşimde bulunmak için yükleme betiklerinde komut satırı aracını kullanın.</span><span class="sxs-lookup"><span data-stu-id="e96ef-477">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>

## <a name="see-also"></a><span data-ttu-id="e96ef-478">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e96ef-478">See also</span></span>

- [<span data-ttu-id="e96ef-479">Araçlar</span><span class="sxs-lookup"><span data-stu-id="e96ef-479">Tools</span></span>](index.md)
- [<span data-ttu-id="e96ef-480">Yönetilen yürütme Işlemi</span><span class="sxs-lookup"><span data-stu-id="e96ef-480">Managed Execution Process</span></span>](../../standard/managed-execution-process.md)
- [<span data-ttu-id="e96ef-481">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="e96ef-481">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="e96ef-482">Komut Istemleri</span><span class="sxs-lookup"><span data-stu-id="e96ef-482">Command Prompts</span></span>](developer-command-prompt-for-vs.md)
