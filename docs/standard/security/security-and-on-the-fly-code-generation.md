---
title: Güvenlik ve Çalışma Sırasında Kod Oluşturma
description: Daha yüksek bir güvende çalışan daha az güven kodu adına kod üretme, özellikle bir arayan kod oluşturmayı etkileyebileceği durumlarda güvenlik konusudur.
ms.date: 07/15/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- code security, on-the-fly code generation
- on-the-fly code generation
- security [.NET], on-the-fly code generation
- secure coding, on-the-fly code generation
ms.assetid: 6d221724-bb21-4d76-90c3-0ee2a2e69be2
ms.openlocfilehash: a3fc51c346feffa85537d95ccdbd23d943827edf
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555701"
---
# <a name="security-and-on-the-fly-code-generation"></a>Güvenlik ve Çalışma Sırasında Kod Oluşturma

Bazı kitaplıklar kod oluşturarak ve çağıran için bir işlem gerçekleştirmek üzere çalıştırılarak çalışır. Temel sorun, daha az güven kodu adına kod oluşturuyor ve daha yüksek bir güvende çalışıyor. Worsens sorunu, çağıran kod oluşturmayı etkileyebileceğinden, yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmanız gerekir.  
  
Her zaman hangi kodu ürettiğinizi tam olarak bilmeniz gerekir. Bu, bir kullanıcıdan aldığınız herhangi bir değer üzerinde katı denetimler olması gerektiği anlamına gelir, bu, tırnak içine alınmış dizeler (beklenmeyen kod öğeleri dahil edilemez), tanımlayıcılar (geçerli tanımlayıcılar olduklarını doğrulamak için denetlenmelidir) veya başka bir şey olabilir. Derlenmiş bir bütünleştirilmiş kod, tanımlayıcılarının büyük olasılıkla bir güvenlik açığı olsa da bunları bozabilecek olan garip karakterler içermesi için değiştirilebildiğinden, tanımlayıcılar tehlikeli olabilir.  
  
Yansıma Yayma ile kod oluşturmanız önerilir, bu da genellikle bu sorunlardan çoğunu önlemenize yardımcı olur.  
  
Kodu derlerken bir kötü amaçlı programın değişiklik yapıp görmediğini göz önünde bulundurun. Kötü amaçlı kodun, derleyici onu okumadan önce veya Code. dll dosyasını yüklemeden önce diskteki kaynak kodu değiştirebileceği küçük bir zaman penceresi var mı? Bu durumda, dosya sistemindeki bir Access Control listesini kullanarak bu dosyaları içeren dizini korumanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](secure-coding-guidelines.md)
- [ASP.NET Core güvenliği](/aspnet/core/security/)
