---
title: Derleme sürümü oluşturma
description: .NET derlemelerinin sürümü oluşturma hakkında bilgi edinin. CLR kullanan derlemelerin tüm sürümü derleme düzeyinde yapılır.
ms.date: 08/20/2019
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
ms.openlocfilehash: fdffbcc0bbafed62228cba35e8f85fbec7f7fbab
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380078"
---
# <a name="assembly-versioning"></a><span data-ttu-id="a3df5-104">Derleme sürümü oluşturma</span><span class="sxs-lookup"><span data-stu-id="a3df5-104">Assembly versioning</span></span>

<span data-ttu-id="a3df5-105">Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-105">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="a3df5-106">Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-106">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="a3df5-107">Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.</span><span class="sxs-lookup"><span data-stu-id="a3df5-107">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3df5-108">Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="a3df5-108">Versioning is done only on assemblies with strong names.</span></span>  
  
<span data-ttu-id="a3df5-109">Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="a3df5-109">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1. <span data-ttu-id="a3df5-110">Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.</span><span class="sxs-lookup"><span data-stu-id="a3df5-110">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2. <span data-ttu-id="a3df5-111">Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.</span><span class="sxs-lookup"><span data-stu-id="a3df5-111">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3. <span data-ttu-id="a3df5-112">Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="a3df5-112">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4. <span data-ttu-id="a3df5-113">Yapılandırma dosyalarında belirtilen genel derleme önbelleğini ve kod temellerini denetler ve [çalışma zamanının derlemeleri nasıl](../../framework/deployment/how-the-runtime-locates-assemblies.md)konumlandırdığını açıklanan yoklama kurallarını kullanarak uygulamanın dizinini ve alt dizinlerini denetler.</span><span class="sxs-lookup"><span data-stu-id="a3df5-113">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
<span data-ttu-id="a3df5-114">Aşağıdaki çizimde bu adımlar gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="a3df5-114">The following illustration shows these steps:</span></span>  
  
![Derleme bağlama isteği çözümlemesindeki adımları gösteren diyagram.](./media/versioning/resolve-assembly-binding-request.gif)
  
<span data-ttu-id="a3df5-116">Uygulamaları yapılandırma hakkında daha fazla bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3df5-116">For more information about configuring applications, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="a3df5-117">Bağlama ilkesi hakkında daha fazla bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a3df5-117">For more information about binding policy, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="a3df5-118">Sürüm bilgileri</span><span class="sxs-lookup"><span data-stu-id="a3df5-118">Version information</span></span>  

<span data-ttu-id="a3df5-119">Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="a3df5-119">Each assembly has two distinct ways of expressing version information:</span></span>  
  
- <span data-ttu-id="a3df5-120">Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="a3df5-120">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="a3df5-121">Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="a3df5-121">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
- <span data-ttu-id="a3df5-122">Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.</span><span class="sxs-lookup"><span data-stu-id="a3df5-122">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="a3df5-123">Derleme sürüm numarası</span><span class="sxs-lookup"><span data-stu-id="a3df5-123">Assembly version number</span></span>  

<span data-ttu-id="a3df5-124">Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-124">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="a3df5-125">Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-125">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="a3df5-126">Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="a3df5-126">This version number is physically represented as a four-part string with the following format:</span></span>  
  
<span data-ttu-id="a3df5-127">\<*ana sürüm*>. \< *ikincil sürüm*>. \< *Yapı numarası*>. \< *Düzeltme*></span><span class="sxs-lookup"><span data-stu-id="a3df5-127">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
<span data-ttu-id="a3df5-128">Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-128">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
<span data-ttu-id="a3df5-129">Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.</span><span class="sxs-lookup"><span data-stu-id="a3df5-129">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
<span data-ttu-id="a3df5-130">Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="a3df5-130">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="a3df5-131">Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="a3df5-131">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
<span data-ttu-id="a3df5-132">Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder.</span><span class="sxs-lookup"><span data-stu-id="a3df5-132">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="a3df5-133">Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-133">Version checking only occurs with strong-named assemblies.</span></span>  
  
<span data-ttu-id="a3df5-134">Sürüm bağlama ilkelerini belirtme hakkında bilgi için bkz. [uygulamaları yapılandırma](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="a3df5-134">For information about specifying version binding policies, see [Configure apps](../../framework/configure-apps/index.md).</span></span> <span data-ttu-id="a3df5-135">Çalışma zamanının belirli bir derlemeyi bulmak için sürüm bilgilerini nasıl kullandığı hakkında bilgi için bkz. [çalışma zamanı derlemeleri nasıl konumlandırır](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a3df5-135">For information about how the runtime uses version information to find a particular assembly, see [How the runtime locates assemblies](../../framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="a3df5-136">Derleme bilgilendirici sürümü</span><span class="sxs-lookup"><span data-stu-id="a3df5-136">Assembly informational version</span></span>  

<span data-ttu-id="a3df5-137">Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a3df5-137">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="a3df5-138">Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="a3df5-138">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="a3df5-139">Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-139">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="a3df5-140">Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="a3df5-140">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a3df5-141">Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür.</span><span class="sxs-lookup"><span data-stu-id="a3df5-141">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="a3df5-142">Bu uyarı zararsız olur.</span><span class="sxs-lookup"><span data-stu-id="a3df5-142">This warning is harmless.</span></span>  
  
<span data-ttu-id="a3df5-143">Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="a3df5-143">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a3df5-144">Bilgilendirici sürüm özniteliği hakkında daha fazla bilgi için bkz. [derleme özniteliklerini ayarlama](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="a3df5-144">For more information about the informational version attribute, see [Set assembly attributes](set-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3df5-145">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a3df5-145">See also</span></span>

- [<span data-ttu-id="a3df5-146">Çalışma zamanının derlemeleri nasıl konumlandırır</span><span class="sxs-lookup"><span data-stu-id="a3df5-146">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="a3df5-147">Uygulama yapılandırma</span><span class="sxs-lookup"><span data-stu-id="a3df5-147">Configure apps</span></span>](../../framework/configure-apps/index.md)
- [<span data-ttu-id="a3df5-148">Derleme özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="a3df5-148">Set assembly attributes</span></span>](set-attributes.md)
- [<span data-ttu-id="a3df5-149">.NET’te bütünleştirilmiş kodlar</span><span class="sxs-lookup"><span data-stu-id="a3df5-149">Assemblies in .NET</span></span>](index.md)
