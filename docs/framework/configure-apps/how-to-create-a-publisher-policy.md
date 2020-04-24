---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 7c36f6126f0d779a43a22fc11e647ba2d3b03a30
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646052"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="be9d0-102">Nasıl yapılır: Yayımcı İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be9d0-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="be9d0-103">Derleme satıcıları, uygulamaların yükseltilmiş derlemeye bir yayımcı ilke dosyası ekleyerek derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="be9d0-104">Yayımcı ilkesi dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve uygulama yapılandırma dosyasıyla aynı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="be9d0-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="be9d0-105">Yayımcı ilkesi dosyası bir derlemeiçine derlenir ve genel derleme önbelleğine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="be9d0-106">Yayımcı ilkesi oluşturmanın üç adımı vardır:</span><span class="sxs-lookup"><span data-stu-id="be9d0-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="be9d0-107">Yayımcı ilkesi dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be9d0-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="be9d0-108">Yayımcı ilkesi derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be9d0-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="be9d0-109">Yayımcı ilkesi derlemesini genel derleme önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="be9d0-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="be9d0-110">Yayımcı ilkesi şeması [Derleme Sürümleri yönlendirme](redirect-assembly-versions.md)açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="be9d0-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="be9d0-111">Aşağıdaki örnek, bir sürümünü diğerine yönlendiren bir `myAssembly` yayımcı ilkesi dosyasını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

```xml
<configuration>
   <runtime>
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
       <dependentAssembly>
         <assemblyIdentity name="myAssembly"
                           publicKeyToken="32ab4ba45e0a69a1"
                           culture="en-us" />
         <!-- Redirecting to version 2.0.0.0 of the assembly. -->
         <bindingRedirect oldVersion="1.0.0.0"
                          newVersion="2.0.0.0"/>
       </dependentAssembly>
      </assemblyBinding>
   </runtime>
</configuration>
```

<span data-ttu-id="be9d0-112">Kod tabanını nasıl belirtin, [bkz.](specify-assembly-location.md)</span><span class="sxs-lookup"><span data-stu-id="be9d0-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="be9d0-113">Yayımcı İlke Derlemesini Oluşturma</span><span class="sxs-lookup"><span data-stu-id="be9d0-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="be9d0-114">Yayımcı ilke derlemesini oluşturmak için [Derleme Bağlantı Cısı'nı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="be9d0-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="be9d0-115">Yayımcı ilkesi derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="be9d0-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="be9d0-116">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="be9d0-116">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="be9d0-117">Şu komutta:</span><span class="sxs-lookup"><span data-stu-id="be9d0-117">In this command:</span></span>

- <span data-ttu-id="be9d0-118">Bağımsız `publisherPolicyFile` değişken, yayımcı ilkesi dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="be9d0-118">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="be9d0-119">Bağımsız `publisherPolicyAssemblyFile` değişken, bu komuttan kaynaklanan yayımcı ilke derlemesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="be9d0-119">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="be9d0-120">Derleme dosya adı biçimi izlemelidir:</span><span class="sxs-lookup"><span data-stu-id="be9d0-120">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="be9d0-121">'policy.majorNumber.minorNumber.mainAssemblyName.dll'</span><span class="sxs-lookup"><span data-stu-id="be9d0-121">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="be9d0-122">Bağımsız `keyPairFile` değişken, anahtar çiftini içeren dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="be9d0-122">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="be9d0-123">Derleme ve yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-123">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="be9d0-124">Bağımsız `processorArchitecture` değişken, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="be9d0-124">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="be9d0-125">.NET Framework 2.0 ile başlayan belirli bir işlemci mimarisini hedefleme olanağı mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="be9d0-125">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="be9d0-126">.NET Framework 2.0 ile başlayan belirli bir işlemci mimarisini hedefleme olanağı mevcuttur.</span><span class="sxs-lookup"><span data-stu-id="be9d0-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="be9d0-127">Aşağıdaki komut, `policy.1.0.myAssembly` `pub.config` `sgKey.snk` dosyadaki anahtar çiftini kullanarak derlemeye güçlü bir ad atayan ve derlemenin x86 işlemci mimarisini hedefaldığını belirten yayımcı ilkesi dosyası ndan çağrılan bir yayımcı ilkesi derlemesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="be9d0-127">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="be9d0-128">Yayımcı ilke derlemesi, uygulandığı derlemenin işlemci mimarisiyle eşleşmelidir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-128">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="be9d0-129">Bu nedenle, derlemenizin <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>bir değeri varsa, bu derleme için `/platform:anycpu`yayımcı ilke derlemesi .</span><span class="sxs-lookup"><span data-stu-id="be9d0-129">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="be9d0-130">İşlemciye özgü her derleme için ayrı bir yayımcı ilkesi derlemesi sağlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-130">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="be9d0-131">Bu kuralın bir sonucu, bir derleme için işlemci mimarisini değiştirmek için, doğru işlemci mimarisi ile yeni bir yayımcı ilke derlemesi sağlamak için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-131">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="be9d0-132">Eski yayımcı ilke derlemesi, derlemeniz farklı bir işlemci mimarisine sahip olduktan sonra derlemenize hizmet veremez.</span><span class="sxs-lookup"><span data-stu-id="be9d0-132">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="be9d0-133">Başka bir sonuç, sürüm 2.0 bağlantı cısının .NET Framework'ün önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak için kullanılamamasıdır, çünkü her zaman işlemci mimarisini belirtir.</span><span class="sxs-lookup"><span data-stu-id="be9d0-133">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="be9d0-134">Yayımcı İlke Derlemesinin Küresel Meclis Önbelleğine Eklenmesi</span><span class="sxs-lookup"><span data-stu-id="be9d0-134">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="be9d0-135">Yayımcı ilke derlemesini genel derleme önbelleğine eklemek için [Genel Derleme Önbellek aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="be9d0-135">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="be9d0-136">Yayımcı ilkesi derlemesini genel derleme önbelleğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="be9d0-136">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="be9d0-137">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="be9d0-137">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="be9d0-138">Aşağıdaki komut, `policy.1.0.myAssembly.dll` genel derleme önbelleğine ekler.</span><span class="sxs-lookup"><span data-stu-id="be9d0-138">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="be9d0-139">`/link` Bağımsız değişkende belirtilen özgün yayımcı ilkesi ilkesi dosyası derlemeyle aynı dizinde bulunmadığı sürece yayımcı ilkesi derlemesi genel derleme önbelleğine eklenemez.</span><span class="sxs-lookup"><span data-stu-id="be9d0-139">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="be9d0-140">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be9d0-140">See also</span></span>

- [<span data-ttu-id="be9d0-141">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="be9d0-141">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="be9d0-142">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="be9d0-142">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="be9d0-143">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="be9d0-143">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="be9d0-144">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="be9d0-144">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="be9d0-145">Yapılandırma Dosya Şema</span><span class="sxs-lookup"><span data-stu-id="be9d0-145">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="be9d0-146">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="be9d0-146">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
