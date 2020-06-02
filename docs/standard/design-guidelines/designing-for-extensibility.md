---
title: Genişletilebilirlik için Tasarlama
ms.date: 10/22/2008
ms.technology: dotnet-standard
helpviewer_keywords:
- extending class libraries
- extensibility with class libraries in .NET Framework
- class library design guidelines [.NET Framework], extensibility
- class library extensibility [.NET Framework]
ms.assetid: 1cdb8740-871a-456c-9bd9-db96ca8d79b3
ms.openlocfilehash: 406c15b6ce42b637ed1bbb61761d05e040995579
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84280250"
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
  
 *, Microsoft Windows geliştirme serisinin bir parçası olarak, [.NET kitaplıkları için 2. sürüm](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , Vazysztof Cwalina ve atacan Abk2008 MS, 4. Adım: Addison-Wesley Professional tarafından yeniden yazdırılmıştır.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve tasarım yönergeleri](index.md)
