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
ms.openlocfilehash: 64ddcc6a379e5719eb734eede13e576a707696fe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705892"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="26211-102">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="26211-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="26211-103">Bazı kitaplıklar kod oluşturarak ve çağıran için bir işlem gerçekleştirmek üzere çalıştırılarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="26211-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="26211-104">Temel sorun, daha az güven kodu adına kod oluşturuyor ve daha yüksek bir güvende çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="26211-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="26211-105">Worsens sorunu, çağıran kod oluşturmayı etkileyebileceğinden, yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26211-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="26211-106">Her zaman hangi kodu ürettiğinizi tam olarak bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="26211-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="26211-107">Bu, bir kullanıcıdan aldığınız herhangi bir değer üzerinde katı denetimlere sahip olmanız gerektiği anlamına gelir, bu durumda tırnak içine alınmış dizeler (beklenmeyen kod öğeleri dahil edilemez), tanımlayıcılar (geçerli olduklarını doğrulamak için denetlenmesi gerekir) tanımlayıcılar) veya başka bir şey.</span><span class="sxs-lookup"><span data-stu-id="26211-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="26211-108">Derlenmiş bir bütünleştirilmiş kod, tanımlayıcılarının büyük olasılıkla bir güvenlik açığı olsa da bunları bozabilecek olan garip karakterler içermesi için değiştirilebildiğinden, tanımlayıcılar tehlikeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="26211-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="26211-109">Yansıma Yayma ile kod oluşturmanız önerilir, bu da genellikle bu sorunlardan çoğunu önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="26211-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="26211-110">Kodu derlerken bir kötü amaçlı programın değişiklik yapıp görmediğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="26211-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="26211-111">Kötü amaçlı kodun, derleyici onu okumadan önce veya Code. dll dosyasını yüklemeden önce diskteki kaynak kodu değiştirebileceği küçük bir zaman penceresi var mı?</span><span class="sxs-lookup"><span data-stu-id="26211-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="26211-112">Bu durumda, dosya sistemindeki bir Access Control listesini kullanarak bu dosyaları içeren dizini korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="26211-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26211-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26211-113">See also</span></span>

- [<span data-ttu-id="26211-114">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="26211-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
