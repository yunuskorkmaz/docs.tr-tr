---
title: "Windows Forms Güvenliği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5cdac074b873d3a627e6971d440fdd1f98952b08
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-security"></a><span data-ttu-id="40ac6-102">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="40ac6-102">Windows Forms Security</span></span>
<span data-ttu-id="40ac6-103">Windows Forms (kod tabanlı güvenlik düzeyleri kod kodu çalıştıran kullanıcının bağımsız olarak ayarlanır) bir güvenlik modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="40ac6-104">Ek olarak, bilgisayar sisteminizdeki zaten yerinde olabilir tüm güvenlik şemaları budur.</span><span class="sxs-lookup"><span data-stu-id="40ac6-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="40ac6-105">Bu tarayıcı (örneğin, bölge tabanlı güvenlik Internet Explorer'da kullanılabilir) veya işletim sistemi (örneğin, Windows NT kimlik bilgisi tabanlı güvenlik) de dahil edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="40ac6-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="40ac6-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="40ac6-106">In This Section</span></span>  
 [<span data-ttu-id="40ac6-107">Windows Forms'a genel bakış güvenliği</span><span class="sxs-lookup"><span data-stu-id="40ac6-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="40ac6-108">.NET Framework güvenlik modeli ve uygulamanızı Windows Forms'ta sağlamak için gereken temel adımlarda güvenli kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40ac6-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="40ac6-109">Daha güvenli dosya ve Windows Forms veri erişimi</span><span class="sxs-lookup"><span data-stu-id="40ac6-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="40ac6-110">Dosyaları ve yarı güvenilir bir ortamda verilerine erişmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="40ac6-111">Windows Forms'ta daha güvenli yazdırma</span><span class="sxs-lookup"><span data-stu-id="40ac6-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="40ac6-112">Yarı güvenilir bir ortamda yazdırma özelliklerine erişmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="40ac6-113">Windows Forms'ta ek güvenlik konuları</span><span class="sxs-lookup"><span data-stu-id="40ac6-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="40ac6-114">Pano kullanma ve yönetilmeyen kod yarı güvenilir bir ortamda aramalarına gerçekleştirme penceresi işleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="40ac6-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="40ac6-115">Related Sections</span></span>  
 [<span data-ttu-id="40ac6-116">NIB: Varsayılan güvenlik ilkesi</span><span class="sxs-lookup"><span data-stu-id="40ac6-116">NIB: Default Security Policy</span></span>](http://msdn.microsoft.com/en-us/2c086873-0894-4f4d-8f7e-47427c1a3b55)  
 <span data-ttu-id="40ac6-117">Tam güven, yerel Intranet ve Internet izni kümelerinde varsayılan izinler listelenmektedir.</span><span class="sxs-lookup"><span data-stu-id="40ac6-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 [<span data-ttu-id="40ac6-118">NIB: Genel Güvenlik İlkesi Yönetimi</span><span class="sxs-lookup"><span data-stu-id="40ac6-118">NIB: General Security Policy Administration</span></span>](http://msdn.microsoft.com/en-us/5121fe35-f0e3-402c-94ab-4f35b0a87b4b)  
 <span data-ttu-id="40ac6-119">.NET Framework güvenlik ilkesini yönetme ve izinleri artırmasını hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="40ac6-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="40ac6-120">Tehlikeli izinler ve ilke yönetimi</span><span class="sxs-lookup"><span data-stu-id="40ac6-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="40ac6-121">Bazı circumvented bir güvenlik sistemi izin verebilir.NET Framework izinler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40ac6-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="40ac6-122">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="40ac6-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="40ac6-123">Güvenli bir şekilde .NET Framework karşı kod yazmaya yönelik en iyi uygulamaları açıklayan konulara bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 [<span data-ttu-id="40ac6-124">NIB: İzinleri isteyen</span><span class="sxs-lookup"><span data-stu-id="40ac6-124">NIB: Requesting Permissions</span></span>](http://msdn.microsoft.com/en-us/0447c49d-8cba-45e4-862c-ff0b59bebdc2)  
 <span data-ttu-id="40ac6-125">Kodunuzu çalıştırmak için gereken izinleri bilmeniz çalışma zamanı izin özniteliklerin kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="40ac6-126">Temel güvenlik kavramları</span><span class="sxs-lookup"><span data-stu-id="40ac6-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="40ac6-127">Kod güvenliği temel yönlerini kapak konulara bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="40ac6-128">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="40ac6-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="40ac6-129">Zaman güvenlik ilkesi çalıştırmak .NET Framework ile çalışmanın temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="40ac6-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 [<span data-ttu-id="40ac6-130">NIB: Güvenlik ilkesini değiştirmek ne zaman belirleme</span><span class="sxs-lookup"><span data-stu-id="40ac6-130">NIB: Determining When to Modify Security Policy</span></span>](http://msdn.microsoft.com/en-us/af749b17-e461-409d-84b9-a3d44789db16)  
 <span data-ttu-id="40ac6-131">Uygulamalarınızın varsayılan güvenlik ilkesinden ayırmak gerektiğinde olmadığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="40ac6-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 [<span data-ttu-id="40ac6-132">NIB: Güvenlik ilkesi dağıtma</span><span class="sxs-lookup"><span data-stu-id="40ac6-132">NIB: Deploying Security Policy</span></span>](http://msdn.microsoft.com/en-us/f936c1e5-033b-4bd9-a3bd-a39ba733a681)  
 <span data-ttu-id="40ac6-133">Güvenlik İlkesi değişikliklerini dağıtmak için en iyi şekilde ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="40ac6-133">Discusses the best manner for deploying security policy changes.</span></span>
