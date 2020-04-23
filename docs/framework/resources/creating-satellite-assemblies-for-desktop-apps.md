---
title: Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma
ms.date: 03/30/2017
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
ms.openlocfilehash: 5efc5001a1a9756e09053d684a2f6673d15fadcf
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458021"
---
# <a name="creating-satellite-assemblies-for-desktop-apps"></a><span data-ttu-id="f8c5d-102">Masaüstü Uygulamaları için Uydu Derlemeleri Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f8c5d-102">Creating Satellite Assemblies for Desktop Apps</span></span>

<span data-ttu-id="f8c5d-103">Kaynak dosyaları, yerelleştirilmiş uygulamalarda merkezi bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-103">Resource files play a central role in localized applications.</span></span> <span data-ttu-id="f8c5d-104">Bu uygulamalar, bir uygulamanın, kullanıcının kendi dilinde ve kültürüne yönelik dizeleri, resimleri ve diğer verileri görüntülemesini ve kullanıcının kendi dili ya da kültürüne yönelik kaynakların kullanılamaz durumda olup olmadığını alternatif veriler sağlamasını etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-104">They enable an application to display strings, images, and other data in the user's own language and culture, and to provide alternate data if resources for the user's own language or culture are unavailable.</span></span> <span data-ttu-id="f8c5d-105">.NET Framework, yerelleştirilmiş kaynakları bulmak ve almak için bir hub ve bağlı bileşen modeli kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-105">The .NET Framework uses a hub-and-spoke model to locate and retrieve localized resources.</span></span> <span data-ttu-id="f8c5d-106">Hub, yerelleştirilemeyen yürütülebilir kodu ve bağımsız veya varsayılan kültür olarak adlandırılan tek bir kültüre yönelik kaynakları içeren ana derlemedir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-106">The hub is the main assembly that contains the non-localizable executable code and the resources for a single culture, which is called the neutral or default culture.</span></span> <span data-ttu-id="f8c5d-107">Varsayılan kültür, uygulamanın geri dönüş kültürüdür; kullanılabilir yerelleştirilmiş kaynaklar olmadığında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-107">The default culture is the fallback culture for the application; it is used when no localized resources are available.</span></span> <span data-ttu-id="f8c5d-108">Uygulamanın varsayılan kültürünün kültürünü belirlemek için <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğini kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-108">You use the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute to designate the culture of the application's default culture.</span></span> <span data-ttu-id="f8c5d-109">Her bir bağlı bileşen, tek bir yerelleştirilmiş kültürün kaynaklarını içeren bir uydu derlemesine bağlanır, ancak herhangi bir kod içermez.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-109">Each spoke connects to a satellite assembly that contains the resources for a single localized culture but does not contain any code.</span></span> <span data-ttu-id="f8c5d-110">Uydu derlemeleri ana derlemenin parçası olmadığından, uygulamanın ana derlemesini değiştirmeden belirli bir kültüre karşılık gelen kaynakları kolayca güncelleştirebilir ya da değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-110">Because the satellite assemblies are not part of the main assembly, you can easily update or replace resources that correspond to a specific culture without replacing the main assembly for the application.</span></span>

> [!NOTE]
> <span data-ttu-id="f8c5d-111">Bir uygulamanın varsayılan kültürünün kaynakları bir uydu derlemesinde da depolanabilir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-111">The resources of an application's default culture can also be stored in a satellite assembly.</span></span> <span data-ttu-id="f8c5d-112">Bunu yapmak için, <xref:System.Resources.NeutralResourcesLanguageAttribute> özniteliğine değerini atarsınız. <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="f8c5d-112">To do this, you assign the <xref:System.Resources.NeutralResourcesLanguageAttribute> attribute a value of <xref:System.Resources.UltimateResourceFallbackLocation.Satellite?displayProperty=nameWithType>.</span></span>

## <a name="satellite-assembly-name-and-location"></a><span data-ttu-id="f8c5d-113">Uydu bütünleştirilmiş kodu adı ve konumu</span><span class="sxs-lookup"><span data-stu-id="f8c5d-113">Satellite Assembly Name and Location</span></span>

<span data-ttu-id="f8c5d-114">Hub ve bağlı bileşen modeli, kaynakların kolayca konumlandırılmaları ve kullanılması için belirli konumlara yerleştirmenizin gerekli olmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-114">The hub-and-spoke model requires that you place resources in specific locations so that they can be easily located and used.</span></span> <span data-ttu-id="f8c5d-115">Kaynakları, beklendiği gibi derleyip veya doğru konumlara yerleştirmiyorsa, ortak dil çalışma zamanı bunları bulamaz ve bunun yerine varsayılan kültürün kaynaklarını kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-115">If you do not compile and name resources as expected, or if you do not place them in the correct locations, the common language runtime will not be able to locate them and will use the resources of the default culture instead.</span></span> <span data-ttu-id="f8c5d-116">Bir <xref:System.Resources.ResourceManager> nesneyle temsil edilen .NET Framework kaynak yöneticisi, yerelleştirilmiş kaynaklara otomatik olarak erişmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-116">The .NET Framework Resource Manager, represented by a <xref:System.Resources.ResourceManager> object, is used to automatically access localized resources.</span></span> <span data-ttu-id="f8c5d-117">Kaynak Yöneticisi şunları gerektirir:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-117">The Resource Manager requires the following:</span></span>

- <span data-ttu-id="f8c5d-118">Tek bir uydu derlemesinin belirli bir kültür için tüm kaynakları içermesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-118">A single satellite assembly must include all the resources for a particular culture.</span></span> <span data-ttu-id="f8c5d-119">Diğer bir deyişle, birden çok *. txt* veya *. resx* dosyasını tek bir ikili *. resources* dosyasında derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-119">In other words, you should compile multiple *.txt* or *.resx* files into a single binary *.resources* file.</span></span>

- <span data-ttu-id="f8c5d-120">Bu kültürün kaynaklarını depolayan her yerelleştirilmiş kültür için uygulama dizininde ayrı bir alt dizin olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-120">There must be a separate subdirectory in the application directory for each localized culture that stores that culture's resources.</span></span> <span data-ttu-id="f8c5d-121">Alt dizin adı kültür adı ile aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-121">The subdirectory name must be the same as the culture name.</span></span> <span data-ttu-id="f8c5d-122">Alternatif olarak, uydu derlemelerinizi genel derleme önbelleğinde saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-122">Alternately, you can store your satellite assemblies in the global assembly cache.</span></span> <span data-ttu-id="f8c5d-123">Bu durumda, derlemenin tanımlayıcı adının kültür bilgileri bileşeni kültürünü belirtmelidir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-123">In this case, the culture information component of the assembly's strong name must indicate its culture.</span></span> <span data-ttu-id="f8c5d-124">(Bu konunun ilerleyen kısımlarında bulunan [genel derleme önbelleği bölümünde uydu derlemelerini yükleme](#SN) bölümüne bakın.)</span><span class="sxs-lookup"><span data-stu-id="f8c5d-124">(See the [Installing Satellite Assemblies in the Global Assembly Cache](#SN) section later in this topic.)</span></span>

  > [!NOTE]
  > <span data-ttu-id="f8c5d-125">Uygulamanız alt kültürler için kaynaklar içeriyorsa, her alt kültürü uygulama dizini altına ayrı bir alt dizine yerleştirin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-125">If your application includes resources for subcultures, place each subculture in a separate subdirectory under the application directory.</span></span> <span data-ttu-id="f8c5d-126">Alt kültürleri ana kültürlerin dizin altındaki alt dizinlere yerleştirmeyin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-126">Do not place subcultures in subdirectories under their main culture's directory.</span></span>

- <span data-ttu-id="f8c5d-127">Uydu derlemesinin uygulamayla aynı ada sahip olması ve ". resources. dll" dosya adı uzantısını kullanması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-127">The satellite assembly must have the same name as the application, and must use the file name extension ".resources.dll".</span></span> <span data-ttu-id="f8c5d-128">Örneğin, bir uygulama *example. exe*olarak adlandırılmışsa, her uydu derlemesinin adı *örnek. resources. dll*olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-128">For example, if an application is named *Example.exe*, the name of each satellite assembly should be *Example.resources.dll*.</span></span> <span data-ttu-id="f8c5d-129">Uydu derleme adının, kaynak dosyalarının kültürünü belirtmediğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-129">Note that the satellite assembly name does not indicate the culture of its resource files.</span></span> <span data-ttu-id="f8c5d-130">Ancak uydu derlemesi, kültürü belirten bir dizinde görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-130">However, the satellite assembly appears in a directory that does specify the culture.</span></span>

- <span data-ttu-id="f8c5d-131">Uydu derlemesinin kültürüyle ilgili bilgiler derlemenin meta verilerinde yer almalıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-131">Information about the culture of the satellite assembly must be included in the assembly's metadata.</span></span> <span data-ttu-id="f8c5d-132">Kültür adını uydu derlemesinin meta verilerinde depolamak için, uydu derlemesine kaynakları eklemek üzere `/culture` [derleme Bağlayıcısı](../tools/al-exe-assembly-linker.md) 'nı kullandığınızda seçeneğini belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-132">To store the culture name in the satellite assembly's metadata, you specify the `/culture` option when you use [Assembly Linker](../tools/al-exe-assembly-linker.md) to embed resources in the satellite assembly.</span></span>

<span data-ttu-id="f8c5d-133">Aşağıdaki çizimde, [genel derleme önbelleğine](../app-domains/gac.md)yüklememiş olduğunuz uygulamalar için örnek bir dizin yapısı ve konum gereksinimleri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-133">The following illustration shows a sample directory structure and location requirements for applications that you are not installing in the [global assembly cache](../app-domains/gac.md).</span></span> <span data-ttu-id="f8c5d-134">. Txt ve. resources uzantılı öğeler son uygulamayla birlikte gelmez.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-134">The items with .txt and .resources extensions will not ship with the final application.</span></span> <span data-ttu-id="f8c5d-135">Bunlar, son uydu kaynak derlemelerini oluşturmak için kullanılan ara kaynak dosyalarıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-135">These are the intermediate resource files used to create the final satellite resource assemblies.</span></span> <span data-ttu-id="f8c5d-136">Bu örnekte,. resx dosyalarını. txt dosyaları için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-136">In this example, you could substitute .resx files for the .txt files.</span></span> <span data-ttu-id="f8c5d-137">Daha fazla bilgi için bkz. [kaynakları paketleme ve dağıtma](packaging-and-deploying-resources-in-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-137">For more information, see [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

<span data-ttu-id="f8c5d-138">Aşağıdaki görüntüde uydu derleme dizini gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-138">The following image shows the satellite assembly directory:</span></span>

![Yerelleştirilmiş kültürler alt dizinleri içeren bir uydu derleme dizini.](./media/creating-satellite-assemblies-for-desktop-apps/satellite-assembly-directory.gif)

## <a name="compiling-satellite-assemblies"></a><span data-ttu-id="f8c5d-140">Uydu derlemelerini derleme</span><span class="sxs-lookup"><span data-stu-id="f8c5d-140">Compiling Satellite Assemblies</span></span>

<span data-ttu-id="f8c5d-141">[Kaynak dosya Oluşturucu (Resgen. exe)](../tools/resgen-exe-resource-file-generator.md) , ikili *. resources* dosyalarına kaynakları IÇEREN metin dosyalarını veya XML (*. resx*) dosyalarını derlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-141">You use [Resource File Generator (Resgen.exe)](../tools/resgen-exe-resource-file-generator.md) to compile text files or XML (*.resx*) files that contain resources to binary *.resources* files.</span></span> <span data-ttu-id="f8c5d-142">Daha sonra, *. resources* dosyalarını uydu Derlemeleriyle derlemek Için [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-142">You then use [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile *.resources* files into satellite assemblies.</span></span> <span data-ttu-id="f8c5d-143">*Al. exe* , belirttiğiniz *. resources* dosyalarından bir derleme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-143">*Al.exe* creates an assembly from the *.resources* files that you specify.</span></span> <span data-ttu-id="f8c5d-144">Uydu derlemeleri yalnızca kaynaklar içerebilir; herhangi bir yürütülebilir kod içeremez.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-144">Satellite assemblies can contain only resources; they cannot contain any executable code.</span></span>

<span data-ttu-id="f8c5d-145">Aşağıdaki *al. exe* komutu, Almanya kaynakları dosya dizelerinden uygulama `Example` için bir uydu derlemesi oluşturur *. de. resources*.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-145">The following *Al.exe* command creates a satellite assembly for the application `Example` from the German resources file *strings.de.resources*.</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll
```

<span data-ttu-id="f8c5d-146">Aşağıdaki *al. exe* komutu ayrıca, uygulama `Example` için dosya dizelerinden bir uydu derlemesi oluşturur *. de. resources*.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-146">The following *Al.exe* command also creates a satellite assembly for the application `Example` from the file *strings.de.resources*.</span></span> <span data-ttu-id="f8c5d-147">**/Template** seçeneği, uydu derlemesinin üst derlemeden (*example. dll*) kültür bilgileri hariç tüm derleme meta verilerini devralmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-147">The **/template** option causes the satellite assembly to inherit all assembly metadata except for its culture information from the parent assembly (*Example.dll*).</span></span>

```console
al -target:lib -embed:strings.de.resources -culture:de -out:Example.resources.dll -template:Example.dll
```  
  
<span data-ttu-id="f8c5d-148">Aşağıdaki tabloda, bu komutlarda daha ayrıntılı olarak kullanılan *al. exe* seçenekleri açıklanmaktadır:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-148">The following table describes the *Al.exe* options used in these commands in more detail:</span></span>
  
|<span data-ttu-id="f8c5d-149">Seçenek</span><span class="sxs-lookup"><span data-stu-id="f8c5d-149">Option</span></span>|<span data-ttu-id="f8c5d-150">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f8c5d-150">Description</span></span>|
|------------|-----------------|
|`-target:lib`|<span data-ttu-id="f8c5d-151">Uydu derlemelerinizin bir kitaplık (. dll) dosyasına derlendiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-151">Specifies that your satellite assembly is compiled to a library (.dll) file.</span></span> <span data-ttu-id="f8c5d-152">Bir uydu derlemesi yürütülebilir kod içermediğinden ve bir uygulamanın ana derlemesi olmadığından, uydu derlemelerini dll olarak kaydetmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-152">Because a satellite assembly does not contain executable code and is not an application's main assembly, you must save satellite assemblies as DLLs.</span></span>|
|`-embed:strings.de.resources`|<span data-ttu-id="f8c5d-153">*Al. exe* derlemeyi derlediğinde, eklenecek kaynak dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-153">Specifies the name of the resource file to embed when *Al.exe* compiles the assembly.</span></span> <span data-ttu-id="f8c5d-154">Birden çok. resources dosyasını bir uydu derlemesine ekleyebilirsiniz, ancak hub ve bağlı bileşen modelini takip ediyorsanız, her kültür için bir uydu derlemesi derlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-154">You can embed multiple .resources files in a satellite assembly, but if you are following the hub-and-spoke model, you must compile one satellite assembly for each culture.</span></span> <span data-ttu-id="f8c5d-155">Ancak, dizeler ve nesneler için ayrı. resources dosyaları oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-155">However, you can create separate .resources files for strings and objects.</span></span>|
|`-culture:de`|<span data-ttu-id="f8c5d-156">Derlenecek kaynağın kültürünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-156">Specifies the culture of the resource to compile.</span></span> <span data-ttu-id="f8c5d-157">Ortak dil çalışma zamanı, belirtilen bir kültürün kaynaklarını ararken bu bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-157">The common language runtime uses this information when it searches for the resources for a specified culture.</span></span> <span data-ttu-id="f8c5d-158">Bu seçeneği atlarsanız, *al. exe* yine de kaynağı derler, ancak çalışma zamanı, bir Kullanıcı istediğinde bu işlemi bulamaz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-158">If you omit this option, *Al.exe* will still compile the resource, but the runtime will not be able to find it when a user requests it.</span></span>|
|`-out:Example.resources.dll`|<span data-ttu-id="f8c5d-159">Çıktı dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-159">Specifies the name of the output file.</span></span> <span data-ttu-id="f8c5d-160">Ad, *baseName*. resources adlandırma standardını izlemelidir. *extension*, burada *baseName* , ana derlemenin adı ve *uzantısının* geçerli bir dosya adı uzantısı (. dll gibi).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-160">The name must follow the naming standard *baseName*.resources.*extension*, where *baseName* is the name of the main assembly and *extension* is a valid file name extension (such as .dll).</span></span> <span data-ttu-id="f8c5d-161">Çalışma zamanının, bir uydu derlemesinin, çıkış dosyası adına göre kültürünü belirleyemediğini unutmayın; belirtmek için **/Culture** seçeneğini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-161">Note that the runtime is not able to determine the culture of a satellite assembly based on its output file name; you must use the **/culture** option to specify it.</span></span>|
|`-template:Example.dll`|<span data-ttu-id="f8c5d-162">Uydu derlemesinin kültür alanı hariç tüm derleme meta verilerini devraldığı bir derlemeyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-162">Specifies an assembly from which the satellite assembly will inherit all assembly metadata except the culture field.</span></span> <span data-ttu-id="f8c5d-163">Bu seçenek, yalnızca [tanımlayıcı ada](../../standard/assembly/strong-named.md)sahip bir derleme belirttiğinizde uydu derlemelerini etkiler.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-163">This option affects satellite assemblies only if you specify an assembly that has a [strong name](../../standard/assembly/strong-named.md).</span></span>|
  
 <span data-ttu-id="f8c5d-164">*Al. exe*ile kullanılabilen seçeneklerin tamamı listesi için bkz. [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-164">For a complete list of options available with *Al.exe*, see [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md).</span></span>
  
## <a name="satellite-assemblies-an-example"></a><span data-ttu-id="f8c5d-165">Uydu derlemeleri: bir örnek</span><span class="sxs-lookup"><span data-stu-id="f8c5d-165">Satellite Assemblies: An Example</span></span>

<span data-ttu-id="f8c5d-166">Aşağıda yerelleştirilmiş bir selamlama içeren ileti kutusunu görüntüleyen basit bir "Hello World" örneği verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-166">The following is a simple "Hello world" example that displays a message box containing a localized greeting.</span></span> <span data-ttu-id="f8c5d-167">Örnek, Ingilizce (Birleşik Devletler), Fransızca (Fransa) ve Rusça (Rusya) kültürleri için kaynakları ve geri dönüş kültürünün Ingilizce olduğunu içerir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-167">The example includes resources for the English (United States), French (France), and Russian (Russia) cultures, and its fallback culture is English.</span></span> <span data-ttu-id="f8c5d-168">Örneği oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-168">To create the example, do the following:</span></span>
  
1. <span data-ttu-id="f8c5d-169">Varsayılan kültür için kaynağı içerecek olan *Greeting. resx* veya *Greeting. txt* adlı bir kaynak dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-169">Create a resource file named *Greeting.resx* or *Greeting.txt* to contain the resource for the default culture.</span></span> <span data-ttu-id="f8c5d-170">"Hello World!" `HelloString` olan ada sahip tek bir dizeyi depola</span><span class="sxs-lookup"><span data-stu-id="f8c5d-170">Store a single string named `HelloString` whose value is "Hello world!"</span></span> <span data-ttu-id="f8c5d-171">Bu dosyada.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-171">in this file.</span></span>

2. <span data-ttu-id="f8c5d-172">Ingilizce (en) uygulamanın varsayılan kültürünün olduğunu göstermek için, uygulamanın AssemblyInfo dosyasına veya <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> uygulamanın ana derlemesine derlenecek ana kaynak kod dosyasına aşağıdaki özniteliği ekleyin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-172">To indicate that English (en) is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly.</span></span>

    [!code-csharp[Conceptual.Resources.Locating#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/assemblyinfo.cs#2)]
    [!code-vb[Conceptual.Resources.Locating#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/assemblyinfo.vb#2)]  
  
3. <span data-ttu-id="f8c5d-173">Uygulamaya aşağıdaki şekilde ek kültürler (en-US, fr-FR ve ru-RU) desteği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-173">Add support for additional cultures (en-US, fr-FR, and ru-RU) to the application as follows:</span></span>  
  
    - <span data-ttu-id="f8c5d-174">En-US veya Ingilizce (Birleşik Devletler) kültürünü desteklemek için, *Greeting. en-US. resx* veya *Greeting. en-US. txt*adlı bir kaynak dosyası oluşturun ve bunu değeri "Hi World!" `HelloString` olan bir tek dize olarak saklayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-174">To support the en-US or English (United States) culture, create a resource file named *Greeting.en-US.resx* or *Greeting.en-US.txt*, and store in it a single string named `HelloString` whose value is "Hi world!".</span></span>
  
    - <span data-ttu-id="f8c5d-175">Fr-FR veya Fransızca (Fransa) kültürünü desteklemek için *Greeting.fr-fr. resx* veya *Greeting.fr-fr. txt*adlı bir kaynak dosyası oluşturun ve bunu değeri "Salut tout Le Monde! `HelloString` " olan tek bir dize olarak saklayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-175">To support the fr-FR or French (France) culture, create a resource file named *Greeting.fr-FR.resx* or *Greeting.fr-FR.txt*, and store in it a single string named `HelloString` whose value is "Salut tout le monde!".</span></span>
  
    - <span data-ttu-id="f8c5d-176">Ru-RU veya Rusça (Rusya) kültürünü desteklemek için *Greeting.ru-ru. resx* veya *Greeting.ru-ru. txt*adlı bir kaynak dosyası oluşturun ve bunu değeri "Всем привет!" `HelloString` olan tek bir dize olarak depolayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-176">To support the ru-RU or Russian (Russia) culture, create a resource file named *Greeting.ru-RU.resx* or *Greeting.ru-RU.txt*, and store in it a single string named `HelloString` whose value is "Всем привет!".</span></span>
  
4. <span data-ttu-id="f8c5d-177">Her metin veya XML kaynak dosyasını bir ikili *. resources* dosyasına derlemek Için [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-177">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary *.resources* file.</span></span> <span data-ttu-id="f8c5d-178">Çıktı, *. resx* veya *. txt* dosyalarıyla aynı kök dosya adına sahip bir dosya kümesidir, ancak *. resources* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-178">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="f8c5d-179">Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-179">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="f8c5d-180">Visual Studio kullanmıyorsanız, *. resx* dosyalarını *. resources* dosyalarına derlemek için aşağıdaki komutları çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-180">If you aren't using Visual Studio, run the following commands to compile the *.resx* files into *.resources* files:</span></span>  
  
    ```console
    resgen Greeting.resx
    resgen Greeting.en-us.resx
    resgen Greeting.fr-FR.resx
    resgen Greeting.ru-RU.resx
    ```

    <span data-ttu-id="f8c5d-181">Kaynaklarınız XML dosyaları yerine metin dosyalarında ise *. resx* uzantısını *. txt*ile değiştirin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-181">If your resources are in text files instead of XML files, replace the *.resx* extension with *.txt*.</span></span>

5. <span data-ttu-id="f8c5d-182">Aşağıdaki kaynak kodu, uygulamanın ana derlemesinde varsayılan kültürün kaynaklarıyla birlikte derleyin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-182">Compile the following source code along with the resources for the default culture into the application's main assembly:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f8c5d-183">Örneği oluşturmak için Visual Studio yerine komut satırını kullanıyorsanız, <xref:System.Resources.ResourceManager> sınıf oluşturucusuna yapılan çağrıyı aşağıdaki şekilde değiştirmelisiniz:`ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span><span class="sxs-lookup"><span data-stu-id="f8c5d-183">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to the following: `ResourceManager rm = new ResourceManager("Greetings", typeof(Example).Assembly);`</span></span>

    [!code-csharp[Conceptual.Resources.Locating#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.locating/cs/program.cs#1)]
    [!code-vb[Conceptual.Resources.Locating#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.locating/vb/module1.vb#1)]

    <span data-ttu-id="f8c5d-184">Uygulamanın adı example ise ve komut satırından derlediğiniz takdirde, C# derleyicisi için komutu şu şekilde olur:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-184">If the application is named Example and you are compiling from the command-line, the command for the C# compiler is:</span></span>

    ```console
    csc Example.cs -res:Greeting.resources
    ```

    <span data-ttu-id="f8c5d-185">Karşılık gelen Visual Basic derleyici komutu:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-185">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc Example.vb -res:Greeting.resources
    ```

6. <span data-ttu-id="f8c5d-186">Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizininde bir alt dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-186">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="f8c5d-187">*En-US*, *fr-fr*ve *ru-ru* alt dizini oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-187">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="f8c5d-188">Visual Studio bu alt dizinleri derleme sürecinin bir parçası olarak otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-188">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span>

7. <span data-ttu-id="f8c5d-189">Kültüre özgü tekil *. resources* dosyalarını uydu derlemelerine ekleyin ve uygun dizine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-189">Embed the individual culture-specific *.resources* files into satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="f8c5d-190">Her *. resources* dosyası için bunu yapmak için komutu:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-190">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Greeting.culture.resources -culture:culture -out:culture\Example.resources.dll
    ```

     <span data-ttu-id="f8c5d-191">Burada *kültür* , kaynakları uydu derlemesinin içerdiği kültürün adıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-191">where *culture* is the name of the culture whose resources the satellite assembly contains.</span></span> <span data-ttu-id="f8c5d-192">Visual Studio bu işlemi otomatik olarak işler.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-192">Visual Studio handles this process automatically.</span></span>

<span data-ttu-id="f8c5d-193">Daha sonra örneği çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-193">You can then run the example.</span></span> <span data-ttu-id="f8c5d-194">Bu işlem, desteklenen kültürlerin geçerli kültürden birini rastgele yapar ve yerelleştirilmiş bir selamlama görüntüler.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-194">It will randomly make one of the supported cultures the current culture and display a localized greeting.</span></span>

<a name="SN"></a>

## <a name="installing-satellite-assemblies-in-the-global-assembly-cache"></a><span data-ttu-id="f8c5d-195">Genel bütünleştirilmiş kod önbelleğine uydu derlemeleri yükleme</span><span class="sxs-lookup"><span data-stu-id="f8c5d-195">Installing Satellite Assemblies in the Global Assembly Cache</span></span>

<span data-ttu-id="f8c5d-196">Derlemeleri yerel bir uygulama alt dizininde yüklemek yerine, bunları genel derleme önbelleğine yükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-196">Instead of installing assemblies in a local application subdirectory, you can install them in the global assembly cache.</span></span> <span data-ttu-id="f8c5d-197">Bu, özellikle birden çok uygulama tarafından kullanılan sınıf kitaplıkları ve sınıf kitaplığı kaynak derlemeleriniz varsa yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-197">This is particularly useful if you have class libraries and class library resource assemblies that are used by multiple applications.</span></span>
  
<span data-ttu-id="f8c5d-198">Derlemeleri genel bütünleştirilmiş kod önbelleğine yüklemek için tanımlayıcı adlara sahip olmaları gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-198">Installing assemblies in the global assembly cache requires that they have strong names.</span></span> <span data-ttu-id="f8c5d-199">Tanımlayıcı adlı derlemeler geçerli bir ortak/özel anahtar çiftiyle imzalanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-199">Strong-named assemblies are signed with a valid public/private key pair.</span></span> <span data-ttu-id="f8c5d-200">Çalışma zamanının, bir bağlama isteğini karşılamak için hangi derlemeyi kullanacağını belirlemede kullandığı sürüm bilgilerini içerirler.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-200">They contain version information that the runtime uses to determine which assembly to use to satisfy a binding request.</span></span> <span data-ttu-id="f8c5d-201">Güçlü adlar ve sürüm oluşturma hakkında daha fazla bilgi için bkz. [derleme sürümü oluşturma](../../standard/assembly/versioning.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-201">For more information about strong names and versioning, see [Assembly Versioning](../../standard/assembly/versioning.md).</span></span> <span data-ttu-id="f8c5d-202">Güçlü adlar hakkında daha fazla bilgi için bkz. [Strong-adlandırılmış derlemeler](../../standard/assembly/strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-202">For more information about strong names, see [Strong-Named Assemblies](../../standard/assembly/strong-named.md).</span></span>

<span data-ttu-id="f8c5d-203">Bir uygulama geliştirirken, son ortak/özel anahtar çiftine erişiminizin olması düşüktür.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-203">When you are developing an application, it is unlikely that you will have access to the final public/private key pair.</span></span> <span data-ttu-id="f8c5d-204">Genel bütünleştirilmiş kod önbelleğine bir uydu derlemesini yüklemek ve beklendiği gibi çalıştığından emin olmak için, Gecikmeli imzalama adlı bir teknik kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-204">In order to install a satellite assembly in the global assembly cache and ensure that it works as expected, you can use a technique called delayed signing.</span></span> <span data-ttu-id="f8c5d-205">Bir derlemeyi imzalamayı ertelerseniz, derleme zamanında tanımlayıcı ad imzası için dosyada alan ayırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-205">When you delay sign an assembly, at build time you reserve space in the file for the strong name signature.</span></span> <span data-ttu-id="f8c5d-206">Son ortak/özel anahtar çifti kullanılabilir olduğunda, gerçek imzalama daha sonra gecikiyor.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-206">The actual signing is delayed until later, when the final public/private key pair is available.</span></span> <span data-ttu-id="f8c5d-207">Gecikmeli imzalama hakkında daha fazla bilgi için bkz. [bir derlemeyi IMZALAMAYı geciktirme](../../standard/assembly/delay-sign.md).</span><span class="sxs-lookup"><span data-stu-id="f8c5d-207">For more information about delayed signing, see [Delay Signing an Assembly](../../standard/assembly/delay-sign.md).</span></span>

### <a name="obtaining-the-public-key"></a><span data-ttu-id="f8c5d-208">Ortak anahtar alma</span><span class="sxs-lookup"><span data-stu-id="f8c5d-208">Obtaining the Public Key</span></span>

<span data-ttu-id="f8c5d-209">Bir derlemeyi imzalamayı geciktirmek için ortak anahtara erişiminizin olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-209">To delay sign an assembly, you must have access to the public key.</span></span> <span data-ttu-id="f8c5d-210">Şirketinizdeki gerçek zamanlı ortak anahtarı elde edebilir veya [tanımlayıcı ad Aracı (sn. exe)](../tools/sn-exe-strong-name-tool.md)kullanarak bir ortak anahtar oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-210">You can either obtain the real public key from the organization in your company that will do the eventual signing, or create a public key by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md).</span></span>

<span data-ttu-id="f8c5d-211">Aşağıdaki *sn. exe* komutu bir test ortak/özel anahtar çifti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-211">The following *Sn.exe* command creates a test public/private key pair.</span></span> <span data-ttu-id="f8c5d-212">**– K** seçeneği, *sn. exe* ' nin yeni bir anahtar çifti oluşturması ve bunu *testkeypair. snk*adlı bir dosyaya kaydetmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-212">The **–k** option specifies that *Sn.exe* should create a new key pair and save it in a file named *TestKeyPair.snk*.</span></span>
  
```console
sn –k TestKeyPair.snk
```

<span data-ttu-id="f8c5d-213">Ortak anahtarı, test anahtar çiftini içeren dosyadan ayıklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-213">You can extract the public key from the file that contains the test key pair.</span></span> <span data-ttu-id="f8c5d-214">Aşağıdaki komut *Testkeypair. snk* öğesinden ortak anahtarı ayıklar ve *PublicKey. snk*içine kaydeder:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-214">The following command extracts the public key from *TestKeyPair.snk* and saves it in *PublicKey.snk*:</span></span>

```console
sn –p TestKeyPair.snk PublicKey.snk
```

### <a name="delay-signing-an-assembly"></a><span data-ttu-id="f8c5d-215">Derleme İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="f8c5d-215">Delay Signing an Assembly</span></span>

<span data-ttu-id="f8c5d-216">Ortak anahtarı aldıktan veya oluşturduktan sonra, derlemeyi derlemek ve Gecikmeli imzalamayı belirtmek için [derleme Bağlayıcısı (al. exe)](../tools/al-exe-assembly-linker.md) kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-216">After you obtain or create the public key, you use the [Assembly Linker (Al.exe)](../tools/al-exe-assembly-linker.md) to compile the assembly and specify delayed signing.</span></span>

<span data-ttu-id="f8c5d-217">Aşağıdaki *al. exe* komutu, *dizeler. ja. resources* dosyasından uygulama StringLibrary için tanımlayıcı adlı bir uydu derlemesi oluşturur:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-217">The following *Al.exe* command creates a strong-named satellite assembly for the application StringLibrary from the *strings.ja.resources* file:</span></span>

```console
al -target:lib -embed:strings.ja.resources -culture:ja -out:StringLibrary.resources.dll -delay+ -keyfile:PublicKey.snk
```

<span data-ttu-id="f8c5d-218">**-Delay +** seçeneği, derleme bağlayıcının derlemeyi imzalamasını geciktirmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-218">The **-delay+** option specifies that the Assembly Linker should delay sign the assembly.</span></span> <span data-ttu-id="f8c5d-219">**-Keyfile** seçeneği, derlemeyi imzalamayı geciktirmede kullanılacak ortak anahtarı içeren anahtar dosyasının adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-219">The **-keyfile** option specifies the name of the key file that contains the public key to use to delay sign the assembly.</span></span>

### <a name="re-signing-an-assembly"></a><span data-ttu-id="f8c5d-220">Derlemeyi yeniden imzalama</span><span class="sxs-lookup"><span data-stu-id="f8c5d-220">Re-signing an Assembly</span></span>

<span data-ttu-id="f8c5d-221">Uygulamanızı dağıtmadan önce, gecikmeli imzalanmış uydu derlemesini gerçek anahtar çiftiyle yeniden imzalamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-221">Before you deploy your application, you must re-sign the delay signed satellite assembly with the real key pair.</span></span> <span data-ttu-id="f8c5d-222">Bu, *sn. exe*' yi kullanarak yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-222">You can do this by using *Sn.exe*.</span></span>

<span data-ttu-id="f8c5d-223">Aşağıdaki *sn. exe* komutu, *StringLibrary. resources. dll* dosyasını *RealKeyPair. snk*dosyasında depolanan anahtar çiftiyle imzalar.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-223">The following *Sn.exe* command signs *StringLibrary.resources.dll* with the key pair stored in the file *RealKeyPair.snk*.</span></span> <span data-ttu-id="f8c5d-224">**– R** seçeneği, önceden imzalanmış veya gecikmeli imzalanmış bir derlemenin yeniden imzalanıp imzalanmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-224">The **–R** option specifies that a previously signed or delay signed assembly is to be re-signed.</span></span>

```console
sn –R StringLibrary.resources.dll RealKeyPair.snk
```

### <a name="installing-a-satellite-assembly-in-the-global-assembly-cache"></a><span data-ttu-id="f8c5d-225">Genel bütünleştirilmiş kod önbelleğine uydu derlemesi yükleme</span><span class="sxs-lookup"><span data-stu-id="f8c5d-225">Installing a Satellite Assembly in the Global Assembly Cache</span></span>

<span data-ttu-id="f8c5d-226">Çalışma zamanı, kaynak geri dönüş işlemindeki kaynakları aradığında, önce [genel derleme önbelleğine](../app-domains/gac.md) bakar.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-226">When the runtime searches for resources in the resource fallback process, it looks in the [global assembly cache](../app-domains/gac.md) first.</span></span> <span data-ttu-id="f8c5d-227">(Daha fazla bilgi için [kaynakları paketleme ve dağıtma](packaging-and-deploying-resources-in-desktop-apps.md) konusunun "kaynak geri dönüş işlemi" bölümüne bakın.) Uydu bütünleştirilmiş kodu bir tanımlayıcı ad ile imzalandığı anda, [genel bütünleştirilmiş kod önbelleği aracı (Gacutil. exe)](../tools/gacutil-exe-gac-tool.md)kullanılarak genel derleme önbelleğine yüklenebilir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-227">(For more information, see the "Resource Fallback Process" section of the [Packaging and Deploying Resources](packaging-and-deploying-resources-in-desktop-apps.md) topic.) As soon as a satellite assembly is signed with a strong name, it can be installed in the global assembly cache by using the [Global Assembly Cache Tool (Gacutil.exe)](../tools/gacutil-exe-gac-tool.md).</span></span>

<span data-ttu-id="f8c5d-228">Aşağıdaki *Gacutil. exe* komutu, genel derleme önbelleğinde *StringLibrary. resources. dll*\* yükler:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-228">The following *Gacutil.exe* command installs *StringLibrary.resources.dll*\* in the global assembly cache:</span></span>

```console
gacutil -i:StringLibrary.resources.dll
```

<span data-ttu-id="f8c5d-229">**/I** seçeneği, *Gacutil. exe* ' nin belirtilen derlemeyi genel derleme önbelleğine yüklemesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-229">The **/i** option specifies that *Gacutil.exe* should install the specified assembly into the global assembly cache.</span></span> <span data-ttu-id="f8c5d-230">Uydu derlemesi önbellekte yüklendikten sonra, içerdiği kaynaklar uydu derlemesini kullanacak şekilde tasarlanan tüm uygulamalar tarafından kullanılabilir hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-230">After the satellite assembly is installed in the cache, the resources it contains become available to all applications that are designed to use the satellite assembly.</span></span>

### <a name="resources-in-the-global-assembly-cache-an-example"></a><span data-ttu-id="f8c5d-231">Genel derleme önbelleğindeki kaynaklar: bir örnek</span><span class="sxs-lookup"><span data-stu-id="f8c5d-231">Resources in the Global Assembly Cache: An Example</span></span>

<span data-ttu-id="f8c5d-232">Aşağıdaki örnek, bir kaynak dosyasından yerelleştirilmiş bir karşılama ayıklamak ve döndürmek için .NET Framework sınıf kitaplığındaki bir yöntemi kullanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-232">The following example uses a method in a .NET Framework class library to extract and return a localized greeting from a resource file.</span></span> <span data-ttu-id="f8c5d-233">Kitaplık ve kaynakları genel derleme önbelleğine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-233">The library and its resources are registered in the global assembly cache.</span></span> <span data-ttu-id="f8c5d-234">Örnek, Ingilizce (Birleşik Devletler), Fransızca (Fransa), Rusça (Rusya) ve Ingilizce kültürlerin kaynaklarını içerir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-234">The example includes resources for the English (United States), French (France), Russian (Russia), and English cultures.</span></span> <span data-ttu-id="f8c5d-235">Varsayılan kültür İngilizce 'dir; kaynakları ana derlemede depolanır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-235">English is the default culture; its resources are stored in the main assembly.</span></span> <span data-ttu-id="f8c5d-236">Örnek Başlangıçta, kitaplığı ve uydu derlemelerini ortak anahtarla imzalar ve sonra bunları ortak/özel anahtar çifti ile yeniden imzalar.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-236">The example initially delay signs the library and its satellite assemblies with a public key, then re-signs them with a public/private key pair.</span></span> <span data-ttu-id="f8c5d-237">Örneği oluşturmak için aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-237">To create the example, do the following:</span></span>

1. <span data-ttu-id="f8c5d-238">Visual Studio kullanmıyorsanız, *Reskey. snk*adlı bir ortak/özel anahtar çifti oluşturmak Için aşağıdaki [tanımlayıcı ad Aracı (sn. exe)](../tools/sn-exe-strong-name-tool.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-238">If you are not using Visual Studio, use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public/private key pair named *ResKey.snk*:</span></span>

    ```console
    sn –k ResKey.snk
    ```

    <span data-ttu-id="f8c5d-239">Visual Studio kullanıyorsanız, anahtar dosyasını oluşturmak için proje **özellikleri** Iletişim kutusunun **imzalama** sekmesini kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-239">If you are using Visual Studio, use the **Signing** tab of the project **Properties** dialog box to generate the key file.</span></span>

2. <span data-ttu-id="f8c5d-240">*PublicKey. snk*adlı bir ortak anahtar dosyası oluşturmak Için aşağıdaki [tanımlayıcı ad Aracı (sn. exe)](../tools/sn-exe-strong-name-tool.md) komutunu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-240">Use the following [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) command to create a public key file named *PublicKey.snk*:</span></span>

    ```console
    sn –p ResKey.snk PublicKey.snk
    ```

3. <span data-ttu-id="f8c5d-241">Varsayılan kültür için kaynağı içerecek *dizeler. resx* adlı bir kaynak dosyası oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-241">Create a resource file named *Strings.resx* to contain the resource for the default culture.</span></span> <span data-ttu-id="f8c5d-242">"Değeri" nasıl yapılır `Greeting` ? "adlı tek bir dizeyi depola</span><span class="sxs-lookup"><span data-stu-id="f8c5d-242">Store a single string named `Greeting` whose value is "How do you do?"</span></span> <span data-ttu-id="f8c5d-243">Bu dosyada.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-243">in that file.</span></span>

4. <span data-ttu-id="f8c5d-244">"En" ın uygulamanın varsayılan kültürü olduğunu belirtmek için, uygulamanın AssemblyInfo dosyasına veya <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> uygulamanın ana derlemesine derlenecek ana kaynak kod dosyasına aşağıdaki özniteliği ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-244">To indicate that "en" is the application's default culture, add the following <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=nameWithType> attribute to the application's AssemblyInfo file or to the main source code file that will be compiled into the application's main assembly:</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#2](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#2)]
    [!code-vb[Conceptual.Resources.Satellites#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#2)]

5. <span data-ttu-id="f8c5d-245">Uygulamaya ek kültürler (en-US, fr-FR ve ru-RU kültürleri) için aşağıdaki şekilde bir destek ekleyin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-245">Add support for additional cultures (the en-US, fr-FR, and ru-RU cultures) to the application as follows:</span></span>

    - <span data-ttu-id="f8c5d-246">"En-US" veya Ingilizce (Birleşik Devletler) kültürünü desteklemek için, *dizeler. en-US. resx* veya *Strings. en-US. txt*adlı bir kaynak dosyası oluşturun ve bunu değeri "Merhaba!" `Greeting` olan tek bir dize içinde saklayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-246">To support the "en-US" or English (United States) culture, create a resource file named *Strings.en-US.resx* or *Strings.en-US.txt*, and store in it a single string named `Greeting` whose value is "Hello!".</span></span>

    - <span data-ttu-id="f8c5d-247">"Fr-FR" veya Fransızca (Fransa) kültürünü desteklemek için, *Strings.fr-fr. resx* veya *Strings.fr-fr. txt* adlı bir kaynak dosyası oluşturun ve bunu değeri "iyi jour!" `Greeting` olan tek bir dize olarak saklayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-247">To support the "fr-FR" or French (France) culture, create a resource file named *Strings.fr-FR.resx* or *Strings.fr-FR.txt* and store in it a single string named `Greeting` whose value is "Bon jour!".</span></span>

    - <span data-ttu-id="f8c5d-248">"Ru-RU" veya Rusça (Rusya) kültürünü desteklemek için, *Strings.ru-ru. resx* veya *Strings.ru-ru. txt* adlı bir kaynak dosyası oluşturun ve bunu değeri "привет!" `Greeting` olan tek bir dize olarak saklayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-248">To support the "ru-RU" or Russian (Russia) culture, create a resource file named *Strings.ru-RU.resx* or *Strings.ru-RU.txt* and store in it a single string named `Greeting` whose value is "Привет!".</span></span>

6. <span data-ttu-id="f8c5d-249">Her metin veya XML kaynak dosyasını bir ikili. resources dosyasına derlemek için [Resgen. exe](../tools/resgen-exe-resource-file-generator.md) ' yi kullanın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-249">Use [Resgen.exe](../tools/resgen-exe-resource-file-generator.md) to compile each text or XML resource file to a binary .resources file.</span></span> <span data-ttu-id="f8c5d-250">Çıktı, *. resx* veya *. txt* dosyalarıyla aynı kök dosya adına sahip bir dosya kümesidir, ancak *. resources* uzantısı.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-250">The output is a set of files that have the same root file name as the *.resx* or *.txt* files, but a *.resources* extension.</span></span> <span data-ttu-id="f8c5d-251">Visual Studio ile örnek oluşturursanız, derleme işlemi otomatik olarak işlenir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-251">If you create the example with Visual Studio, the compilation process is handled automatically.</span></span> <span data-ttu-id="f8c5d-252">Visual Studio kullanmıyorsanız, *. resx* dosyalarını *. resources* dosyalarına derlemek için aşağıdaki komutu çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-252">If you aren't using Visual Studio, run the following command to compile the *.resx* files into *.resources* files:</span></span>

    ```console
    resgen filename
    ```

    <span data-ttu-id="f8c5d-253">Burada *Dosya* adı, *. resx* veya metin dosyasının uzantısı olan isteğe bağlı yoldur.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-253">Where *filename* is the optional path, file name, and extension of the *.resx* or text file.</span></span>

7. <span data-ttu-id="f8c5d-254">*StringLibrary. vb* veya *StringLibrary.cs* için aşağıdaki kaynak kodu, varsayılan kültürün kaynaklarla birlikte *StringLibrary. dll*adlı gecikmeli imzalanmış bir kitaplık derlemesi olarak derleyin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-254">Compile the following source code for *StringLibrary.vb* or *StringLibrary.cs* along with the resources for the default culture into a delay signed library assembly named *StringLibrary.dll*:</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="f8c5d-255">Örneği oluşturmak için Visual Studio yerine komut satırını kullanıyorsanız, <xref:System.Resources.ResourceManager> sınıf oluşturucusuna olan çağrıyı olarak `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`değiştirmelisiniz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-255">If you are using the command line rather than Visual Studio to create the example, you should modify the call to the <xref:System.Resources.ResourceManager> class constructor to `ResourceManager rm = new ResourceManager("Strings",` `typeof(Example).Assembly);`.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#1](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/stringlibrary.cs#1)]
    [!code-vb[Conceptual.Resources.Satellites#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/stringlibrary.vb#1)]

    <span data-ttu-id="f8c5d-256">C# derleyicisi için komutu:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-256">The command for the C# compiler is:</span></span>

    ```console
    csc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.cs
    ```

    <span data-ttu-id="f8c5d-257">Karşılık gelen Visual Basic derleyici komutu:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-257">The corresponding Visual Basic compiler command is:</span></span>

    ```console
    vbc -t:library -resource:Strings.resources -delaysign+ -keyfile:publickey.snk StringLibrary.vb
    ```

8. <span data-ttu-id="f8c5d-258">Uygulama tarafından desteklenen her yerelleştirilmiş kültür için ana uygulama dizininde bir alt dizin oluşturun.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-258">Create a subdirectory in the main application directory for each localized culture supported by the application.</span></span> <span data-ttu-id="f8c5d-259">*En-US*, *fr-fr*ve *ru-ru* alt dizini oluşturmalısınız.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-259">You should create an *en-US*, an *fr-FR*, and an *ru-RU* subdirectory.</span></span> <span data-ttu-id="f8c5d-260">Visual Studio bu alt dizinleri derleme sürecinin bir parçası olarak otomatik olarak oluşturur.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-260">Visual Studio creates these subdirectories automatically as part of the compilation process.</span></span> <span data-ttu-id="f8c5d-261">Tüm uydu derlemeleri aynı dosya adına sahip olduğundan, ortak/özel anahtar çifti ile imzalanana kadar kültüre özgü ayrı uydu derlemelerini depolamak için alt dizinler kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-261">Because all satellite assemblies have the same file name, the subdirectories are used to store individual culture-specific satellite assemblies until they are signed with a public/private key pair.</span></span>

9. <span data-ttu-id="f8c5d-262">Kültüre özgü bağımsız *. resources* dosyalarını gecikmeli imzalanmış uydu derlemelerine katıştırın ve uygun dizine kaydedin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-262">Embed the individual culture-specific *.resources* files into delay signed satellite assemblies and save them to the appropriate directory.</span></span> <span data-ttu-id="f8c5d-263">Her *. resources* dosyası için bunu yapmak için komutu:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-263">The command to do this for each *.resources* file is:</span></span>

    ```console
    al -target:lib -embed:Strings.culture.resources -culture:culture -out:culture\StringLibrary.resources.dll -delay+ -keyfile:publickey.snk
    ```

    <span data-ttu-id="f8c5d-264">Burada *kültür* bir kültürün adıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-264">where *culture* is the name of a culture.</span></span> <span data-ttu-id="f8c5d-265">Bu örnekte, kültür adları en-US, fr-FR ve ru-RU ' dir.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-265">In this example, the culture names are en-US, fr-FR, and ru-RU.</span></span>

10. <span data-ttu-id="f8c5d-266">*StringLibrary. dll* dosyasını aşağıdaki gibi [tanımlayıcı ad Aracı (sn. exe)](../tools/sn-exe-strong-name-tool.md) kullanarak yeniden imzalayın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-266">Re-sign *StringLibrary.dll* by using the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows:</span></span>

    ```console
    sn –R StringLibrary.dll RealKeyPair.snk
    ```

11. <span data-ttu-id="f8c5d-267">Tek tek uydu derlemelerini yeniden imzalayın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-267">Re-sign the individual satellite assemblies.</span></span> <span data-ttu-id="f8c5d-268">Bunu yapmak için, her uydu derlemesi için [tanımlayıcı ad aracı 'nı (sn. exe)](../tools/sn-exe-strong-name-tool.md) aşağıdaki gibi kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-268">To do this, use the [Strong Name Tool (Sn.exe)](../tools/sn-exe-strong-name-tool.md) as follows for each satellite assembly:</span></span>

    ```console
    sn –R StringLibrary.resources.dll RealKeyPair.snk
    ```

12. <span data-ttu-id="f8c5d-269">Şu komutu kullanarak *StringLibrary. dll dosyasını* ve tüm uydu derlemelerini genel derleme önbelleğinde kaydedin:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-269">Register *StringLibrary.dll* and each of its satellite assemblies in the global assembly cache by using the following command:</span></span>

    ```console
    gacutil -i filename
    ```

    <span data-ttu-id="f8c5d-270">Burada *filename* , kayıt yapılacak dosyanın adıdır.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-270">where *filename* is the name of the file to register.</span></span>

13. <span data-ttu-id="f8c5d-271">Visual Studio kullanıyorsanız, adlı `Example`yeni bir **konsol uygulaması** projesi oluşturun, *StringLibrary. dll* ' ye ve aşağıdaki kaynak koda bir başvuru ekleyin ve derleyin.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-271">If you are using Visual Studio, create a new **Console Application** project named `Example`, add a reference to *StringLibrary.dll* and the following source code to it, and compile.</span></span>

    [!code-csharp[Conceptual.Resources.Satellites#3](~/samples/snippets/csharp/VS_Snippets_CLR/conceptual.resources.satellites/cs/example.cs#3)]
    [!code-vb[Conceptual.Resources.Satellites#3](~/samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.resources.satellites/vb/example.vb#3)]

    <span data-ttu-id="f8c5d-272">Komut satırından derlemek için, C# derleyicisi için aşağıdaki komutu kullanın:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-272">To compile from the command line, use the following command for the C# compiler:</span></span>

    ```console
    csc Example.cs -r:StringLibrary.dll
    ```

    <span data-ttu-id="f8c5d-273">Visual Basic Derleyicisi için komut satırı:</span><span class="sxs-lookup"><span data-stu-id="f8c5d-273">The command line for the Visual Basic compiler is:</span></span>

    ```console
    vbc Example.vb -r:StringLibrary.dll
    ```

14. <span data-ttu-id="f8c5d-274">*Example. exe dosyasını*çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-274">Run *Example.exe*.</span></span>

## <a name="see-also"></a><span data-ttu-id="f8c5d-275">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c5d-275">See also</span></span>

- [<span data-ttu-id="f8c5d-276">Kaynakları Paketleme ve Dağıtma</span><span class="sxs-lookup"><span data-stu-id="f8c5d-276">Packaging and Deploying Resources</span></span>](packaging-and-deploying-resources-in-desktop-apps.md)
- [<span data-ttu-id="f8c5d-277">Bütünleştirilmiş Kod İmzalamayı Geciktirme</span><span class="sxs-lookup"><span data-stu-id="f8c5d-277">Delay Signing an Assembly</span></span>](../../standard/assembly/delay-sign.md)
- [<span data-ttu-id="f8c5d-278">Al. exe (bütünleştirilmiş kod bağlayıcı)</span><span class="sxs-lookup"><span data-stu-id="f8c5d-278">Al.exe (Assembly Linker)</span></span>](../tools/al-exe-assembly-linker.md)
- [<span data-ttu-id="f8c5d-279">Sn. exe (tanımlayıcı ad aracı)</span><span class="sxs-lookup"><span data-stu-id="f8c5d-279">Sn.exe (Strong Name Tool)</span></span>](../tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="f8c5d-280">Gacutil. exe (Genel Bütünleştirilmiş Kod Önbelleği Aracı)</span><span class="sxs-lookup"><span data-stu-id="f8c5d-280">Gacutil.exe (Global Assembly Cache Tool)</span></span>](../tools/gacutil-exe-gac-tool.md)
- [<span data-ttu-id="f8c5d-281">Masaüstü uygulamalarındaki kaynaklar</span><span class="sxs-lookup"><span data-stu-id="f8c5d-281">Resources in Desktop Apps</span></span>](index.md)
