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
ms.openlocfilehash: cd5db2d1e299df1b3d0f706ebc507e6855b72505
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709471"
---
# <a name="designing-for-extensibility"></a>Genişletilebilirlik için Tasarlama
Çerçeve tasarlamanın önemli bir yönü, Framework 'ün genişletilebilirliğini dikkatle ele aldığınızdan emin olmak. Bunun için çeşitli genişletilebilirlik mekanizmalarıyla ilişkili maliyetleri ve avantajları anlamanız gerekir. Bu bölüm, genişletilebilirlik mekanizmalarının (altsınıflama, olaylar, sanal üyeler, geri çağırmalar vb.) en iyi şekilde ne kadar uygun olduğuna karar vermenize yardımcı olur.  
  
 Çerçeveler içinde genişletilebilirlik sağlamak için birçok yol vardır. Bunlar, daha az güçlü, ancak pahalı, ancak pahalıdır. Herhangi bir genişletilebilirlik gereksinimi için, gereksinimleri karşılayan en düşük maliyetli genişletilebilirlik mekanizmasını seçmeniz gerekir. Daha sonra daha fazla genişletilebilirlik eklemek mümkün olsa da, önemli değişikliklere bildirmeden hiçbir zaman daha fazla işlem yapabilirsiniz.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Mühürsüz Sınıflar](../../../docs/standard/design-guidelines/unsealed-classes.md)  
 [Korumalı Üyeler](../../../docs/standard/design-guidelines/protected-members.md)  
 [Etkinlikler ve Geri Aramalar](../../../docs/standard/design-guidelines/events-and-callbacks.md)  
 [Sanal Üyeler](../../../docs/standard/design-guidelines/virtual-members.md)  
 [Soyutlamalar (Soyut Türler ve Arabirimler)](../../../docs/standard/design-guidelines/abstractions-abstract-types-and-interfaces.md)  
 [Soyutlama Uygulamak için Temel Sınıflar](../../../docs/standard/design-guidelines/base-classes-for-implementing-abstractions.md)  
 [Mühürleme](../../../docs/standard/design-guidelines/sealing.md)  
 *© Bölümleri 2005, 2009 Microsoft Corporation. Tüm hakları saklıdır.*  
  
 *İzni Pearson eğitim, Inc. tarafından yeniden yazdırılmaları [çerçeve tasarım yönergeleri: kuralları, deyimlerini ve yeniden kullanılabilir .NET kitaplıkları, sürüm 2 için desenler](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina ve Brad Abrams, 22 Eki 2008 tarafından yayımlanan Microsoft Windows geliştirme serisi bir parçası olarak Addison Wesley Professional.*  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çerçeve Tasarım Yönergeleri](../../../docs/standard/design-guidelines/index.md)
