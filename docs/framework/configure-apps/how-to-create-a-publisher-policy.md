---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 5484dfeb8cf5292fb43393bb39b9878114119d29
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991190"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="62f66-102">Nasıl yapılır: Yayımcı İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="62f66-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="62f66-103">Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="62f66-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="62f66-104">Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="62f66-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="62f66-105">Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="62f66-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="62f66-106">Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="62f66-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="62f66-107">Bir yayımcı ilke dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62f66-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="62f66-108">Yayımcı ilkesi derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="62f66-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="62f66-109">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="62f66-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="62f66-110">Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="62f66-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="62f66-111">Aşağıdaki örnek, bir sürümünü `myAssembly` diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="62f66-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="62f66-112">Bir kod tabanının nasıl belirtileceği hakkında bilgi edinmek için bkz. [derlemenin konumunu belirtme](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="62f66-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="62f66-113">Yayımcı Ilkesi derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="62f66-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="62f66-114">Yayımcı ilke derlemesini oluşturmak için [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="62f66-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="62f66-115">Yayımcı ilkesi derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="62f66-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="62f66-116">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="62f66-116">Type the following command at the command prompt:</span></span>

<span data-ttu-id="62f66-117">**Al/Link:** *publisherPolicyFile* **/Out:** *Publisherpolicyassemblyfile* **/keyfile:** *keyPairFile* **/Platform:** *ProcessorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="62f66-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>

<span data-ttu-id="62f66-118">Bu komutta:</span><span class="sxs-lookup"><span data-stu-id="62f66-118">In this command:</span></span>

- <span data-ttu-id="62f66-119">*PublisherPolicyFile* bağımsız değişkeni, yayımcı ilkesi dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="62f66-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="62f66-120">*Publisherpolicyassemblyfile* bağımsız değişkeni, bu komutun sonucu olan yayımcı ilkesi derlemesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="62f66-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="62f66-121">Derleme dosyası adı şu biçimde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="62f66-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="62f66-122">**ilkesinin.**</span><span class="sxs-lookup"><span data-stu-id="62f66-122">**policy.**</span></span> <span data-ttu-id="62f66-123">*Majornumber* **.**</span><span class="sxs-lookup"><span data-stu-id="62f66-123">*majorNumber* **.**</span></span> <span data-ttu-id="62f66-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="62f66-124">*minorNumber* **.**</span></span> <span data-ttu-id="62f66-125">*ana AssemblyName* **. dll**</span><span class="sxs-lookup"><span data-stu-id="62f66-125">*mainAssemblyName* **.dll**</span></span>

- <span data-ttu-id="62f66-126">*KeyPairFile* bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="62f66-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="62f66-127">Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="62f66-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="62f66-128">*ProcessorArchitecture* bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="62f66-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="62f66-129">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="62f66-129">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="62f66-130">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2.0 ile başlayarak kullanılabilir. aşağıdaki komut, adlı `policy.1.0.myAssembly` `pub.config`bir yayımcı ilke dosyasından çağrılan bir yayımcı ilkesi derlemesi oluşturur, öğesine güçlü bir ad atar. derleme, `sgKey.snk` dosyadaki anahtar çiftini kullanarak ve derlemenin x86 işlemci mimarisini hedeflediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="62f66-130">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="62f66-131">Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="62f66-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="62f66-132">Bu nedenle, derlemenizin bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> <xref:System.Reflection.ProcessorArchitecture.MSIL>değeri varsa, bu derleme için yayımcı ilke derlemesinin ile `/platform:anycpu`oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="62f66-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="62f66-133">İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="62f66-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="62f66-134">Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="62f66-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="62f66-135">Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="62f66-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="62f66-136">Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="62f66-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="62f66-137">Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme</span><span class="sxs-lookup"><span data-stu-id="62f66-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="62f66-138">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="62f66-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="62f66-139">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="62f66-139">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="62f66-140">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="62f66-140">Type the following command at the command prompt:</span></span>

<span data-ttu-id="62f66-141">**Gacutil /i** *publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="62f66-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>

<span data-ttu-id="62f66-142">Aşağıdaki komut, genel `policy.1.0.myAssembly.dll` derleme önbelleğine ekler.</span><span class="sxs-lookup"><span data-stu-id="62f66-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="62f66-143">Yayımcı ilkesi derlemesi, özgün yayımcı ilke dosyası derlemeyle aynı dizinde yer aldığı sürece genel derleme önbelleğine eklenemez.</span><span class="sxs-lookup"><span data-stu-id="62f66-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="62f66-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="62f66-144">See also</span></span>

- [<span data-ttu-id="62f66-145">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="62f66-145">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="62f66-146">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="62f66-146">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="62f66-147">Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="62f66-147">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="62f66-148">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="62f66-148">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="62f66-149">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="62f66-149">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="62f66-150">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="62f66-150">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
