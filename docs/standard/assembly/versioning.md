---
title: Derleme sürümü oluşturma
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1363ce758929414f054e3d28dc6cd02bd618a8ac
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053961"
---
# <a name="assembly-versioning"></a><span data-ttu-id="08068-102">Derleme sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="08068-102">Assembly versioning</span></span>

<span data-ttu-id="08068-103">Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="08068-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="08068-104">Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="08068-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="08068-105">Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.</span><span class="sxs-lookup"><span data-stu-id="08068-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08068-106">Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="08068-106">Versioning is done only on assemblies with strong names.</span></span>  
  
<span data-ttu-id="08068-107">Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="08068-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1. <span data-ttu-id="08068-108">Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.</span><span class="sxs-lookup"><span data-stu-id="08068-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2. <span data-ttu-id="08068-109">Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.</span><span class="sxs-lookup"><span data-stu-id="08068-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3. <span data-ttu-id="08068-110">Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="08068-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4. <span data-ttu-id="08068-111">Yapılandırma dosyalarında belirtilen genel derleme önbelleğini ve kod temellerini denetler ve [çalışma zamanının derlemeleri nasıl](../../framework/deployment/how-the-runtime-locates-assemblies.md)konumlandırdığını açıklanan yoklama kurallarını kullanarak uygulamanın dizinini ve alt dizinlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="08068-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
<span data-ttu-id="08068-112">Aşağıdaki çizimde bu adımlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="08068-112">The following illustration shows these steps:</span></span>  
  
![Derleme bağlama isteği çözümlemesindeki adımları gösteren diyagram.](./media/versioning/resolve-assembly-binding-request.gif)
  
<span data-ttu-id="08068-114">Uygulamaları yapılandırma hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="08068-114">For more information about configuring applications, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="08068-115">Bağlama ilkesi hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="08068-115">For more information about binding policy, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="08068-116">Sürüm bilgileri</span><span class="sxs-lookup"><span data-stu-id="08068-116">Version information</span></span>  

<span data-ttu-id="08068-117">Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="08068-117">Each assembly has two distinct ways of expressing version information:</span></span>  
  
- <span data-ttu-id="08068-118">Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="08068-118">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="08068-119">Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="08068-119">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
- <span data-ttu-id="08068-120">Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.</span><span class="sxs-lookup"><span data-stu-id="08068-120">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="08068-121">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="08068-121">Assembly version number</span></span>  

<span data-ttu-id="08068-122">Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="08068-122">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="08068-123">Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="08068-123">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="08068-124">Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="08068-124">This version number is physically represented as a four-part string with the following format:</span></span>  
  
<span data-ttu-id="08068-125">\<*ana sürüm*>. *ikincil sürüm >.* \< *Yapı numarası >.* \< \< *Düzeltme*></span><span class="sxs-lookup"><span data-stu-id="08068-125">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
<span data-ttu-id="08068-126">Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.</span><span class="sxs-lookup"><span data-stu-id="08068-126">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
<span data-ttu-id="08068-127">Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.</span><span class="sxs-lookup"><span data-stu-id="08068-127">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
<span data-ttu-id="08068-128">Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="08068-128">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="08068-129">Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="08068-129">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
<span data-ttu-id="08068-130">Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder.</span><span class="sxs-lookup"><span data-stu-id="08068-130">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="08068-131">Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="08068-131">Version checking only occurs with strong-named assemblies.</span></span>  
  
<span data-ttu-id="08068-132">Sürüm bağlama ilkelerini belirtme hakkında bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="08068-132">For information about specifying version binding policies, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="08068-133">Çalışma zamanının belirli bir derlemeyi bulmak için sürüm bilgilerini nasıl kullandığı hakkında bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="08068-133">For information about how the runtime uses version information to find a particular assembly, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="08068-134">Derleme bilgilendirici sürümü</span><span class="sxs-lookup"><span data-stu-id="08068-134">Assembly informational version</span></span>  

<span data-ttu-id="08068-135">Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="08068-135">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="08068-136">Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="08068-136">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="08068-137">Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir.</span><span class="sxs-lookup"><span data-stu-id="08068-137">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="08068-138">Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="08068-138">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08068-139">Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür.</span><span class="sxs-lookup"><span data-stu-id="08068-139">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="08068-140">Bu uyarı zararsız olur.</span><span class="sxs-lookup"><span data-stu-id="08068-140">This warning is harmless.</span></span>  
  
<span data-ttu-id="08068-141">Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="08068-141">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="08068-142">Bilgilendirici sürüm özniteliği hakkında daha fazla bilgi için bkz. [derleme özniteliklerini ayarlama](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="08068-142">For more information about the informational version attribute, see [Set assembly attributes](set-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08068-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08068-143">See also</span></span>

- [<span data-ttu-id="08068-144">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="08068-144">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="08068-145">Uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="08068-145">Configure apps</span></span>](../../framework/configure-apps/index.md)
- [<span data-ttu-id="08068-146">Derleme özniteliklerini ayarla</span><span class="sxs-lookup"><span data-stu-id="08068-146">Set assembly attributes</span></span>](set-attributes.md)
- [<span data-ttu-id="08068-147">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="08068-147">Assemblies in .NET</span></span>](index.md)
