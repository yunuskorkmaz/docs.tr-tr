---
title: 'Nasıl yapılır: Yayımcı ilkesi oluşturma'
ms.date: 03/30/2017
helpviewer_keywords:
- publisher policy assembly
- publisher policy files
- GAC (global assembly cache), publisher policy assembly
- global assembly cache, publisher policy assembly
ms.assetid: 8046bc5d-2fa9-4277-8a5e-6dcc96c281d9
ms.openlocfilehash: 5b69d6add9a01b890cdcc1c6f3be1b1d35f3cd78
ms.sourcegitcommit: b351b0781a035616c90c68ccae6dd60aae66a953
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/26/2019
ms.locfileid: "55083515"
---
# <a name="how-to-create-a-publisher-policy"></a><span data-ttu-id="6ebdb-102">Nasıl yapılır: Yayımcı ilkesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ebdb-102">How to: Create a Publisher Policy</span></span>
<span data-ttu-id="6ebdb-103">Derleme satıcıları, uygulamaları yükseltilen derlemeye bir yayımcı ilkesi dosyası dahil ederek bir derlemenin daha yeni bir sürümünü kullanacağını durumu.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-103">Vendors of assemblies can state that applications should use a newer version of an assembly by including a publisher policy file with the upgraded assembly.</span></span> <span data-ttu-id="6ebdb-104">Yayımcı ilkesi dosyası, derleme yeniden yönlendirmesini ve kod temel ayarları belirtir ve bir uygulama yapılandırma dosyası aynı biçimi kullanır.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-104">The publisher policy file specifies assembly redirection and code base settings, and uses the same format as an application configuration file.</span></span> <span data-ttu-id="6ebdb-105">Yayımcı ilkesi dosyası bir bütünleştirilmiş kod içine derlenmiş ve genel bütünleştirilmiş kod önbelleğine yerleştirilmesi.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-105">The publisher policy file is compiled into an assembly and placed in the global assembly cache.</span></span>  
  
 <span data-ttu-id="6ebdb-106">Yayımcı ilkesi oluşturmak için gerekli olan üç adım vardır:</span><span class="sxs-lookup"><span data-stu-id="6ebdb-106">There are three steps involved in creating a publisher policy:</span></span>  
  
1.  <span data-ttu-id="6ebdb-107">Yayımcı ilkesi dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-107">Create a publisher policy file.</span></span>  
  
2.  <span data-ttu-id="6ebdb-108">Yayımcı ilke derlemesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-108">Create a publisher policy assembly.</span></span>  
  
3.  <span data-ttu-id="6ebdb-109">Yayımcı ilke derlemesi genel derleme önbelleğine ekleme.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-109">Add the publisher policy assembly to the global assembly cache.</span></span>  
  
 <span data-ttu-id="6ebdb-110">Yayımcı ilkesi için şema açıklanan [derleme sürümlerini yeniden yönlendirme](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span><span class="sxs-lookup"><span data-stu-id="6ebdb-110">The schema for publisher policy is described in [Redirecting Assembly Versions](../../../docs/framework/configure-apps/redirect-assembly-versions.md).</span></span> <span data-ttu-id="6ebdb-111">Aşağıdaki örnek, bir yayımcı gösterir. bir sürümü yönlendiren ilke dosyası `myAssembly` diğerine.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-111">The following example shows a publisher policy file that redirects one version of `myAssembly` to another.</span></span>  
  
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
  
 <span data-ttu-id="6ebdb-112">Bir kod tabanına belirleme konusunda bilgi edinmek için [bir derlemenin konumunu belirtme](../../../docs/framework/configure-apps/specify-assembly-location.md).</span><span class="sxs-lookup"><span data-stu-id="6ebdb-112">To learn how to specify a code base, see [Specifying an Assembly's Location](../../../docs/framework/configure-apps/specify-assembly-location.md).</span></span>  
  
## <a name="creating-the-publisher-policy-assembly"></a><span data-ttu-id="6ebdb-113">Yayımcı ilke derlemesi oluşturma</span><span class="sxs-lookup"><span data-stu-id="6ebdb-113">Creating the Publisher Policy Assembly</span></span>  
 <span data-ttu-id="6ebdb-114">Kullanım [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) yayımcı ilke derlemesi oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-114">Use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to create the publisher policy assembly.</span></span>  
  
#### <a name="to-create-a-publisher-policy-assembly"></a><span data-ttu-id="6ebdb-115">Yayımcı ilke derlemesi oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="6ebdb-115">To create a publisher policy assembly</span></span>  
  
1.  <span data-ttu-id="6ebdb-116">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ebdb-116">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="6ebdb-117">**Al/Link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:**  *keyPairFile* **/Platform:** *processorArchitecture*</span><span class="sxs-lookup"><span data-stu-id="6ebdb-117">**al /link:** *publisherPolicyFile* **/out:** *publisherPolicyAssemblyFile* **/keyfile:** *keyPairFile* **/platform:** *processorArchitecture*</span></span>  
  
     <span data-ttu-id="6ebdb-118">Bu komutta:</span><span class="sxs-lookup"><span data-stu-id="6ebdb-118">In this command:</span></span>  
  
    -   <span data-ttu-id="6ebdb-119">*PublisherPolicyFile* bağımsız yayımcı ilkesi dosyası adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-119">The *publisherPolicyFile* argument is the name of the publisher policy file.</span></span>  
  
    -   <span data-ttu-id="6ebdb-120">*PublisherPolicyAssemblyFile* bağımsız değişkeni, bu komutu sonuçları yayımcı ilke derlemesi adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-120">The *publisherPolicyAssemblyFile* argument is the name of the publisher policy assembly that results from this command.</span></span> <span data-ttu-id="6ebdb-121">Derleme dosya adı biçimi izlemelidir:</span><span class="sxs-lookup"><span data-stu-id="6ebdb-121">The assembly file name must follow the format:</span></span>  
  
         <span data-ttu-id="6ebdb-122">**ilke.**</span><span class="sxs-lookup"><span data-stu-id="6ebdb-122">**policy.**</span></span> <span data-ttu-id="6ebdb-123">*majorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="6ebdb-123">*majorNumber* **.**</span></span> <span data-ttu-id="6ebdb-124">*minorNumber* **.**</span><span class="sxs-lookup"><span data-stu-id="6ebdb-124">*minorNumber* **.**</span></span> <span data-ttu-id="6ebdb-125">*mainAssemblyName* **.dll**</span><span class="sxs-lookup"><span data-stu-id="6ebdb-125">*mainAssemblyName* **.dll**</span></span>  
  
    -   <span data-ttu-id="6ebdb-126">*KeyPairFile* bağımsız değişkeni anahtar çiftini içeren dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-126">The *keyPairFile* argument is the name of the file containing the key pair.</span></span> <span data-ttu-id="6ebdb-127">Derleme ve yayımcı ilke derlemesi aynı anahtar çifti ile oturum açması gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-127">You must sign the assembly and publisher policy assembly with the same key pair.</span></span>  
  
    -   <span data-ttu-id="6ebdb-128">*ProcessorArchitecture* bağımsız değişkeni bir işlemciye özel derleme tarafından hedeflenen platformun tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-128">The *processorArchitecture* argument identifies the platform targeted by a processor-specific assembly.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="6ebdb-129">Belirli bir işlemci mimarisini hedefleyen olanağı, .NET Framework 2.0 sürümünde yenidir.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-129">The ability to target a specific processor architecture is new in the .NET Framework version 2.0.</span></span>  
  
     <span data-ttu-id="6ebdb-130">Aşağıdaki komut, adı verilen bir yayımcı ilke derlemesi oluşturur `policy.1.0.myAssembly` Yayımcı ilkesi dosyası olarak adlandırılan `pub.config`, içindeki anahtar çifti kullanarak derlemeyi tanımlayıcı bir ad atar `sgKey.snk` dosya ve derleme x86 hedefleyen belirtir İşlemci mimarisi.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-130">The following command creates a publisher policy assembly called `policy.1.0.myAssembly` from a publisher policy file called `pub.config`, assigns a strong name to the assembly using the key pair in the `sgKey.snk` file, and specifies that the assembly targets the x86 processor architecture.</span></span>  
  
    ```  
    al /link:pub.config /out:policy.1.0.myAssembly.dll /keyfile:sgKey.snk /platform:x86  
    ```  
  
     <span data-ttu-id="6ebdb-131">Yayımcı ilke derlemesi için geçerli bir derlemenin İşlemci mimarisi eşleşmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-131">The publisher policy assembly must match the processor architecture of the assembly that it applies to.</span></span> <span data-ttu-id="6ebdb-132">Bu nedenle, derlemenizin varsa bir <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> değerini <xref:System.Reflection.ProcessorArchitecture.MSIL>, o derleme için yayımcı ilke derlemesi ile oluşturulmalıdır `/platform:anycpu`.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-132">Thus, if your assembly has a <xref:System.Reflection.AssemblyName.ProcessorArchitecture%2A> value of <xref:System.Reflection.ProcessorArchitecture.MSIL>, the publisher policy assembly for that assembly must be created with `/platform:anycpu`.</span></span> <span data-ttu-id="6ebdb-133">Ayrı bir sağlamanız gereken her işlemciye özel derleme için yayımcı ilke derlemesi.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-133">You must provide a separate publisher policy assembly for each processor-specific assembly.</span></span>  
  
     <span data-ttu-id="6ebdb-134">Yeni bir yayımcı ilke derlemesi doğru işlemci mimarisini ile sağlayabilirsiniz bu kural bir sonucu bir derleme için İşlemci mimarisi değiştirmek için sürüm numarasının büyük veya küçük bileşen değiştirmeniz gerekir, böylelikle.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-134">A consequence of this rule is that in order to change the processor architecture for an assembly, you must change the major or minor component of the version number, so that you can supply a new publisher policy assembly with the correct processor architecture.</span></span> <span data-ttu-id="6ebdb-135">Derlemenizi farklı bir işlemci mimarisine olduğunda eski yayımcı ilke derlemesi, derlemenizi hizmet veremiyor.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-135">The old publisher policy assembly cannot service your assembly once your assembly has a different processor architecture.</span></span>  
  
     <span data-ttu-id="6ebdb-136">Başka bir sonucu, sürüm 2.0 bağlayıcı İşlemci mimarisi her zaman belirttiğinden .NET Framework'ün önceki sürümleri kullanılarak derlenmiş bir derleme için bir yayımcı ilke derlemesi oluşturmak için kullanılamaz olur.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-136">Another consequence is that the version 2.0 linker cannot be used to create a publisher policy assembly for an assembly compiled using earlier versions of the .NET Framework, because it always specifies processor architecture.</span></span>  
  
## <a name="adding-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="6ebdb-137">Yayımcı ilke derlemesi genel derleme önbelleğine ekleme</span><span class="sxs-lookup"><span data-stu-id="6ebdb-137">Adding the Publisher Policy Assembly to the Global Assembly Cache</span></span>  
 <span data-ttu-id="6ebdb-138">Kullanım [Genel Derleme Önbelleği aracını (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) yayımcı ilke derlemesi genel derleme önbelleğine eklemek için.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-138">Use the [Global Assembly Cache tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) to add the publisher policy assembly to the global assembly cache.</span></span>  
  
#### <a name="to-add-the-publisher-policy-assembly-to-the-global-assembly-cache"></a><span data-ttu-id="6ebdb-139">Yayımcı ilke derlemesi genel derleme önbelleğine eklemek için</span><span class="sxs-lookup"><span data-stu-id="6ebdb-139">To add the publisher policy assembly to the global assembly cache</span></span>  
  
1.  <span data-ttu-id="6ebdb-140">Komut isteminde aşağıdaki komutu yazın:</span><span class="sxs-lookup"><span data-stu-id="6ebdb-140">Type the following command at the command prompt:</span></span>  
  
     <span data-ttu-id="6ebdb-141">\**Gacutil /i\*\*\*publisherPolicyAssemblyFile*</span><span class="sxs-lookup"><span data-stu-id="6ebdb-141">**gacutil /i**  *publisherPolicyAssemblyFile*</span></span>  
  
     <span data-ttu-id="6ebdb-142">Aşağıdaki komut ekler `policy.1.0.myAssembly.dll` için Genel Derleme Önbelleği.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-142">The following command adds `policy.1.0.myAssembly.dll` to the global assembly cache.</span></span>  
  
    ```  
    gacutil /i policy.1.0.myAssembly.dll  
    ```  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="6ebdb-143">Özgün Yayımcı ilkesi dosyası derleme olarak aynı dizinde bulunan sürece, yayımcı ilke derlemesi genel derleme önbelleğine eklenemez.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-143">The publisher policy assembly cannot be added to the global assembly cache unless the original publisher policy file is located in the same directory as the assembly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ebdb-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ebdb-144">See also</span></span>
- [<span data-ttu-id="6ebdb-145">Bütünleştirilmiş Kodlarla Programlama</span><span class="sxs-lookup"><span data-stu-id="6ebdb-145">Programming with Assemblies</span></span>](../../../docs/framework/app-domains/programming-with-assemblies.md)
- [<span data-ttu-id="6ebdb-146">Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması</span><span class="sxs-lookup"><span data-stu-id="6ebdb-146">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6ebdb-147">Uygulamaları Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ebdb-147">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)
- [<span data-ttu-id="6ebdb-148">.NET Framework uygulamalarını yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6ebdb-148">Configuring .NET Framework Apps</span></span>](https://msdn.microsoft.com/library/d789b592-fcb5-4e3d-8ac9-e0299adaaa42)
- [<span data-ttu-id="6ebdb-149">Çalışma Zamanı Ayarları Şeması</span><span class="sxs-lookup"><span data-stu-id="6ebdb-149">Runtime Settings Schema</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [<span data-ttu-id="6ebdb-150">Yapılandırma Dosyası Şeması</span><span class="sxs-lookup"><span data-stu-id="6ebdb-150">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="6ebdb-151">Bütünleştirilmiş Kod Sürümlerini Yönlendirme</span><span class="sxs-lookup"><span data-stu-id="6ebdb-151">Redirecting Assembly Versions</span></span>](../../../docs/framework/configure-apps/redirect-assembly-versions.md)
