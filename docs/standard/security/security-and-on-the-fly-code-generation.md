---
title: Güvenlik ve Çalışma Sırasında Kod Oluşturma
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ffb1081c80c31353ad38080ae16ef9f8a74b5481
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61860548"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="c4d2b-102">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="c4d2b-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="c4d2b-103">Kod oluşturup arayanı için bazı işlemi gerçekleştirmek için çalışan bazı kitaplıklar çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="c4d2b-104">Temel sorun daha düşük güven kodu adına kod oluşturma ve daha yüksek bir güven çalışır.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="c4d2b-105">Yalnızca güvenli göz önünde bulundurun kod oluşturulur emin olmanız gerekir, böylece çağıran kod oluşturma işlemini etkileyebilir, sorun worsens.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="c4d2b-106">Her zaman tam olarak hangi kodun ürettiğini bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="c4d2b-107">Bu bir kullanıcı tarafından size herhangi bir değeri katı denetimleri gerektiği anlamına gelir, (beklenmeyen kod öğeleri dahil edemezsiniz bırakmayarak Atlanan) tırnak işareti içine alınmış dizeler (denetlenmelidir geçerli olduğunu doğrulamak için tanımlayıcılar tanımlayıcılar) veya başka bir şey.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="c4d2b-108">Böylece kendi tanımlayıcıları (Bu nadiren bir güvenlik açığı olmasına rağmen), büyük olasılıkla keser garip karakterler içeren bir derlemede değiştirilebilir tanımlayıcıları tehlikeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="c4d2b-109">Yansıma ile kod oluşturmak önerilir yayma, genellikle çoğu bu sorunları önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="c4d2b-110">Kodu derlediğinizde, kötü amaçlı bir programdır bunu değiştirebilir şekilde olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="c4d2b-111">Küçük bir sırasında kötü amaçlı kod diskteki kaynak kod derleyici okuduğu önce veya kodunuzu .dll dosyasını yüklemeden önce değiştirebileceğiniz zaman penceresi var mı?</span><span class="sxs-lookup"><span data-stu-id="c4d2b-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="c4d2b-112">Öyleyse, uygun olarak dosya sistemindeki erişim denetimi listesi kullanarak bu dosyaları içeren dizine korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4d2b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4d2b-113">See also</span></span>

- [<span data-ttu-id="c4d2b-114">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c4d2b-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
