---
description: 'Daha fazla bilgi edinin: genişletilebilirlik için tasarlama'
title: Genişletilebilirlik için Tasarlama
ms.date: 10/22/2008
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 148ae25380698a5a1161fb9fbdd3cc60102e865d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99642272"
---
# <a name="designing-for-extensibility"></a>Genişletilebilirlik için Tasarlama

Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak. Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir. Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.  
  
 Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır. Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır. Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir. Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  

 [Korumasız sınıflar](unsealed-classes.md)  
 [Korumalı Üyeler](protected-members.md)  
 [Olaylar ve geri çağrılar](events-and-callbacks.md)  
 [Sanal Üyeler](virtual-members.md)  
 [Soyutlamalar (soyut türler ve arabirimler)](abstractions-abstract-types-and-interfaces.md)  
 [Soyutlamalar uygulamak için temel sınıflar](base-classes-for-implementing-abstractions.md)  
 [Mühürleme](sealing.md)  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *Microsoft Windows geliştirme serisi 'nin bir parçası olarak, Addison-Wesley Professional tarafından, yeniden [kullanılabilir .NET kitaplıkları Için kurallar, deyimler ve desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vabzysztof Cwalina ve atacan Abkms, yayımlandı Ekim 22, 2008 tarafından yeniden yazdırılmıştır.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
