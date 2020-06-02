---
title: Güvenlik ve Çalışma Sırasında Kod Oluşturma
description: Daha yüksek bir güvende çalışan daha az güven kodu adına kod üretme, özellikle bir arayan kod oluşturmayı etkileyebileceği durumlarda güvenlik konusudur.
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: 7e5168aa9305c559cf5ea2fb197b2c23ce2a05b0
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291038"
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="e8b06-103">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e8b06-103">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="e8b06-104">Bazı kitaplıklar kod oluşturarak ve çağıran için bir işlem gerçekleştirmek üzere çalıştırılarak çalışır.</span><span class="sxs-lookup"><span data-stu-id="e8b06-104">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="e8b06-105">Temel sorun, daha az güven kodu adına kod oluşturuyor ve daha yüksek bir güvende çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="e8b06-105">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="e8b06-106">Worsens sorunu, çağıran kod oluşturmayı etkileyebileceğinden, yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8b06-106">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="e8b06-107">Her zaman hangi kodu ürettiğinizi tam olarak bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8b06-107">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="e8b06-108">Bu, bir kullanıcıdan aldığınız herhangi bir değer üzerinde katı denetimler olması gerektiği anlamına gelir, bu, tırnak içine alınmış dizeler (beklenmeyen kod öğeleri dahil edilemez), tanımlayıcılar (geçerli tanımlayıcılar olduklarını doğrulamak için denetlenmelidir) veya başka bir şey olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8b06-108">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="e8b06-109">Derlenmiş bir bütünleştirilmiş kod, tanımlayıcılarının büyük olasılıkla bir güvenlik açığı olsa da bunları bozabilecek olan garip karakterler içermesi için değiştirilebildiğinden, tanımlayıcılar tehlikeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="e8b06-109">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="e8b06-110">Yansıma Yayma ile kod oluşturmanız önerilir, bu da genellikle bu sorunlardan çoğunu önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="e8b06-110">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="e8b06-111">Kodu derlerken bir kötü amaçlı programın değişiklik yapıp görmediğini göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e8b06-111">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="e8b06-112">Kötü amaçlı kodun, derleyici onu okumadan önce veya Code. dll dosyasını yüklemeden önce diskteki kaynak kodu değiştirebileceği küçük bir zaman penceresi var mı?</span><span class="sxs-lookup"><span data-stu-id="e8b06-112">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="e8b06-113">Bu durumda, dosya sistemindeki bir Access Control listesini kullanarak bu dosyaları içeren dizini korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="e8b06-113">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b06-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8b06-114">See also</span></span>

- [<span data-ttu-id="e8b06-115">Güvenli Kodlama Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="e8b06-115">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
