---
title: Derleme Konumu
ms.date: 03/30/2017
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91fc7cf6ea66952fa5770ce73ecb1a8c129a9a2d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743920"
---
# <a name="assembly-location"></a>Derleme Konumu
Derlemenin konumunu ortak dil çalışma zamanı, başvurulan sırasında bulabilir ve da derlemeyi diğer Derlemelerle paylaşılabilir olup olmadığını belirlemeniz olup olmadığını belirler. Bir derlemeyi aşağıdaki konumlarda dağıtabilirsiniz:  
  
-   Uygulamanın dizin veya dizin.  
  
     Bu, bir derlemeyi dağıtmak için en yaygın konumdur. Bir uygulamanın kök dizininin alt dizinleri dil veya kültür dayalı olabilir. Derleme kültür özniteliğinde bilgi varsa, bu kültürün adıyla uygulama dizininin altında bir alt dizinde olması gerekir.  
  
-   Genel Derleme Önbelleği.  
  
     Bu ortak dil çalışma zamanı yüklü olduğunda, yüklü olduğu bir makineye kod önbelleğidir. Birden çok uygulama ile bir derlemeyi paylaşmak istiyorsanız, çoğu durumda, bu genel derleme önbelleğine dağıtmanız gerekir.  
  
-   Bir HTTP sunucusunda.  
  
     Bir HTTP sunucusu üzerinde dağıtılan bir derleme tanımlayıcı adı olmalıdır; Uygulamanın yapılandırma dosyasına codebase bölümünü derlemede üzerine gelin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar Oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Çalışma Zamanının Bütünleştirilmiş Kodların Konumunu Bulması](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Bütünleştirilmiş Kodlarla Programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
