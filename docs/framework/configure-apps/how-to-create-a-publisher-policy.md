---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
description: Derleme satıcılarının, uygulamaların daha yeni sürümü kullanması gerektiğini öğrenmek için .NET 'teki yükseltilmiş bir derleme ile bir yayımcı ilke dosyası oluşturma hakkında bilgi edinin.
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 23e9d8144ec5742e0371d566b7af59dc9dd30c9b
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/19/2020
ms.locfileid: "85105409"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="36dcb-103">Nasıl yapılır: Yayımcı İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36dcb-103">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="36dcb-104">Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-104">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="36dcb-105">Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="36dcb-105">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="36dcb-106">Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-106">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="36dcb-107">Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="36dcb-107">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="36dcb-108">Bir yayımcı ilke dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36dcb-108">Create a publisher policy file.</span></span>

2. <span data-ttu-id="36dcb-109">Yayımcı ilkesi derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36dcb-109">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="36dcb-110">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36dcb-110">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="36dcb-111">Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36dcb-111">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="36dcb-112">Aşağıdaki örnek, bir sürümünü diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir `myAssembly` .</span><span class="sxs-lookup"><span data-stu-id="36dcb-112">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="36dcb-113">Bir kod tabanının nasıl belirtileceği hakkında bilgi edinmek için bkz. [derlemenin konumunu belirtme](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="36dcb-113">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="36dcb-114">Yayımcı Ilkesi derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="36dcb-114">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="36dcb-115">Yayımcı ilke derlemesini oluşturmak için [Derleme Bağlayıcı (Al.exe)](../tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="36dcb-115">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="36dcb-116">Yayımcı ilkesi derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="36dcb-116">To create a publisher policy assembly</span></span>

<span data-ttu-id="36dcb-117">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="36dcb-117">Type the following command at the command prompt:</span></span>

```console
al /link:publisherPolicyFile /out:publisherPolicyAssemblyFile /keyfile:keyPairFile /platform:processorArchitecture
```

<span data-ttu-id="36dcb-118">Şu komutta:</span><span class="sxs-lookup"><span data-stu-id="36dcb-118">In this command:</span></span>

- <span data-ttu-id="36dcb-119">`publisherPolicyFile`Bağımsız değişkeni Yayımcı ilke dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="36dcb-119">The `publisherPolicyFile` argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="36dcb-120">`publisherPolicyAssemblyFile`Bağımsız değişkeni, bu komutun sonucu olan yayımcı ilke derlemesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="36dcb-120">The `publisherPolicyAssemblyFile` argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="36dcb-121">Derleme dosyası adı şu biçimde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="36dcb-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="36dcb-122">'policy.majorNumber.minorNumber.mainAssemblyName.dll '</span><span class="sxs-lookup"><span data-stu-id="36dcb-122">\`policy.majorNumber.minorNumber.mainAssemblyName.dll'</span></span>

- <span data-ttu-id="36dcb-123">`keyPairFile`Bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="36dcb-123">The `keyPairFile` argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="36dcb-124">Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-124">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="36dcb-125">`processorArchitecture`Bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36dcb-125">The `processorArchitecture` argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="36dcb-126">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-126">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="36dcb-127">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-127">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="36dcb-128">Aşağıdaki komut, adlı bir yayımcı ilke dosyasından çağrılan bir yayımcı ilkesi derlemesi oluşturur `policy.1.0.myAssembly` `pub.config` , dosyadaki anahtar çiftini kullanarak derlemeye tanımlayıcı bir ad atar `sgKey.snk` ve derlemenin x86 işlemci mimarisini hedeflediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-128">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```console
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="36dcb-129">Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-129">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="36dcb-130">Bu nedenle, derlemenizin bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değeri varsa <xref:System.Reflection.ProcessorArchitecture.MSIL> , bu derleme için yayımcı ilke derlemesinin ile oluşturulması gerekir `/platform:anycpu` .</span><span class="sxs-lookup"><span data-stu-id="36dcb-130">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="36dcb-131">İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="36dcb-131">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="36dcb-132">Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36dcb-132">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="36dcb-133">Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="36dcb-133">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="36dcb-134">Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="36dcb-134">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="36dcb-135">Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme</span><span class="sxs-lookup"><span data-stu-id="36dcb-135">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="36dcb-136">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="36dcb-136">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="36dcb-137">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="36dcb-137">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="36dcb-138">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="36dcb-138">Type the following command at the command prompt:</span></span>

```console
gacutil /i publisherPolicyAssemblyFile
```

<span data-ttu-id="36dcb-139">Aşağıdaki komut, `policy.1.0.myAssembly.dll` genel derleme önbelleğine ekler.</span><span class="sxs-lookup"><span data-stu-id="36dcb-139">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```console
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="36dcb-140">Bağımsız değişkende belirtilen özgün yayımcı ilkesi dosyası `/link` derlemeyle aynı dizinde yer aldığı sürece Yayımcı ilkesi derlemesi genel derleme önbelleğine eklenemez.</span><span class="sxs-lookup"><span data-stu-id="36dcb-140">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file specified in the `/link` argument is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="36dcb-141">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36dcb-141">See also</span></span>

- [<span data-ttu-id="36dcb-142">Derlemelerle Programlama</span><span class="sxs-lookup"><span data-stu-id="36dcb-142">Programming with Assemblies</span></span>](../../standard/assembly/index.md)
- [<span data-ttu-id="36dcb-143">Çalışma Zamanının Derlemelerin Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="36dcb-143">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="36dcb-144">Yapılandırma Dosyalarını Kullanarak Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36dcb-144">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="36dcb-145">Çalışma zamanı ayarları şeması</span><span class="sxs-lookup"><span data-stu-id="36dcb-145">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="36dcb-146">Yapılandırma dosyası şeması</span><span class="sxs-lookup"><span data-stu-id="36dcb-146">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="36dcb-147">Derleme Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="36dcb-147">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
