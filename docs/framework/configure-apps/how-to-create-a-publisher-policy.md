---
title: 'Nasıl yapılır: Yayımcı İlkesi Oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 608918828bf72369a1bd48e2391e2423078e9df0
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72846830"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="36b26-102">Nasıl yapılır: Yayımcı İlkesi Oluşturma</span><span class="sxs-lookup"><span data-stu-id="36b26-102">How to: Create a Publisher Policy</span></span>

<span data-ttu-id="36b26-103">Derlemelerin satıcıları, yükseltilen derlemeye bir yayımcı ilke dosyası ekleyerek uygulamaların bir derlemenin daha yeni bir sürümünü kullanması gerektiğini belirtebilir.</span><span class="sxs-lookup"><span data-stu-id="36b26-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="36b26-104">Yayımcı ilke dosyası, derleme yeniden yönlendirme ve kod tabanı ayarlarını belirtir ve bir uygulama yapılandırma dosyası ile aynı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="36b26-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="36b26-105">Yayımcı ilke dosyası bir derlemede derlenir ve genel derleme önbelleğine yerleştirilir.</span><span class="sxs-lookup"><span data-stu-id="36b26-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>

<span data-ttu-id="36b26-106">Yayımcı ilkesi oluşturma ile ilgili üç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="36b26-106">There are three steps involved in creating a publisher policy:</span></span>

1. <span data-ttu-id="36b26-107">Bir yayımcı ilke dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36b26-107">Create a publisher policy file.</span></span>

2. <span data-ttu-id="36b26-108">Yayımcı ilkesi derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="36b26-108">Create a publisher policy assembly.</span></span>

3. <span data-ttu-id="36b26-109">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleyin.</span><span class="sxs-lookup"><span data-stu-id="36b26-109">Add the publisher policy assembly to the global assembly cache.</span></span>

<span data-ttu-id="36b26-110">Yayımcı ilkesi şeması, [derleme sürümlerini yeniden yönlendirme](redirect-assembly-versions.md)bölümünde açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="36b26-110">The schema for publisher policy is described in [Redirecting Assembly Versions](redirect-assembly-versions.md).</span></span> <span data-ttu-id="36b26-111">Aşağıdaki örnek, `myAssembly` bir sürümünü diğerine yönlendiren bir yayımcı ilkesi dosyası gösterir.</span><span class="sxs-lookup"><span data-stu-id="36b26-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>

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

<span data-ttu-id="36b26-112">Bir kod tabanının nasıl belirtileceği hakkında bilgi edinmek için bkz. [derlemenin konumunu belirtme](specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="36b26-112">To learn how to specify a code base, see [Specifying an Assembly's Location](specify-assembly-location.md).</span></span>

## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="36b26-113">Yayımcı Ilkesi derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="36b26-113">Creating the Publisher Policy Assembly</span></span>

<span data-ttu-id="36b26-114">Yayımcı ilke derlemesini oluşturmak için [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="36b26-114">Use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>

#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="36b26-115">Yayımcı ilkesi derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="36b26-115">To create a publisher policy assembly</span></span>

<span data-ttu-id="36b26-116">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="36b26-116">Type the following command at the command prompt:</span></span>

<span data-ttu-id="36b26-117">**Al/Link:** *publisherPolicyFile* **/Out:** *publisherpolicyassemblyfile* **/keyfile:** *keyPairFile* **/Platform:** *ProcessorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="36b26-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>

<span data-ttu-id="36b26-118">Bu komutta:</span><span class="sxs-lookup"><span data-stu-id="36b26-118">In this command:</span></span>

- <span data-ttu-id="36b26-119">*PublisherPolicyFile* bağımsız değişkeni, yayımcı ilkesi dosyasının adıdır.</span><span class="sxs-lookup"><span data-stu-id="36b26-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>

- <span data-ttu-id="36b26-120">*Publisherpolicyassemblyfile* bağımsız değişkeni, bu komutun sonucu olan yayımcı ilkesi derlemesinin adıdır.</span><span class="sxs-lookup"><span data-stu-id="36b26-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="36b26-121">Derleme dosyası adı şu biçimde olmalıdır:</span><span class="sxs-lookup"><span data-stu-id="36b26-121">The assembly file name must follow the format:</span></span>

  <span data-ttu-id="36b26-122">**ilkesinin.**</span><span class="sxs-lookup"><span data-stu-id="36b26-122">**policy.**</span></span> <span data-ttu-id="36b26-123">*Majornumber* **.**</span><span class="sxs-lookup"><span data-stu-id="36b26-123">*majorNumber* **.**</span></span> <span data-ttu-id="36b26-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="36b26-124">*minorNumber* **.**</span></span> <span data-ttu-id="36b26-125">*MainAssemblyName* **. dll**</span><span class="sxs-lookup"><span data-stu-id="36b26-125">*mainAssemblyName* **.dll**</span></span>

- <span data-ttu-id="36b26-126">*KeyPairFile* bağımsız değişkeni, anahtar çiftini içeren dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="36b26-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="36b26-127">Derleme ve Yayımcı ilke derlemesini aynı anahtar çiftiyle imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="36b26-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>

- <span data-ttu-id="36b26-128">*ProcessorArchitecture* bağımsız değişkeni, işlemciye özgü bir derleme tarafından hedeflenen platformu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="36b26-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>

  > [!NOTE]
  > <span data-ttu-id="36b26-129">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36b26-129">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span>

<span data-ttu-id="36b26-130">Belirli bir işlemci mimarisini hedefleme özelliği .NET Framework 2,0 ' den başlayarak kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="36b26-130">The ability to target a specific processor architecture is available starting with .NET Framework 2.0.</span></span> <span data-ttu-id="36b26-131">Aşağıdaki komut `pub.config`adlı bir yayımcı ilke dosyasından `policy.1.0.myAssembly` adlı bir yayımcı ilke derlemesi oluşturur, `sgKey.snk` dosyasında anahtar çiftini kullanarak derlemeye tanımlayıcı bir ad atar ve derlemenin x86 işlemcisini hedeflediğini belirtir mimarisini.</span><span class="sxs-lookup"><span data-stu-id="36b26-131">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>

```
al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86
```

<span data-ttu-id="36b26-132">Yayımcı ilke derlemesinin, uygulandığı derlemenin işlemci mimarisiyle eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="36b26-132">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="36b26-133">Bu nedenle, derlemenizin <xref:System.Reflection.ProcessorArchitecture.MSIL>bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değeri varsa, bu derleme için yayımcı ilke derlemesinin `/platform:anycpu`ile oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="36b26-133">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="36b26-134">İşlemciye özgü her derleme için ayrı bir yayımcı ilke derlemesi sağlamalısınız.</span><span class="sxs-lookup"><span data-stu-id="36b26-134">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>

<span data-ttu-id="36b26-135">Bu kuralın bir sonucu, bir derlemenin işlemci mimarisini değiştirmek için, sürüm numarasının büyük veya küçük bileşenini değiştirmeniz, böylece doğru işlemci mimarisine sahip yeni bir yayımcı ilke derlemesi sağlayabilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="36b26-135">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="36b26-136">Derlemelerinizin farklı bir işlemci mimarisi varsa, eski yayımcı ilkesi derlemesi derlemenizi kullanamaz.</span><span class="sxs-lookup"><span data-stu-id="36b26-136">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>

<span data-ttu-id="36b26-137">Bunun nedeni, sürüm 2,0 bağlayıcının, .NET Framework önceki sürümleri kullanılarak derlenen bir derleme için yayımcı ilkesi derlemesi oluşturmak üzere kullanılamediği, her zaman işlemci mimarisini belirttiğinden bu bir sonucudur.</span><span class="sxs-lookup"><span data-stu-id="36b26-137">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>

## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="36b26-138">Yayımcı Ilke derlemesini genel bütünleştirilmiş kod önbelleğine ekleme</span><span class="sxs-lookup"><span data-stu-id="36b26-138">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>

<span data-ttu-id="36b26-139">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için [genel derleme önbelleği aracını (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md) kullanın.</span><span class="sxs-lookup"><span data-stu-id="36b26-139">Use the [Global Assembly Cache tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>

### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="36b26-140">Yayımcı ilke derlemesini genel bütünleştirilmiş kod önbelleğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="36b26-140">To add the publisher policy assembly to the global assembly cache</span></span>

<span data-ttu-id="36b26-141">Komut istemine aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="36b26-141">Type the following command at the command prompt:</span></span>

<span data-ttu-id="36b26-142">**Gacutil/I**  *publisherpolicyassemblyfile*</span><span class="sxs-lookup"><span data-stu-id="36b26-142">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>

<span data-ttu-id="36b26-143">Aşağıdaki komut, genel derleme önbelleğine `policy.1.0.myAssembly.dll` ekler.</span><span class="sxs-lookup"><span data-stu-id="36b26-143">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>

```
gacutil /i policy.1.0.myAssembly.dll
```

> [!IMPORTANT]
> <span data-ttu-id="36b26-144">Yayımcı ilkesi derlemesi, özgün yayımcı ilke dosyası derlemeyle aynı dizinde yer aldığı sürece genel derleme önbelleğine eklenemez.</span><span class="sxs-lookup"><span data-stu-id="36b26-144">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="36b26-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36b26-145">See also</span></span>

- [<span data-ttu-id="36b26-146">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="36b26-146">Programming with Assemblies</span></span>](../../standard/assembly/program.md)
- [<span data-ttu-id="36b26-147">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="36b26-147">How the Runtime Locates Assemblies</span></span>](../deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="36b26-148">Yapılandırma dosyalarını kullanarak uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="36b26-148">Configuring Apps by using Configuration Files</span></span>](index.md)
- [<span data-ttu-id="36b26-149">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="36b26-149">Runtime Settings Schema</span></span>](./file-schema/runtime/index.md)
- [<span data-ttu-id="36b26-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="36b26-150">Configuration File Schema</span></span>](./file-schema/index.md)
- [<span data-ttu-id="36b26-151">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="36b26-151">Redirecting Assembly Versions</span></span>](redirect-assembly-versions.md)
