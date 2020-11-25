---
title: Korumalı Üyeler
ms.date: 10/22/2008
helpviewer_keywords:
- members [.NET Framework], protected
- protected members
- classes [.NET Framework], unsealed
- classes [.NET Framework], protected members
- unsealed classes
- customizing class behavior
ms.assetid: aa0b58ee-3956-494d-ab48-471ae5db8740
ms.openlocfilehash: a6f36ac4f994fdc3211cac619cc0b20f7b0335b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730961"
---
# <a name="protected-members"></a>Korumalı Üyeler

Kendilerine göre korunan Üyeler herhangi bir genişletilebilirlik sağlamaz, ancak altsınıflama ile daha güçlü genişletilebilirlik yapabilir. Bu kişiler, ana ortak arabirimi gereksiz şekilde bilmeden gelişmiş özelleştirme seçeneklerini göstermek için kullanılabilirler.

 "Protected" adı yanlış bir güvenlik hissi verebildiğinden, çerçeve tasarımcılarının Korunan üyelere dikkatli olması gerekir. Herhangi biri korumasız bir sınıfın alt sınıfını oluşturup korumalı üyelere erişebilir ve bu nedenle ortak üyeler için kullanılan tüm savunma kodlama uygulamalarının korunan üyeler için de uygulanması mümkün olur.

 ✔️ Gelişmiş özelleştirme için korumalı üyeleri kullanmayı göz önünde bulundurun.

 Güvenlik, belge ve uyumluluk analizine yönelik olarak korumasız sınıflarda korunan üyeleri ortak olarak işleme ✔️.

 Herhangi biri bir sınıftan devralınabilir ve korunan üyelere erişebilir.

 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*

 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*

## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
- [Genişletilebilirlik için Tasarlama](designing-for-extensibility.md)
