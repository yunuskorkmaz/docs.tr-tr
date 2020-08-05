---
title: .NET için güvenli kodlama yönergeleri
description: Birlikte çalışmak için tasarım kodu. Kötü amaçlı kodun verilere erişmesini veya diğer eylemleri gerçekleştirmesini önlemeye yardımcı olmak için NET uygulama izinleri ve diğer zorlama.
ms.date: 07/15/2020
helpviewer_keywords:
- managed wrapper to native code implementation
- secure coding
- reusable components
- library code that exposes protected resources
- code, security
- code security
- secure coding, options
- components [.NET], security
- code security, options
- security-neutral code
- security [.NET], coding guidelines
ms.assetid: 4f882d94-262b-4494-b0a6-ba9ba1f5f177
ms.openlocfilehash: a05e0cec2814be88ac835d05601d5cf5f66383c3
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555962"
---
# <a name="secure-coding-guidelines"></a><span data-ttu-id="e9162-103">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e9162-103">Secure coding guidelines</span></span>

<span data-ttu-id="e9162-104">Çoğu uygulama kodu yalnızca .NET tarafından uygulanan altyapıyı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e9162-104">Most application code can simply use the infrastructure implemented by .NET.</span></span> <span data-ttu-id="e9162-105">Bazı durumlarda, güvenlik sistemini genişleterek veya yeni geçici yöntemler kullanılarak oluşturulan uygulamaya özgü ek güvenlik gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-105">In some cases, additional application-specific security is required, built either by extending the security system or by using new ad hoc methods.</span></span>

<span data-ttu-id="e9162-106">Kodunuzda .NET tarafından zorlanan izinleri ve diğer uygulamayı kullanarak, kötü amaçlı kodun, istemediğiniz bilgilere erişmesini veya başka istenmeyen eylemler gerçekleştirmesini istemediğiniz bilgilere erişmesini önlemeye yönelik engelleri almalısınız.</span><span class="sxs-lookup"><span data-stu-id="e9162-106">Using .NET enforced permissions and other enforcement in your code, you should erect barriers to prevent malicious code from accessing information that you don't want it to have or performing other undesirable actions.</span></span> <span data-ttu-id="e9162-107">Ayrıca, güvenilen kod kullanarak beklenen tüm senaryolarda güvenlik ve kullanılabilirlik arasında bir denge oluşturmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-107">Additionally, you must strike a balance between security and usability in all the expected scenarios using trusted code.</span></span>

<span data-ttu-id="e9162-108">Bu genel bakışta kodun güvenlik sistemiyle çalışmak için tasarlanma yöntemi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e9162-108">This overview describes the different ways code can be designed to work with the security system.</span></span>

## <a name="securing-resource-access"></a><span data-ttu-id="e9162-109">Kaynak erişiminin güvenliğini sağlama</span><span class="sxs-lookup"><span data-stu-id="e9162-109">Securing resource access</span></span>

<span data-ttu-id="e9162-110">Kodunuzu tasarlarken ve yazarken, özellikle de bilinmeyen kaynak kodu kullanırken veya çağırılırken, kodun kaynaklarla olan erişimini korumanız ve sınırlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-110">When designing and writing your code, you need to protect and limit the access that code has to resources, especially when using or invoking code of unknown origin.</span></span> <span data-ttu-id="e9162-111">Bu nedenle, kodunuzun güvende olduğundan emin olmak için aşağıdaki teknikleri aklınızda bulundurun:</span><span class="sxs-lookup"><span data-stu-id="e9162-111">So, keep in mind the following techniques to ensure your code is secure:</span></span>

- <span data-ttu-id="e9162-112">Kod erişim güvenliği (CAS) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-112">Do not use Code Access Security (CAS).</span></span>

- <span data-ttu-id="e9162-113">Kısmi güvenilir kod kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-113">Do not use partial trusted code.</span></span>

- <span data-ttu-id="e9162-114">[Allowpartiallytrustedcaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) özniteliğini (aptca) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-114">Do not use the [AllowPartiallyTrustedCaller](xref:System.Security.AllowPartiallyTrustedCallersAttribute) attribute (APTCA).</span></span>

- <span data-ttu-id="e9162-115">.NET uzaktan Iletişim kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-115">Do not use .NET Remoting.</span></span>

- <span data-ttu-id="e9162-116">Dağıtılmış bileşen nesne modeli (DCOM) kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-116">Do not use Distributed Component Object Model (DCOM).</span></span>

- <span data-ttu-id="e9162-117">İkili formatlayıcıları kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-117">Do not use binary formatters.</span></span>

<span data-ttu-id="e9162-118">Kod erişimi güvenliği ve güvenlik açısından saydam kod, kısmen güvenilen kod içeren bir güvenlik sınırı olarak desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="e9162-118">Code Access Security and Security-Transparent Code are not supported as a security boundary with partially trusted code.</span></span> <span data-ttu-id="e9162-119">Bilinmeyen kaynaklardan gelen kodların, alternatif güvenlik önlemleri alınmadan yüklenmesi ve yürütülmesi önerilmez.</span><span class="sxs-lookup"><span data-stu-id="e9162-119">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="e9162-120">Alternatif güvenlik ölçüleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="e9162-120">The alternative security measures are:</span></span>

- <span data-ttu-id="e9162-121">Sanallaştırma</span><span class="sxs-lookup"><span data-stu-id="e9162-121">Virtualization</span></span>

- <span data-ttu-id="e9162-122">AppContainers</span><span class="sxs-lookup"><span data-stu-id="e9162-122">AppContainers</span></span>

- <span data-ttu-id="e9162-123">İşletim sistemi (OS) kullanıcıları ve izinleri</span><span class="sxs-lookup"><span data-stu-id="e9162-123">Operating system (OS) users and permissions</span></span>

- <span data-ttu-id="e9162-124">Hyper-V kapsayıcıları</span><span class="sxs-lookup"><span data-stu-id="e9162-124">Hyper-V containers</span></span>

## <a name="security-neutral-code"></a><span data-ttu-id="e9162-125">Güvenlikle bağımsız kod</span><span class="sxs-lookup"><span data-stu-id="e9162-125">Security-neutral code</span></span>

<span data-ttu-id="e9162-126">Güvenlik için bağımsız kod, güvenlik sistemiyle hiçbir şey yapmaz.</span><span class="sxs-lookup"><span data-stu-id="e9162-126">Security-neutral code does nothing explicit with the security system.</span></span> <span data-ttu-id="e9162-127">Aldığı izinlerle çalışır.</span><span class="sxs-lookup"><span data-stu-id="e9162-127">It runs with whatever permissions it receives.</span></span> <span data-ttu-id="e9162-128">Korunan işlemlerle ilişkili güvenlik özel durumlarını (örneğin, dosya ve ağ kullanımı gibi) yakalayamayan uygulamalar işlenmeyen bir özel durumla sonuçlansa da, güvenlikle bağımsız kod yine de .NET 'teki güvenlik teknolojilerinden faydalanır.</span><span class="sxs-lookup"><span data-stu-id="e9162-128">Although applications that fail to catch security exceptions associated with protected operations (such as using files, networking, and so on) can result in an unhandled exception, security-neutral code still takes advantage of the security technologies in .NET.</span></span>

<span data-ttu-id="e9162-129">Güvenlikle bağımsız bir kitaplıkta anlamanız gereken özel özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="e9162-129">A security-neutral library has special characteristics that you should understand.</span></span> <span data-ttu-id="e9162-130">Kitaplığınızın dosyaları kullanan veya yönetilmeyen kodu çağıran API öğeleri sağladığını varsayalım.</span><span class="sxs-lookup"><span data-stu-id="e9162-130">Suppose your library provides API elements that use files or call unmanaged code.</span></span> <span data-ttu-id="e9162-131">Kodunuzun karşılık gelen izni yoksa, açıklanan şekilde çalışmaz.</span><span class="sxs-lookup"><span data-stu-id="e9162-131">If your code doesn't have the corresponding permission, it won't run as described.</span></span> <span data-ttu-id="e9162-132">Ancak, kod izne sahip olsa bile, çağıran herhangi bir uygulama kodunun çalışması için aynı izne sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-132">However, even if the code has the permission, any application code that calls it must have the same permission in order to work.</span></span> <span data-ttu-id="e9162-133">Çağıran kodun doğru izni yoksa, <xref:System.Security.SecurityException> kod erişimi güvenlik yığını ilermasının sonucu olarak bir görünür.</span><span class="sxs-lookup"><span data-stu-id="e9162-133">If the calling code doesn't have the right permission, a <xref:System.Security.SecurityException> appears as a result of the code access security stack walk.</span></span>

## <a name="application-code-that-isnt-a-reusable-component"></a><span data-ttu-id="e9162-134">Yeniden kullanılabilir bir bileşen olmayan uygulama kodu</span><span class="sxs-lookup"><span data-stu-id="e9162-134">Application code that isn't a reusable component</span></span>

<span data-ttu-id="e9162-135">Kodunuz, başka kod tarafından çağrılmayan bir uygulamanın parçasıysa, güvenlik basittir ve özel kodlama gerekli olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="e9162-135">If your code is part of an application that won't be called by other code, security is simple and special coding might not be required.</span></span> <span data-ttu-id="e9162-136">Ancak, kötü amaçlı kodun kodunuzun çağıraolabileceğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-136">However, remember that malicious code can call your code.</span></span> <span data-ttu-id="e9162-137">Kod erişimi güvenliği kötü amaçlı kodun kaynaklara erişmesini durdurmasına karşın, bu kod, gizli bilgiler içerebilen alanlarınızın veya özelliklerinin değerlerini yine de okuyabilir.</span><span class="sxs-lookup"><span data-stu-id="e9162-137">While code access security might stop malicious code from accessing resources, such code could still read values of your fields or properties that might contain sensitive information.</span></span>

<span data-ttu-id="e9162-138">Ayrıca, kodunuz Internet veya diğer güvenilir olmayan kaynaklardan Kullanıcı girişini kabul ediyorsa kötü amaçlı giriş konusunda dikkatli olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-138">Additionally, if your code accepts user input from the Internet or other unreliable sources, you must be careful about malicious input.</span></span>

## <a name="managed-wrapper-to-native-code-implementation"></a><span data-ttu-id="e9162-139">Yerel kod uygulamasına yönetilen sarmalayıcı</span><span class="sxs-lookup"><span data-stu-id="e9162-139">Managed wrapper to native code implementation</span></span>

<span data-ttu-id="e9162-140">Genellikle bu senaryoda, bazı yararlı işlevler, yönetilen kod için kullanılabilir hale getirmek istediğiniz yerel kodda uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e9162-140">Typically in this scenario, some useful functionality is implemented in native code that you want to make available to managed code.</span></span> <span data-ttu-id="e9162-141">Yönetilen sarmalayıcılardan, platform çağırma veya COM birlikte çalışabilirliği kullanılarak kolayca yazılabilir.</span><span class="sxs-lookup"><span data-stu-id="e9162-141">Managed wrappers are easy to write using either platform invoke or COM interop.</span></span> <span data-ttu-id="e9162-142">Ancak bunu yaparsanız, sarmalayıcılarınızın başarılı olması için yönetilmeyen kod haklarına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e9162-142">However, if you do this, callers of your wrappers must have unmanaged code rights in order to succeed.</span></span> <span data-ttu-id="e9162-143">Varsayılan ilke altında bu, bir intranet veya Internet 'ten indirilen kodun sarmalayıcılarla birlikte çalışacağı anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9162-143">Under default policy, this means that code downloaded from an intranet or the Internet won't work with the wrappers.</span></span>

<span data-ttu-id="e9162-144">Bu sarmalayıcıları kullanan tüm uygulamalara yönetilmeyen kod hakları vermek yerine, bu hakları yalnızca sarmalayıcı koduna vermek daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="e9162-144">Instead of giving unmanaged code rights to all applications that use these wrappers, it's better to give these rights only to the wrapper code.</span></span> <span data-ttu-id="e9162-145">Temeldeki işlevsellik hiçbir kaynak açığa çıkardığı ve uygulamanın aynı şekilde güvende olması halinde, sarmalayıcının yalnızca kendi haklarını sağlaması gerekir, bu da herhangi bir kodun bunun üzerinde çağrı yapmasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e9162-145">If the underlying functionality exposes no resources and the implementation is likewise safe, the wrapper only needs to assert its rights, which enables any code to call through it.</span></span> <span data-ttu-id="e9162-146">Kaynaklar dahil edildiğinde, güvenlik kodlaması, sonraki bölümde açıklanan kitaplık kodu durumuyla aynı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e9162-146">When resources are involved, security coding should be the same as the library code case described in the next section.</span></span> <span data-ttu-id="e9162-147">Sarmalayıcı, bu kaynaklara çağıranları ortaya çıkardığından, yerel kodun güvenliğine dikkat etmeniz gerekir ve sarmalayıcı sorumluluğunda olur.</span><span class="sxs-lookup"><span data-stu-id="e9162-147">Because the wrapper is potentially exposing callers to these resources, careful verification of the safety of the native code is necessary and is the wrapper's responsibility.</span></span>

## <a name="library-code-that-exposes-protected-resources"></a><span data-ttu-id="e9162-148">Korumalı kaynakları açığa çıkaran kitaplık kodu</span><span class="sxs-lookup"><span data-stu-id="e9162-148">Library code that exposes protected resources</span></span>

<span data-ttu-id="e9162-149">Aşağıdaki yaklaşım, güvenlik kodlaması için en güçlü ve potansiyel olarak tehlikeli (yanlış yapılmasa) olabilir: kitaplığınız, .NET sınıflarının kullandıkları kaynaklar için izinleri zorladığından, diğer kodun başka bir şekilde kullanılamayan belirli kaynaklara erişmesi için bir arabirim görevi görür.</span><span class="sxs-lookup"><span data-stu-id="e9162-149">The following approach is the most powerful and hence potentially dangerous (if done incorrectly) for security coding: your library serves as an interface for other code to access certain resources that aren't otherwise available, just as the .NET classes enforce permissions for the resources they use.</span></span> <span data-ttu-id="e9162-150">Bir kaynağı kullanıma sunduğunuzdan, kodunuzun öncelikle kaynağa uygun olan izni talep etmelidir (yani, bir güvenlik denetimi gerçekleştirmesi gerekir) ve tipik olarak gerçek işlemi gerçekleştirmek için haklarını onaylayın.</span><span class="sxs-lookup"><span data-stu-id="e9162-150">Wherever you expose a resource, your code must first demand the permission appropriate to the resource (that is, it must perform a security check) and then typically assert its rights to perform the actual operation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9162-151">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9162-151">See also</span></span>

- [<span data-ttu-id="e9162-152">Durum Verilerinin Güvenliğini Sağlama</span><span class="sxs-lookup"><span data-stu-id="e9162-152">Securing State Data</span></span>](securing-state-data.md)
- [<span data-ttu-id="e9162-153">Güvenlik ve Kullanıcı Girdisi</span><span class="sxs-lookup"><span data-stu-id="e9162-153">Security and User Input</span></span>](security-and-user-input.md)
- [<span data-ttu-id="e9162-154">Güvenlik ve Yarış Durumları</span><span class="sxs-lookup"><span data-stu-id="e9162-154">Security and Race Conditions</span></span>](security-and-race-conditions.md)
- [<span data-ttu-id="e9162-155">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e9162-155">Security and On-the-Fly Code Generation</span></span>](security-and-on-the-fly-code-generation.md)
- [<span data-ttu-id="e9162-156">Rol Tabanlı Güvenlik</span><span class="sxs-lookup"><span data-stu-id="e9162-156">Role-Based Security</span></span>](role-based-security.md)
- [<span data-ttu-id="e9162-157">ASP.NET Core güvenliği</span><span class="sxs-lookup"><span data-stu-id="e9162-157">ASP.NET Core Security</span></span>](/aspnet/core/security/)
