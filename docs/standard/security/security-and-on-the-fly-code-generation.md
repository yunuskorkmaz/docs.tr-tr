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
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2018
ms.locfileid: "45512848"
---
# <a name="security-and-on-the-fly-code-generation"></a>Güvenlik ve Çalışma Sırasında Kod Oluşturma
Kod oluşturup arayanı için bazı işlemi gerçekleştirmek için çalışan bazı kitaplıklar çalışır. Temel sorun daha düşük güven kodu adına kod oluşturma ve daha yüksek bir güven çalışır. Yalnızca güvenli göz önünde bulundurun kod oluşturulur emin olmanız gerekir, böylece çağıran kod oluşturma işlemini etkileyebilir, sorun worsens.  
  
 Her zaman tam olarak hangi kodun ürettiğini bilmeniz gerekir. Bu bir kullanıcı tarafından size herhangi bir değeri katı denetimleri gerektiği anlamına gelir, (beklenmeyen kod öğeleri dahil edemezsiniz bırakmayarak Atlanan) tırnak işareti içine alınmış dizeler (denetlenmelidir geçerli olduğunu doğrulamak için tanımlayıcılar tanımlayıcılar) veya başka bir şey. Böylece kendi tanımlayıcıları (Bu nadiren bir güvenlik açığı olmasına rağmen), büyük olasılıkla keser garip karakterler içeren bir derlemede değiştirilebilir tanımlayıcıları tehlikeli olabilir.  
  
 Yansıma ile kod oluşturmak önerilir yayma, genellikle çoğu bu sorunları önlemenize yardımcı olur.  
  
 Kodu derlediğinizde, kötü amaçlı bir programdır bunu değiştirebilir şekilde olup olmadığını göz önünde bulundurun. Küçük bir sırasında kötü amaçlı kod diskteki kaynak kod derleyici okuduğu önce veya kodunuzu .dll dosyasını yüklemeden önce değiştirebileceğiniz zaman penceresi var mı? Öyleyse, uygun olarak dosya sistemindeki erişim denetimi listesi kullanarak bu dosyaları içeren dizine korumanız gerekir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenli Kodlama Yönergeleri](../../../docs/standard/security/secure-coding-guidelines.md)
