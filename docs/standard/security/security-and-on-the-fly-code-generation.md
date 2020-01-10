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
# <a name="security-and-on-the-fly-code-generation"></a>Güvenlik ve Çalışma Sırasında Kod Oluşturma
Bazı kitaplıklar kod oluşturarak ve çağıran için bir işlem gerçekleştirmek üzere çalıştırılarak çalışır. Temel sorun, daha az güven kodu adına kod oluşturuyor ve daha yüksek bir güvende çalışıyor. Worsens sorunu, çağıran kod oluşturmayı etkileyebileceğinden, yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmanız gerekir.  
  
 Her zaman hangi kodu ürettiğinizi tam olarak bilmeniz gerekir. Bu, bir kullanıcıdan aldığınız herhangi bir değer üzerinde katı denetimlere sahip olmanız gerektiği anlamına gelir, bu durumda tırnak içine alınmış dizeler (beklenmeyen kod öğeleri dahil edilemez), tanımlayıcılar (geçerli olduklarını doğrulamak için denetlenmesi gerekir) tanımlayıcılar) veya başka bir şey. Derlenmiş bir bütünleştirilmiş kod, tanımlayıcılarının büyük olasılıkla bir güvenlik açığı olsa da bunları bozabilecek olan garip karakterler içermesi için değiştirilebildiğinden, tanımlayıcılar tehlikeli olabilir.  
  
 Yansıma Yayma ile kod oluşturmanız önerilir, bu da genellikle bu sorunlardan çoğunu önlemenize yardımcı olur.  
  
 Kodu derlerken bir kötü amaçlı programın değişiklik yapıp görmediğini göz önünde bulundurun. Kötü amaçlı kodun, derleyici onu okumadan önce veya Code. dll dosyasını yüklemeden önce diskteki kaynak kodu değiştirebileceği küçük bir zaman penceresi var mı? Bu durumda, dosya sistemindeki bir Access Control listesini kullanarak bu dosyaları içeren dizini korumanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
