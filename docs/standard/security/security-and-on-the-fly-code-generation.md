---
title: Güvenlik ve Çalışma Sırasında Kod Oluşturma
description: Daha yüksek bir güvenle çalışan daha az güven kodu adına kod oluşturmak, özellikle bir arayan kod oluşturmayı etkileyebiliyorsa, bir güvenlik sorunudur.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 34ebda27a81ca29ebb27a721b77b735a12be882e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186795"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="6b36d-103">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="6b36d-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="6b36d-104">Bazı kitaplıklar kod oluşturarak ve arayan için bazı işlemi gerçekleştirmek için çalıştırarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="6b36d-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="6b36d-105">Temel sorun, daha az güven kodu adına kod oluşturmak ve daha yüksek bir güven de çalıştırmaktır.</span><span class="sxs-lookup"><span data-stu-id="6b36d-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="6b36d-106">Arayan kod oluşturmayı etkileyebildiği zaman sorun daha da kötüleşir, bu nedenle yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmalısınız.</span><span class="sxs-lookup"><span data-stu-id="6b36d-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="6b36d-107">Her zaman tam olarak hangi kodu ürettiğinizi bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b36d-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="6b36d-108">Bu, bir kullanıcıdan aldığınız değerler üzerinde sıkı denetimlere sahip olduğunuz anlamına gelir, bunlar teklif eklenmiş dizeleri (beklenmeyen kod öğeleri içeremez, bu yüzden kaçılmalıdır), tanımlayıcılar (geçerli olup olmadığını doğrulamak için kontrol edilmelidir tanımlayıcılar) veya başka bir şey.</span><span class="sxs-lookup"><span data-stu-id="6b36d-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="6b36d-109">Tanımlayıcıları garip karakterler içerecek şekilde değiştirilebilir, çünkü tanımlayıcıları tehlikeli olabilir (bu nadiren bir güvenlik açığı olmasına rağmen).</span><span class="sxs-lookup"><span data-stu-id="6b36d-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="6b36d-110">Genellikle bu sorunların çoğunu önlemenize yardımcı olan yansıma yayıyla kod oluşturmanız önerilir.</span><span class="sxs-lookup"><span data-stu-id="6b36d-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="6b36d-111">Kodu derlediğinizde, kötü amaçlı bir programın kodu değiştirmenin bir yolu olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="6b36d-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="6b36d-112">Derleyici okumadan önce veya kodun .dll dosyasını yüklemeden önce kötü amaçlı kodun diskteki kaynak kodunu değiştirebileceği küçük bir zaman penceresi var mı?</span><span class="sxs-lookup"><span data-stu-id="6b36d-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="6b36d-113">Bu durumda, dosya sisteminde ki Bir Erişim Denetim Listesi kullanarak bu dosyaları içeren dizini uygun şekilde korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="6b36d-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b36d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6b36d-114">See also</span></span>

- [<span data-ttu-id="6b36d-115">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="6b36d-115">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
