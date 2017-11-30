---
title: "Güvenlik ve Çalışma Sırasında Kod Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET Framework], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c00c66be812f2a1cdfdf761f681d2a0561a284bf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="security-and-on-the-fly-code-generation"></a><span data-ttu-id="0d174-102">Güvenlik ve Çalışma Sırasında Kod Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d174-102">Security and On-the-Fly Code Generation</span></span>
<span data-ttu-id="0d174-103">Kod oluşturma ve çağıran için başka bir işlem gerçekleştirmek için çalıştırarak bazı kitaplıklar çalışır.</span><span class="sxs-lookup"><span data-stu-id="0d174-103">Some libraries operate by generating code and running it to perform some operation for the caller.</span></span> <span data-ttu-id="0d174-104">Temel sorun güven küçük koda adına kod oluşturma ve yüksek güven çalıştıran.</span><span class="sxs-lookup"><span data-stu-id="0d174-104">The basic problem is generating code on behalf of lesser-trust code and running it at a higher trust.</span></span> <span data-ttu-id="0d174-105">Yalnızca güvenli göz önünde bulundurun kod üretilir emin olmalısınız şekilde çağrıyı yapan kod oluşturma etkileyebilir olduğunda sorun worsens.</span><span class="sxs-lookup"><span data-stu-id="0d174-105">The problem worsens when the caller can influence code generation, so you must ensure that only code you consider safe is generated.</span></span>  
  
 <span data-ttu-id="0d174-106">Tam olarak hangi kodu her zaman oluşturduğunu bilmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d174-106">You need to know exactly what code you are generating at all times.</span></span> <span data-ttu-id="0d174-107">Bu, bir kullanıcıdan aldığınız herhangi bir değeri katı denetimlere gerektiği anlamına gelir, (beklenmeyen kod öğeleri içeremez şekilde hangi kaçışlı) tırnak içine alınmış dizeler olmaları (hangi geçerli olduğunu doğrulamak üzere denetlenmesi tanımlayıcıları tanımlayıcılar) veya başka bir şey.</span><span class="sxs-lookup"><span data-stu-id="0d174-107">This means that you must have strict controls on any values that you get from a user, be they quote-enclosed strings (which should be escaped so they cannot include unexpected code elements), identifiers (which should be checked to verify that they are valid identifiers), or anything else.</span></span> <span data-ttu-id="0d174-108">Böylece kendi tanımlayıcıları (Bu nadiren bir güvenlik açığı olmasına rağmen), büyük olasılıkla kesecektir garip karakterler içeren derlenmiş bir bütünleştirilmiş kod değiştirilebildiğinden tanımlayıcıları tehlikeli olabilir.</span><span class="sxs-lookup"><span data-stu-id="0d174-108">Identifiers can be dangerous because a compiled assembly can be modified so that its identifiers contain strange characters, which will probably break it (although this is rarely a security vulnerability).</span></span>  
  
 <span data-ttu-id="0d174-109">Yansıma ile kodu oluşturmak önerilir yayma, genellikle çoğu bu sorunları önlemenize yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="0d174-109">It is recommended that you generate code with reflection emit, which often helps you avoid many of these problems.</span></span>  
  
 <span data-ttu-id="0d174-110">Kodu derlemek zaman amaçlı bir program bu değiştirebileceği herhangi bir şekilde olup olmadığını göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="0d174-110">When you compile the code, consider whether there is some way a malicious program could modify it.</span></span> <span data-ttu-id="0d174-111">Küçük bir pencere sırasında kötü amaçlı kod kaynak kodu diskteki Derleyici bunu okuyan önce ya da kodunuzu .dll dosyasını yüklemeden önce değiştirebileceğiniz zaman var mı?</span><span class="sxs-lookup"><span data-stu-id="0d174-111">Is there a small window of time during which malicious code can change source code on disk before the compiler reads it or before your code loads the .dll file?</span></span> <span data-ttu-id="0d174-112">Öyleyse, uygun olarak dosya sistemindeki erişim denetim listesi kullanarak bu dosyaları içeren dizini korumanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0d174-112">If so, you must protect the directory containing these files, using an Access Control List in the file system, as appropriate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d174-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0d174-113">See Also</span></span>  
 [<span data-ttu-id="0d174-114">Güvenli kodlama yönergeleri</span><span class="sxs-lookup"><span data-stu-id="0d174-114">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
