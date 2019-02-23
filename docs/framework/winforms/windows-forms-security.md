---
title: Windows Forms Güvenliği
ms.date: 03/30/2017
helpviewer_keywords:
- designer access security [Windows Forms]
- permissions [Windows Forms], Windows Forms
- Windows Forms, security
- security [Windows Forms]
- access control [Windows Forms], Windows Forms
- security policy [Windows Forms], Windows Forms
ms.assetid: 932d438a-5285-46d8-a958-8c93d0ad6cae
ms.openlocfilehash: 1da8e2c6ed8091b5931e8b0a881b54329228e82a
ms.sourcegitcommit: 8f95d3a37e591963ebbb9af6e90686fd5f3b8707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/23/2019
ms.locfileid: "56746791"
---
# <a name="windows-forms-security"></a><span data-ttu-id="53f72-102">Windows Forms Güvenliği</span><span class="sxs-lookup"><span data-stu-id="53f72-102">Windows Forms Security</span></span>
<span data-ttu-id="53f72-103">Windows Forms (kod tabanlı güvenlik düzeyleri kod, kodu çalıştıran kullanıcının bağımsız olarak ayarlanır) bir güvenlik modeli sunar.</span><span class="sxs-lookup"><span data-stu-id="53f72-103">Windows Forms features a security model that is code-based (security levels are set for code, regardless of the user running the code).</span></span> <span data-ttu-id="53f72-104">Bu bilgisayar sisteminizin üzerinde zaten bir yerde olabilir herhangi bir güvenlik şemaları ek niteliğindedir.</span><span class="sxs-lookup"><span data-stu-id="53f72-104">This is in addition to any security schemas that may be in place already on your computer system.</span></span> <span data-ttu-id="53f72-105">Bunlar tarayıcı (örneğin, bölgeye göre güvenlik Internet Explorer'da kullanılabilir) veya işletim sistemi (örneğin, Windows NT kimlik tabanlı güvenlik) de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="53f72-105">These can include those in the browser (such as the zone-based security available in Internet Explorer) or the operating system (such as the credential-based security of Windows NT).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="53f72-106">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="53f72-106">In This Section</span></span>  
 [<span data-ttu-id="53f72-107">Windows Forms'ta Güvenliğe Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="53f72-107">Security in Windows Forms Overview</span></span>](../../../docs/framework/winforms/security-in-windows-forms-overview.md)  
 <span data-ttu-id="53f72-108">.NET Framework güvenlik modeli ve uygulamanızın Windows Forms'ta sağlamak için gerekli temel adımlar güvenli kısaca açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="53f72-108">Briefly explains the .NET Framework security model and the basic steps necessary to ensure the Windows Forms in your application are secure.</span></span>  
  
 [<span data-ttu-id="53f72-109">Windows Forms'ta Daha Güvenli Dosya ve Veri Erişimi</span><span class="sxs-lookup"><span data-stu-id="53f72-109">More Secure File and Data Access in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-file-and-data-access-in-windows-forms.md)  
 <span data-ttu-id="53f72-110">Dosyaları ve verileri kısmen güvenilir bir ortamda nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-110">Describes how to access files and data in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="53f72-111">Windows Forms'ta Daha Güvenli Yazdırma</span><span class="sxs-lookup"><span data-stu-id="53f72-111">More Secure Printing in Windows Forms</span></span>](../../../docs/framework/winforms/more-secure-printing-in-windows-forms.md)  
 <span data-ttu-id="53f72-112">Yarı güvenilir bir ortamda yazdırma özelliklerine erişmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-112">Describes how to access printing features in a semi-trusted environment.</span></span>  
  
 [<span data-ttu-id="53f72-113">Windows Forms'ta Ek Güvenlik Konuları</span><span class="sxs-lookup"><span data-stu-id="53f72-113">Additional Security Considerations in Windows Forms</span></span>](../../../docs/framework/winforms/additional-security-considerations-in-windows-forms.md)  
 <span data-ttu-id="53f72-114">Pano'yu kullanıyor ve yönetilmeyen kod kısmen güvenilen bir ortamda aramaların gerçekleştirme penceresi işleme açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-114">Describes performing window manipulation, using the Clipboard, and making calls to unmanaged code in a semi-trusted environment.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="53f72-115">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="53f72-115">Related Sections</span></span>  
 <span data-ttu-id="53f72-116">[Varsayılan güvenlik ilkesi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53f72-116">[Default Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/03kwzyfc(v=vs.100))</span></span>  
 <span data-ttu-id="53f72-117">Tam güven, yerel Intranet ve İnternet'e izin kümeleri, verilen varsayılan izinleri listeler.</span><span class="sxs-lookup"><span data-stu-id="53f72-117">Lists the default permissions granted in the Full Trust, Local Intranet, and Internet permission sets.</span></span>  
  
 <span data-ttu-id="53f72-118">[Genel Güvenlik İlkesi Yönetimi](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53f72-118">[General Security Policy Administration](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ed5htz45(v=vs.100))</span></span>  
 <span data-ttu-id="53f72-119">.NET Framework Güvenlik İlkesi Yönetimi ve izinleri yükseltme hakkında bilgi verir.</span><span class="sxs-lookup"><span data-stu-id="53f72-119">Gives information about the administering the .NET Framework security policy and elevating permissions.</span></span>  
  
 [<span data-ttu-id="53f72-120">Tehlikeli izinler ve ilke yönetimi</span><span class="sxs-lookup"><span data-stu-id="53f72-120">Dangerous Permissions and Policy Administration</span></span>](../../../docs/framework/misc/dangerous-permissions-and-policy-administration.md)  
 <span data-ttu-id="53f72-121">Bazı olası circumvented güvenlik sistemi izin verebilirsiniz.NET Framework izinleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-121">Discusses some of the.NET Framework permissions that can potentially allow the security system to be circumvented.</span></span>  
  
 [<span data-ttu-id="53f72-122">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="53f72-122">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)  
 <span data-ttu-id="53f72-123">Kodu .NET Framework karşı güvenli bir şekilde yazmak için en iyi açıklayan konulara bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="53f72-123">Links to topics that explain the best practices for securely writing code against the .NET Framework.</span></span>  
  
 <span data-ttu-id="53f72-124">[İzinler isteyen](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53f72-124">[Requesting Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/yd267cce(v=vs.100))</span></span>  
 <span data-ttu-id="53f72-125">Kodunuzu çalıştırmak için gereken izinleri bilmeniz çalışma zamanının özniteliklerin kullanmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-125">Discusses the use of attributes to let the runtime know what permissions your code needs to run.</span></span>  
  
 [<span data-ttu-id="53f72-126">Temel Güvenlik Kavramları</span><span class="sxs-lookup"><span data-stu-id="53f72-126">Key Security Concepts</span></span>](../../../docs/standard/security/key-security-concepts.md)  
 <span data-ttu-id="53f72-127">Kod güvenliği temel özelliklerini kapsayan konulara bağlantılar.</span><span class="sxs-lookup"><span data-stu-id="53f72-127">Links to topics that cover the basic aspects of code security.</span></span>  
  
 [<span data-ttu-id="53f72-128">Kod erişimi güvenliği temelleri</span><span class="sxs-lookup"><span data-stu-id="53f72-128">Code Access Security Basics</span></span>](../../../docs/framework/misc/code-access-security-basics.md)  
 <span data-ttu-id="53f72-129">Çalıştırma zamanında güvenlik ilkesi .NET Framework ile çalışmanın temelleri açıklanır.</span><span class="sxs-lookup"><span data-stu-id="53f72-129">Discusses the basics of working with the .NET Framework run time security policy.</span></span>  
  
 <span data-ttu-id="53f72-130">[Güvenlik ilkesini değiştirmek ne zaman belirleme](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53f72-130">[Determining When to Modify Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/xky659fc(v=vs.100))</span></span>  
 <span data-ttu-id="53f72-131">Uygulamalarınızı varsayılan güvenlik ilkesinden ayırmak gerektiğinde olmadığının nasıl belirleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-131">Explains how to determine when your applications need to diverge from the default security policy.</span></span>  
  
 <span data-ttu-id="53f72-132">[Güvenlik İlkesi dağıtma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="53f72-132">[Deploying Security Policy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/13wcxx6y(v=vs.100))</span></span>  
 <span data-ttu-id="53f72-133">Güvenlik İlkesi değişikliklerini dağıtmak için en iyi şekilde açıklar.</span><span class="sxs-lookup"><span data-stu-id="53f72-133">Discusses the best manner for deploying security policy changes.</span></span>
