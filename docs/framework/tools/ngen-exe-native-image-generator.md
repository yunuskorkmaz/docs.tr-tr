---
title: Ngen.exe (Yerel Görüntü Oluşturucu)
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34fc8fb78a1dcd2637ff9ce0d0de8e7c1509bd3c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116275"
---
# <a name="ngenexe-native-image-generator"></a><span data-ttu-id="98048-102">Ngen.exe (Yerel Görüntü Oluşturucu)</span><span class="sxs-lookup"><span data-stu-id="98048-102">Ngen.exe (Native Image Generator)</span></span>
<span data-ttu-id="98048-103">Yerel Görüntü Oluşturucusu (Ngen.exe), yönetilen uygulamaların performansını artıran bir araçtır.</span><span class="sxs-lookup"><span data-stu-id="98048-103">The Native Image Generator (Ngen.exe) is a tool that improves the performance of managed applications.</span></span> <span data-ttu-id="98048-104">Ngen.exe, işlemciye özel derlenmiş makine kodu içeren dosyalar olan yerel görüntüler oluşturur ve bunları yerel bilgisayarın yerel görüntü önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="98048-104">Ngen.exe creates native images, which are files containing compiled processor-specific machine code, and installs them into the native image cache on the local computer.</span></span> <span data-ttu-id="98048-105">Çalışma zamanı orijinal derlemeyi derlemek için anlık (JIT) derleyiciyi kullanmak yerine önbellekteki yerel görüntüleri kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-105">The runtime can use native images from the cache instead of using the just-in-time (JIT) compiler to compile the original assembly.</span></span>  
  
 <span data-ttu-id="98048-106">Ngen.exe değişiklikleri [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="98048-106">Changes to Ngen.exe in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)]:</span></span>  
  
-   <span data-ttu-id="98048-107">Ngen.exe artık derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="98048-107">Ngen.exe now compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
-   <span data-ttu-id="98048-108">Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="98048-108">Native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span>  
  
 <span data-ttu-id="98048-109">Ngen.exe'ye .NET Framework 2.0 içinde yapılan değişiklikler:</span><span class="sxs-lookup"><span data-stu-id="98048-109">Changes to Ngen.exe in the .NET Framework version 2.0:</span></span>  
  
-   <span data-ttu-id="98048-110">Bir derlemeyi yüklemek ayrıca bağımlılıklarını da yükleyerek Ngen.exe'nin sözdizimini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="98048-110">Installing an assembly also installs its dependencies, simplifying the syntax of Ngen.exe.</span></span>  
  
-   <span data-ttu-id="98048-111">Yerel görüntüler artık uygulama etki alanları arasında paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-111">Native images can now be shared across application domains.</span></span>  
  
-   <span data-ttu-id="98048-112">Yeni bir eylem `update`, kılınan görüntüleri yeniden oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98048-112">A new action, `update`, re-creates images that have been invalidated.</span></span>  
  
-   <span data-ttu-id="98048-113">Eylemler, görüntüleri oluşturmak ve yüklemek için bilgisayardaki boşta kalma süresini kullanan bir servis tarafından ertelenebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-113">Actions can be deferred for execution by a service that uses idle time on the computer to generate and install images.</span></span>  
  
-   <span data-ttu-id="98048-114">Görüntü geçersiz kılmanın bazı nedenleri kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="98048-114">Some causes of image invalidation have been eliminated.</span></span>  
  
 <span data-ttu-id="98048-115">Windows 8'de bkz [Native Image Task](#native-image-task).</span><span class="sxs-lookup"><span data-stu-id="98048-115">On Windows 8, see [Native Image Task](#native-image-task).</span></span>  
  
 <span data-ttu-id="98048-116">Ngen.exe ve yerel görüntü hizmetini kullanma hakkında ek bilgi için bkz: [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-116">For additional information on using Ngen.exe and the native image service, see [Native Image Service](#native-image-service).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-117">1.0 ve 1.1 .NET Framework sürümleri için Ngen.exe sözdizimi bulunabilir [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="98048-117">Ngen.exe syntax for versions 1.0 and 1.1 of the .NET Framework can be found in [Native Image Generator (Ngen.exe) Legacy Syntax](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms165073(v=vs.100)).</span></span>  
  
 <span data-ttu-id="98048-118">Bu araç, Visual Studio ile birlikte otomatik olarak yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-118">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="98048-119">Aracı çalıştırmak için Visual Studio (veya Windows 7'de Visual Studio komut istemi) için geliştirici Komut İstemi'ni kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-119">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="98048-120">Daha fazla bilgi için [komut istemleri](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span><span class="sxs-lookup"><span data-stu-id="98048-120">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="98048-121">Komut satırına şunu yazın:</span><span class="sxs-lookup"><span data-stu-id="98048-121">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98048-122">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98048-122">Syntax</span></span>  
  
```  
ngen action [options]  
```  
  
```  
ngen /? | /help  
```  
  
## <a name="actions"></a><span data-ttu-id="98048-123">Eylemler</span><span class="sxs-lookup"><span data-stu-id="98048-123">Actions</span></span>  
 <span data-ttu-id="98048-124">Aşağıdaki tabloda her söz dizimi görülmektedir `action`.</span><span class="sxs-lookup"><span data-stu-id="98048-124">The following table shows the syntax of each `action`.</span></span> <span data-ttu-id="98048-125">Ayrı bölümlerini açıklamaları için bir `action`, bkz: [bağımsız değişkenleri](#ArgumentTable), [öncelik düzeyleri](#PriorityTable), [senaryoları](#ScenarioTable), ve [Config](#ConfigTable)tablolar.</span><span class="sxs-lookup"><span data-stu-id="98048-125">For descriptions of the individual parts of an `action`, see the [Arguments](#ArgumentTable), [Priority Levels](#PriorityTable), [Scenarios](#ScenarioTable), and [Config](#ConfigTable) tables.</span></span> <span data-ttu-id="98048-126">[Seçenekleri](#OptionTable) tablo açıklar `options` ve Yardım anahtarlarını.</span><span class="sxs-lookup"><span data-stu-id="98048-126">The [Options](#OptionTable) table describes the `options` and the help switches.</span></span>  
  
|<span data-ttu-id="98048-127">Eylem</span><span class="sxs-lookup"><span data-stu-id="98048-127">Action</span></span>|<span data-ttu-id="98048-128">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-128">Description</span></span>|  
|------------|-----------------|  
|`install` <span data-ttu-id="98048-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span><span class="sxs-lookup"><span data-stu-id="98048-129">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`] [`/queue`[`:`{`1`&#124;`2`&#124;`3`}]]</span></span>|<span data-ttu-id="98048-130">Bir derleme ve bağımlılıkları için yerel görüntüler oluştur ve görüntüleri yerel görüntü önbelleğine yükle.</span><span class="sxs-lookup"><span data-stu-id="98048-130">Generate native images for an assembly and its dependencies and install the images in the native image cache.</span></span><br /><br /> <span data-ttu-id="98048-131">Varsa `/queue` belirtilirse, eylem yerel görüntü hizmetinde sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="98048-131">If `/queue` is specified, the action is queued for the native image service.</span></span> <span data-ttu-id="98048-132">Varsayılan öncelik 3'tür.</span><span class="sxs-lookup"><span data-stu-id="98048-132">The default priority is 3.</span></span> <span data-ttu-id="98048-133">Bkz: [öncelik düzeyleri](#PriorityTable) tablo.</span><span class="sxs-lookup"><span data-stu-id="98048-133">See the [Priority Levels](#PriorityTable) table.</span></span>|  
|`uninstall` <span data-ttu-id="98048-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span><span class="sxs-lookup"><span data-stu-id="98048-134">[`assemblyName` &#124; `assemblyPath`] [`scenarios`] [`config`]</span></span>|<span data-ttu-id="98048-135">Bir derleme ve bağımlılıklarının yerel görüntülerini yerel görüntü önbelleğinden sil.</span><span class="sxs-lookup"><span data-stu-id="98048-135">Delete the native images of an assembly and its dependencies from the native image cache.</span></span><br /><br /> <span data-ttu-id="98048-136">Tek bir görüntüyü ve bağımlılıklarını kaldırmak için, görüntüyü yüklemek için kullanılan aynı komut satırı bağımsız değişkenlerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-136">To uninstall a single image and its dependencies, use the same command-line arguments that were used to install the image.</span></span> <span data-ttu-id="98048-137">**Not:**  İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], eylem `uninstall` \* artık desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="98048-137">**Note:**  Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the action `uninstall` \* is no longer supported.</span></span>|  
|`update` <span data-ttu-id="98048-138">[`/queue`]</span><span class="sxs-lookup"><span data-stu-id="98048-138">[`/queue`]</span></span>|<span data-ttu-id="98048-139">Geçersiz olan yerel görüntüleri güncelleştir.</span><span class="sxs-lookup"><span data-stu-id="98048-139">Update native images that have become invalid.</span></span><br /><br /> <span data-ttu-id="98048-140">Varsa `/queue` belirtilirse, güncelleştirmeler yerel görüntü hizmetinde sıraya alınır.</span><span class="sxs-lookup"><span data-stu-id="98048-140">If `/queue` is specified, the updates are queued for the native image service.</span></span> <span data-ttu-id="98048-141">Güncelleştirmeler her zaman 3 önceliğindedir ve bilgisayar boşta olduğunda çalışır.</span><span class="sxs-lookup"><span data-stu-id="98048-141">Updates are always scheduled at priority 3, so they run when the computer is idle.</span></span>|  
|`display` <span data-ttu-id="98048-142">[`assemblyName` &#124; `assemblyPath`]</span><span class="sxs-lookup"><span data-stu-id="98048-142">[`assemblyName` &#124; `assemblyPath`]</span></span>|<span data-ttu-id="98048-143">Bir derleme ve bağımlılıkları için yerel görüntülerin durumunu görüntüle.</span><span class="sxs-lookup"><span data-stu-id="98048-143">Display the state of the native images for an assembly and its dependencies.</span></span><br /><br /> <span data-ttu-id="98048-144">Eğer bağımsız değişken sağlanmazsa, yerel görüntü önbelleğindeki her şey görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="98048-144">If no argument is supplied, everything in the native image cache is displayed.</span></span>|  
|`executeQueuedItems` <span data-ttu-id="98048-145">[<code>1&#124;2&#124;3</code>]</span><span class="sxs-lookup"><span data-stu-id="98048-145">[<code>1&#124;2&#124;3</code>]</span></span><br /><br /> <span data-ttu-id="98048-146">-veya-</span><span class="sxs-lookup"><span data-stu-id="98048-146">-or-</span></span><br /><br /> `eqi` <span data-ttu-id="98048-147">[1&#124;2&#124;3]</span><span class="sxs-lookup"><span data-stu-id="98048-147">[1&#124;2&#124;3]</span></span>|<span data-ttu-id="98048-148">Sıraya alınan derleme işlerini yürüt.</span><span class="sxs-lookup"><span data-stu-id="98048-148">Execute queued compilation jobs.</span></span><br /><br /> <span data-ttu-id="98048-149">Eğer bir öncelik belirtilirse, ona eşit veya daha büyük önceliğe sahip derleme işleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="98048-149">If a priority is specified, compilation jobs with greater or equal priority are executed.</span></span> <span data-ttu-id="98048-150">Eğer öncelik belirtilmezse, sıraya alınan tüm derleme işleri yürütülür.</span><span class="sxs-lookup"><span data-stu-id="98048-150">If no priority is specified, all queued compilation jobs are executed.</span></span>|  
|`queue` <span data-ttu-id="98048-151">{`pause` &#124; `continue` &#124; `status`}</span><span class="sxs-lookup"><span data-stu-id="98048-151">{`pause` &#124; `continue` &#124; `status`}</span></span>|<span data-ttu-id="98048-152">Yerel görüntü hizmetini duraklat, duraklatılan hizmetin devam etmesine izin ver veya hizmetin durumunu sorgula.</span><span class="sxs-lookup"><span data-stu-id="98048-152">Pause the native image service, allow the paused service to continue, or query the status of the service.</span></span>|  
  
<a name="ArgumentTable"></a>   
## <a name="arguments"></a><span data-ttu-id="98048-153">Arguments</span><span class="sxs-lookup"><span data-stu-id="98048-153">Arguments</span></span>  
  
|<span data-ttu-id="98048-154">Bağımsız Değişken</span><span class="sxs-lookup"><span data-stu-id="98048-154">Argument</span></span>|<span data-ttu-id="98048-155">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-155">Description</span></span>|  
|--------------|-----------------|  
|`assemblyName`|<span data-ttu-id="98048-156">Derlemenin tam görünen adı.</span><span class="sxs-lookup"><span data-stu-id="98048-156">The full display name of the assembly.</span></span> <span data-ttu-id="98048-157">Örneğin: `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`</span><span class="sxs-lookup"><span data-stu-id="98048-157">For example, `"myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5"`.</span></span> <span data-ttu-id="98048-158">**Not:**  Gibi bir kısmi derleme adı sağlayabilirsiniz `myAssembly`, için `display` ve `uninstall` eylemler.</span><span class="sxs-lookup"><span data-stu-id="98048-158">**Note:**  You can supply a partial assembly name, such as `myAssembly`, for the `display` and `uninstall` actions.</span></span> <br /><br /> <span data-ttu-id="98048-159">Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-159">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
|`assemblyPath`|<span data-ttu-id="98048-160">Derlemenin açık yolu.</span><span class="sxs-lookup"><span data-stu-id="98048-160">The explicit path of the assembly.</span></span> <span data-ttu-id="98048-161">Tam veya göreli bir yol belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-161">You can specify a full or relative path.</span></span><br /><br /> <span data-ttu-id="98048-162">Eğer bir yol belirtmeden dosya adı belirtilseniz, derleme geçerli dizinde bulunmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-162">If you specify a file name without a path, the assembly must be located in the current directory.</span></span><br /><br /> <span data-ttu-id="98048-163">Her Ngen.exe komut satırında yalnızca bir derleme belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-163">Only one assembly can be specified per Ngen.exe command line.</span></span>|  
  
<a name="PriorityTable"></a>   
## <a name="priority-levels"></a><span data-ttu-id="98048-164">Öncelik Düzeyleri</span><span class="sxs-lookup"><span data-stu-id="98048-164">Priority Levels</span></span>  
  
|<span data-ttu-id="98048-165">Öncelik</span><span class="sxs-lookup"><span data-stu-id="98048-165">Priority</span></span>|<span data-ttu-id="98048-166">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-166">Description</span></span>|  
|--------------|-----------------|  
|`1`|<span data-ttu-id="98048-167">Yerel görüntüler, boşta kalma süresi beklenmeden hemen oluşturulur ve yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-167">Native images are generated and installed immediately, without waiting for idle time.</span></span>|  
|`2`|<span data-ttu-id="98048-168">Yerel görüntüler boşta kalma süresi beklenmeden, ancak tüm 1 öncelikli eylemler (ve bağımlılıkları) tamamlandıktan sonra yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-168">Native images are generated and installed without waiting for idle time, but after all priority 1 actions (and their dependencies) have completed.</span></span>|  
|`3`|<span data-ttu-id="98048-169">Yerel görüntüler, yerel görüntü hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-169">Native images are installed when the native image service detects that the computer is idle.</span></span> <span data-ttu-id="98048-170">Bkz: [yerel görüntü hizmeti](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-170">See [Native Image Service](#native-image-service).</span></span>|  
  
<a name="ScenarioTable"></a>   
## <a name="scenarios"></a><span data-ttu-id="98048-171">Senaryolar</span><span class="sxs-lookup"><span data-stu-id="98048-171">Scenarios</span></span>  
  
|<span data-ttu-id="98048-172">Senaryo</span><span class="sxs-lookup"><span data-stu-id="98048-172">Scenario</span></span>|<span data-ttu-id="98048-173">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-173">Description</span></span>|  
|--------------|-----------------|  
|`/Debug`|<span data-ttu-id="98048-174">Bir hata ayıklayıcı altında kullanılabilen yerel görüntüler oluştur.</span><span class="sxs-lookup"><span data-stu-id="98048-174">Generate native images that can be used under a debugger.</span></span>|  
|`/Profile`|<span data-ttu-id="98048-175">Bir profil oluşturucu altında kullanılabilen yerel görüntüler oluştur.</span><span class="sxs-lookup"><span data-stu-id="98048-175">Generate native images that can be used under a profiler.</span></span>|  
|`/NoDependencies`|<span data-ttu-id="98048-176">Belirli senaryo seçeneklerinin gerektirdiği en az sayıda yerel görüntü oluştur.</span><span class="sxs-lookup"><span data-stu-id="98048-176">Generate the minimum number of native images required by the specified scenario options.</span></span>|  
  
<a name="ConfigTable"></a>   
## <a name="config"></a><span data-ttu-id="98048-177">Config</span><span class="sxs-lookup"><span data-stu-id="98048-177">Config</span></span>  
  
|<span data-ttu-id="98048-178">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="98048-178">Configuration</span></span>|<span data-ttu-id="98048-179">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-179">Description</span></span>|  
|-------------------|-----------------|  
|`/ExeConfig:` `exePath`|<span data-ttu-id="98048-180">Belirtilen çalıştırılabilir derlemesinin yapılandırmasını kullan.</span><span class="sxs-lookup"><span data-stu-id="98048-180">Use the configuration of the specified executable assembly.</span></span><br /><br /> <span data-ttu-id="98048-181">Ngen.exe, bağımlılıklara bağlarken yükleyici ile aynı kararları almalıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-181">Ngen.exe needs to make the same decisions as the loader when binding to dependencies.</span></span> <span data-ttu-id="98048-182">Paylaşılan bir bileşen çalışma zamanında yüklendiğinde kullanarak <xref:System.Reflection.Assembly.Load%2A> yöntemi, uygulamanın yapılandırma dosyası paylaşılan bileşen için yüklenen bağımlılıkları belirler — örneğin, yüklenen bir bağımlılığın sürümü.</span><span class="sxs-lookup"><span data-stu-id="98048-182">When a shared component is loaded at run time, using the <xref:System.Reflection.Assembly.Load%2A> method, the application's configuration file determines the dependencies that are loaded for the shared component — for example, the version of a dependency that is loaded.</span></span> <span data-ttu-id="98048-183">`/ExeConfig` Anahtar üzerinde bağımlılıkları yüklenemeyen çalışma zamanında Ngen.exe rehberlik sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-183">The `/ExeConfig` switch gives Ngen.exe guidance on which dependencies would be loaded at run time.</span></span>|  
|`/AppBase:` `directoryPath`|<span data-ttu-id="98048-184">Bağımlılıkları bulurken, uygulama tabanı olarak belirtilen dizini kullan.</span><span class="sxs-lookup"><span data-stu-id="98048-184">When locating dependencies, use the specified directory as the application base.</span></span>|  
  
<a name="OptionTable"></a>   
## <a name="options"></a><span data-ttu-id="98048-185">Seçenekler</span><span class="sxs-lookup"><span data-stu-id="98048-185">Options</span></span>  
  
|<span data-ttu-id="98048-186">Seçenek</span><span class="sxs-lookup"><span data-stu-id="98048-186">Option</span></span>|<span data-ttu-id="98048-187">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98048-187">Description</span></span>|  
|------------|-----------------|  
|`/nologo`|<span data-ttu-id="98048-188">Microsoft başlangıç başlığını bastır.</span><span class="sxs-lookup"><span data-stu-id="98048-188">Suppress the Microsoft startup banner display.</span></span>|  
|`/silent`|<span data-ttu-id="98048-189">Başarı iletilerinin görüntülenmesini bastır.</span><span class="sxs-lookup"><span data-stu-id="98048-189">Suppress the display of success messages.</span></span>|  
|`/verbose`|<span data-ttu-id="98048-190">Hata ayıklama için ayrıntılı bilgi görüntüle.</span><span class="sxs-lookup"><span data-stu-id="98048-190">Display detailed information for debugging.</span></span> <span data-ttu-id="98048-191">**Not:**  İşletim sistemi sınırlamaları nedeniyle, bu seçenek Windows 98 ve Windows Millennium Edition üzerinde çok fazla ek bilgi görüntülemez.</span><span class="sxs-lookup"><span data-stu-id="98048-191">**Note:**  Due to operating system limitations, this option does not display as much additional information on Windows 98 and Windows Millennium Edition.</span></span>|  
|`/help`<span data-ttu-id="98048-192">,</span><span class="sxs-lookup"><span data-stu-id="98048-192">,</span></span> `/?`|<span data-ttu-id="98048-193">Geçerli yayın için komut sözdizimi ve seçenekleri görüntüle.</span><span class="sxs-lookup"><span data-stu-id="98048-193">Display command syntax and options for the current release.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98048-194">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98048-194">Remarks</span></span>  
 <span data-ttu-id="98048-195">Ngen.exe'yi çalıştırabilmek için yönetici ayrıcalıklarınızın olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98048-195">To run Ngen.exe, you must have administrative privileges.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="98048-196">Ngen.exe'yi tam güvenilir olmayan derlemeler üzerinde çalıştırmayın.</span><span class="sxs-lookup"><span data-stu-id="98048-196">Do not run Ngen.exe on assemblies that are not fully trusted.</span></span> <span data-ttu-id="98048-197">İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe derlemeleri tam güven ile derler ve kod erişimi güvenliği (CAS) ilkesi artık değerlendirilmez.</span><span class="sxs-lookup"><span data-stu-id="98048-197">Starting with the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Ngen.exe compiles assemblies with full trust, and code access security (CAS) policy is no longer evaluated.</span></span>  
  
 <span data-ttu-id="98048-198">İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], Ngen.exe ile oluşturulan yerel görüntüler artık kısmi güvende çalışan uygulamaların içine yüklenemez.</span><span class="sxs-lookup"><span data-stu-id="98048-198">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], the native images that are generated with Ngen.exe can no longer be loaded into applications that are running in partial trust.</span></span> <span data-ttu-id="98048-199">Bunun yerine anlık (JIT) derleyici çağrılır.</span><span class="sxs-lookup"><span data-stu-id="98048-199">Instead, the just-in-time (JIT) compiler is invoked.</span></span>  
  
 <span data-ttu-id="98048-200">Ngen.exe belirtilen derleme için yerel görüntüler oluşturur `assemblyname` bağımsız değişkeni `install` eylem ve tüm bağımlılıkları.</span><span class="sxs-lookup"><span data-stu-id="98048-200">Ngen.exe generates native images for the assembly specified by the `assemblyname` argument to the `install` action and all its dependencies.</span></span> <span data-ttu-id="98048-201">Bağlılıklar derleme bildirisindeki referanslar ile belirlenir.</span><span class="sxs-lookup"><span data-stu-id="98048-201">Dependencies are determined from references in the assembly manifest.</span></span> <span data-ttu-id="98048-202">Yansıma, örneğin çağırarak kullanarak uygulamayı yüklediğinde, içinde bir bağımlılığı ayrı olarak yüklemeniz gereken tek senaryo olduğundan <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98048-202">The only scenario in which you need to install a dependency separately is when the application loads it using reflection, for example by calling the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="98048-203">Kullanmayın <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> yöntemi ile yerel görüntüler.</span><span class="sxs-lookup"><span data-stu-id="98048-203">Do not use the <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> method with native images.</span></span> <span data-ttu-id="98048-204">Bu metotla yüklenen bir görüntü, yürütme bağlamındaki diğer derlemeler tarafından kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98048-204">An image loaded with this method cannot be used by other assemblies in the execution context.</span></span>  
  
 <span data-ttu-id="98048-205">Ngen.exe bağımlılıklar için bir sayaç tutar.</span><span class="sxs-lookup"><span data-stu-id="98048-205">Ngen.exe maintains a count on dependencies.</span></span> <span data-ttu-id="98048-206">Örneğin, varsayalım `MyAssembly.exe` ve `YourAssembly.exe` hem de yerel görüntü önbelleğine yüklendiğini ve her ikisi de başvurmuş `OurDependency.dll`.</span><span class="sxs-lookup"><span data-stu-id="98048-206">For example, suppose `MyAssembly.exe` and `YourAssembly.exe` are both installed in the native image cache, and both have references to `OurDependency.dll`.</span></span> <span data-ttu-id="98048-207">Varsa `MyAssembly.exe` kaldırılır, `OurDependency.dll` kaldırılmamış.</span><span class="sxs-lookup"><span data-stu-id="98048-207">If `MyAssembly.exe` is uninstalled, `OurDependency.dll` is not uninstalled.</span></span> <span data-ttu-id="98048-208">Yalnızca ne zaman kaldırıldı `YourAssembly.exe` de kaldırıldığında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="98048-208">It is only removed when `YourAssembly.exe` is also uninstalled.</span></span>  
  
 <span data-ttu-id="98048-209">Eğer genel derleme önbelleğindeki bir derleme için doğal görüntü üretiyorsanız, onun görünür ismini belirtiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-209">If you are generating a native image for an assembly in the global assembly cache, specify its display name.</span></span> <span data-ttu-id="98048-210">Bkz. <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="98048-210">See <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="98048-211">Ngen.exe'nin ürettiği doğal görüntüler uygulama alanı içerisinde paylaşılabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-211">The native images that Ngen.exe generates can be shared across application domains.</span></span> <span data-ttu-id="98048-212">Bu, Ngen.exe'yi derlemelerin uygulama etki alanları arasında paylaşılması gerektiği senaryolarda kullanabileceğiniz anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="98048-212">This means you can use Ngen.exe in application scenarios that require assemblies to be shared across application domains.</span></span> <span data-ttu-id="98048-213">Alan bağımsızlığını belirtmek için:</span><span class="sxs-lookup"><span data-stu-id="98048-213">To specify domain neutrality:</span></span>  
  
-   <span data-ttu-id="98048-214">Uygulama <xref:System.LoaderOptimizationAttribute> uygulamanıza.</span><span class="sxs-lookup"><span data-stu-id="98048-214">Apply the <xref:System.LoaderOptimizationAttribute> attribute to your application.</span></span>  
  
-   <span data-ttu-id="98048-215">Ayarlama <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> yeni bir uygulama etki alanı kurulum bilgilerini oluşturduğunuzda özelliği.</span><span class="sxs-lookup"><span data-stu-id="98048-215">Set the <xref:System.AppDomainSetup.LoaderOptimization%2A?displayProperty=nameWithType> property when you create setup information for a new application domain.</span></span>  
  
 <span data-ttu-id="98048-216">Birden çok uygulama alanına aynı derleme yüklediğiniz zaman mutlaka alan-bağımsız kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-216">Always use domain-neutral code when loading the same assembly into multiple application domains.</span></span> <span data-ttu-id="98048-217">Eğer bir doğal görüntü paylaşılmış alana yüklendikten sonra paylaşılmamış alana yüklenirse, görüntü kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="98048-217">If a native image is loaded into a nonshared application domain after having been loaded into a shared domain, it cannot be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-218">Alan-bağımsız kod yüklemesi geri alınamaz (geri döndürülemez) ve performans, özellikle statik elemanlara erişildiği zaman, çok az daha yavaş olabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-218">Domain-neutral code cannot be unloaded, and performance may be slightly slower, particularly when accessing static members.</span></span>  
  
 <span data-ttu-id="98048-219">Bu açıklamalar bölümünde:</span><span class="sxs-lookup"><span data-stu-id="98048-219">In this Remarks section:</span></span>  
  
-   [<span data-ttu-id="98048-220">Farklı senaryolar için görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="98048-220">Generating images for different scenarios</span></span>](#Scenarios)  
  
-   [<span data-ttu-id="98048-221">Ne zaman yerel görüntü kullanılacağını belirleme</span><span class="sxs-lookup"><span data-stu-id="98048-221">Determining when to Use native images</span></span>](#WhenToUse)  
  
    -   [<span data-ttu-id="98048-222">Bellek kullanımı İyileştirildi</span><span class="sxs-lookup"><span data-stu-id="98048-222">Improved memory use</span></span>](#Memory)  
  
    -   [<span data-ttu-id="98048-223">Daha hızlı uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="98048-223">Faster application startup</span></span>](#Startup)  
  
    -   [<span data-ttu-id="98048-224">Kullanım değerlendirmelerine özeti</span><span class="sxs-lookup"><span data-stu-id="98048-224">Summary of usage considerations</span></span>](#UsageSummary)  
  
-   [<span data-ttu-id="98048-225">Derleme temel adreslerinin önemi</span><span class="sxs-lookup"><span data-stu-id="98048-225">Importance of assembly base addresses</span></span>](#BaseAddresses)  
  
-   [<span data-ttu-id="98048-226">Sıkı bağlama</span><span class="sxs-lookup"><span data-stu-id="98048-226">Hard binding</span></span>](#HardBinding)  
  
    -   [<span data-ttu-id="98048-227">Bir bağımlılık için bağlama tavsiyesi belirtmek</span><span class="sxs-lookup"><span data-stu-id="98048-227">Specifying a binding hint for a dependency</span></span>](#DependencyHint)  
  
    -   [<span data-ttu-id="98048-228">Bir derleme için varsayılan bağlama tavsiyesi belirtmek</span><span class="sxs-lookup"><span data-stu-id="98048-228">Specifying a default binding hint for an assembly</span></span>](#AssemblyHint)  
  
-   [<span data-ttu-id="98048-229">Ertelenen işlem</span><span class="sxs-lookup"><span data-stu-id="98048-229">Deferred processing</span></span>](#Deferred)  
  
-   [<span data-ttu-id="98048-230">Yerel görüntüler ve JIT derlemesi</span><span class="sxs-lookup"><span data-stu-id="98048-230">Native images and JIT compilation</span></span>](#JITCompilation)  
  
    -   [<span data-ttu-id="98048-231">Geçersiz görüntüler</span><span class="sxs-lookup"><span data-stu-id="98048-231">Invalid images</span></span>](#InvalidImages)  
  
-   [<span data-ttu-id="98048-232">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="98048-232">Troubleshooting</span></span>](#Troubleshooting)  
  
    -   [<span data-ttu-id="98048-233">Derleme Bağlaması Günlük Görüntüleyici</span><span class="sxs-lookup"><span data-stu-id="98048-233">Assembly Binding Log Viewer</span></span>](#Fusion)  
  
    -   [<span data-ttu-id="98048-234">Jıtcompilationstart yönetilen hata ayıklama Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="98048-234">The JITCompilationStart managed debugging assistant</span></span>](#MDA)  
  
    -   [<span data-ttu-id="98048-235">Yerel görüntü oluşturma dışında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="98048-235">Opting out of native image generation</span></span>](#OptOut)  
  
<a name="Scenarios"></a>   
## <a name="generating-images-for-----different-scenarios"></a><span data-ttu-id="98048-236">Farklı senaryolar için görüntü oluşturma</span><span class="sxs-lookup"><span data-stu-id="98048-236">Generating images for     different scenarios</span></span>  
 <span data-ttu-id="98048-237">Bir derleme için yerel bir görüntü oluşturduktan sonra çalışma zamanı otomatik olarak bulun ve bu derlemeyi her çalıştırdığı zaman bu doğal görüntüyü kullanmak çalışır.</span><span class="sxs-lookup"><span data-stu-id="98048-237">After you have generated a native image for an assembly, the runtime automatically attempts to locate and use this native   image each time it runs the assembly.</span></span> <span data-ttu-id="98048-238">Kullanım senaryolarına göre, birden fazla görüntüler oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-238">Multiple images can be generated, depending on usage scenarios.</span></span>  
  
 <span data-ttu-id="98048-239">Bir derlemeyi hata ayıklama veya profil oluşturma senaryosunda çalıştırırsanız, örneğin, çalışma zamanı ile oluşturulan yerel bir görüntü arar `/Debug` veya `/Profile` seçenekleri.</span><span class="sxs-lookup"><span data-stu-id="98048-239">For example, if you run an assembly in a debugging or profiling scenario, the runtime looks for a native image that was generated with the `/Debug` or `/Profile` options.</span></span> <span data-ttu-id="98048-240">Eğer eşleşen bir doğal görüntü bulamazsa, çalışma zamanı standart JIT derlemesine geri döner.</span><span class="sxs-lookup"><span data-stu-id="98048-240">If it is unable to find a matching native image, the runtime reverts to standard JIT compilation.</span></span> <span data-ttu-id="98048-241">Doğal görüntüleri ayıklamanın tek yolu, bir doğal görüntü ile oluşturmaktır `/Debug` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="98048-241">The only way to debug native images is to create a native image with the `/Debug` option.</span></span>  
  
 <span data-ttu-id="98048-242">`uninstall` Eylemi de senaryoları destekler, dolayısıyla tüm senaryoları veya yalnızca seçili senaryoları kaldırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-242">The `uninstall` action also recognize scenarios, so you can uninstall all scenarios or only selected scenarios.</span></span>  
  
<a name="WhenToUse"></a>   
## <a name="determining-when-to-use-native-images"></a><span data-ttu-id="98048-243">Ne zaman yerel görüntü kullanılacağını belirleme</span><span class="sxs-lookup"><span data-stu-id="98048-243">Determining when to Use native images</span></span>  
 <span data-ttu-id="98048-244">Yerel görüntüler iki alanda performans iyileştirmesi sağlayabilir: daha iyi bellek kullanımı ve daha az başlangıç zamanı.</span><span class="sxs-lookup"><span data-stu-id="98048-244">Native images can provide performance improvements in two areas: improved memory use and reduced startup time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-245">Yerel görüntülerin performansı; kod ve veri erişim desenleri, modül sınırları dışına yapılan çağrı sayısı ve diğer uygulamalar tarafından şimdiye kadar yüklenmiş olan bağımlılık sayısı gibi analizi zorlaştıran çeşitli etkenlere bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-245">Performance of native images depends on a number of factors that make analysis difficult, such as code and data access patterns, how many calls are made across module boundaries, and how many dependencies have already been loaded by other applications.</span></span> <span data-ttu-id="98048-246">Yerel görüntülerin uygulamanıza yararlı olup olmadığını belirlemenin tek yolu, anahtar dağıtım senaryolarınızda yapacağını dikkatli performans ölçümleridir.</span><span class="sxs-lookup"><span data-stu-id="98048-246">The only way to determine whether native images benefit your application is by careful performance measurements in your key deployment scenarios.</span></span>  
  
<a name="Memory"></a>   
### <a name="improved-memory-use"></a><span data-ttu-id="98048-247">Bellek kullanımı İyileştirildi</span><span class="sxs-lookup"><span data-stu-id="98048-247">Improved memory use</span></span>  
 <span data-ttu-id="98048-248">Yerel görüntüler kod işlemler arasında paylaşıldığında bellek kullanımını önemli ölçüde iyileştirebilirler.</span><span class="sxs-lookup"><span data-stu-id="98048-248">Native images can significantly improve memory use when code is shared between processes.</span></span> <span data-ttu-id="98048-249">Yerel görüntüler Windows PE dosyalarıdır, yani bir .dll dosyasının tek kopyası birden çok işlem tarafından paylaşılabilir; buna karşılık, JIT derleyicisi tarafından üretilen yerel kod özel bellekte tutulur ve paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="98048-249">Native images are Windows PE files, so a single copy of a .dll file can be shared by multiple processes; by contrast, native code produced by the JIT compiler is stored in private memory and cannot be shared.</span></span>  
  
 <span data-ttu-id="98048-250">Terminal hizmetleri altında çalışan uygulamalar da paylaşılan kod sayfalarından yararlanabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-250">Applications that are run under terminal services can also benefit from shared code pages.</span></span>  
  
 <span data-ttu-id="98048-251">Ek olarak, JIT derleyicisini yüklememek her uygulama örneği için sabit bir miktarda bellek kazandırır.</span><span class="sxs-lookup"><span data-stu-id="98048-251">In addition, not loading the JIT compiler saves a fixed amount of memory for each application instance.</span></span>  
  
<a name="Startup"></a>   
### <a name="faster-application-startup"></a><span data-ttu-id="98048-252">Daha hızlı uygulama başlatma</span><span class="sxs-lookup"><span data-stu-id="98048-252">Faster application startup</span></span>  
 <span data-ttu-id="98048-253">Derlemeleri Ngen.exe ile ön derlemek bazı uygulamalar için başlangıç süresini iyileştirebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-253">Precompiling assemblies with Ngen.exe can improve the startup time for some applications.</span></span> <span data-ttu-id="98048-254">Genel olarak, uygulamalar bileşen derlemelerini paylaştığında kazanç olabilir, çünkü ilk uygulama başladıktan sonra paylaşılan bileşenler sonraki uygulamalar için zaten yüklü olur.</span><span class="sxs-lookup"><span data-stu-id="98048-254">In general, gains can be made when applications share component assemblies because after the first application has been started the shared components are already loaded for subsequent applications.</span></span> <span data-ttu-id="98048-255">Uygulamadaki tüm derlemelerin sabit diskten yüklenmesini gerektiren soğuk başlangıç yerel görüntülerden pek fayda kazanmaz, çünkü sabit disk erişim süresi baskın olur.</span><span class="sxs-lookup"><span data-stu-id="98048-255">Cold startup, in which all the assemblies in an application must be loaded from the hard disk, does not benefit as much from native images because the hard disk access time predominates.</span></span>  
  
 <span data-ttu-id="98048-256">Sabit bağlama başlatma süresini etkileyebilir, çünkü ana uygulama derlemesine sabit bağlı olan tüm resimler aynı anda yüklenmelidirler.</span><span class="sxs-lookup"><span data-stu-id="98048-256">Hard binding can affect startup time, because all images that are hard bound to the main application assembly must be loaded at the same time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-257">Önce [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], yükleyici genel derleme önbelleğinde etkili bir şekilde herhangi bir geliştirme ortadan olmayan tanımlayıcı adlı derlemeler ek doğrulama gerçekleştirdiğinden paylaşılan, tanımlayıcı adlı bileşenleri genel bütünleştirilmiş kod önbelleğinde koymanız gerekir Yerel görüntüler kullanmanın sağladığı başlangıç zamanında.</span><span class="sxs-lookup"><span data-stu-id="98048-257">Before the [!INCLUDE[net_v35SP1_long](../../../includes/net-v35sp1-long-md.md)], you should put shared, strong-named components in the global assembly cache, because the loader performs extra validation on strong-named assemblies that are not in the global assembly cache, effectively eliminating any improvement in startup time gained by using native images.</span></span> <span data-ttu-id="98048-258">Sürümünde yapılan iyileştirmeler [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] ek doğrulamayı kaldırır.</span><span class="sxs-lookup"><span data-stu-id="98048-258">Optimizations that were introduced in the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] removed the extra validation.</span></span>  
  
<a name="UsageSummary"></a>   
### <a name="summary-of-usage-considerations"></a><span data-ttu-id="98048-259">Kullanım değerlendirmelerine özeti</span><span class="sxs-lookup"><span data-stu-id="98048-259">Summary of usage considerations</span></span>  
 <span data-ttu-id="98048-260">Aşağıdaki genel önemli noktalar ve uygulama önemli noktaları uygulamanız için yerel görüntüleri değerlendirmek üzere çaba harcayıp harcamamaya karar vermenize yardımcı olabilir:</span><span class="sxs-lookup"><span data-stu-id="98048-260">The following general considerations and application considerations may assist you in deciding whether to undertake the effort of evaluating native images for your application:</span></span>  
  
-   <span data-ttu-id="98048-261">Yerel görüntüler MSIL'den daha hızlı yüklenir çünkü JIT derlemesi ve tür güvenliği doğrulaması gibi pek çok başlangıç aktivitesine gereksinimi ortadan kaldırırlar.</span><span class="sxs-lookup"><span data-stu-id="98048-261">Native images load faster than MSIL because they eliminate the need for many startup activities, such as JIT compilation and type-safety verification.</span></span>  
  
-   <span data-ttu-id="98048-262">Yerel görüntüler daha küçük ilk çalışma kümesi gerektirirler çünkü JIT derleyicisine gerek yoktur.</span><span class="sxs-lookup"><span data-stu-id="98048-262">Native images require a smaller initial working set because there is no need for the JIT compiler.</span></span>  
  
-   <span data-ttu-id="98048-263">Yerel görüntüler işlemler arasında kod paylaşımını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="98048-263">Native images enable code sharing between processes.</span></span>  
  
-   <span data-ttu-id="98048-264">Yerel görüntüler MSIL derlemelerinden daha fazla sabit disk alanı gerektirir ve üretmek için büyük miktarda zaman gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-264">Native images require more hard disk space than MSIL assemblies and may require considerable time to generate.</span></span>  
  
-   <span data-ttu-id="98048-265">Yerel görüntüler bakılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-265">Native images must be maintained.</span></span>  
  
    -   <span data-ttu-id="98048-266">Orijinal derleme veya bağımlılıklarından biri değiştiğinde görüntüler yeniden oluşturulmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-266">Images need to be regenerated when the original assembly or one of its dependencies is serviced.</span></span>  
  
    -   <span data-ttu-id="98048-267">Tek bir derleme farklı uygulamalarda ya da farklı senaryolarda kullanılması için birden çok yerel görüntüye ihtiyaç duyabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-267">A single assembly may need multiple native images for use in different applications or different scenarios.</span></span> <span data-ttu-id="98048-268">Örneğin, iki uygulamadaki yapılandırma bilgileri aynı bağımlı derleme için farklı bağlama kararlarına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-268">For example, the configuration information in two applications might result in different binding decisions for the same dependent assembly.</span></span>  
  
    -   <span data-ttu-id="98048-269">Yerel görüntüler bir yönetici, yani Yöneticiler grubu içindeki bir Windows hesabı, tarafından üretilmelidir.</span><span class="sxs-lookup"><span data-stu-id="98048-269">Native images must be generated by an administrator; that is, from a Windows account in the Administrators group.</span></span>  
  
 <span data-ttu-id="98048-270">Bu genel önemli noktalara ek olarak, yerel görüntülerin bir performans kazancı sağlayıp sağlamayacağını belirlerken uygulamanızın doğası da göz önüne alınmalıdır:</span><span class="sxs-lookup"><span data-stu-id="98048-270">In addition to these general considerations, the nature of your application must be considered when determining whether native images might provide a performance benefit:</span></span>  
  
-   <span data-ttu-id="98048-271">Eğer uygulamanız pek çok paylaşılan bileşen kullanan bir ortamda çalışıyorsa, yerel görüntüler bileşenlerin birden çok işlem tarafından paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-271">If your application runs in an environment that uses many shared components, native images allow the components to be shared by multiple processes.</span></span>  
  
-   <span data-ttu-id="98048-272">Eğer uygulamanız birden çok uygulama alanı kullanıyorsa, yerel görüntüler alanlar arasında kod sayfalarının paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-272">If your application uses multiple application domains, native images allow code pages to be shared across domains.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="98048-273">.NET Framework 1.0 ve 1.1 sürümlerinde, yerel görüntüler uygulama etki alanları arasında paylaşılamaz.</span><span class="sxs-lookup"><span data-stu-id="98048-273">In the .NET Framework versions 1.0 and 1.1, native images cannot be shared across application domains.</span></span> <span data-ttu-id="98048-274">Bu, sürüm 2.0 ve sonrasında geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="98048-274">This is not the case in version 2.0 or later.</span></span>  
  
-   <span data-ttu-id="98048-275">Eğer uygulamanız Terminal Server altında çalışacaksa, yerel görüntüler kod sayfalarının paylaşılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-275">If your application will be run under Terminal Server, native images allow sharing of code pages.</span></span>  
  
-   <span data-ttu-id="98048-276">Büyük uygulamalar yerel görüntülere derlemekten genellikle yarar görür.</span><span class="sxs-lookup"><span data-stu-id="98048-276">Large applications generally benefit from compilation to native images.</span></span> <span data-ttu-id="98048-277">Küçük uygulamalar genellikle yarar görmez.</span><span class="sxs-lookup"><span data-stu-id="98048-277">Small applications generally do not benefit.</span></span>  
  
-   <span data-ttu-id="98048-278">Uzun süre çalışan uygulamalarda, çalışma zamanı JIT derlemesi yerel görüntülerden biraz daha iyi çalışır.</span><span class="sxs-lookup"><span data-stu-id="98048-278">For long-running applications, run-time JIT compilation performs slightly better than native images.</span></span> <span data-ttu-id="98048-279">(Sabit bağlama bu performans farkını belirli bir ölçüde azaltabilir.)</span><span class="sxs-lookup"><span data-stu-id="98048-279">(Hard binding can mitigate this performance difference to some degree.)</span></span>  
  
<a name="BaseAddresses"></a>   
## <a name="importance-of-assembly-base-addresses"></a><span data-ttu-id="98048-280">Derleme temel adreslerinin önemi</span><span class="sxs-lookup"><span data-stu-id="98048-280">Importance of assembly base addresses</span></span>  
 <span data-ttu-id="98048-281">Yerel görüntüler Windows PE dosyaları olduğu için, diğer çalıştırılabilir dosyalardaki aynı yeniden temellendirme sorunlarıyla karşılaşırlar.</span><span class="sxs-lookup"><span data-stu-id="98048-281">Because native images are Windows PE files, they are subject to the same rebasing issues as other executable files.</span></span> <span data-ttu-id="98048-282">Eğer sıkı bağlama kullanılırsa, yeniden konumlandırmanın performans maliyeti daha da belirgin olur.</span><span class="sxs-lookup"><span data-stu-id="98048-282">The performance cost of relocation is even more pronounced if hard binding is employed.</span></span>  
  
 <span data-ttu-id="98048-283">Bir yerel görüntü için temel adresi ayarlamak için, derlemenin temel adresini ayarlama amacıyla derleyicinizin uygun seçeneğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-283">To set the base address for a native image, use the appropriate option of your compiler to set the base address for the assembly.</span></span> <span data-ttu-id="98048-284">Ngen.exe yerel görüntü için bu temel adresi kullanır.</span><span class="sxs-lookup"><span data-stu-id="98048-284">Ngen.exe uses this base address for the native image.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-285">Yerel görüntüler, oluşturuldukları yönetilen derlemelerden daha büyüktür.</span><span class="sxs-lookup"><span data-stu-id="98048-285">Native images are larger than the managed assemblies from which they were created.</span></span> <span data-ttu-id="98048-286">Bu daha büyük boyutlara izin vermek için temel adresler hesaplanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-286">Base addresses must be calculated to allow for these larger sizes.</span></span>  
  
 <span data-ttu-id="98048-287">Bir yerel görüntünün tercih edilen temel adresini görüntülemek için dumpbin.exe gibi bir araç kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-287">You can use a tool such as dumpbin.exe to view the preferred base address of a native image.</span></span>  
  
<a name="HardBinding"></a>   
## <a name="hard-binding"></a><span data-ttu-id="98048-288">Sıkı bağlama</span><span class="sxs-lookup"><span data-stu-id="98048-288">Hard binding</span></span>  
 <span data-ttu-id="98048-289">Sıkı bağlama doğal görüntüler için birim zamanda yapılan işi artırır ve çalışma seti alanını azaltır.</span><span class="sxs-lookup"><span data-stu-id="98048-289">Hard binding increases throughput and reduces working set size for native images.</span></span> <span data-ttu-id="98048-290">Sıkı bağlamanın dezavantajı, bir derleme yüklendiğinde o derlemeye sıkı bağlı olan tüm görüntülerin de yüklenmesinin gerekmesidir.</span><span class="sxs-lookup"><span data-stu-id="98048-290">The disadvantage of hard binding is that all the images that are hard bound to an assembly must be loaded when the assembly is loaded.</span></span> <span data-ttu-id="98048-291">Bu büyük bir uygulama için başlatma zamanını önemli derecede artırabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-291">This can significantly increase startup time for a large application.</span></span>  
  
 <span data-ttu-id="98048-292">Sıkı bağlama, uygulamanızın performansının kritik olduğu senaryolarda yüklenen bağımlılıklar için uygundur.</span><span class="sxs-lookup"><span data-stu-id="98048-292">Hard binding is appropriate for dependencies that are loaded in all your application's performance-critical scenarios.</span></span> <span data-ttu-id="98048-293">Herhangi bir doğal görüntü kullanımında, sıkı bağlanmanın uygulamanızın performansını arttırıp arttırmadığını öğrenmenin tek yolu dikkatli(hassas) performans ölçümleridir.</span><span class="sxs-lookup"><span data-stu-id="98048-293">As with any aspect of native image use, careful performance measurements are the only way to determine whether hard binding improves your application's performance.</span></span>  
  
 <span data-ttu-id="98048-294"><xref:System.Runtime.CompilerServices.DependencyAttribute> Ve <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> öznitelikleri Ngen.exe'ye sıkı bağlama ipuçları sağlamanıza izin verin.</span><span class="sxs-lookup"><span data-stu-id="98048-294">The <xref:System.Runtime.CompilerServices.DependencyAttribute> and <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> attributes allow you to provide hard binding hints to Ngen.exe.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-295">Bu değerler Ngen.exe'ye teknik/tavsiyelerdir, komutlar değillerdir.</span><span class="sxs-lookup"><span data-stu-id="98048-295">These attributes are hints to Ngen.exe, not commands.</span></span> <span data-ttu-id="98048-296">Bunları kullanmak sıkı bağlamayı garanti etmez.</span><span class="sxs-lookup"><span data-stu-id="98048-296">Using them does not guarantee hard binding.</span></span> <span data-ttu-id="98048-297">Bu değerlerin anlamları ileri yayınlarda değişebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-297">The meaning of these attributes may change in future releases.</span></span>  
  
<a name="DependencyHint"></a>   
### <a name="specifying-a-binding-hint-for-a-dependency"></a><span data-ttu-id="98048-298">Bir bağımlılık için bağlama tavsiyesi belirtmek</span><span class="sxs-lookup"><span data-stu-id="98048-298">Specifying a binding hint for a dependency</span></span>  
 <span data-ttu-id="98048-299">Uygulama <xref:System.Runtime.CompilerServices.DependencyAttribute> belirtilen bağımlılık yüklenecek olasılığını belirtmek için bir derleme.</span><span class="sxs-lookup"><span data-stu-id="98048-299">Apply the <xref:System.Runtime.CompilerServices.DependencyAttribute> to an assembly to indicate the likelihood that a specified dependency will be loaded.</span></span> <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> <span data-ttu-id="98048-300">sıkı bağlamanın uygun olduğunu gösterir <xref:System.Runtime.CompilerServices.LoadHint.Default> varsayılan bağımlılık için kullanılmasını gösteren ve <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> sıkı bağlamanın uygun olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="98048-300">indicates that hard binding is appropriate, <xref:System.Runtime.CompilerServices.LoadHint.Default> indicates that the default for the dependency should be used, and <xref:System.Runtime.CompilerServices.LoadHint.Sometimes> indicates that hard binding is not appropriate.</span></span>  
  
 <span data-ttu-id="98048-301">Aşağıdaki kod, iki bağlılığı olan bir derlemenin özniteliklerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="98048-301">The following code shows the attributes for an assembly that has two dependencies.</span></span> <span data-ttu-id="98048-302">İlk bağımlılık (Assembly1) sıkı bağlama için uygun bir adaydır ve ikinci bağımlılık (Assembly2) değildir.</span><span class="sxs-lookup"><span data-stu-id="98048-302">The first dependency (Assembly1) is an appropriate candidate for hard binding, and the second (Assembly2) is not.</span></span>  
  
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
  
 <span data-ttu-id="98048-303">Derleme ismi dosya ismi uzantısını içermez.</span><span class="sxs-lookup"><span data-stu-id="98048-303">The assembly name does not include the file name extension.</span></span> <span data-ttu-id="98048-304">Görünür isim kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-304">Display names can be used.</span></span>  
  
<a name="AssemblyHint"></a>   
### <a name="specifying-a-default-binding-hint-for-an-assembly"></a><span data-ttu-id="98048-305">Bir derleme için varsayılan bağlama tavsiyesi belirtmek</span><span class="sxs-lookup"><span data-stu-id="98048-305">Specifying a default binding hint for an assembly</span></span>  
 <span data-ttu-id="98048-306">Varsayılan bağlama ipuçları, yalnızca onlara bağlılığı olan herhangi bir uygulama tarafından anında ve sıkça kullanılacak olan derlemeler için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="98048-306">Default binding hints are only needed for assemblies that will be used immediately and frequently by any application that has a dependency on them.</span></span> <span data-ttu-id="98048-307">Uygulama <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> ile <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> gibi derlemelerde sıkı bağlamanın kullanılması gerektiğini belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="98048-307">Apply the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> with <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> to such assemblies to specify that hard binding should be used.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-308">Geçerli bir sebep olmadığı <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> dışında herhangi bir değere sahip bir öznitelik uygulamak için bu kategoriye giren değil .dll derlemelere <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> özniteliği hiç uygulama değil aynı etkiye sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98048-308">There is no reason to apply <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to .dll assemblies that do not fall into this category, because applying the attribute with any value other than <xref:System.Runtime.CompilerServices.LoadHint.Always?displayProperty=nameWithType> has the same effect as not applying the attribute at all.</span></span>  
  
 <span data-ttu-id="98048-309">Microsoft'un kullandığı <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> sıkı bağlamanın derlemeler .NET Framework içerisindeki mscorlib.dll gibi çok az sayıda için varsayılan değer olduğunu belirtmek için.</span><span class="sxs-lookup"><span data-stu-id="98048-309">Microsoft uses the <xref:System.Runtime.CompilerServices.DefaultDependencyAttribute> to specify that hard binding is the default for a very small number of assemblies in the .NET Framework, such as mscorlib.dll.</span></span>  
  
<a name="Deferred"></a>   
## <a name="deferred-processing"></a><span data-ttu-id="98048-310">Ertelenen işlem</span><span class="sxs-lookup"><span data-stu-id="98048-310">Deferred processing</span></span>  
 <span data-ttu-id="98048-311">Çok büyük bir uygulama için yerel görüntü oluşturmak uzun bir süre alabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-311">Generation of native images for a very large application can take considerable time.</span></span> <span data-ttu-id="98048-312">Benzer şekilde, paylaşılan bir bileşene veya bilgisayar seçeneklerine yapılan değişiklikler pek çok yerel görüntünün güncellenmesini gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-312">Similarly, changes to a shared component or changes to computer settings might require many native images to be updated.</span></span> <span data-ttu-id="98048-313">`install` Ve `update` eylemlerinde bir `/queue` yerel görüntü hizmeti tarafından Ertelenen yürütme için işlemi kuyruklar seçeneği.</span><span class="sxs-lookup"><span data-stu-id="98048-313">The `install` and `update` actions have a `/queue` option that queues the operation for deferred execution by the native image service.</span></span> <span data-ttu-id="98048-314">Ayrıca, Ngen.exe sahip `queue` ve `executeQueuedItems` hizmet üzerinde bir miktar denetim sağlayan eylemler.</span><span class="sxs-lookup"><span data-stu-id="98048-314">In addition, Ngen.exe has `queue` and `executeQueuedItems` actions that provide some control over the service.</span></span> <span data-ttu-id="98048-315">Daha fazla bilgi için [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-315">For more information, see [Native Image Service](#native-image-service).</span></span>  
  
<a name="JITCompilation"></a>   
## <a name="native-images-and-jit-compilation"></a><span data-ttu-id="98048-316">Yerel görüntüler ve JIT derlemesi</span><span class="sxs-lookup"><span data-stu-id="98048-316">Native images and JIT compilation</span></span>  
 <span data-ttu-id="98048-317">Eğer Ngen.exe assembly içerisinde oluşturamayacağı herhangi bir metotla karşılaşırsa, onları doğal görüntü (özgün görüntü) içerisine dahil etmez.</span><span class="sxs-lookup"><span data-stu-id="98048-317">If Ngen.exe encounters any methods in an assembly that it cannot generate, it excludes them from the native image.</span></span> <span data-ttu-id="98048-318">Çalışma zamanı bu derlemeyi çalıştırdığı zaman, doğal görüntünün içerisine dahil edilmeyen metotlar için JIT derleme işlemine döner</span><span class="sxs-lookup"><span data-stu-id="98048-318">When the runtime executes this assembly, it reverts to JIT compilation for the methods that were not included in the native image.</span></span>  
  
 <span data-ttu-id="98048-319">Ek olarak, derleme yükseltildiyse veya görüntü herhangi bir sebeple geçersiz kılındıysa yerel görüntüler kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="98048-319">In addition, native images are not used if the assembly has been upgraded, or if the image has been invalidated for any reason.</span></span>  
  
<a name="InvalidImages"></a>   
### <a name="invalid-images"></a><span data-ttu-id="98048-320">Geçersiz görüntüler</span><span class="sxs-lookup"><span data-stu-id="98048-320">Invalid images</span></span>  
 <span data-ttu-id="98048-321">Ngen.exe'yi bir derlemenin yerel görüntüsünü oluşturmak için kullandığınızda; çıktı, belirlediğin komut satırı seçeneklerine ve bilgisayarınızdaki belirli ayarlara bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-321">When you use Ngen.exe to create a native image of an assembly, the output depends upon the command-line options that you specify and certain settings on your computer.</span></span> <span data-ttu-id="98048-322">Bu ayarlar aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="98048-322">These settings include the following:</span></span>  
  
-   <span data-ttu-id="98048-323">.NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="98048-323">The version of the .NET Framework.</span></span>  
  
-   <span data-ttu-id="98048-324">Windows 9 x ailesinden Windows NT ailesine değişiklikse işletim sistemi, sürümü.</span><span class="sxs-lookup"><span data-stu-id="98048-324">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
-   <span data-ttu-id="98048-325">Derlemenin tam kimliği (yeniden derleme kimliği değiştirir).</span><span class="sxs-lookup"><span data-stu-id="98048-325">The exact identity of the assembly (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="98048-326">Derlemenin başvurduğu tüm derlemelerin tam kimliği (yeniden derleme kimliği değiştirir).</span><span class="sxs-lookup"><span data-stu-id="98048-326">The exact identity of all assemblies that the assembly references (recompilation changes identity).</span></span>  
  
-   <span data-ttu-id="98048-327">Güvenlik etkenleri.</span><span class="sxs-lookup"><span data-stu-id="98048-327">Security factors.</span></span>  
  
 <span data-ttu-id="98048-328">Ngen.exe bir doğal görüntü oluşturduğu zaman bu bilgiyi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="98048-328">Ngen.exe records this information when it generates a native image.</span></span> <span data-ttu-id="98048-329">Bir derlemeyi çalıştırdığınız zaman, çalışma zamanı bilgisayarın o anki çevresine uyan seçenekler ve ayarlarla oluşturulmuş olan doğal görüntüyü arar.</span><span class="sxs-lookup"><span data-stu-id="98048-329">When you execute an assembly, the runtime looks for the native image generated with options and settings that match the computer's current environment.</span></span> <span data-ttu-id="98048-330">Çalışma zamanı eğer eşleşen bir doğal görüntü bulamazsa, derlemeyi JIT ile derleme yoluna gider.</span><span class="sxs-lookup"><span data-stu-id="98048-330">The runtime reverts to JIT compilation of an assembly if it cannot find a matching native image.</span></span> <span data-ttu-id="98048-331">Bilgisayarın ayarlarına ve çevresine uygulanan aşağıdaki değişiklikler doğal görüntünün geçersiz olmasına sebep olur:</span><span class="sxs-lookup"><span data-stu-id="98048-331">The following changes to a computer's settings and environment cause native images to become invalid:</span></span>  
  
-   <span data-ttu-id="98048-332">.NET Framework sürümü.</span><span class="sxs-lookup"><span data-stu-id="98048-332">The version of the .NET Framework.</span></span>  
  
     <span data-ttu-id="98048-333">Eğer .NET framework'e güncelleme uygularsanız, Ngen.exe kullanarak oluşturduğunuz bütün imajlar geçersiz sayılır.</span><span class="sxs-lookup"><span data-stu-id="98048-333">If you apply an update to the .NET Framework, all native images that you have created using Ngen.exe become invalid.</span></span> <span data-ttu-id="98048-334">Bu nedenle, .NET Framework'ün tüm güncelleştirmeleri yürütme `Ngen Update` tüm yerel görüntüleri yeniden oluşturulduğunu garantilemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="98048-334">For this reason, all updates of the .NET Framework execute the `Ngen Update` command, to ensure that all native images are regenerated.</span></span> <span data-ttu-id="98048-335">.NET framework kuracağı .Net framework kütüphaneleri için yeni görüntüleri otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98048-335">The .NET Framework automatically creates new native images for the .NET Framework libraries that it installs.</span></span>  
  
-   <span data-ttu-id="98048-336">Windows 9 x ailesinden Windows NT ailesine değişiklikse işletim sistemi, sürümü.</span><span class="sxs-lookup"><span data-stu-id="98048-336">The version of the operating system, if the change is from the Windows 9x family to the Windows NT family.</span></span>  
  
     <span data-ttu-id="98048-337">Örneğin, bir bilgisayarda çalışan işletim sistemi sürümünü Windows 98'den Windows XP'ye değişirse, yerel görüntü önbelleğinde depolanan tüm özgün görüntüler geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="98048-337">For example, if the version of the operating system running on a computer changes from Windows 98 to Windows XP, all native images stored in the native image cache become invalid.</span></span> <span data-ttu-id="98048-338">İşletim sistemi Windows 2000'den Windows XP'ye değişirse, ancak görüntüleri geçersiz kılınır değil.</span><span class="sxs-lookup"><span data-stu-id="98048-338">However, if the operating system changes from Windows 2000 to Windows XP, the images are not invalidated.</span></span>  
  
-   <span data-ttu-id="98048-339">Derlemenin kesin kimliği.</span><span class="sxs-lookup"><span data-stu-id="98048-339">The exact identity of the assembly.</span></span>  
  
     <span data-ttu-id="98048-340">Eğer derlemeyi yeniden derlerseniz, derlemeye karşılık gelen doğal görüntü geçersiz olur.</span><span class="sxs-lookup"><span data-stu-id="98048-340">If you recompile an assembly, the assembly's corresponding native image becomes invalid.</span></span>  
  
-   <span data-ttu-id="98048-341">Derlemenin referans ettiği bütün derlemelerin tam kimliği.</span><span class="sxs-lookup"><span data-stu-id="98048-341">The exact identity of any assemblies the assembly references.</span></span>  
  
     <span data-ttu-id="98048-342">Eğer yönetilmiş bir derlemeyi güncellerseniz, o derlemeye direk ya da dolaylı yoldan bağlı olan bütün doğal görüntüler geçersiz olur ve yeniden oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98048-342">If you update a managed assembly, all native images that directly or indirectly depend on that assembly become invalid and need to be regenerated.</span></span> <span data-ttu-id="98048-343">Bu hem normal tercihleri/ayarları hem de sıkı-bağlama bağlılıklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="98048-343">This includes both ordinary references and hard-bound dependencies.</span></span> <span data-ttu-id="98048-344">Bir uygulama güncellemesi uygulanırsa olduğunda, yükleme programının yürütülecek bir `Ngen Update` bütün bağlı doğal görüntülerin yeniden oluşturulduğunu garantilemek için komutu.</span><span class="sxs-lookup"><span data-stu-id="98048-344">Whenever a software update is applied, the installation program should execute an `Ngen Update` command to ensure that all dependent native images are regenerated.</span></span>  
  
-   <span data-ttu-id="98048-345">Güvenlik etkenleri.</span><span class="sxs-lookup"><span data-stu-id="98048-345">Security factors.</span></span>  
  
     <span data-ttu-id="98048-346">Önceden yetkilendirilmiş bir derlemenin izinlerini kısıtlamak için makina güvenlik politikasında değişiklik yapmak, o derleme için önceden derlenmiş olan doğal imajın geçersiz olmasına sebep olabilir</span><span class="sxs-lookup"><span data-stu-id="98048-346">Changing machine security policy to restrict permissions previously granted to an assembly can cause a previously compiled native image for that assembly to become invalid.</span></span>  
  
     <span data-ttu-id="98048-347">Ortak dil çalışma zamanı kod erişim güvenliğini nasıl yönettiği ve izinleri nasıl kullandığı hakkında ayrıntılı bilgi için bkz: [kod erişim güvenliği](../../../docs/framework/misc/code-access-security.md).</span><span class="sxs-lookup"><span data-stu-id="98048-347">For detailed information about how the common language runtime administers code access security and how to use permissions, see [Code Access Security](../../../docs/framework/misc/code-access-security.md).</span></span>  
  
<a name="Troubleshooting"></a>   
## <a name="troubleshooting"></a><span data-ttu-id="98048-348">Sorun giderme</span><span class="sxs-lookup"><span data-stu-id="98048-348">Troubleshooting</span></span>  
 <span data-ttu-id="98048-349">Aşağıdaki sorun giderme konularına hangi yerel görüntüler kullanılır ve uygulamanız tarafından kullanılamaz görmenize olanak veren, JIT derleyicisi, bir yöntem derlemeye başlar ve yerel görüntü derlemesi dışında nasıl gösterir belirlemek üzere belirlenen yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="98048-349">The following troubleshooting topics allow you to see which native images are being used and which cannot be used by your application, to determine when the JIT compiler starts to compile a method, and shows how to opt out of native image compilation of specified methods.</span></span>  
  
<a name="Fusion"></a>   
### <a name="assembly-binding-log-viewer"></a><span data-ttu-id="98048-350">Derleme Bağlaması Günlük Görüntüleyici</span><span class="sxs-lookup"><span data-stu-id="98048-350">Assembly Binding Log Viewer</span></span>  
 <span data-ttu-id="98048-351">Yerel görüntüler, uygulamanız tarafından kullanıldığını onaylamak için kullanabileceğiniz [Fuslogvw.exe (Derleme bağlaması Günlük Görüntüleyici)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span><span class="sxs-lookup"><span data-stu-id="98048-351">To confirm that native images are being used by your application, you can use the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md).</span></span> <span data-ttu-id="98048-352">Seçin **yerel görüntüleri** içinde **günlük kategorileri** bağlaması Günlük Görüntüleyici penceresinde kutusu.</span><span class="sxs-lookup"><span data-stu-id="98048-352">Select **Native Images** in the **Log Categories** box on the binding log viewer window.</span></span> <span data-ttu-id="98048-353">Fuslogvw.exe bir doğal imajın neden reddedildiği hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-353">Fuslogvw.exe provides information about why a native image was rejected.</span></span>  
  
<a name="MDA"></a>   
### <a name="the-jitcompilationstart-managed-debugging-assistant"></a><span data-ttu-id="98048-354">Jıtcompilationstart yönetilen hata ayıklama Yardımcısı</span><span class="sxs-lookup"><span data-stu-id="98048-354">The JITCompilationStart managed debugging assistant</span></span>  
 <span data-ttu-id="98048-355">Kullanabileceğiniz [Jıtcompilationstart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) yönetilen hata ayıklama Yardımcısı (MDA) JIT Derleyici bir işlevi derlemeye ne başladığında belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="98048-355">You can use the [jitCompilationStart](../../../docs/framework/debug-trace-profile/jitcompilationstart-mda.md) managed debugging assistant (MDA) to determine when the JIT compiler starts to compile a function.</span></span>  
  
<a name="OptOut"></a>   
### <a name="opting-out-of-native-image-generation"></a><span data-ttu-id="98048-356">Yerel görüntü oluşturma dışında seçim yapma</span><span class="sxs-lookup"><span data-stu-id="98048-356">Opting out of native image generation</span></span>  
 <span data-ttu-id="98048-357">Bazı durumlarda, NGen.exe yerel görüntü için belirli bir yöntemi veya yöntem JIT olarak tercih edebilirsiniz, yerine yerel bir görüntü için derlenmiş zorluk oluşturma olabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-357">In some cases, NGen.exe may have difficulty generating a native image for a specific method, or you may prefer that the method be JIT compiled rather then compiled to a native image.</span></span> <span data-ttu-id="98048-358">Bu durumda, kullanabileceğiniz `System.Runtime.BypassNGenAttribute` NGen.exe bir doğal görüntü belirli bir yöntem için oluşturmasını önlemek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="98048-358">In this case, you can use the `System.Runtime.BypassNGenAttribute` attribute to prevent NGen.exe from generating a native image for a particular method.</span></span> <span data-ttu-id="98048-359">Öznitelik kod doğal görüntünün içerisine dahil etmek istemediğiniz her yöntem için ayrı ayrı uygulanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="98048-359">The attribute must be applied individually to each method whose code you do not want to include in the native image.</span></span> <span data-ttu-id="98048-360">NGen.exe, öznitelik tanır ve yerel görüntü karşılık gelen yöntemi için kod oluşturmaz.</span><span class="sxs-lookup"><span data-stu-id="98048-360">NGen.exe recognizes the attribute and does not generate code in the native image for the corresponding method.</span></span>  
  
 <span data-ttu-id="98048-361">Ancak, unutmayın, `BypassNGenAttribute` .NET Framework sınıf kitaplığındaki bir tür olarak tanımlı değil.</span><span class="sxs-lookup"><span data-stu-id="98048-361">Note, however, that `BypassNGenAttribute` is not defined as a type in the .NET Framework Class Library.</span></span> <span data-ttu-id="98048-362">Öznitelik, kodunuzu kullanmak için önce bunu şu şekilde tanımlamanız gerekir:</span><span class="sxs-lookup"><span data-stu-id="98048-362">In order to consume the attribute in your code, you must first define it as follows:</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#1)]
 [!code-vb[System.Runtime.BypassNGenAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#1)]  
  
 <span data-ttu-id="98048-363">Ardından, öznitelik bir yöntem başına temelinde uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-363">You can then apply the attribute on a per-method basis.</span></span> <span data-ttu-id="98048-364">Aşağıdaki örnek, bir yerel görüntü üretmemelidir Native Image Generator talimatı verir `ExampleClass.ToJITCompile` yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98048-364">The following example instructs the Native Image Generator that it should not generate a native image for the `ExampleClass.ToJITCompile` method.</span></span>  
  
 [!code-csharp[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/cs/Optout1.cs#2)]
 [!code-vb[System.Runtime.BypassNGenAttribute#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/System.Runtime.BypassNGenAttribute/vb/Optout1.vb#2)]  
  
## <a name="examples"></a><span data-ttu-id="98048-365">Örnekler</span><span class="sxs-lookup"><span data-stu-id="98048-365">Examples</span></span>  
 <span data-ttu-id="98048-366">Aşağıdaki komutu bir yerel görüntü oluşturur `ClientApp.exe`geçerli dizinde bulunan ve görüntünün yerel görüntü önbelleğine yükler.</span><span class="sxs-lookup"><span data-stu-id="98048-366">The following command generates a native image for `ClientApp.exe`, located in the current directory, and installs the image in the native image cache.</span></span> <span data-ttu-id="98048-367">Derleme için bir yapılandırma dosyası varsa, onu Ngen.exe kullanır.</span><span class="sxs-lookup"><span data-stu-id="98048-367">If a configuration file exists for the assembly, Ngen.exe uses it.</span></span> <span data-ttu-id="98048-368">Ayrıca, herhangi bir .dll dosyası için özgün görüntüler oluşturulur `ClientApp.exe` başvuruları.</span><span class="sxs-lookup"><span data-stu-id="98048-368">In addition, native images are generated for any .dll files that `ClientApp.exe` references.</span></span>  
  
```  
ngen install ClientApp.exe  
```  
  
 <span data-ttu-id="98048-369">Ngen.exe ile yüklenmiş bir resim, bir kök olarak da adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="98048-369">An image installed with Ngen.exe is also called a root.</span></span> <span data-ttu-id="98048-370">Kök, bir uygulama veya paylaşılan bir bileşen olabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-370">A root can be an application or a shared component.</span></span>  
  
 <span data-ttu-id="98048-371">Aşağıdaki komutu bir yerel görüntü oluşturur `MyAssembly.exe` belirtilen yola sahip.</span><span class="sxs-lookup"><span data-stu-id="98048-371">The following command generates a native image for `MyAssembly.exe` with the specified path.</span></span>  
  
```  
ngen install c:\myfiles\MyAssembly.exe  
```  
  
 <span data-ttu-id="98048-372">Derlemeler ve bağımlılıklarını belirlerken Ngen.exe ortak dil çalışma zamanı tarafından kullanılan aynı algılama mantığını kullanır.</span><span class="sxs-lookup"><span data-stu-id="98048-372">When locating assemblies and their dependencies, Ngen.exe uses the same probing logic used by the common language runtime.</span></span> <span data-ttu-id="98048-373">Varsayılan olarak, dizin içeren `ClientApp.exe` uygulama temel dizini olarak kullanılır ve bütün derleme yoklamaları dizinde başlar.</span><span class="sxs-lookup"><span data-stu-id="98048-373">By default, the directory that contains `ClientApp.exe` is used as the application base directory, and all assembly probing begins in this directory.</span></span> <span data-ttu-id="98048-374">Kullanarak bu davranışı geçersiz kılabilirsiniz `/AppBase` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="98048-374">You can override this behavior by using the `/AppBase` option.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-375">Bu, uygulama temel dizininin geçerli dizin olarak ayarlandığı .NET Framework 1.0 ve 1.1 sürümlerindeki Ngen.exe davranışından farklıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-375">This is a change from Ngen.exe behavior in the .NET Framework versions 1.0 and 1.1, where the application base is set to the current directory.</span></span>  
  
 <span data-ttu-id="98048-376">Bir derlemeyi kullanarak bir .dll dosyası yüklenirse, örneğin bir başvuru olmadan bağımlılığa sahip olabilir <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="98048-376">An assembly can have a dependency without a reference, for example if it loads a .dll file by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="98048-377">Şekildeki bir .dll dosyası için bir yerel görüntü uygulama derlemesindeki yapılandırma bilgilerini kullanarak oluşturabileceğiniz `/ExeConfig` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="98048-377">You can create a native image for such a .dll file by using configuration information for the application assembly, with the `/ExeConfig` option.</span></span> <span data-ttu-id="98048-378">Aşağıdaki komutu bir yerel görüntü oluşturur `MyLib.dll,` yapılandırma bilgisini kullanarak `MyApp.exe`.</span><span class="sxs-lookup"><span data-stu-id="98048-378">The following command generates a native image for `MyLib.dll,` using the configuration information from `MyApp.exe`.</span></span>  
  
```  
ngen install c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="98048-379">Uygulamayı kaldırdığınızda, bu şekilde yüklenen derlemeler kaldırılmaz.</span><span class="sxs-lookup"><span data-stu-id="98048-379">Assemblies installed in this way are not removed when the application is removed.</span></span>  
  
 <span data-ttu-id="98048-380">Bir bağımlılık kaldırmak için yüklemek için kullanılan aynı komut satırı seçeneklerini kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-380">To uninstall a dependency, use the same command-line options that were used to install it.</span></span> <span data-ttu-id="98048-381">Aşağıdaki komutu kaldırır `MyLib.dll` önceki örnekte.</span><span class="sxs-lookup"><span data-stu-id="98048-381">The following command uninstalls the `MyLib.dll` from the previous example.</span></span>  
  
```  
ngen uninstall c:\myfiles\MyLib.dll /ExeConfig:c:\myapps\MyApp.exe  
```  
  
 <span data-ttu-id="98048-382">Genel bütünleştirilmiş kod önbelleğindeki bir derleme için yerel görüntü oluşturmak için, derlemenin görünen adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-382">To create a native image for an assembly in the global assembly cache, use the display name of the assembly.</span></span> <span data-ttu-id="98048-383">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="98048-383">For example:</span></span>  
  
```  
ngen install "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
```  
  
 <span data-ttu-id="98048-384">NGen.exe yüklediğiniz her senaryo için ayrı bir görüntü kümesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="98048-384">NGen.exe generates a separate set of images for each scenario you install.</span></span> <span data-ttu-id="98048-385">Örneğin, aşağıdaki komutlar normal işlemler için tamamen yerel görüntü kümesi, hata ayıklama için farklı bir küme ve belirleme için üçüncüyü yükler:</span><span class="sxs-lookup"><span data-stu-id="98048-385">For example, the following commands install a complete set of native images for normal operation, another complete set for debugging, and a third for profiling:</span></span>  
  
```  
ngen install MyApp.exe  
ngen install MyApp.exe /debug  
ngen install MyApp.exe /profile  
```  
  
### <a name="displaying-the-native-image-cache"></a><span data-ttu-id="98048-386">Yerel Görüntü Önbelleğini Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="98048-386">Displaying the Native Image Cache</span></span>  
 <span data-ttu-id="98048-387">Yerel görüntüler önbelleğe yüklendikten sonra, Ngen.exe kullanılarak görüntülenebilirler.</span><span class="sxs-lookup"><span data-stu-id="98048-387">Once native images are installed in the cache, they can be displayed using Ngen.exe.</span></span> <span data-ttu-id="98048-388">Aşağıdaki komut yerel görüntü belleğindeki tüm yerel görüntüleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="98048-388">The following command displays all native images in the native image cache.</span></span>  
  
```  
ngen display  
```  
  
 <span data-ttu-id="98048-389">`display` Eylem tüm kök derlemeleri listeler ilk olarak, ardından da bilgisayardaki tüm yerel görüntüleri listesi tarafından.</span><span class="sxs-lookup"><span data-stu-id="98048-389">The `display` action lists all the root assemblies first, followed by a list of all the native images on the computer.</span></span>  
  
 <span data-ttu-id="98048-390">Yalnızca bir derlemenin bilgilerini görüntülemek için o derlemenin basit adını kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-390">Use the simple name of an assembly to display information only for that assembly.</span></span> <span data-ttu-id="98048-391">Aşağıdaki komut, kısmi adıyla eşleşen bir yerel görüntü belleğindeki tüm yerel görüntüleri görüntüler `MyAssembly`, bağımlılıklarını ve üzerinde bir bağımlılığa sahip olan tüm kökleri `MyAssembly`:</span><span class="sxs-lookup"><span data-stu-id="98048-391">The following command displays all native images in the native image cache that match the partial name `MyAssembly`, their dependencies, and all roots that have a dependency on `MyAssembly`:</span></span>  
  
```  
ngen display MyAssembly  
```  
  
 <span data-ttu-id="98048-392">Bir paylaşılan bileşen derlemesine hangi köklerin bağımlı olduğunu bilmek etkisini ölçmek için kullanışlıdır bir `update` paylaşılan bileşen yükseltildikten sonraki eylem.</span><span class="sxs-lookup"><span data-stu-id="98048-392">Knowing what roots depend on a shared component assembly is useful in gauging the impact of an `update` action after the shared component is upgraded.</span></span>  
  
 <span data-ttu-id="98048-393">Eğer bir derlemenin dosya uzantısını belirtirseniz, ya yolu belirtmeniz ya da Ngen.exe'yi derlemeyi içeren dizinden yürütmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="98048-393">If you specify an assembly's file extension, you must either specify the path or execute Ngen.exe from the directory containing the assembly:</span></span>  
  
```  
ngen display c:\myApps\MyAssembly.exe  
```  
  
 <span data-ttu-id="98048-394">Aşağıdaki komut yerel görüntü önbelleğinde ada sahip tüm yerel görüntüleri görüntüler `MyAssembly` ve sürüm 1.0.0.0.</span><span class="sxs-lookup"><span data-stu-id="98048-394">The following command displays all native images in the native image cache with the name `MyAssembly` and the version 1.0.0.0.</span></span>  
  
```  
ngen display "myAssembly, version=1.0.0.0"  
```  
  
### <a name="updating-images"></a><span data-ttu-id="98048-395">Görüntüleri Güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="98048-395">Updating Images</span></span>  
 <span data-ttu-id="98048-396">Görüntüler genellikle paylaşılan bir bileşen yükseltildikten sonra güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="98048-396">Images are typically updated after a shared component has been upgraded.</span></span> <span data-ttu-id="98048-397">Değişen veya bağımlılıkları değişen tüm yerel görüntüleri güncelleştirmek için `update` eylemini bağımsız değişken olmadan.</span><span class="sxs-lookup"><span data-stu-id="98048-397">To update all native images that have changed, or whose dependencies have changed, use the `update` action with no arguments.</span></span>  
  
```  
ngen update  
```  
  
 <span data-ttu-id="98048-398">Tüm görüntüleri güncelleştirmek uzun süren bir işlem olabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-398">Updating all images can be a lengthy process.</span></span> <span data-ttu-id="98048-399">Yürütme için güncelleştirmeleri kullanarak yerel görüntü hizmeti tarafından sıraya alabilirsiniz `/queue` seçeneği.</span><span class="sxs-lookup"><span data-stu-id="98048-399">You can queue the updates for execution by the native image service by using the `/queue` option.</span></span> <span data-ttu-id="98048-400">Daha fazla bilgi için `/queue` seçeneği ve yükleme öncelikleri bkz [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-400">For more information on the `/queue` option and installation priorities, see [Native Image Service](#native-image-service).</span></span>  
  
```  
ngen update /queue  
```  
  
### <a name="uninstalling-images"></a><span data-ttu-id="98048-401">Görüntüleri Kaldırma</span><span class="sxs-lookup"><span data-stu-id="98048-401">Uninstalling Images</span></span>  
 <span data-ttu-id="98048-402">Ngen.exe bağımlılıkların bir listesini tutar, yani paylaşılan bileşenler yalnızca onlara bağlı olan tüm derlemeler kaldırıldığında kaldırılır.</span><span class="sxs-lookup"><span data-stu-id="98048-402">Ngen.exe maintains a list of dependencies, so that shared components are removed only when all assemblies that depend on them have been removed.</span></span> <span data-ttu-id="98048-403">Ek olarak kök olarak yüklenmiş ortak bileşenler silinmez.</span><span class="sxs-lookup"><span data-stu-id="98048-403">In addition, a shared component is not removed if it has been installed as a root.</span></span>  
  
 <span data-ttu-id="98048-404">Aşağıdaki komut kök için tüm senaryoları kaldırır `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="98048-404">The following command uninstalls all scenarios for the root `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp  
```  
  
 <span data-ttu-id="98048-405">`uninstall` Eylemi belirli senaryoları kaldırmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-405">The `uninstall` action can be used to remove specific scenarios.</span></span> <span data-ttu-id="98048-406">Aşağıdaki komutu için tüm hata ayıklama senaryolarını kaldırır `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="98048-406">The following command uninstalls all debug scenarios for `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall ClientApp /debug  
```  
  
> [!NOTE]
>  <span data-ttu-id="98048-407">Kaldırma `/debug` senaryoları hem de içeren bir senaryoyu kaldırmaz `/profile` ve</span><span class="sxs-lookup"><span data-stu-id="98048-407">Uninstalling `/debug` scenarios does not uninstall a scenario that includes both `/profile` and</span></span> `/debug.`  
  
 <span data-ttu-id="98048-408">Aşağıdaki komut belirli bir sürümü için tüm senaryoları kaldırır `ClientApp.exe`:</span><span class="sxs-lookup"><span data-stu-id="98048-408">The following command uninstalls all scenarios for a specific version of `ClientApp.exe`:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0"  
```  
  
 <span data-ttu-id="98048-409">Tüm senaryolar için aşağıdaki komutları kaldırma `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` veya yalnızca o derleme için hata ayıklama senaryosunu:</span><span class="sxs-lookup"><span data-stu-id="98048-409">The following commands uninstall all scenarios for `"ClientApp, Version=1.0.0.0, Culture=neutral, PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL",` or just the debug scenario for that assembly:</span></span>  
  
```  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL"  
ngen uninstall "ClientApp, Version=1.0.0.0, Culture=neutral,   
  PublicKeyToken=3c7ba247adcd2081, processorArchitecture=MSIL" /debug  
```  
  
 <span data-ttu-id="98048-410">Olduğu gibi `install` eylemi, bir uzantı sağlamak ya Ngen.exe'nin derlemeyi içeren veya bir tam yol belirtilmesini dizinden yürütülmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="98048-410">As with the `install` action, supplying an extension requires either executing Ngen.exe from the directory containing the assembly or specifying a full path.</span></span>  
  
 <span data-ttu-id="98048-411">Yerel görüntü hizmetiyle ilgili örnekler için bkz. [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-411">For examples relating to the native image service, see [Native Image Service](#native-image-service).</span></span>  
  
## <a name="native-image-task"></a><span data-ttu-id="98048-412">Yerel Görüntü Görevi</span><span class="sxs-lookup"><span data-stu-id="98048-412">Native Image Task</span></span>  
 <span data-ttu-id="98048-413">Yerel görüntü görevi oluşturur ve yerel görüntüler tutar Windows bir görevdir.</span><span class="sxs-lookup"><span data-stu-id="98048-413">The native image task is a Windows task that generates and maintains native images.</span></span> <span data-ttu-id="98048-414">Yerel görüntü görevi oluşturur ve yerel görüntüleri için desteklenen senaryolar için bir otomatik olarak geri kazanır.</span><span class="sxs-lookup"><span data-stu-id="98048-414">The native image task generates and reclaims native images automatically for supported scenarios.</span></span> <span data-ttu-id="98048-415">Ayrıca, kullanmak yükleyicileri sağlar [Ngen.exe (yerel Görüntü Oluşturucu)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) oluşturup ertelenmiş aynı anda yerel görüntüleri güncelleştir.</span><span class="sxs-lookup"><span data-stu-id="98048-415">It also enables installers to use [Ngen.exe (Native Image Generator)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) to create and update native images at a deferred time.</span></span>  
  
 <span data-ttu-id="98048-416">Yerel görüntü görevi her CPU için mimarisini hedefleyen uygulamalar için derleme izin vermek için bilgisayarda her mimari desteklenen sonra kayıtlı:</span><span class="sxs-lookup"><span data-stu-id="98048-416">The native image task is registered once for each CPU architecture supported on a computer, to allow compilation for applications that target each architecture:</span></span>  
  
|<span data-ttu-id="98048-417">Görev adı</span><span class="sxs-lookup"><span data-stu-id="98048-417">Task name</span></span>|<span data-ttu-id="98048-418">32 bit bilgisayar</span><span class="sxs-lookup"><span data-stu-id="98048-418">32-bit computer</span></span>|<span data-ttu-id="98048-419">64 bit bilgisayar</span><span class="sxs-lookup"><span data-stu-id="98048-419">64-bit computer</span></span>|  
|---------------|----------------------|----------------------|  
|<span data-ttu-id="98048-420">NET Framework NGEN v4.0.30319</span><span class="sxs-lookup"><span data-stu-id="98048-420">NET Framework NGEN v4.0.30319</span></span>|<span data-ttu-id="98048-421">Evet</span><span class="sxs-lookup"><span data-stu-id="98048-421">Yes</span></span>|<span data-ttu-id="98048-422">Evet</span><span class="sxs-lookup"><span data-stu-id="98048-422">Yes</span></span>|  
|<span data-ttu-id="98048-423">NET Framework NGEN v4.0.30319 64</span><span class="sxs-lookup"><span data-stu-id="98048-423">NET Framework NGEN v4.0.30319 64</span></span>|<span data-ttu-id="98048-424">Hayır</span><span class="sxs-lookup"><span data-stu-id="98048-424">No</span></span>|<span data-ttu-id="98048-425">Evet</span><span class="sxs-lookup"><span data-stu-id="98048-425">Yes</span></span>|  
  
 <span data-ttu-id="98048-426">Yerel görüntü Görevi çalıştırırken Windows 8 veya daha sonra .NET Framework 4.5 ve sonraki sürümlerinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98048-426">The native image task is available in the .NET Framework 4.5 and later versions, when running on Windows 8 or later.</span></span> <span data-ttu-id="98048-427">Önceki Windows sürümlerinde .NET Framework kullanan [Native Image Service](#native-image-service).</span><span class="sxs-lookup"><span data-stu-id="98048-427">On earlier versions of Windows, the .NET Framework uses the [Native Image Service](#native-image-service).</span></span>  
  
### <a name="task-lifetime"></a><span data-ttu-id="98048-428">Görev ömrü</span><span class="sxs-lookup"><span data-stu-id="98048-428">Task Lifetime</span></span>  
 <span data-ttu-id="98048-429">Genel olarak, Windows Görev Zamanlayıcısı'nı bilgisayar boşta olduğunda her gece yerel görüntü görevi başlatır.</span><span class="sxs-lookup"><span data-stu-id="98048-429">In general, the Windows Task Scheduler starts the native image task every night when the computer is idle.</span></span> <span data-ttu-id="98048-430">Görev uygulama yükleyicileri, tüm ertelenmiş yerel görüntü güncelleştirme istekleri ve herhangi bir otomatik görüntü oluşturma tarafından sıraya alınan tüm ertelenmiş çalışmadır denetler.</span><span class="sxs-lookup"><span data-stu-id="98048-430">The task checks for any deferred work that is queued by application installers, any deferred native image update requests, and any automatic image creation.</span></span> <span data-ttu-id="98048-431">Görev, bekleyen iş öğeleri tamamlandıktan ve kapanır.</span><span class="sxs-lookup"><span data-stu-id="98048-431">The task completes outstanding work items and then shuts down.</span></span> <span data-ttu-id="98048-432">Bilgisayar, Görev yürütülürken boşta kaldıktan durduğunda, görev durdurur.</span><span class="sxs-lookup"><span data-stu-id="98048-432">If the computer stops being idle while the task is running, the task stops.</span></span>  
  
 <span data-ttu-id="98048-433">Yerel görüntü görevi Ngen.exe'ye el ile yapılan çağrıları veya Görev Zamanlayıcı kullanıcı Arabirimi aracılığıyla el ile de başlatabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-433">You can also start the native image task manually through the Task Scheduler UI or through manual calls to NGen.exe.</span></span> <span data-ttu-id="98048-434">Görev bu yöntemlerden birini başlatılırsa, bilgisayar artık boştayken çalışmaya devam edecek.</span><span class="sxs-lookup"><span data-stu-id="98048-434">If the task is started through either of these methods, it will continue running when the computer is no longer idle.</span></span> <span data-ttu-id="98048-435">NGen.exe kullanarak el ile oluşturulmuş görüntüleri uygulama yükleyicileri için tahmin edilebilir davranış sağlamak önceliklendirilir.</span><span class="sxs-lookup"><span data-stu-id="98048-435">Images created manually by using NGen.exe are prioritized to enable predictable behavior for application installers.</span></span>  
  
## <a name="native-image-service"></a><span data-ttu-id="98048-436">Yerel Görüntü Hizmeti</span><span class="sxs-lookup"><span data-stu-id="98048-436">Native Image Service</span></span>  
 <span data-ttu-id="98048-437">Yerel görüntü hizmeti oluşturur ve yerel görüntüler tutan bir Windows hizmetidir.</span><span class="sxs-lookup"><span data-stu-id="98048-437">The native image service is a Windows service that generates and maintains native images.</span></span> <span data-ttu-id="98048-438">Yerel görüntü hizmetini yükleme ve bilgisayar boşta olduğunda dönemlere yerel görüntülerin güncelleştirmesi erteleme Geliştirici sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-438">The native image service allows the developer to defer the installation and update of native images to periods when the computer is idle.</span></span>  
  
 <span data-ttu-id="98048-439">Normalde, yerel görüntü hizmeti, bir uygulama veya güncelleştirme için yükleme programını (Yükleyici) tarafından başlatılır.</span><span class="sxs-lookup"><span data-stu-id="98048-439">Normally, the native image service is initiated by the installation program (installer) for an application or update.</span></span> <span data-ttu-id="98048-440">Öncelik 3 eylemler için bilgisayardaki boşta kalma süresi boyunca hizmeti yürütür.</span><span class="sxs-lookup"><span data-stu-id="98048-440">For priority 3 actions, the service executes during idle time on the computer.</span></span> <span data-ttu-id="98048-441">Hizmet durumunu kaydeder ve birden çok yeniden başlatma gerekiyorsa devam etmeden özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="98048-441">The service saves its state and is capable of continuing through multiple reboots if necessary.</span></span> <span data-ttu-id="98048-442">Birden çok görüntü derlemeleri sıraya alınmış.</span><span class="sxs-lookup"><span data-stu-id="98048-442">Multiple image compilations can be queued.</span></span>  
  
 <span data-ttu-id="98048-443">Hizmet ayrıca el ile Ngen.exe komut ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="98048-443">The service also interacts with the manual Ngen.exe command.</span></span> <span data-ttu-id="98048-444">El ile komutları arka plan etkinliği daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="98048-444">Manual commands take precedence over background activity.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="98048-445">Windows Vista'da, yerel görüntü hizmetinde görüntülenen "Microsoft.NET Framework NGEN sürüm 2.0.50727_X86" veya "Microsoft.NET Framework NGEN sürüm 2.0.50727_x64" addır.</span><span class="sxs-lookup"><span data-stu-id="98048-445">On Windows Vista, the name displayed for the native image service is "Microsoft.NET Framework NGEN v2.0.50727_X86" or "Microsoft.NET Framework NGEN v2.0.50727_X64".</span></span> <span data-ttu-id="98048-446">Tüm önceki sürümlerinde Microsoft Windows, adı ".NET çalışma zamanı en iyi duruma getirme hizmeti sürüm 2.0.50727_X86" veya ".NET çalışma zamanı en iyi duruma getirme hizmeti sürüm 2.0.50727_x64" şeklindedir.</span><span class="sxs-lookup"><span data-stu-id="98048-446">On all earlier versions of Microsoft Windows, the name is ".NET Runtime Optimization Service v2.0.50727_X86" or ".NET Runtime Optimization Service v2.0.50727_X64".</span></span>  
  
### <a name="launching-deferred-operations"></a><span data-ttu-id="98048-447">Ertelenmiş işlem başlatma</span><span class="sxs-lookup"><span data-stu-id="98048-447">Launching Deferred Operations</span></span>  
 <span data-ttu-id="98048-448">Bir yükleme veya yükseltme başlamadan önce hizmetin duraklatılması önerilir.</span><span class="sxs-lookup"><span data-stu-id="98048-448">Before beginning an installation or upgrade, pausing the service is recommended.</span></span> <span data-ttu-id="98048-449">Bu yükleyici dosyalarını kopyalama veya genel derleme önbelleğinde derlemeleri yerleştirme sırasında hizmet yürütmez sağlar.</span><span class="sxs-lookup"><span data-stu-id="98048-449">This ensures that the service does not execute while the installer is copying files or putting assemblies in the global assembly cache.</span></span> <span data-ttu-id="98048-450">Ngen.exe komut satırını hizmet duraklatır:</span><span class="sxs-lookup"><span data-stu-id="98048-450">The following Ngen.exe command line pauses the service:</span></span>  
  
```  
ngen queue pause  
```  
  
 <span data-ttu-id="98048-451">Tüm ertelenmiş işlemler kuyruğa atılmış hizmeti sürdürmek aşağıdaki komutu sağlar:</span><span class="sxs-lookup"><span data-stu-id="98048-451">When all deferred operations have been queued, the following command allows the service to resume:</span></span>  
  
```  
ngen queue continue  
```  
  
 <span data-ttu-id="98048-452">Yerel görüntü oluşturma yeni bir uygulama yüklerken veya paylaşılan bir bileşen güncelleştirirken ertelemek için kullanmak `/queue` seçeneğini `install` veya `update` eylemler.</span><span class="sxs-lookup"><span data-stu-id="98048-452">To defer native image generation when installing a new application or when updating a shared component, use the `/queue` option with the `install` or `update` actions.</span></span> <span data-ttu-id="98048-453">Aşağıdaki Ngen.exe komut satırları, paylaşılan bir bileşen için yerel bir görüntü yükleyin ve etkilenmiş tüm kökleri güncelleştirmesi gerçekleştirin:</span><span class="sxs-lookup"><span data-stu-id="98048-453">The following Ngen.exe command lines install a native image for a shared component and perform an update of all roots that may have been affected:</span></span>  
  
```  
ngen install MyComponent /queue  
ngen update /queue  
```  
  
 <span data-ttu-id="98048-454">`update` Eylemi yeniden oluşturur kılınan, tüm yerel görüntüleri yalnızca kullananlar `MyComponent`.</span><span class="sxs-lookup"><span data-stu-id="98048-454">The `update` action regenerates all native images that have been invalidated, not just those that use `MyComponent`.</span></span>  
  
 <span data-ttu-id="98048-455">Uygulamanız birçok kökleri oluşuyorsa, ertelenmiş işlemler önceliğini kontrol edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="98048-455">If your application consists of many roots, you can control the priority of the deferred actions.</span></span> <span data-ttu-id="98048-456">Aşağıdaki komutları üç kökleri yüklenmesini kuyruğa alın.</span><span class="sxs-lookup"><span data-stu-id="98048-456">The following commands queue the installation of three roots.</span></span> `Assembly1` <span data-ttu-id="98048-457">boşta kalma süresi beklenmeden önce yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-457">is installed first, without waiting for idle time.</span></span> `Assembly2` <span data-ttu-id="98048-458">boşta kalma süresi için ancak tüm 1 öncelikli Eylemler tamamladıktan sonra beklenmeden de yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-458">is also installed without waiting for idle time, but after all priority 1 actions have completed.</span></span> `Assembly3` <span data-ttu-id="98048-459">hizmeti bilgisayarın boşta olduğunu algıladığında yüklenir.</span><span class="sxs-lookup"><span data-stu-id="98048-459">is installed when the service detects that the computer is idle.</span></span>  
  
```  
ngen install Assembly1 /queue:1  
ngen install Assembly2 /queue:2  
ngen install Assembly3 /queue:3  
```  
  
 <span data-ttu-id="98048-460">Kuyruğa Alınan eylemleri kullanarak zaman uyumlu olarak gerçekleşmesi için zorlayabilirsiniz `executeQueuedItems` eylem.</span><span class="sxs-lookup"><span data-stu-id="98048-460">You can force queued actions to occur synchronously by using the `executeQueuedItems` action.</span></span> <span data-ttu-id="98048-461">İsteğe bağlı öncelik sağlarsanız, bu eylem, eşit veya daha düşük önceliğe sahip kuyruğa alınan eylemleri etkiler.</span><span class="sxs-lookup"><span data-stu-id="98048-461">If you supply the optional priority, this action affects only the queued actions that have equal or lower priority.</span></span> <span data-ttu-id="98048-462">Varsayılan öncelik aşağıdaki Ngen.exe komut tüm kuyruğa alınan eylemleri hemen işler ve bitene kadar döndürmeyen 3, olduğundan:</span><span class="sxs-lookup"><span data-stu-id="98048-462">The default priority is 3, so the following Ngen.exe command processes all queued actions immediately, and does not return until they are finished:</span></span>  
  
```  
ngen executeQueuedItems  
```  
  
 <span data-ttu-id="98048-463">Zaman uyumlu komutları tarafından Ngen.exe yürütüldüğü, yerel görüntü hizmeti kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="98048-463">Synchronous commands are executed by Ngen.exe and do not use the native image service.</span></span> <span data-ttu-id="98048-464">Ngen.exe yerel görüntü hizmeti çalışırken kullanarak eylemleri yürütebilir.</span><span class="sxs-lookup"><span data-stu-id="98048-464">You can execute actions using Ngen.exe while the native image service is running.</span></span>  
  
### <a name="service-shutdown"></a><span data-ttu-id="98048-465">Hizmet kapanması</span><span class="sxs-lookup"><span data-stu-id="98048-465">Service Shutdown</span></span>  
 <span data-ttu-id="98048-466">İçeren bir Ngen.exe komut yürütülmesi tarafından başlatılan sonra `/queue` seçeneği, hizmetin arka planda çalışır tüm eylemleri tamamlanana kadar.</span><span class="sxs-lookup"><span data-stu-id="98048-466">After being initiated by the execution of an Ngen.exe command that includes the `/queue` option, the service runs in the background until all actions have been completed.</span></span> <span data-ttu-id="98048-467">Birden çok yeniden başlatma gerekirse sürdürebilmek hizmet durumunu kaydeder.</span><span class="sxs-lookup"><span data-stu-id="98048-467">The service saves its state so that it can continue through multiple reboots if necessary.</span></span> <span data-ttu-id="98048-468">Hizmet olduğunu algıladığında kuyruğa başka eylem yok, böylece bir bilgisayar önyüklendiğinde sonraki sefer yeniden başlatmaz durumunu sıfırlar ve ardından kendini kapatır.</span><span class="sxs-lookup"><span data-stu-id="98048-468">When the service detects that there are no more actions queued, it resets its status so that it will not restart the next time the computer is booted, and then it shuts itself down.</span></span>  
  
### <a name="service-interaction-with-clients"></a><span data-ttu-id="98048-469">İstemcilerin hizmet etkileşim</span><span class="sxs-lookup"><span data-stu-id="98048-469">Service Interaction with Clients</span></span>  
 <span data-ttu-id="98048-470">.NET Framework sürüm 2. 0'da, yerel görüntü hizmeti ilgili tek etkileşim komut satırı Ngen.exe aracıdır.</span><span class="sxs-lookup"><span data-stu-id="98048-470">In the .NET Framework version 2.0, the only interaction with the native image service is through the command-line tool Ngen.exe.</span></span> <span data-ttu-id="98048-471">Komut satırı aracı kuyruğu eylemlerini yükleme betikleri yerel görüntü hizmeti ve hizmetiyle etkileşim kurmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="98048-471">Use the command-line tool in installation scripts to queue actions for the native image service and to interact with the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98048-472">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98048-472">See also</span></span>

- [<span data-ttu-id="98048-473">Araçlar</span><span class="sxs-lookup"><span data-stu-id="98048-473">Tools</span></span>](../../../docs/framework/tools/index.md)
- [<span data-ttu-id="98048-474">Yönetilen Yürütme İşlemi</span><span class="sxs-lookup"><span data-stu-id="98048-474">Managed Execution Process</span></span>](../../../docs/standard/managed-execution-process.md)
- [<span data-ttu-id="98048-475">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="98048-475">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="98048-476">Komut İstemleri</span><span class="sxs-lookup"><span data-stu-id="98048-476">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
