---
title: "Kısmen Güvenilen Koddan Kitaplıkları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security [.NET Framework], partially trusted code
- partially trusted code
- partial trust
- AllowPartiallyTrustedCallersAttribute attribute
- code access security, partially trusted code
- APTCA
ms.assetid: dd66cd4c-b087-415f-9c3e-94e3a1835f74
caps.latest.revision: "25"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7a452370df7c18f3e3f0190a14979099152485f9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="using-libraries-from-partially-trusted-code"></a><span data-ttu-id="b08d7-102">Kısmen Güvenilen Koddan Kitaplıkları Kullanma</span><span class="sxs-lookup"><span data-stu-id="b08d7-102">Using Libraries from Partially Trusted Code</span></span>
[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]  
  
> [!NOTE]
>  <span data-ttu-id="b08d7-103">Bu konuda tanımlayıcı adlı derlemeler davranışını yöneliktir ve yalnızca geçerli [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) derlemeler.</span><span class="sxs-lookup"><span data-stu-id="b08d7-103">This topic addresses the behavior of strong-named assemblies and applies only to [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) assemblies.</span></span> <span data-ttu-id="b08d7-104">[Güvenliği saydam kod, Düzey 2](../../../docs/framework/misc/security-transparent-code-level-2.md) derlemelerde [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] veya üzeri tanımlayıcı adlar tarafından etkilenmez.</span><span class="sxs-lookup"><span data-stu-id="b08d7-104">[Security-Transparent Code, Level 2](../../../docs/framework/misc/security-transparent-code-level-2.md) assemblies in the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] or later are not affected by strong names.</span></span> <span data-ttu-id="b08d7-105">Güvenlik sistemi değişiklikler hakkında daha fazla bilgi için bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).</span><span class="sxs-lookup"><span data-stu-id="b08d7-105">For more information about changes to the security system, see [Security Changes](../../../docs/framework/security/security-changes.md).</span></span>  
  
 <span data-ttu-id="b08d7-106">Paylaşılan çağırmak için tam güven kendi ana bilgisayardan veya korumalı alan verilmez daha az alan uygulamalar yönetilen kitaplıkları kitaplığı yazan özellikle kullanım yoluyla kendisine izin vermediği sürece <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b08d7-106">Applications that receive less than full trust from their host or sandbox are not allowed to call shared managed libraries unless the library writer specifically allows them to through the use of the <xref:System.Security.AllowPartiallyTrustedCallersAttribute> attribute.</span></span> <span data-ttu-id="b08d7-107">Bu nedenle, uygulama yazarları bazı kitaplıklar onlara kısmen güvenilen bağlamından kullanılabilir olmayacağını farkında olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b08d7-107">Therefore, application writers must be aware that some libraries will not be available to them from a partially trusted context.</span></span> <span data-ttu-id="b08d7-108">Varsayılan olarak, tüm kod yürütmelerinin kısmi güvende [korumalı alan](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) ve buna tam güven derleme listesi kısmen güvenilir değil.</span><span class="sxs-lookup"><span data-stu-id="b08d7-108">By default, all code that executes in a partial-trust [sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md) and is not in the list of full-trust assemblies is partially trusted.</span></span> <span data-ttu-id="b08d7-109">Kısmen güvenilen bağlamından yürütülecek veya kısmen güvenilen kod tarafından çağrılacak kodunuzu düşünmüyorsanız bu bölümdeki bilgiler hakkında endişelenmeniz gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b08d7-109">If you do not expect your code to be executed from a partially trusted context or to be called by partially trusted code, you do not have to be concerned about the information in this section.</span></span> <span data-ttu-id="b08d7-110">Ancak, kısmen güvenilen bağlamından kısmen güvenilen kodla etkileşim veya çalışması gerekir kodu yazarsanız, aşağıdaki etmenleri düşünmeniz gerekir:</span><span class="sxs-lookup"><span data-stu-id="b08d7-110">However, if you write code that must interact with partially trusted code or operate from a partially trusted context, you should consider the following factors:</span></span>  
  
-   <span data-ttu-id="b08d7-111">Kitaplıklar, birden çok uygulama tarafından paylaşılması için tanımlayıcı bir ad ile imzalanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b08d7-111">Libraries must be signed with a strong name in order to be shared by multiple applications.</span></span> <span data-ttu-id="b08d7-112">Tanımlayıcı adlar izin genel derleme önbelleğinde yerleştirilen veya tam güven listesine bir korumalı alan, kodunuzun <xref:System.AppDomain>, ve belirli bir mobil kod gerçekten sizden kaynağının olduğunu doğrulamak tüketicilere izin verin.</span><span class="sxs-lookup"><span data-stu-id="b08d7-112">Strong names allow your code to be placed in the global assembly cache or added to the full-trust list of a sandboxing <xref:System.AppDomain>, and allow consumers to verify that a particular piece of mobile code actually originates from you.</span></span>  
  
-   <span data-ttu-id="b08d7-113">Varsayılan olarak, tanımlayıcı adlı [düzey 1](../../../docs/framework/misc/security-transparent-code-level-1.md) paylaşılan kitaplıklar gerçekleştirmek örtülü [LinkDemand](../../../docs/framework/misc/link-demands.md) için tam güven otomatik olarak, herhangi bir şey yapmanıza gerek kalmadan kitaplığı yazan.</span><span class="sxs-lookup"><span data-stu-id="b08d7-113">By default, strong-named [Level 1](../../../docs/framework/misc/security-transparent-code-level-1.md) shared libraries perform an implicit [LinkDemand](../../../docs/framework/misc/link-demands.md) for full trust automatically, without the library writer having to do anything.</span></span>  
  
-   <span data-ttu-id="b08d7-114">Çağıran tam güven yok ancak yine de bu tür bir kitaplık çağırmayı dener, çalışma zamanı döndürürse bir <xref:System.Security.SecurityException> ve arayan Kitaplığı'na bağlamak için izin verilmiyor.</span><span class="sxs-lookup"><span data-stu-id="b08d7-114">If a caller does not have full trust but still tries to call such a library, the runtime throws a <xref:System.Security.SecurityException> and the caller is not allowed to link to the library.</span></span>  
  
-   <span data-ttu-id="b08d7-115">Otomatik devre dışı bırakmak için **LinkDemand** ve oluşturulan gelen özel durum önlemek için yerleştireceğiniz **AllowPartiallyTrustedCallersAttribute** paylaşılan derleme kapsamını özniteliği Kitaplığı.</span><span class="sxs-lookup"><span data-stu-id="b08d7-115">In order to disable the automatic **LinkDemand** and prevent the exception from being thrown, you can place the **AllowPartiallyTrustedCallersAttribute** attribute on the assembly scope of a shared library.</span></span> <span data-ttu-id="b08d7-116">Bu öznitelik Kitaplıklarınızı kısmen güvenilen yönetilen koddan çağrılan sağlar.</span><span class="sxs-lookup"><span data-stu-id="b08d7-116">This attribute allows your libraries to be called from partially trusted managed code.</span></span>  
  
-   <span data-ttu-id="b08d7-117">Bu öznitelik bir kitaplıkla erişim izni kısmen güvenilen kod tarafından tanımlanan hala sınırlamalar tabidir <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="b08d7-117">Partially trusted code that is granted access to a library with this attribute is still subject to further restrictions defined by the <xref:System.AppDomain>.</span></span>  
  
-   <span data-ttu-id="b08d7-118">Hiçbir programlı şekilde sahip olmayan bir kitaplık çağrılacak kısmen güvenilen kod için **AllowPartiallyTrustedCallersAttribute** özniteliği.</span><span class="sxs-lookup"><span data-stu-id="b08d7-118">There is no programmatic way for partially trusted code to call a library that does not have the **AllowPartiallyTrustedCallersAttribute** attribute.</span></span>  
  
 <span data-ttu-id="b08d7-119">Belirli bir uygulamaya özel kitaplıkları bir güçlü ad gerekli olmadığı veya **AllowPartiallyTrustedCallersAttribute** özniteliği ve uygulama dışında kötü amaçlı kodlar tarafından başvurulamaz.</span><span class="sxs-lookup"><span data-stu-id="b08d7-119">Libraries that are private to a specific application do not require a strong name or the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be referenced by potentially malicious code outside the application.</span></span> <span data-ttu-id="b08d7-120">Bu tür kodu kasıtlı olarak veya yanlışlıkla kötüye karşı ek bir şey yapmanıza gerek kalmadan Geliştirici mobil kısmen güvenilen kod tarafından korunur.</span><span class="sxs-lookup"><span data-stu-id="b08d7-120">Such code is protected against intentional or unintentional misuse by partially trusted mobile code without the developer having to do anything extra.</span></span>  
  
 <span data-ttu-id="b08d7-121">Açıkça kod aşağıdaki türleri için kısmen güvenilen kod tarafından kullanım etkinleştirmeyi düşünebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="b08d7-121">You should consider explicitly enabling use by partially trusted code for the following types of code:</span></span>  
  
-   <span data-ttu-id="b08d7-122">Güvenlik açıklarını titizlikle test edilmiştir ve açıklanan yönergeleri uyumlu olan kodu [güvenli kodlama yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md).</span><span class="sxs-lookup"><span data-stu-id="b08d7-122">Code that has been diligently tested for security vulnerabilities and is in compliance with the guidelines described in [Secure Coding Guidelines](../../../docs/standard/security/secure-coding-guidelines.md).</span></span>  
  
-   <span data-ttu-id="b08d7-123">Kısmen güvenilen senaryoları için özel olarak yazılmış tanımlayıcı adlı kodu kitaplıkları.</span><span class="sxs-lookup"><span data-stu-id="b08d7-123">Strong-named code libraries that are specifically written for partially trusted scenarios.</span></span>  
  
-   <span data-ttu-id="b08d7-124">Tüm bileşenleri (kısmen veya tamamen güvenilir olup olmadığını) Internet'ten indirilen kod tarafından çağrılan bir güçlü ad ile imzalanmış.</span><span class="sxs-lookup"><span data-stu-id="b08d7-124">Any components (whether partially or fully trusted) signed with a strong name that will be called by code that is downloaded from the Internet.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b08d7-125">.NET Framework Sınıf Kitaplığı'nda bazı sınıfları olmadığı **AllowPartiallyTrustedCallersAttribute** özniteliği ve kısmen güvenilen kod tarafından çağrılamaz.</span><span class="sxs-lookup"><span data-stu-id="b08d7-125">Some classes in the .NET Framework class library do not have the **AllowPartiallyTrustedCallersAttribute** attribute and cannot be called by partially trusted code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b08d7-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b08d7-126">See Also</span></span>  
 [<span data-ttu-id="b08d7-127">Kod erişimi güvenliği</span><span class="sxs-lookup"><span data-stu-id="b08d7-127">Code Access Security</span></span>](../../../docs/framework/misc/code-access-security.md)
