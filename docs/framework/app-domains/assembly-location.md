---
title: Derleme Konumu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a0b065fe488031329815f6ec38da9661fd19700d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54529940"
---
# <a name="assembly-location"></a>Derleme Konumu
Derlemenin konumunu ortak dil çalışma zamanı başvurulduğunda bulmak, derleme diğer derlemeleri ile paylaşılan olup olmadığını belirlemek olup olmadığını belirler. Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:  
  
-   Uygulamanın dizin veya alt dizinleri.  
  
     Bu, bir derlemenin dağıtımı için en yaygın konumdur. Uygulamaya ait kök dizinin alt dizinlerinin dil veya kültür temel alabilir. Bir derlemeyi kültüre özniteliğinde bilgisi yoksa, bu kültürün adı ile uygulama dizininin bir alt dizinde olması gerekir.  
  
-   Genel Derleme Önbelleği.  
  
     Ortak dil çalışma zamanı yüklü olduğu her yerde, yüklü olan bir makine düzeyinde kod önbelleği budur. Bir derlemeyi birden çok uygulama ile paylaşmak istiyorsanız, çoğu durumda, bu genel bütünleştirilmiş kod önbelleğine dağıtmanız gerekir.  
  
-   Bir HTTP sunucusu.  
  
     Bir HTTP sunucusu üzerinde dağıtılan bir derlemeyi tanımlayıcı bir ada sahip olmalıdır; Uygulamanın yapılandırma dosyasına bir kod temelinde bölümündeki derleme gelin.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)
- [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)
- [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
