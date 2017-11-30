---
title: "Derleme Sürümü Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- informational versions
- version numbers, assemblies
- assemblies [.NET Framework], versioning
- resolving assembly binding requests
- versioning, assemblies
ms.assetid: 775ad4fb-914f-453c-98ef-ce1089b6f903
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a956e0c4521e4a1079b331868e811e68af2e710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="assembly-versioning"></a><span data-ttu-id="6e22a-102">Derleme Sürümü Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6e22a-102">Assembly Versioning</span></span>
<span data-ttu-id="6e22a-103">Ortak dil çalışma zamanını kullanan tüm derlemelerin sürüm oluşturma işlemi, derleme düzeyinde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-103">All versioning of assemblies that use the common language runtime is done at the assembly level.</span></span> <span data-ttu-id="6e22a-104">Bir derlemenin belirli sürümü ve bağımlı derlemelerin sürümleri, derlemenin bildirimine kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-104">The specific version of an assembly and the versions of dependent assemblies are recorded in the assembly's manifest.</span></span> <span data-ttu-id="6e22a-105">Çalışma zamanı için varsayılan sürüm ilkesi, yapılandırma dosyalarındaki sürüm ilkelerinde açıkça geçersiz kılınmadığı sürece (uygulama yapılandırma dosyası, yayımcı ilke dosyası ve bilgisayar yöneticisinin yapılandırma dosyası) uygulamaların yalnızca yapılandırıldığı ve test edildiği sürümlerle çalışmasıdır.</span><span class="sxs-lookup"><span data-stu-id="6e22a-105">The default version policy for the runtime is that applications run only with the versions they were built and tested with, unless overridden by explicit version policy in configuration files (the application configuration file, the publisher policy file, and the computer's administrator configuration file).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e22a-106">Sürüm oluşturma yalnızca tanımlayıcı ada sahip derlemeler üzerinde yapılır.</span><span class="sxs-lookup"><span data-stu-id="6e22a-106">Versioning is done only on assemblies with strong names.</span></span>  
  
 <span data-ttu-id="6e22a-107">Çalışma zamanı, bir derleme bağlama isteğini çözmek için birkaç adım gerçekleştirir:</span><span class="sxs-lookup"><span data-stu-id="6e22a-107">The runtime performs several steps to resolve an assembly binding request:</span></span>  
  
1.  <span data-ttu-id="6e22a-108">Bağlanacak derlemenin sürümünü belirlemek için orijinal derleme başvurusunu denetler.</span><span class="sxs-lookup"><span data-stu-id="6e22a-108">Checks the original assembly reference to determine the version of the assembly to be bound.</span></span>  
  
2.  <span data-ttu-id="6e22a-109">Sürüm ilkesini uygulamak için uygulanabilir tüm yapılandırma dosyalarını denetler.</span><span class="sxs-lookup"><span data-stu-id="6e22a-109">Checks for all applicable configuration files to apply version policy.</span></span>  
  
3.  <span data-ttu-id="6e22a-110">Orijinal derleme başvurusundan ve yapılandırma dosyalarında belirtilen yeniden yönlendirmelerden doğru derlemeyi belirler ve çağıran derlemeye bağlanacak olan sürümü belirler.</span><span class="sxs-lookup"><span data-stu-id="6e22a-110">Determines the correct assembly from the original assembly reference and any redirection specified in the configuration files, and determines the version that should be bound to the calling assembly.</span></span>  
  
4.  <span data-ttu-id="6e22a-111">Genel derleme önbelleği denetler, olarak kullanılabilecek kod temeli yapılandırma dosyalarını ve uygulamanın dizin ve alt dizinleri algılama kurallarını kullanarak içinde açıklanan sonra denetimleri içinde belirtilen [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-111">Checks the global assembly cache, codebases specified in configuration files, and then checks the application's directory and subdirectories using the probing rules explained in [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
 <span data-ttu-id="6e22a-112">Aşağıdaki resim bu adımları gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-112">The following illustration shows these steps.</span></span>  
  
 <span data-ttu-id="6e22a-113">![.Assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span><span class="sxs-lookup"><span data-stu-id="6e22a-113">![.assembly extern myAssembly](../../../docs/framework/app-domains/media/versioningover.gif "versioningover")</span></span>  
<span data-ttu-id="6e22a-114">Bir derleme bağlama isteğinin çözülmesi</span><span class="sxs-lookup"><span data-stu-id="6e22a-114">Resolving an assembly binding request</span></span>  
  
 <span data-ttu-id="6e22a-115">Uygulamaları yapılandırma hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-115">For more information about configuring applications, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="6e22a-116">Bağlama ilkesi hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-116">For more information about binding policy, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
## <a name="version-information"></a><span data-ttu-id="6e22a-117">Sürüm Bilgileri</span><span class="sxs-lookup"><span data-stu-id="6e22a-117">Version Information</span></span>  
 <span data-ttu-id="6e22a-118">Her derlemenin sürüm bilgisini ifade etmek için iki farklı yolu vardır:</span><span class="sxs-lookup"><span data-stu-id="6e22a-118">Each assembly has two distinct ways of expressing version information:</span></span>  
  
-   <span data-ttu-id="6e22a-119">Derleme adı ve kültür bilgisiyle birlikte derlemenin kimliğinin bir parçası olan derleme sürüm numarası.</span><span class="sxs-lookup"><span data-stu-id="6e22a-119">The assembly's version number, which, together with the assembly name and culture information, is part of the assembly's identity.</span></span> <span data-ttu-id="6e22a-120">Bu numara çalışma zamanı tarafından sürüm ilkesini uygulamak için kullanılır ve çalışma zamanında tür çözümleme işleminde önemli bir rol oynar.</span><span class="sxs-lookup"><span data-stu-id="6e22a-120">This number is used by the runtime to enforce version policy and plays a key part in the type resolution process at run time.</span></span>  
  
-   <span data-ttu-id="6e22a-121">Sadece bilgi amaçlı olarak eklenen ek sürüm bilgilerini temsil eden bir dize olan bilgilendirme sürümü.</span><span class="sxs-lookup"><span data-stu-id="6e22a-121">An informational version, which is a string that represents additional version information included for informational purposes only.</span></span>  
  
### <a name="assembly-version-number"></a><span data-ttu-id="6e22a-122">Derleme Sürüm Numarası</span><span class="sxs-lookup"><span data-stu-id="6e22a-122">Assembly Version Number</span></span>  
 <span data-ttu-id="6e22a-123">Her derleme, kimliğinin bir parçası olarak bir sürüm numarasına sahiptir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-123">Each assembly has a version number as part of its identity.</span></span> <span data-ttu-id="6e22a-124">Bu nedenle, sürüm numarası farklı olan iki derleme, çalışma zamanı tarafından tamamen farklı derlemeler olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-124">As such, two assemblies that differ by version number are considered by the runtime to be completely different assemblies.</span></span> <span data-ttu-id="6e22a-125">Bu sürüm numarası, fiziksel olarak aşağıdaki biçime sahip dört bölümlü bir dize olarak temsil edilir:</span><span class="sxs-lookup"><span data-stu-id="6e22a-125">This version number is physically represented as a four-part string with the following format:</span></span>  
  
 <span data-ttu-id="6e22a-126">\<*ana sürüm*>.\< *alt sürüm*>.\< *yapı numarası*>.\< *düzeltme*></span><span class="sxs-lookup"><span data-stu-id="6e22a-126">\<*major version*>.\<*minor version*>.\<*build number*>.\<*revision*></span></span>  
  
 <span data-ttu-id="6e22a-127">Örneğin, 1.5.1254.0 sürümü ana sürüm olarak 1, alt sürüm olarak 5, yapı numarası olarak 1254 ve düzeltme numarası olarak da 0 belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-127">For example, version 1.5.1254.0 indicates 1 as the major version, 5 as the minor version, 1254 as the build number, and 0 as the revision number.</span></span>  
  
 <span data-ttu-id="6e22a-128">Sürüm numarası, derleme adı ve ortak anahtarı içeren kimlik bilgisinin yanı sıra ilişkiler hakkında bilgi ve uygulamayla bağlı olan diğer derlemelerin kimlikleriyle birlikte derleme bildiriminde saklanır.</span><span class="sxs-lookup"><span data-stu-id="6e22a-128">The version number is stored in the assembly manifest along with other identity information, including the assembly name and public key, as well as information on relationships and identities of other assemblies connected with the application.</span></span>  
  
 <span data-ttu-id="6e22a-129">Bir derleme yapılandırıldığında, geliştirme aracı derleme bildiriminde atıf yapılan her derleme için bağımlılık bilgisi kaydeder.</span><span class="sxs-lookup"><span data-stu-id="6e22a-129">When an assembly is built, the development tool records dependency information for each assembly that is referenced in the assembly manifest.</span></span> <span data-ttu-id="6e22a-130">Çalışma zamanı bu sürüm numaralarını bir yönetici, uygulama veya yayımcı tarafından ayarlanan yapılandırma bilgisiyle birlikte kullanarak başvurulan bir derlemenin uygun sürümünü yükler.</span><span class="sxs-lookup"><span data-stu-id="6e22a-130">The runtime uses these version numbers, in conjunction with configuration information set by an administrator, an application, or a publisher, to load the proper version of a referenced assembly.</span></span>  
  
 <span data-ttu-id="6e22a-131">Çalışma zamanı, normal ve tanımlayıcı ada sahip derlemeleri sürüm oluşturma amacıyla ayırt eder.</span><span class="sxs-lookup"><span data-stu-id="6e22a-131">The runtime distinguishes between regular and strong-named assemblies for the purposes of versioning.</span></span> <span data-ttu-id="6e22a-132">Sürüm denetleme yalnızca tanımlayıcı ada sahip derlemelerde gerçekleşir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-132">Version checking only occurs with strong-named assemblies.</span></span>  
  
 <span data-ttu-id="6e22a-133">Sürüm bağlama ilkeleri belirtme hakkında daha fazla bilgi için bkz: [yapılandırma uygulamaları](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-133">For information about specifying version binding policies, see [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span> <span data-ttu-id="6e22a-134">Sürüm bilgileri çalışma zamanı belirli bir derleme bulmak için nasıl kullandığı hakkında daha fazla bilgi için bkz: [nasıl çalışma zamanı bulur derlemeleri](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-134">For information about how the runtime uses version information to find a particular assembly, see [How the Runtime Locates Assemblies](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md).</span></span>  
  
### <a name="assembly-informational-version"></a><span data-ttu-id="6e22a-135">Derleme Bilgilendirme Sürümü</span><span class="sxs-lookup"><span data-stu-id="6e22a-135">Assembly Informational Version</span></span>  
 <span data-ttu-id="6e22a-136">Bilgilendirme sürümü, bir derlemeye yalnızca bilgilendirme amacıyla ek sürüm bilgileri ekleyen bir dizedir; bu bilgi çalışma zamanında kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6e22a-136">The informational version is a string that attaches additional version information to an assembly for informational purposes only; this information is not used at run time.</span></span> <span data-ttu-id="6e22a-137">Metin tabanlı bilgilendirme sürümü, ürünün pazarlama belgelerine, paketlemesine veya ürün adına karşılık gelir ve çalışma zamanı tarafından kullanılmaz.</span><span class="sxs-lookup"><span data-stu-id="6e22a-137">The text-based informational version corresponds to the product's marketing literature, packaging, or product name and is not used by the runtime.</span></span> <span data-ttu-id="6e22a-138">Örneğin, bir bilgilendirme sürümü "Ortak Dil Çalışma Zamanı sürüm 1.0" veya "NET Control SP 2" olabilir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-138">For example, an informational version could be "Common Language Runtime version 1.0" or "NET Control SP 2".</span></span> <span data-ttu-id="6e22a-139">Microsoft Windows'daki dosya özellikleri iletişim kutusunun Sürüm sekmesinde, bu bilgi "Ürün Sürümü" öğesinde görünür.</span><span class="sxs-lookup"><span data-stu-id="6e22a-139">On the Version tab of the file properties dialog in Microsoft Windows, this information appears in the item "Product Version".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e22a-140">Herhangi bir metni ayarlayabilseniz de dize derleme sürüm numarası tarafından kullanılan biçimde değilse veya o biçimdeyse ancak jokerler içeriyorsa derleme esnasında bir uyarı iletisi görünür.</span><span class="sxs-lookup"><span data-stu-id="6e22a-140">Although you can specify any text, a warning message appears on compilation if the string is not in the format used by the assembly version number, or if it is in that format but contains wildcards.</span></span> <span data-ttu-id="6e22a-141">Uyarı zararsız budur.</span><span class="sxs-lookup"><span data-stu-id="6e22a-141">This warning is harmless.</span></span>  
  
 <span data-ttu-id="6e22a-142">Bilgilendirme sürümü <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType> özel özniteliği kullanılarak temsil edilir.</span><span class="sxs-lookup"><span data-stu-id="6e22a-142">The informational version is represented using the custom attribute <xref:System.Reflection.AssemblyInformationalVersionAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e22a-143">Bilgilendirme sürümü özniteliği hakkında daha fazla bilgi için bkz: [ayarı derleme özniteliklerinin](../../../docs/framework/app-domains/set-assembly-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6e22a-143">For more information about the informational version attribute, see [Setting Assembly Attributes](../../../docs/framework/app-domains/set-assembly-attributes.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e22a-144">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e22a-144">See Also</span></span>  
 [<span data-ttu-id="6e22a-145">Çalışma zamanı derlemeleri nasıl bulur</span><span class="sxs-lookup"><span data-stu-id="6e22a-145">How the Runtime Locates Assemblies</span></span>](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [<span data-ttu-id="6e22a-146">Uygulamaları yapılandırma</span><span class="sxs-lookup"><span data-stu-id="6e22a-146">Configuring Apps</span></span>](../../../docs/framework/configure-apps/index.md)  
 [<span data-ttu-id="6e22a-147">Derleme özniteliklerini ayarlama</span><span class="sxs-lookup"><span data-stu-id="6e22a-147">Setting Assembly Attributes</span></span>](../../../docs/framework/app-domains/set-assembly-attributes.md)  
 [<span data-ttu-id="6e22a-148">Ortak dil çalışma zamanı derlemeleri</span><span class="sxs-lookup"><span data-stu-id="6e22a-148">Assemblies in the Common Language Runtime</span></span>](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)
