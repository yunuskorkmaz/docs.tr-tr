---
title: Derleme Konumu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- locating assemblies
- assemblies [.NET Framework], location
ms.assetid: 9f1f41a7-2954-49d3-a2c0-62b6ef4d40ab
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e069c1636004896bfb193fd70a352195ba045865
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Derlemeleri oluşturma](../../../docs/framework/app-domains/create-assemblies.md)  
 [Genel Derleme Önbelleği](../../../docs/framework/app-domains/gac.md)  
 [Çalışma zamanı derlemeleri nasıl bulur](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Derlemelerle programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)
