---
title: Güvenlik
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: a3debf487b9b2a04277d9ce3007f28662fa4899e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734497"
---
# <a name="windows-forms-security"></a><span data-ttu-id="899a9-102">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="899a9-102">Windows Forms Security</span></span>
<span data-ttu-id="899a9-103">Windows Forms, kod tabanlı bir güvenlik modeline sahiptir (kodu çalıştıran kullanıcı ne olursa olsun, kod için güvenlik düzeyleri ayarlanır).</span><span class="sxs-lookup"><span data-stu-id="899a9-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="899a9-104">Bu, daha önce bilgisayar sisteminizde yer alan herhangi bir güvenlik şemasına ek niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="899a9-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="899a9-105">Bunlar tarayıcıda (Internet Explorer 'da bulunan bölge tabanlı güvenlik gibi) veya işletim sistemi (Windows NT 'nin kimlik bilgileri tabanlı güvenliği gibi) içerebilir.</span><span class="sxs-lookup"><span data-stu-id="899a9-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="899a9-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="899a9-106">In This Section</span></span>  
 [<span data-ttu-id="899a9-107">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="899a9-107">Security in Windows Forms Overview</span></span>](security-in-windows-forms-overview.md)  
 <span data-ttu-id="899a9-108">.NET Framework güvenlik modelini ve uygulamanızdaki Windows Forms güvende olmasını sağlamak için gereken temel adımları kısaca açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="899a9-109">Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="899a9-109">More Secure File and Data Access in Windows Forms</span></span>](more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="899a9-110">Yarı güvenilir bir ortamda dosya ve verilere nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="899a9-111">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="899a9-111">More Secure Printing in Windows Forms</span></span>](more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="899a9-112">Yarı güvenilir bir ortamda yazdırma özelliklerine nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="899a9-113">Windows Forms'ta Ek Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="899a9-113">Additional Security Considerations in Windows Forms</span></span>](additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="899a9-114">Pencere işleme, Panoyu kullanma ve yarı güvenilir bir ortamda yönetilmeyen koda çağrı yapma işlemlerini açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="899a9-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="899a9-115">Related Sections</span></span>  
 <span data-ttu-id="899a9-116">[Varsayılan Güvenlik Ilkesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899a9-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="899a9-117">Tam güven, yerel Intranet ve Internet izin kümelerinde verilen varsayılan izinleri listeler.</span><span class="sxs-lookup"><span data-stu-id="899a9-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="899a9-118">[Genel Güvenlik Ilkesi yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899a9-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="899a9-119">.NET Framework güvenlik ilkesini yönetme ve izinleri yükseltme hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="899a9-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="899a9-120">Tehlikeli Izinler ve Ilke yönetimi</span><span class="sxs-lookup"><span data-stu-id="899a9-120">Dangerous Permissions and Policy Administration</span></span>](../misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="899a9-121">Güvenlik sisteminin atlalanmasına izin verebilecek the.NET Framework izinlerinden bazılarını açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="899a9-122">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="899a9-122">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="899a9-123">.NET Framework karşı güvenli bir şekilde kod yazmak için en iyi uygulamaları açıklayan konuların bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="899a9-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="899a9-124">[Izin isteme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899a9-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="899a9-125">Çalışma zamanının, kodunuzun hangi izinleri çalıştırması gerektiğini bilmesini sağlamak için özniteliklerin kullanımını açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="899a9-126">Temel Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="899a9-126">Key Security Concepts</span></span>](../../standard/security/key-security-concepts.md)  
 <span data-ttu-id="899a9-127">Kod güvenliğinin temel yönlerini kapsayan konuların bağlantıları.</span><span class="sxs-lookup"><span data-stu-id="899a9-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="899a9-128">Kod erişim güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="899a9-128">Code Access Security Basics</span></span>](../misc/code-access-security-basics.md)  
 <span data-ttu-id="899a9-129">.NET Framework çalıştırma zamanı güvenlik ilkesiyle çalışma hakkında temel bilgileri açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="899a9-130">[Güvenlik Ilkesinin ne zaman değiştirileceğini belirleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899a9-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="899a9-131">Uygulamalarınızın varsayılan güvenlik ilkesinden ne zaman yönlendirilme ihtiyacı olduğunu nasıl belirleyebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="899a9-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="899a9-132">[Güvenlik Ilkesi dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="899a9-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="899a9-133">Güvenlik İlkesi değişikliklerinin dağıtılmasının en iyi şekilde anlatılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="899a9-133">Discusses the best manner for deploying security policy changes.</span></span>
