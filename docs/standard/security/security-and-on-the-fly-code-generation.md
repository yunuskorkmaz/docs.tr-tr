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
# <a name="security-and-on-the-fly-code-generation"></a>Güvenlik ve Çalışma Sırasında Kod Oluşturma
Bazı kitaplıklar kod oluşturarak ve arayan için bazı işlemi gerçekleştirmek için çalıştırarak çalışır. Temel sorun, daha az güven kodu adına kod oluşturmak ve daha yüksek bir güven de çalıştırmaktır. Arayan kod oluşturmayı etkileyebildiği zaman sorun daha da kötüleşir, bu nedenle yalnızca güvenli olduğunu düşündüğünüz kodun oluşturulduğundan emin olmalısınız.  
  
 Her zaman tam olarak hangi kodu ürettiğinizi bilmeniz gerekir. Bu, bir kullanıcıdan aldığınız değerler üzerinde sıkı denetimlere sahip olduğunuz anlamına gelir, bunlar teklif eklenmiş dizeleri (beklenmeyen kod öğeleri içeremez, bu yüzden kaçılmalıdır), tanımlayıcılar (geçerli olup olmadığını doğrulamak için kontrol edilmelidir tanımlayıcılar) veya başka bir şey. Tanımlayıcıları garip karakterler içerecek şekilde değiştirilebilir, çünkü tanımlayıcıları tehlikeli olabilir (bu nadiren bir güvenlik açığı olmasına rağmen).  
  
 Genellikle bu sorunların çoğunu önlemenize yardımcı olan yansıma yayıyla kod oluşturmanız önerilir.  
  
 Kodu derlediğinizde, kötü amaçlı bir programın kodu değiştirmenin bir yolu olup olmadığını göz önünde bulundurun. Derleyici okumadan önce veya kodun .dll dosyasını yüklemeden önce kötü amaçlı kodun diskteki kaynak kodunu değiştirebileceği küçük bir zaman penceresi var mı? Bu durumda, dosya sisteminde ki Bir Erişim Denetim Listesi kullanarak bu dosyaları içeren dizini uygun şekilde korumanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
