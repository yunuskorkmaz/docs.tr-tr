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
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c6bb895979fb44616349505a07591f9ced9fedac
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="security-and-on-the-fly-code-generation"></a>Güvenlik ve Çalışma Sırasında Kod Oluşturma
Kod oluşturma ve çağıran için başka bir işlem gerçekleştirmek için çalıştırarak bazı kitaplıklar çalışır. Temel sorun güven küçük koda adına kod oluşturma ve yüksek güven çalıştıran. Yalnızca güvenli göz önünde bulundurun kod üretilir emin olmalısınız şekilde çağrıyı yapan kod oluşturma etkileyebilir olduğunda sorun worsens.  
  
 Tam olarak hangi kodu her zaman oluşturduğunu bilmeniz gerekir. Bu, bir kullanıcıdan aldığınız herhangi bir değeri katı denetimlere gerektiği anlamına gelir, (beklenmeyen kod öğeleri içeremez şekilde hangi kaçışlı) tırnak içine alınmış dizeler olmaları (hangi geçerli olduğunu doğrulamak üzere denetlenmesi tanımlayıcıları tanımlayıcılar) veya başka bir şey. Böylece kendi tanımlayıcıları (Bu nadiren bir güvenlik açığı olmasına rağmen), büyük olasılıkla kesecektir garip karakterler içeren derlenmiş bir bütünleştirilmiş kod değiştirilebildiğinden tanımlayıcıları tehlikeli olabilir.  
  
 Yansıma ile kodu oluşturmak önerilir yayma, genellikle çoğu bu sorunları önlemenize yardımcı olur.  
  
 Kodu derlemek zaman amaçlı bir program bu değiştirebileceği herhangi bir şekilde olup olmadığını göz önünde bulundurun. Küçük bir pencere sırasında kötü amaçlı kod kaynak kodu diskteki Derleyici bunu okuyan önce ya da kodunuzu .dll dosyasını yüklemeden önce değiştirebileceğiniz zaman var mı? Öyleyse, uygun olarak dosya sistemindeki erişim denetim listesi kullanarak bu dosyaları içeren dizini korumanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
