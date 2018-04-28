---
title: WPF Güvenlik Stratejisi - Güvenlik Mühendisliği
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 79ab5b1a86ad94913750cfb3ec4fdc765db40282
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="wpf-security-strategy---security-engineering"></a><span data-ttu-id="c116c-102">WPF Güvenlik Stratejisi - Güvenlik Mühendisliği</span><span class="sxs-lookup"><span data-stu-id="c116c-102">WPF Security Strategy - Security Engineering</span></span>
<span data-ttu-id="c116c-103">Güvenilir bilgi işlem, güvenli kod üretim sağlamaya yönelik bir Microsoft girişimidir.</span><span class="sxs-lookup"><span data-stu-id="c116c-103">Trustworthy Computing is a Microsoft initiative for ensuring the production of secure code.</span></span> <span data-ttu-id="c116c-104">Güvenilir bilgi işlem Initiative önemli bir unsurdur [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c116c-104">A key element of the Trustworthy Computing initiative is the [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)].</span></span> <span data-ttu-id="c116c-105">[!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Standart mühendislik işlemler ile birlikte güvenli kod teslimini kolaylaştırmak için kullanılan bir mühendislik uygulamasıdır.</span><span class="sxs-lookup"><span data-stu-id="c116c-105">The [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] is an engineering practice that is used in conjunction with standard engineering processes to facilitate the delivery of secure code.</span></span> <span data-ttu-id="c116c-106">[!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] Formalization, measurability ve ek yapı ile en iyi yöntemler birleştiren on aşamadan oluşur dahil olmak üzere:</span><span class="sxs-lookup"><span data-stu-id="c116c-106">The [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] consists of ten phases that combine best practices with formalization, measurability, and additional structure, including:</span></span>  
  
-   <span data-ttu-id="c116c-107">Güvenlik tasarım çözümlemesi</span><span class="sxs-lookup"><span data-stu-id="c116c-107">Security design analysis</span></span>  
  
-   <span data-ttu-id="c116c-108">Aracı tabanlı kalite denetimleri</span><span class="sxs-lookup"><span data-stu-id="c116c-108">Tool-based quality checks</span></span>  
  
-   <span data-ttu-id="c116c-109">Sızma test etme</span><span class="sxs-lookup"><span data-stu-id="c116c-109">Penetration testing</span></span>  
  
-   <span data-ttu-id="c116c-110">Son güvenlik incelemesi</span><span class="sxs-lookup"><span data-stu-id="c116c-110">Final security review</span></span>  
  
-   <span data-ttu-id="c116c-111">POST yayın ürün güvenlik yönetimi</span><span class="sxs-lookup"><span data-stu-id="c116c-111">Post release product security management</span></span>  
  
## <a name="wpf-specifics"></a><span data-ttu-id="c116c-112">WPF özellikleri</span><span class="sxs-lookup"><span data-stu-id="c116c-112">WPF Specifics</span></span>  
 <span data-ttu-id="c116c-113">[!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] Mühendislik ekibi hem uygular ve genişleten [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], aşağıdaki unsur birleşimini içerir:</span><span class="sxs-lookup"><span data-stu-id="c116c-113">The [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] engineering team both applies and extends the [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], the combination of which includes the following key aspects:</span></span>  
  
 [<span data-ttu-id="c116c-114">Tehdit modelleme</span><span class="sxs-lookup"><span data-stu-id="c116c-114">Threat Modeling</span></span>](#threat_modeling)  
  
 [<span data-ttu-id="c116c-115">Güvenlik analizi ve düzenleme araçları</span><span class="sxs-lookup"><span data-stu-id="c116c-115">Security Analysis and Editing Tools</span></span>](#tools)  
  
 [<span data-ttu-id="c116c-116">Sınama teknikleri</span><span class="sxs-lookup"><span data-stu-id="c116c-116">Testing Techniques</span></span>](#techniques)  
  
 [<span data-ttu-id="c116c-117">Kritik kod Yönetimi</span><span class="sxs-lookup"><span data-stu-id="c116c-117">Critical Code Management</span></span>](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a><span data-ttu-id="c116c-118">Tehdit modelleme</span><span class="sxs-lookup"><span data-stu-id="c116c-118">Threat Modeling</span></span>  
 <span data-ttu-id="c116c-119">Tehdit modelleme bir bileşenidir çekirdek [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)]ve olası güvenlik açıklarını belirlemek için sistemin profilini için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c116c-119">Threat modeling is a core component of the [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], and is used to profile a system to determine potential security vulnerabilities.</span></span> <span data-ttu-id="c116c-120">Güvenlik açıkları tanımlandıktan sonra tehdit modelleme ayrıca uygun Azaltıcı Etkenler yerinde olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="c116c-120">Once the vulnerabilities are identified, threat modeling also ensures that appropriate mitigations are in place.</span></span>  
  
 <span data-ttu-id="c116c-121">Yüksek bir düzeyde tehdit modelleme market örnek olarak kullanarak aşağıdaki anahtar adımları içerir:</span><span class="sxs-lookup"><span data-stu-id="c116c-121">At a high level, threat modeling involves the following key steps by using a grocery store as an example:</span></span>  
  
1.  <span data-ttu-id="c116c-122">**Varlıklar tanımlayan**.</span><span class="sxs-lookup"><span data-stu-id="c116c-122">**Identifying Assets**.</span></span> <span data-ttu-id="c116c-123">Marketin varlıklar çalışanlar, güvenli, Yazar Kasa ve stok içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c116c-123">A grocery store's assets might include employees, a safe, cash registers, and inventory.</span></span>  
  
2.  <span data-ttu-id="c116c-124">**Giriş noktaları numaralandırma**.</span><span class="sxs-lookup"><span data-stu-id="c116c-124">**Enumerating Entry Points**.</span></span> <span data-ttu-id="c116c-125">Marketin giriş noktalarını ön ve arka kapı, windows, yükleme noktası ve havalandırma içerebilir.</span><span class="sxs-lookup"><span data-stu-id="c116c-125">A grocery store's entry points might include the front and back doors, windows, the loading dock, and air conditioning units.</span></span>  
  
3.  <span data-ttu-id="c116c-126">**Giriş noktaları kullanarak varlıklar saldırıları araştırma**.</span><span class="sxs-lookup"><span data-stu-id="c116c-126">**Investigating Attacks against Assets using Entry Points**.</span></span> <span data-ttu-id="c116c-127">Olası bir saldırı marketin hedef *güvenli* aracılığıyla varlığını *klima* klima; giriş noktası birimi aracılığıyla ve işyeri dışında çekebilir güvenli izin vermek için unscrewed olabilir Depo.</span><span class="sxs-lookup"><span data-stu-id="c116c-127">One possible attack could target a grocery store's *safe* asset through the *air conditioning* entry point; the air conditioning unit could be unscrewed to allow the safe to be pulled up through it and out of the store.</span></span>  
  
 <span data-ttu-id="c116c-128">Tehdit modelleme boyunca uygulanır [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] ve aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="c116c-128">Threat modeling is applied throughout [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] and includes the following:</span></span>  
  
-   <span data-ttu-id="c116c-129">Nasıl [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] ayrıştırıcı dosyalarını okur, karşılık gelen nesne modeli sınıfları ile metni eşleştirir ve fiili kodu oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c116c-129">How the [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] parser reads files, maps text to corresponding object model classes, and creates the actual code.</span></span>  
  
-   <span data-ttu-id="c116c-130">Nasıl pencere işleyicisi (hWnd) oluşturulur, iletileri gönderir ve bir pencere içeriğini çizmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c116c-130">How a window handle (hWnd) is created, sends messages, and is used for rendering the contents of a window.</span></span>  
  
-   <span data-ttu-id="c116c-131">Nasıl veri bağlama kaynakları alır ve sistemi ile etkileşim kurar.</span><span class="sxs-lookup"><span data-stu-id="c116c-131">How data binding obtains resources and interacts with the system.</span></span>  
  
 <span data-ttu-id="c116c-132">Bu tehdit modelleri geliştirme sürecinde tanımlayıcı güvenlik tasarım gereksinimleri ve tehdit Azaltıcı için önemlidir.</span><span class="sxs-lookup"><span data-stu-id="c116c-132">These threat models are important for identifying security design requirements and threat mitigations during the development process.</span></span>  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a><span data-ttu-id="c116c-133">Kaynak çözümleme ve düzenleme araçları</span><span class="sxs-lookup"><span data-stu-id="c116c-133">Source Analysis and Editing Tools</span></span>  
 <span data-ttu-id="c116c-134">Ek olarak el ile güvenlik kodu öğelerini gözden geçirmeniz [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] takım güvenlik açıklarını azaltmak için kaynak çözümleme ve ilişkili düzenlemeleri için çeşitli araçlar kullanır.</span><span class="sxs-lookup"><span data-stu-id="c116c-134">In addition to the manual security code review elements of the [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] team uses several tools for source analysis and associated edits to decrease security vulnerabilities.</span></span> <span data-ttu-id="c116c-135">Çok çeşitli kaynak araçları kullanılır ve şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="c116c-135">A wide range of source tools are used, and include the following:</span></span>  
  
-   <span data-ttu-id="c116c-136">**FXCop**: yönetilen kod devralma kurallarından güvenle yönetilmeyen kod ile birlikte çalışmak nasıl kod erişimi güvenliği kullanımı arasında değişen ortak güvenlik sorunlarını bulur.</span><span class="sxs-lookup"><span data-stu-id="c116c-136">**FXCop**: Finds common security issues in managed code ranging from inheritance rules to code access security usage to how to safely interoperate with unmanaged code.</span></span> <span data-ttu-id="c116c-137">Bkz: [FXCop](http://www.gotdotnet.com/team/fxcop/).</span><span class="sxs-lookup"><span data-stu-id="c116c-137">See [FXCop](http://www.gotdotnet.com/team/fxcop/).</span></span>  
  
-   <span data-ttu-id="c116c-138">**Önek/Prefast**: bulur Güvenlik Açıkları ve ortak güvenlik sorunlarını arabellek taşmaları gibi yönetilmeyen kodunda biçim dizesi sorunları ve hata denetimi.</span><span class="sxs-lookup"><span data-stu-id="c116c-138">**Prefix/Prefast**: Finds security vulnerabilities and common security issues in unmanaged code such as buffer overruns, format string issues, and error checking.</span></span>  
  
-   <span data-ttu-id="c116c-139">**API yasaklanan**: aramaları kaynak güvenlik sorunları gibi neden olduğu bilinen işlevleri yanlışlıkla kullanımını belirlemek için kodu `strcpy`.</span><span class="sxs-lookup"><span data-stu-id="c116c-139">**Banned APIs**: Searches source code to identify accidental usage of functions that are well-known for causing security issues, such as `strcpy`.</span></span> <span data-ttu-id="c116c-140">Tanımlandıktan sonra bu işlevler daha güvenli alternatifler ile değiştirilir.</span><span class="sxs-lookup"><span data-stu-id="c116c-140">Once identified, these functions are replaced with alternatives that are more security.</span></span>  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a><span data-ttu-id="c116c-141">Sınama teknikleri</span><span class="sxs-lookup"><span data-stu-id="c116c-141">Testing Techniques</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="c116c-142"> çeşitli güvenlik sınama dahil teknikleri kullanır:</span><span class="sxs-lookup"><span data-stu-id="c116c-142"> uses a variety of security testing techniques that include:</span></span>  
  
-   <span data-ttu-id="c116c-143">**Whitebox Sınama**: Sınayıcılar kaynak kodu görüntüleme ve yararlanma testleri oluşturma</span><span class="sxs-lookup"><span data-stu-id="c116c-143">**Whitebox Testing**: Testers view source code, and then build exploit tests</span></span>  
  
-   <span data-ttu-id="c116c-144">**Blackbox sınama**: sınayıcılar güvenlik yararlanan API ve özelliklerini inceleyerek bulmaya ve ürün saldırı deneyin.</span><span class="sxs-lookup"><span data-stu-id="c116c-144">**Blackbox Testing**: Testers try to find security exploits by examining the API and features, and then try to attack the product.</span></span>  
  
-   <span data-ttu-id="c116c-145">**Güvenlik sorunlarını gerileme diğer ürünleri**: uygun yerlerde ilgili ürünlerden güvenlik sorunları sınanır.</span><span class="sxs-lookup"><span data-stu-id="c116c-145">**Regressing Security Issues from other Products**: Where relevant, security issues from related products are tested.</span></span> <span data-ttu-id="c116c-146">Örneğin, yaklaşık altmış güvenlik sorunlarını çeşitlemelerini uygun [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] tanımlanır ve bunların uygulanabilirliğini çalıştı [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c116c-146">For example, appropriate variants of approximately sixty security issues for [!INCLUDE[TLA2#tla_ie](../../../includes/tla2sharptla-ie-md.md)] have been identified and tried for their applicability to [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
-   <span data-ttu-id="c116c-147">**Dosya karıştırma aracılığıyla sızma testi tabanlı Araçları**: Dosya karıştırma olan bir dosya okuyucu yararlanılması girişleri çeşitli aralığı girdisini.</span><span class="sxs-lookup"><span data-stu-id="c116c-147">**Tools-Based Penetration Testing through File Fuzzing**: File fuzzing is the exploitation of a file reader's input range through a variety of inputs.</span></span> <span data-ttu-id="c116c-148">Bir örnekte [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] burada bu yöntem resim kod çözme hatası olup olmadığını denetlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c116c-148">One example in [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] where this technique is used is to check for failure in image decoding code.</span></span>  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a><span data-ttu-id="c116c-149">Kritik kod Yönetimi</span><span class="sxs-lookup"><span data-stu-id="c116c-149">Critical Code Management</span></span>  
 <span data-ttu-id="c116c-150">İçin [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] işaretleme ve ayrıcalıkları artırılan güvenlik açısından kritik kod izleme için .NET Framework Destek kullanarak, bir güvenlik sandbox oluşturur (bkz **güvenlik açısından kritik Metodoloji** içinde [WPF Güvenlik stratejisi - Platform güvenliği](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).</span><span class="sxs-lookup"><span data-stu-id="c116c-150">For [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)], [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] builds a security sandbox by using .NET Framework support for marking and tracking security-critical code that elevates privileges (see **Security-Critical Methodology** in [WPF Security Strategy - Platform Security](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)).</span></span> <span data-ttu-id="c116c-151">Güvenlik açısından kritik koda yüksek güvenlik kalite gereksinimlerini verildiğinde, bu tür kod ek bir kaynak yönetimi denetim ve güvenlik denetim düzeyi alır.</span><span class="sxs-lookup"><span data-stu-id="c116c-151">Given the high security quality requirements on security critical code, such code receives an additional level of source management control and security audit.</span></span> <span data-ttu-id="c116c-152">Yaklaşık 5 ile % 10, [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] adanmış bir gözden geçirme ekibi tarafından gözden güvenlik açısından kritik kod oluşur.</span><span class="sxs-lookup"><span data-stu-id="c116c-152">Approximately 5% to 10% of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] consists of security-critical code, which is reviewed by a dedicated reviewing team.</span></span> <span data-ttu-id="c116c-153">Kaynak kodu ve iade etme işlemi, güvenlik açısından kritik kodu izleme ve kritik her varlık (yani kritik kod içeren bir yöntem), oturum durumu devre dışı eşleme tarafından yönetilir.</span><span class="sxs-lookup"><span data-stu-id="c116c-153">The source code and check-in process is managed by tracking security critical code and mapping each critical entity (i.e. a method that contains critical code) to its sign off state.</span></span> <span data-ttu-id="c116c-154">Oturum durumu devre dışı bir veya daha fazla gözden geçirenlerin adlarını içerir.</span><span class="sxs-lookup"><span data-stu-id="c116c-154">The sign off state includes the names of one or more reviewers.</span></span> <span data-ttu-id="c116c-155">Her günlük yapılandırmanın [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] kritik kod onaylanmamış değişiklikleri denetlemek için önceki derlemelerinde karşılaştırır.</span><span class="sxs-lookup"><span data-stu-id="c116c-155">Each daily build of [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] compares the critical code to that in previous builds to check for unapproved changes.</span></span> <span data-ttu-id="c116c-156">Mühendisin kritik kod gözden geçirme ekibinin onayı olmadan değiştirirse, tanımlanır ve hemen düzeltilir.</span><span class="sxs-lookup"><span data-stu-id="c116c-156">If an engineer modifies critical code without approval from the reviewing team, it is identified and fixed immediately.</span></span> <span data-ttu-id="c116c-157">Bu işlem üzerinden uygulama ve Bakım scrutiny özellikle yüksek bir düzeyde sağlar [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] korumalı alan kodu.</span><span class="sxs-lookup"><span data-stu-id="c116c-157">This process enables the application and maintenance of an especially high level of scrutiny over [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] sandbox code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c116c-158">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c116c-158">See Also</span></span>  
 [<span data-ttu-id="c116c-159">Güvenlik</span><span class="sxs-lookup"><span data-stu-id="c116c-159">Security</span></span>](../../../docs/framework/wpf/security-wpf.md)  
 [<span data-ttu-id="c116c-160">WPF Kısmi Güven Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c116c-160">WPF Partial Trust Security</span></span>](../../../docs/framework/wpf/wpf-partial-trust-security.md)  
 [<span data-ttu-id="c116c-161">WPF Güvenlik Stratejisi - Platform Güvenliği</span><span class="sxs-lookup"><span data-stu-id="c116c-161">WPF Security Strategy - Platform Security</span></span>](../../../docs/framework/wpf/wpf-security-strategy-platform-security.md)  
 [<span data-ttu-id="c116c-162">Güvenilir bilgi işlem</span><span class="sxs-lookup"><span data-stu-id="c116c-162">Trustworthy Computing</span></span>](http://www.microsoft.com/mscorp/twc/default.mspx)  
 [<span data-ttu-id="c116c-163">Uygulama iş parçacığı modelleme</span><span class="sxs-lookup"><span data-stu-id="c116c-163">Application Threat Modeling</span></span>](http://msdn.microsoft.com/security/securecode/threatmodeling/acetm/)  
 [<span data-ttu-id="c116c-164">Güvenlik yönergeleri: .NET Framework 2.0</span><span class="sxs-lookup"><span data-stu-id="c116c-164">Security Guidelines: .NET Framework 2.0</span></span>](http://msdn.microsoft.com/library/default.asp?url=/library/dnpag2/html/PAGGuidelines0003.asp)
