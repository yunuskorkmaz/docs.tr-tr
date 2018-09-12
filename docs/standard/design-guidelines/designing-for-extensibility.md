---
title: Genişletilebilirlik için tasarlama
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1690d0cdf1f57eaf0a794d6e71babfa4fa6425
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44493809"
---
# <a name="designing-for-extensibility"></a>Genişletilebilirlik için tasarlama
Bir çerçeve tasarlamanın önemli yönlerinden biri framework'ün genişletilebilirlik dikkatle emin olmak. Bu, çeşitli genişletilebilirlik mekanizması ile ilişkili avantajlarını ve maliyetlerini anlamak gerektirir. Bu bölümde, genişletilebilirlik mekanizması karar vermenize yardımcı olur — sınıflara, olayları, sanal üyeleri, geri çağrılar ve benzeri — Çerçevenizi gereksinimlerini en iyi karşılayabilecek.  
  
 Genişletilebilirlik çerçeveleri alanında izin vermek için birçok yolu vardır. Bunlar daha güçlü ancak daha az maliyetli pahalı ancak çok güçlü aralığının. Herhangi bir belirli genişletilebilirlik gereksinim için gereksinimleri karşılayan az maliyetli genişletilebilirlik mekanizması seçmeniz gerekir. Daha sonra daha fazla genişletilebilirlik eklemek genellikle mümkündür, ancak hiçbir zaman onu hemen bozucu değişiklikleri oluşturmaksızın uygulayabileceğiniz aklınızda bulundurun.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Mühürsüz Sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Korumalı Üyeler](../../../docs/standard/design-guidelines/protected-members.md)  
 [Etkinlikler ve Geri Aramalar](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Sanal Üyeler](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Soyutlamalar (Soyut Türler ve Arabirimler)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Soyutlama Uygulamak için Temel Sınıflar](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)  
 *Kısımları © 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
