---
title: Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- deploying applications [.NET Framework], resources
- resource files, deploying
- hub-and-spoke resource deployment model
- resource files, packaging
- application resources, packaging
- public keys, obtaining
- satellite assemblies
- assemblies [.NET Framework], signing
- application resources, deploying
- Al.exe
- GAC (global assembly cache), satellite assemblies
- Assembly Linker
- directory locations for satellite assemblies
- global assembly cache, satellite assemblies
- packaging application resources
- compiling satellite assemblies
- re-signing assemblies
ms.assetid: 8d5c6044-2919-41d2-8321-274706b295ac
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2f75da3332c8172a6a888e6f40c66383866799ea
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="33e4a-102">Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="33e4a-102">Creating Satellite Assemblies for Desktop Apps</span></span>
<span data-ttu-id="33e4a-103">Kaynak dosyaları yerelleştirilmiş uygulamalarda merkezi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="33e4a-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="33e4a-104">Bunlar, bir uygulama kullanıcının kendi dil ve kültür dizeleri, resimleri ve diğer verileri görüntülemek ve kullanıcının kendi dilini veya kültür için kaynaklar kullanılamıyorsa alternatif veri sağlamak için etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="33e4a-105">.NET Framework bulun ve yerelleştirilmiş kaynaklar almak için bir hub ve bağlı bileşen modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="33e4a-106">Hub yerelleştirilemeyen yürütülebilir kod ve bağımsız olarak adlandırılan tek bir kültür için kaynakları içeren ana derlemedir veya varsayılan kültür.</span><span class="sxs-lookup"><span data-stu-id="33e4a-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="33e4a-107">Geri dönüş kültürü uygulama için varsayılan kültürdür; hiçbir yerelleştirilmiş kaynaklar kullanılabilir olduğunda kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="33e4a-108">Kullandığınız <xref:System.Resources.NeutralResourcesLanguageAttribute> uygulamanın varsayılan kültürü kültürünü atamak özniteliği.</span><span class="sxs-lookup"><span data-stu-id="33e4a-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="33e4a-109">Her bağlı bileşen tek bir yerelleştirilmiş kültür için kaynakları içerir, ancak herhangi bir kod içermiyor bir uydu derleme bağlanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="33e4a-110">Uydu derlemeleri ana derleme parçası olmadığından, kolayca güncelleştirme veya uygulama için ana derleme değiştirmeden belirli bir kültür karşılık kaynakları değiştirin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33e4a-111">Bir uygulamanın varsayılan kültürü kaynakları da bir uydu derlemede depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="33e4a-112">Bunu yapmak için Ata <xref:System.Resources.NeutralResourcesLanguageAttribute> değerini özniteliği <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="33e4a-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>  
  
## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="33e4a-113">Uydu derleme adı ve konumu</span><span class="sxs-lookup"><span data-stu-id="33e4a-113">Satellite Assembly Name and Location</span></span>  
 <span data-ttu-id="33e4a-114">Hub ve bağlı bileşen modeli, böylece bunlar kolayca bulunan ve kullanılabilecek kaynaklar belirli konumlara yerleştirebilir gerektirir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="33e4a-115">Derleme ve ad kaynakları beklendiği gibi yapmak veya bunları doğru konumlara yerleştirmeyin, ortak dil çalışma zamanı bunları bulmak mümkün olmaz ve varsayılan kültürü kaynakları yerine kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="33e4a-116">.NET Framework kaynağı tarafından temsil edilen Yöneticisi bir <xref:System.Resources.ResourceManager> nesnesi, otomatik olarak yerelleştirilmiş kaynaklara erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="33e4a-117">Kaynak Yöneticisi için şunlar gerekir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-117">The Resource Manager requires the following:</span></span>  
  
-   <span data-ttu-id="33e4a-118">Belirli bir kültür için tüm kaynakları tek bir uydu derlemesi içermelidir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="33e4a-119">Diğer bir deyişle, bir tek ikili kaynaklar dosyasına birden çok .txt veya .resx dosyaları derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-119">In other words, you should compile multiple .txt or .resx files into a single binary .resources file.</span></span>  
  
-   <span data-ttu-id="33e4a-120">Bu kültürün kaynaklarının depolar her yerelleştirilmiş kültür için uygulama dizinindeki ayrı bir alt dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="33e4a-121">Alt dizinin adı kültür adı ile aynı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="33e4a-122">Alternatif olarak, genel derleme önbelleğinde uydu derlemelerini depolayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="33e4a-123">Bu durumda, derleme tanımlayıcı adı kültür bilgilerini bileşeninin kültürü belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="33e4a-124">(Bkz [yükleme uydu derlemeleri Genel Derleme Önbelleği'ndeki](#SN) bu konunun ilerleyen bölümlerinde.)</span><span class="sxs-lookup"><span data-stu-id="33e4a-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33e4a-125">Uygulamanızı subcultures kaynakları içeriyorsa, her alt uygulama dizini altındaki ayrı bir alt dizin yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="33e4a-126">Subcultures kendi ana kültürün dizini altındaki dizinlerindeki yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>  
  
-   <span data-ttu-id="33e4a-127">Uydu derlemesi uygulama adıyla aynı olmalıdır ve dosya adı uzantısını kullanmalıdır ". resources.dll".</span><span class="sxs-lookup"><span data-stu-id="33e4a-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="33e4a-128">Örneğin, bir uygulama Example.exe olarak adlandırılmışsa, her uydu derlemenin adını Example.resources.dll olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-128">For example, if an application is named Example.exe, the name of each satellite assembly should be Example.resources.dll.</span></span> <span data-ttu-id="33e4a-129">Uydu derleme adı, kaynak dosyaları kültürünü göstermez unutmayın.</span><span class="sxs-lookup"><span data-stu-id="33e4a-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="33e4a-130">Ancak, uydu derlemesi kültür belirtmek bir dizinde görünür.</span><span class="sxs-lookup"><span data-stu-id="33e4a-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>  
  
-   <span data-ttu-id="33e4a-131">Uydu derlemesi kültürle ilgili bilgileri derlemenin meta verilerde eklenmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="33e4a-132">Kültür adı uydu derlemenin meta verilerini depolamak için belirttiğiniz `/culture` seçeneğini kullandığınızda [derleme bağlayıcı](../../../docs/framework/tools/al-exe-assembly-linker.md) kaynakları uydu derlemede katıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="33e4a-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../../../docs/framework/tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>  
  
 <span data-ttu-id="33e4a-133">İçinde yüklemiyorsanız uygulamaları için bir örnek dizin yapısını ve konum gereksinimleri aşağıda gösterilmiştir [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../../../docs/framework/app-domains/gac.md).</span></span> <span data-ttu-id="33e4a-134">.Txt ve .resources uzantıları öğeleriyle son uygulama ile birlikte değil.</span><span class="sxs-lookup"><span data-stu-id="33e4a-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="33e4a-135">Bu, son uydu kaynak derlemelerini oluşturmak için kullanılan ara kaynak dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="33e4a-136">Bu örnekte, .resx dosyaları .txt dosyaları için alternatif.</span><span class="sxs-lookup"><span data-stu-id="33e4a-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="33e4a-137">Daha fazla bilgi için bkz: [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-137">For more information, see [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>  
  
 <span data-ttu-id="33e4a-138">![Uydu derlemeleri](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")</span><span class="sxs-lookup"><span data-stu-id="33e4a-138">![Satellite assemblies](../../../docs/framework/resources/media/satelliteassemblydir.gif "satelliteassemblydir")</span></span>  
<span data-ttu-id="33e4a-139">Uydu derleme dizini</span><span class="sxs-lookup"><span data-stu-id="33e4a-139">Satellite assembly directory</span></span>  
  
## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="33e4a-140">Uydu derlemelerini derleme</span><span class="sxs-lookup"><span data-stu-id="33e4a-140">Compiling Satellite Assemblies</span></span>  
 <span data-ttu-id="33e4a-141">Kullandığınız [kaynak dosya oluşturucu (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) metin veya ikili .resources dosyaları için kaynakları içeren XML (.resx) dosyaları derlemek için.</span><span class="sxs-lookup"><span data-stu-id="33e4a-141">You use [Resource File Generator (Resgen.exe)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile text files or XML (.resx) files that contain resources to binary .resources files.</span></span> <span data-ttu-id="33e4a-142">Daha sonra [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) .resources dosyaları uydu derlemeye derlemesi için.</span><span class="sxs-lookup"><span data-stu-id="33e4a-142">You then use [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile .resources files into satellite assemblies.</span></span> <span data-ttu-id="33e4a-143">Al.exe bir derleme belirttiğiniz .resources dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33e4a-143">Al.exe creates an assembly from the .resources files that you specify.</span></span> <span data-ttu-id="33e4a-144">Uydu derlemeleri yalnızca kaynakları içerebilir; Bunlar yürütülebilir kod içeremez.</span><span class="sxs-lookup"><span data-stu-id="33e4a-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>  
  
 <span data-ttu-id="33e4a-145">Uygulama için bir uydu derleme aşağıdaki Al.exe komut oluşturur `Example` Almanca kaynakları dosya strings.de.resources gelen.</span><span class="sxs-lookup"><span data-stu-id="33e4a-145">The following Al.exe command creates a satellite assembly for the application `Example` from the German resources file strings.de.resources.</span></span>  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll  
```  
  
 <span data-ttu-id="33e4a-146">Aşağıdaki Al.exe komut ayrıca uygulama için bir uydu derleme oluşturur `Example` dosya strings.de.resources gelen.</span><span class="sxs-lookup"><span data-stu-id="33e4a-146">The following Al.exe command also creates a satellite assembly for the application `Example` from the file strings.de.resources.</span></span> <span data-ttu-id="33e4a-147">**/Template** seçenek kültür bilgilerini hariç tüm derleme meta verilerini üst derleme (Example.dll) devralmak uydu derlemesi neden olur.</span><span class="sxs-lookup"><span data-stu-id="33e4a-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (Example.dll).</span></span>  
  
```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll  
```  
  
 <span data-ttu-id="33e4a-148">Aşağıdaki tabloda daha ayrıntılı bu komutları kullanılan Al.exe seçenekleri açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-148">The following table describes the Al.exe options used in these commands in more detail.</span></span>  
  
|<span data-ttu-id="33e4a-149">Seçenek</span><span class="sxs-lookup"><span data-stu-id="33e4a-149">Option</span></span>|<span data-ttu-id="33e4a-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33e4a-150">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="33e4a-151">**-Hedef:**lib</span><span class="sxs-lookup"><span data-stu-id="33e4a-151">**-target:**lib</span></span>|<span data-ttu-id="33e4a-152">Uydu derlemenizi kitaplığı (.dll) dosyasına derlenir belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-152">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="33e4a-153">Uydu derlemesi yürütülebilir kod içermiyor ve bir uygulamanın ana derleme olmadığından uydu derlemelerini DLL'ler olarak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-153">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|  
|<span data-ttu-id="33e4a-154">**-katıştırmak:**strings.de.resources</span><span class="sxs-lookup"><span data-stu-id="33e4a-154">**-embed:**strings.de.resources</span></span>|<span data-ttu-id="33e4a-155">Al.exe derleme derlediğinde katıştırmak için kaynak dosya adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-155">Specifies the name of the resource file to embed when Al.exe compiles the assembly.</span></span> <span data-ttu-id="33e4a-156">Uydu bütünleştirilmiş kodunda birden fazla .resources dosyaları eklenebilir, ancak hub ve bağlı bileşen modeli izliyorsanız, her kültür için bir uydu derlemesi derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-156">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="33e4a-157">Ancak, dizeleri ve nesneler için ayrı .resources dosyaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-157">However, you can create separate .resources files for strings and objects.</span></span>|  
|<span data-ttu-id="33e4a-158">**-kültür:**Gizle</span><span class="sxs-lookup"><span data-stu-id="33e4a-158">**-culture:**de</span></span>|<span data-ttu-id="33e4a-159">Derlemek için kaynak kültürü belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-159">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="33e4a-160">Belirtilen kültür için kaynakları için aradığında ortak dil çalışma zamanı bu bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-160">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="33e4a-161">Bu seçeneği atlayın, Al.exe kaynak derleme, ancak çalışma zamanı bir kullanıcı bulmak mümkün olmaz ister.</span><span class="sxs-lookup"><span data-stu-id="33e4a-161">If you omit this option, Al.exe will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|  
|<span data-ttu-id="33e4a-162">**-out:**Example.resources.dll</span><span class="sxs-lookup"><span data-stu-id="33e4a-162">**-out:**Example.resources.dll</span></span>|<span data-ttu-id="33e4a-163">Çıktı dosyası adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-163">Specifies the name of the output file.</span></span> <span data-ttu-id="33e4a-164">Ad adlandırma standardı izlemelidir *baseName*.resources. *Uzantı*, burada *baseName* ana derleme adıdır ve *uzantısı* geçerli dosya adı uzantısıdır (örneğin, .dll).</span><span class="sxs-lookup"><span data-stu-id="33e4a-164">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="33e4a-165">Çalışma zamanı, çıkış dosyasının adına dayanarak bir uydu derleme kültürünü belirlemek mümkün olmadığını unutmayın; kullanmalısınız **/kültür** belirlemek için seçeneği.</span><span class="sxs-lookup"><span data-stu-id="33e4a-165">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|  
|<span data-ttu-id="33e4a-166">**-Şablon:**Example.dll</span><span class="sxs-lookup"><span data-stu-id="33e4a-166">**-template:**Example.dll</span></span>|<span data-ttu-id="33e4a-167">Uydu derlemesi kültür alanı dışında tüm derleme meta verilerini devralır derleme belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-167">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="33e4a-168">Bu seçenek, uydu derlemelerini etkiler, yalnızca sahip bir derleme belirtirseniz bir [güçlü ad](../../../docs/framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-168">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>|  
  
 <span data-ttu-id="33e4a-169">Al.exe ile kullanılabilir seçenekler tam bir listesi için bkz: [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-169">For a complete list of options available with Al.exe, see [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md).</span></span>  
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="33e4a-170">Uydu derlemeleri: Örnek</span><span class="sxs-lookup"><span data-stu-id="33e4a-170">Satellite Assemblies: An Example</span></span>  
 <span data-ttu-id="33e4a-171">Yerelleştirilmiş Tebrik içeren bir ileti kutusu görüntüler basit bir "Hello world" örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-171">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="33e4a-172">İngilizce (ABD), Fransızca (Fransa) ve Rusça (Rusya) kültürler için örnek kaynaklar içerir ve geri dönüş kültürü İngilizce'dir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-172">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="33e4a-173">Örnek oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="33e4a-173">To create the example, do the following:</span></span>  
  
1.  <span data-ttu-id="33e4a-174">Greeting.resx veya Greeting.txt varsayılan kültür için kaynak içerecek şekilde adlı bir kaynak dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="33e4a-174">Create a resource file named Greeting.resx or Greeting.txt to contain the resource for the default culture.</span></span> <span data-ttu-id="33e4a-175">Adlı tek bir dize depolamak `HelloString` "Hello world!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-175">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="33e4a-176">Bu dosyada.</span><span class="sxs-lookup"><span data-stu-id="33e4a-176">in this file.</span></span>  
  
2.  <span data-ttu-id="33e4a-177">İngilizce (TR) uygulamanın varsayılan kültürü olduğunu belirtmek için aşağıdaki ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> uygulamanın AssemblyInfo dosyası veya uygulamanın ana derlemeye derlenmiş ana kaynak kodu dosyasına özniteliği.</span><span class="sxs-lookup"><span data-stu-id="33e4a-177">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>  
  
     [!code-csharp[Conceptual.Resources.Locating#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
     [!code-vb[Conceptual.Resources.Locating#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3.  <span data-ttu-id="33e4a-178">Ek kültürler (en-US, fr-FR ve ru-RU) için destek uygulamayı aşağıdaki şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="33e4a-178">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    -   <span data-ttu-id="33e4a-179">En-US veya İngilizce (ABD) kültür desteklemek için Greeting.en US.resx veya Greeting.en US.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Hi world!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-179">To support the en-US or English (United States) culture, create a resource file named Greeting.en-US.resx or Greeting.en-US.txt, and store in it a single string named `HelloString` whose value is "Hi world!"</span></span>  
  
    -   <span data-ttu-id="33e4a-180">Fr-FR veya Fransızca (Fransa) kültür desteklemek için Greeting.fr FR.resx veya Greeting.fr FR.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Salut tout le monde!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-180">To support the fr-FR or French (France) culture, create a resource file named Greeting.fr-FR.resx or Greeting.fr-FR.txt, and store in it a single string named `HelloString` whose value is "Salut tout le monde!"</span></span>  
  
    -   <span data-ttu-id="33e4a-181">Ru-RU veya Rusça (Rusya) kültür desteklemek için Greeting.ru RU.resx veya Greeting.ru RU.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `HelloString` "Всем привет!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-181">To support the ru-RU or Russian (Russia) culture, create a resource file named Greeting.ru-RU.resx or Greeting.ru-RU.txt, and store in it a single string named `HelloString` whose value is "Всем привет!"</span></span>  
  
4.  <span data-ttu-id="33e4a-182">Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya ikili .resources dosyası XML kaynak dosyasına derlemek için.</span><span class="sxs-lookup"><span data-stu-id="33e4a-182">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="33e4a-183">Çıkış, kök dosya adıyla aynı .resx veya .txt dosyaları, ancak bir .resources uzantısına sahip dosyalar kümesidir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-183">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="33e4a-184">Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-184">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="33e4a-185">Visual Studio kullanmıyorsanız, .resx dosyaları .resources dosyalarıyla derlemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="33e4a-185">If you aren't using Visual Studio, run the following commands to compile the .resx files into .resources files:</span></span>  
  
    ```console
    resgen Greeting.resx  
    resgen Greeting.en-us.resx  
    resgen Greeting.fr-FR.resx  
    resgen Greeting.ru-RU.resx  
    ```  
  
     <span data-ttu-id="33e4a-186">XML dosyaları yerine metin dosyalarında kaynaklarınız varsa, .resx uzantısı .txt ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-186">If your resources are in text files instead of XML files, replace the .resx extension with .txt.</span></span>  
  
5.  <span data-ttu-id="33e4a-187">Aşağıdaki kaynak kodu varsayılan kültür için kaynaklar yanı sıra uygulamanın ana derlemeye derleyin:</span><span class="sxs-lookup"><span data-stu-id="33e4a-187">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="33e4a-188">Örnek oluşturmak için Visual Studio yerine komut satırı kullanıyorsanız çağrısı değiştirmelisiniz <xref:System.Resources.ResourceManager> şu sınıfı oluşturucusu: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="33e4a-188">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>  
  
     [!code-csharp[Conceptual.Resources.Locating#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
     [!code-vb[Conceptual.Resources.Locating#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]  
  
     <span data-ttu-id="33e4a-189">Örnek uygulama adı ve komut satırından derleme, C# derleyici komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-189">If the application is named Example and you are compiling from the command line, the command for the C# compiler is:</span></span>  
  
    ```console  
    csc Example.cs -res:Greeting.resources  
    ```  
  
     <span data-ttu-id="33e4a-190">Karşılık gelen Visual Basic derleyici komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-190">The corresponding Visual Basic compiler command is:</span></span>  
  
    ```console  
    vbc Example.vb -res:Greeting.resources  
    ```  
  
6.  <span data-ttu-id="33e4a-191">Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizinindeki bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="33e4a-191">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="33e4a-192">Bir en-US, fr-FR ve ru-RU alt oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-192">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="33e4a-193">Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33e4a-193">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>  
  
7.  <span data-ttu-id="33e4a-194">Uydu derlemeleri tek tek kültüre özgü .resources dosyaları ekleme ve uygun dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-194">Embed the individual culture-specific .resources files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="33e4a-195">Bunu yapmak için her .resources dosyası için bir komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-195">The command to do this for each .resources file is:</span></span>  
  
    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll  
    ```  
  
     <span data-ttu-id="33e4a-196">Burada *kültür* kaynakları uydu derleme içeren kültür adı.</span><span class="sxs-lookup"><span data-stu-id="33e4a-196">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="33e4a-197">Visual Studio bu işlemi otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="33e4a-197">Visual Studio handles this process automatically.</span></span>  
  
 <span data-ttu-id="33e4a-198">Bu örnek daha sonra çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-198">You can then run the example.</span></span> <span data-ttu-id="33e4a-199">Bu rastgele desteklenen birini yapacak geçerli kültürü cultures ve yerelleştirilmiş Tebrik görüntüler.</span><span class="sxs-lookup"><span data-stu-id="33e4a-199">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>  
  
<a name="SN"></a>   
## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="33e4a-200">Uydu derlemeleri genel derleme önbelleğine yükleme</span><span class="sxs-lookup"><span data-stu-id="33e4a-200">Installing Satellite Assemblies in the Global Assembly Cache</span></span>  
 <span data-ttu-id="33e4a-201">Yerel uygulama alt dizinindeki derlemelerini yüklemek yerine, genel derleme önbelleğinde yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-201">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="33e4a-202">Sınıf kitaplıkları ve birden çok uygulama tarafından kullanılan sınıf kitaplığı kaynak derlemeleri varsa, bu özellikle yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-202">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>  
  
 <span data-ttu-id="33e4a-203">Genel derleme önbelleğinde derlemeleri yükleme tanımlayıcı adlar sahip olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-203">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="33e4a-204">Tanımlayıcı adlı derlemeler ile geçerli bir ortak/özel anahtar çifti imzalanmıştır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-204">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="33e4a-205">Çalışma zamanı hangi derleme bağlama isteği karşılamak için kullanılacağını belirlemek için kullanır sürüm bilgilerini içerir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-205">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="33e4a-206">Tanımlayıcı adlar ve sürüm oluşturma hakkında daha fazla bilgi için bkz: [derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-206">For more information about strong names and versioning, see [Assembly Versioning](../../../docs/framework/app-domains/assembly-versioning.md).</span></span> <span data-ttu-id="33e4a-207">Tanımlayıcı adlar hakkında daha fazla bilgi için bkz: [Strong-Named derlemeler](../../../docs/framework/app-domains/strong-named-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-207">For more information about strong names, see [Strong-Named Assemblies](../../../docs/framework/app-domains/strong-named-assemblies.md).</span></span>  
  
 <span data-ttu-id="33e4a-208">Bir uygulama geliştirirken, son ortak/özel anahtar çifti erişimi sahip düşüktür.</span><span class="sxs-lookup"><span data-stu-id="33e4a-208">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="33e4a-209">Bir derlemeyi genel derleme önbelleğinde yüklemek ve beklendiği gibi çalıştığından emin olmak için Gecikmeli imzalama adı verilen bir tekniği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-209">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="33e4a-210">Derleme zamanında oturum bütünleştirilmiş gecikme, dosyanın sağlam ad imzası için alan ayırın.</span><span class="sxs-lookup"><span data-stu-id="33e4a-210">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="33e4a-211">Daha sonra gerçek imzalama gecikti son ortak/özel anahtar çifti olduğunda kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-211">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="33e4a-212">Gecikmeli imzalama hakkında daha fazla bilgi için bkz: [Gecikmeli bir derleme imzalama](../../../docs/framework/app-domains/delay-sign-assembly.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-212">For more information about delayed signing, see [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md).</span></span>  
  
### <a name="obtaining-the-public-key"></a><span data-ttu-id="33e4a-213">Ortak anahtarı edinme</span><span class="sxs-lookup"><span data-stu-id="33e4a-213">Obtaining the Public Key</span></span>  
 <span data-ttu-id="33e4a-214">Oturum bütünleştirilmiş geciktirmek için ortak anahtar erişiminiz olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-214">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="33e4a-215">Ya da gerçek ortak anahtarı kuruluş tarafından nihai imzalama yapın veya ortak anahtar kullanarak oluşturmak, şirketinizdeki alabilirsiniz [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-215">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).</span></span>  
  
 <span data-ttu-id="33e4a-216">Aşağıdaki Sn.exe komut bir test ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33e4a-216">The following Sn.exe command creates a test public/private key pair.</span></span> <span data-ttu-id="33e4a-217">**– K** seçeneği belirtir Sn.exe'nin yeni bir anahtar çifti oluşturma ve TestKeyPair.snk adlı bir dosyaya kaydedin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-217">The **–k** option specifies that Sn.exe should create a new key pair and save it in a file named TestKeyPair.snk.</span></span>  
  
```console
sn –k TestKeyPair.snk   
```  
  
 <span data-ttu-id="33e4a-218">Ortak anahtar test anahtar çiftini içeren dosyasından ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-218">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="33e4a-219">Aşağıdaki komut ortak anahtar TestKeyPair.snk ayıklar ve içinde PublicKey.snk kaydeder:</span><span class="sxs-lookup"><span data-stu-id="33e4a-219">The following command extracts the public key from TestKeyPair.snk and saves it in PublicKey.snk:</span></span>  
  
```console
sn –p TestKeyPair.snk PublicKey.snk  
```  
  
### <a name="delay-signing-an-assembly"></a><span data-ttu-id="33e4a-220">Derleme İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="33e4a-220">Delay Signing an Assembly</span></span>  
 <span data-ttu-id="33e4a-221">Ortak anahtar oluşturma veya alma sonra kullandığınız [derleme bağlayıcı (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) derlemeyi derlemek ve belirtmek için imzalama ertelendi.</span><span class="sxs-lookup"><span data-stu-id="33e4a-221">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>  
  
 <span data-ttu-id="33e4a-222">Aşağıdaki Al.exe komutu StringLibrary uygulama için bir uydu tanımlayıcı adlı derleme strings.ja.resources dosyasından oluşturur:</span><span class="sxs-lookup"><span data-stu-id="33e4a-222">The following Al.exe command creates a strong-named satellite assembly for the application StringLibrary from the strings.ja.resources file:</span></span>  
  
```console 
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk  
```  
  
 <span data-ttu-id="33e4a-223">**-Gecikme +** seçeneği, derleme bağlayıcı derlemenin imzalanmasını gecikme belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-223">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="33e4a-224">**- Keyfile** seçeneği, gecikme için kullanılacak ortak anahtarı içeren anahtar dosyasının adını derleme oturum belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-224">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>  
  
### <a name="re-signing-an-assembly"></a><span data-ttu-id="33e4a-225">Bir derlemeyi yeniden imzalama</span><span class="sxs-lookup"><span data-stu-id="33e4a-225">Re-signing an Assembly</span></span>  
 <span data-ttu-id="33e4a-226">Uygulamanızı dağıtmadan önce gecikme yeniden imzalamalısınız uydu derleme gerçek anahtar çifti ile imzalanmamış.</span><span class="sxs-lookup"><span data-stu-id="33e4a-226">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="33e4a-227">Sn.exe kullanarak bunu yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-227">You can do this by using Sn.exe.</span></span>  
  
 <span data-ttu-id="33e4a-228">Aşağıdaki Sn.exe komutu StringLibrary.resources.dll RealKeyPair.snk dosyasında depolanan anahtar çifti ile imzalar.</span><span class="sxs-lookup"><span data-stu-id="33e4a-228">The following Sn.exe command signs StringLibrary.resources.dll with the key pair stored in the file RealKeyPair.snk.</span></span> <span data-ttu-id="33e4a-229">**– R** seçeneği belirtir daha önce imzalanmış veya gecikme imzalı derlemedir yeniden imzalanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-229">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>  
  
```console
sn –R StringLibrary.resources.dll RealKeyPair.snk   
```  
  
### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="33e4a-230">Bir derlemeyi genel derleme önbelleğinde yükleme</span><span class="sxs-lookup"><span data-stu-id="33e4a-230">Installing a Satellite Assembly in the Global Assembly Cache</span></span>  
 <span data-ttu-id="33e4a-231">Çalışma zamanı için kaynak geri dönüş işlemi kaynaklarında aradığında, görünüyor [genel derleme önbelleği](../../../docs/framework/app-domains/gac.md) ilk.</span><span class="sxs-lookup"><span data-stu-id="33e4a-231">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../../../docs/framework/app-domains/gac.md) first.</span></span> <span data-ttu-id="33e4a-232">(Daha fazla bilgi için "Kaynak geri dönüş işlemi" bölümüne bakın [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) konu.) Bir uydu derleme güçlü bir ad ile imzalandığında hemen genel derleme önbelleğinde kullanılarak yüklenebilir [Genel Derleme Önbelleği Aracı (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span><span class="sxs-lookup"><span data-stu-id="33e4a-232">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md).</span></span>  
  
 <span data-ttu-id="33e4a-233">Aşağıdaki Gacutil.exe komutu StringLibrary.resources.dll genel derleme önbelleğinde yükler:</span><span class="sxs-lookup"><span data-stu-id="33e4a-233">The following Gacutil.exe command installs StringLibrary.resources.dll in the global assembly cache:</span></span>  
  
```console
gacutil -i:StringLibrary.resources.dll  
```  
  
 <span data-ttu-id="33e4a-234">**/İ** seçeneği, Gacutil.exe belirtilen derleme genel derleme önbelleğine yüklemeniz gerekip gerekmediğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-234">The **/i** option specifies that Gacutil.exe should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="33e4a-235">Uydu sonra uydu derlemesi kullanmak üzere tasarlanmış tüm uygulamalar için kullanılabilir hale içerdiği kaynakların önbelleğinde derleme yüklenir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-235">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>  
  
### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="33e4a-236">Genel Derleme Önbelleği kaynaklarında: örneği</span><span class="sxs-lookup"><span data-stu-id="33e4a-236">Resources in the Global Assembly Cache: An Example</span></span>  
 <span data-ttu-id="33e4a-237">Aşağıdaki örnek ayıklamak ve bir kaynak dosyasından yerelleştirilmiş Tebrik dönmek için bir .NET Framework Sınıf Kitaplığı'nda bir yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-237">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="33e4a-238">Kitaplık ve kaynaklarına genel derleme önbelleğinde kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-238">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="33e4a-239">Örneğin İngilizce (ABD), Fransızca (Fransa), Rusça (Rusya) ve İngilizce kültürler için kaynakları içerir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-239">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="33e4a-240">İngilizce varsayılan kültürdür; kaynaklarıyla ana derlemede depolanır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-240">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="33e4a-241">Kitaplık ve kendisine ait bir ortak anahtar ile uydu derlemelerini daha sonra yeniden oturum açtığında bunları ortak/özel anahtar çifti ile işaretlerini başlangıçta gecikme örnek.</span><span class="sxs-lookup"><span data-stu-id="33e4a-241">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="33e4a-242">Örnek oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="33e4a-242">To create the example, do the following:</span></span>  
  
1.  <span data-ttu-id="33e4a-243">Visual Studio kullanmıyorsanız, aşağıdaki kullanın [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu ResKey.snk adlı bir genel/özel anahtar çifti oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="33e4a-243">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named ResKey.snk:</span></span>  
  
    ```console
    sn –k ResKey.snk  
    ```  
  
     <span data-ttu-id="33e4a-244">Visual Studio kullanıyorsanız **imzalama** Proje sekmesinde **özellikleri** anahtar dosyası oluşturmak için iletişim kutusu.</span><span class="sxs-lookup"><span data-stu-id="33e4a-244">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>  
  
2.  <span data-ttu-id="33e4a-245">Aşağıdaki [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) komutu PublicKey.snk adlı ortak bir anahtar dosyası oluşturmak için:</span><span class="sxs-lookup"><span data-stu-id="33e4a-245">Use the following [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command to create a public key file named PublicKey.snk:</span></span>  
  
    ```console
    sn –p ResKey.snk PublicKey.snk  
    ```  
  
3.  <span data-ttu-id="33e4a-246">Varsayılan kültür için kaynak içerecek şekilde Strings.resx adlı bir kaynak dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="33e4a-246">Create a resource file named Strings.resx to contain the resource for the default culture.</span></span> <span data-ttu-id="33e4a-247">Adlı tek bir dize depolamak `Greeting` değeri olan "Nasıl you musunuz?"</span><span class="sxs-lookup"><span data-stu-id="33e4a-247">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="33e4a-248">Bu dosyada.</span><span class="sxs-lookup"><span data-stu-id="33e4a-248">in that file.</span></span>  
  
4.  <span data-ttu-id="33e4a-249">"En" uygulamanın varsayılan kültürü olduğunu belirtmek için aşağıdaki ekleyin <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> özniteliği uygulamanın AssemblyInfo dosyası veya uygulamanın ana derlemeye derlenmiş ana kaynak kodu dosyasına:</span><span class="sxs-lookup"><span data-stu-id="33e4a-249">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>  
  
     [!code-csharp[Conceptual.Resources.Satellites#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
     [!code-vb[Conceptual.Resources.Satellites#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]  
  
5.  <span data-ttu-id="33e4a-250">Ek kültürler (en-US, fr-FR ve ru-RU kültürler) için destek uygulamayı aşağıdaki şekilde ekleyin:</span><span class="sxs-lookup"><span data-stu-id="33e4a-250">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>  
  
    -   <span data-ttu-id="33e4a-251">"En-US" veya İngilizce (ABD) kültür desteklemek için Strings.en US.resx veya Strings.en US.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` değeri olan "Hello!".</span><span class="sxs-lookup"><span data-stu-id="33e4a-251">To support the "en-US" or English (United States) culture, create a resource file named Strings.en-US.resx or Strings.en-US.txt, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>  
  
    -   <span data-ttu-id="33e4a-252">"Fr-FR" veya Fransızca (Fransa) kültür desteklemek için Strings.fr FR.resx veya Strings.fr FR.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` "İyi günlüğü!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-252">To support the "fr-FR" or French (France) culture, create a resource file named Strings.fr-FR.resx or Strings.fr-FR.txt and store in it a single string named `Greeting` whose value is "Bon jour!"</span></span>  
  
    -   <span data-ttu-id="33e4a-253">"Ru-RU" veya Rusça (Rusya) kültür desteklemek için Strings.ru RU.resx veya Strings.ru RU.txt adlı bir kaynak dosyası oluşturun ve bunu adlı tek bir dize depolamak `Greeting` "Привет!" değeri olan</span><span class="sxs-lookup"><span data-stu-id="33e4a-253">To support the "ru-RU" or Russian (Russia) culture, create a resource file named Strings.ru-RU.resx or Strings.ru-RU.txt and store in it a single string named `Greeting` whose value is "Привет!"</span></span>  
  
6.  <span data-ttu-id="33e4a-254">Kullanım [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) her bir metin veya ikili .resources dosyası XML kaynak dosyasına derlemek için.</span><span class="sxs-lookup"><span data-stu-id="33e4a-254">Use [Resgen.exe](../../../docs/framework/tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="33e4a-255">Çıkış, kök dosya adıyla aynı .resx veya .txt dosyaları, ancak bir .resources uzantısına sahip dosyalar kümesidir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-255">The output is a set of files that have the same root file name as the .resx or .txt files, but a .resources extension.</span></span> <span data-ttu-id="33e4a-256">Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-256">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="33e4a-257">Visual Studio kullanmıyorsanız, .resx dosyaları .resources dosyalarıyla derlemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="33e4a-257">If you aren't using Visual Studio, run the following command to compile the .resx files into .resources files:</span></span>  
  
    ```console
    resgen filename  
    ```  
  
     <span data-ttu-id="33e4a-258">Burada *filename* isteğe bağlı yol, dosya adı ve uzantısı .resx veya metin dosyası.</span><span class="sxs-lookup"><span data-stu-id="33e4a-258">where *filename* is the optional path, file name, and extension of the .resx or text file.</span></span>  
  
7.  <span data-ttu-id="33e4a-259">Aşağıdaki kaynak kodu derleyin StringLibrary.vb veya StringLibrary.cs için bir gecikme içine varsayılan kültür için kaynaklar birlikte StringLibrary.dll adlı kitaplığı derleme imzalanmamış:</span><span class="sxs-lookup"><span data-stu-id="33e4a-259">Compile the following source code for StringLibrary.vb or StringLibrary.cs along with the resources for the default culture into a delay signed library assembly named StringLibrary.dll:</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="33e4a-260">Örnek oluşturmak için Visual Studio yerine komut satırı kullanıyorsanız çağrısı değiştirmelisiniz <xref:System.Resources.ResourceManager> sınıfı oluşturucuya `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span><span class="sxs-lookup"><span data-stu-id="33e4a-260">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>  
  
     [!code-csharp[Conceptual.Resources.Satellites#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
     [!code-vb[Conceptual.Resources.Satellites#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]  
  
     <span data-ttu-id="33e4a-261">C# derleyici komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-261">The command for the C# compiler is:</span></span>  
  
    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs  
    ```  
  
     <span data-ttu-id="33e4a-262">Karşılık gelen Visual Basic derleyici komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-262">The corresponding Visual Basic compiler command is:</span></span>  
  
    ```console  
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb  
    ```  
  
8.  <span data-ttu-id="33e4a-263">Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizinindeki bir dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="33e4a-263">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="33e4a-264">Bir en-US, fr-FR ve ru-RU alt oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="33e4a-264">You should create an en-US, an fr-FR, and an ru-RU subdirectory.</span></span> <span data-ttu-id="33e4a-265">Bu alt dizinleri, Visual Studio derleme işleminin bir parçası otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="33e4a-265">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="33e4a-266">Tüm uydu derlemelerini aynı dosya adına sahip olduğundan, alt dizinleri ortak/özel anahtar çifti ile imzalanmış kadar tek tek kültüre özgü uydu derlemeleri depolamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-266">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>  
  
9. <span data-ttu-id="33e4a-267">Tek tek ekleme kültüre özgü .resources dosyaları imzalı gecikme içine uydu derlemeleri ve bunları uygun dizinine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-267">Embed the individual culture-specific .resources files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="33e4a-268">Bunu yapmak için her .resources dosyası için bir komut şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-268">The command to do this for each .resources file is:</span></span>  
  
    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk  
    ```  
  
     <span data-ttu-id="33e4a-269">Burada *kültür* bir kültür adı.</span><span class="sxs-lookup"><span data-stu-id="33e4a-269">where *culture* is the name of a culture.</span></span> <span data-ttu-id="33e4a-270">Bu örnekte kültür en-US, fr-FR ve ru-RU adlarıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-270">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>  
  
10. <span data-ttu-id="33e4a-271">StringLibrary.dll kullanarak yeniden oturum [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi:</span><span class="sxs-lookup"><span data-stu-id="33e4a-271">Re-sign StringLibrary.dll by using the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows:</span></span>  
  
    ```console
    sn –R StringLibrary.dll RealKeyPair.snk  
    ```  
  
11. <span data-ttu-id="33e4a-272">Tek tek uydu derlemelerini yeniden oturum açın.</span><span class="sxs-lookup"><span data-stu-id="33e4a-272">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="33e4a-273">Bunu yapmak için kullanın [tanımlayıcı ad Aracı (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) gibi her uydu derlemesi için:</span><span class="sxs-lookup"><span data-stu-id="33e4a-273">To do this, use the [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>  
  
    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk  
    ```  
  
12. <span data-ttu-id="33e4a-274">StringLibrary.dll ve her biri kendi uydu derlemeleri genel derleme önbelleğinde aşağıdaki komutu kullanarak kaydedin:</span><span class="sxs-lookup"><span data-stu-id="33e4a-274">Register StringLibrary.dll and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>  
  
    ```console
    gacutil -i filename  
    ```  
  
     <span data-ttu-id="33e4a-275">Burada *filename* kaydetmek için dosyayı adıdır.</span><span class="sxs-lookup"><span data-stu-id="33e4a-275">where *filename* is the name of the file to register.</span></span>  
  
13. <span data-ttu-id="33e4a-276">Visual Studio kullanıyorsanız, yeni bir oluşturma **konsol uygulaması** adlı projesi `Example`StringLibrary.dll başvuru ve aşağıdaki kaynak kodu ekleyin ve derleyin.</span><span class="sxs-lookup"><span data-stu-id="33e4a-276">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to StringLibrary.dll and the following source code to it, and compile.</span></span>  
  
     [!code-csharp[Conceptual.Resources.Satellites#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
     [!code-vb[Conceptual.Resources.Satellites#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]  
  
     <span data-ttu-id="33e4a-277">Komut satırından derlemek için C# derleyici için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="33e4a-277">To compile from the command line, use the following command for the C# compiler:</span></span>  
  
    ```console
    csc Example.cs -r:StringLibrary.dll   
    ```  
  
     <span data-ttu-id="33e4a-278">Visual Basic derleyici komut satırı şöyledir:</span><span class="sxs-lookup"><span data-stu-id="33e4a-278">The command line for the Visual Basic compiler is:</span></span>  
  
    ```console
    vbc Example.vb -r:StringLibrary.dll   
    ```  
  
14. <span data-ttu-id="33e4a-279">Example.exe çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="33e4a-279">Run Example.exe.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e4a-280">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33e4a-280">See Also</span></span>  
 [<span data-ttu-id="33e4a-281">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="33e4a-281">Packaging and Deploying Resources</span></span>](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)  
 [<span data-ttu-id="33e4a-282">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="33e4a-282">Delay Signing an Assembly</span></span>](../../../docs/framework/app-domains/delay-sign-assembly.md)  
 [<span data-ttu-id="33e4a-283">Al.exe (Bütünleştirilmiş Kod Bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="33e4a-283">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="33e4a-284">Sn.exe (Tanımlayıcı Ad Aracı)</span><span class="sxs-lookup"><span data-stu-id="33e4a-284">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="33e4a-285">Gacutil.exe (Genel Derleme Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="33e4a-285">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [<span data-ttu-id="33e4a-286">Masaüstü Uygulamalarındaki Kaynaklar</span><span class="sxs-lookup"><span data-stu-id="33e4a-286">Resources in Desktop Apps</span></span>](../../../docs/framework/resources/index.md)
