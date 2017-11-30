---
title: "Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45fd02c4f87d33766741e6fd023f9b40b9964d63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
Hizmet verilen bileşenleri (yönetilen kod COM + bileşenleri), genel derleme önbelleğinde moduna geçirmelisiniz. Bazı senaryolarda, genel derleme önbelleğinde olmayan hizmet verilen bileşenler Ortak dil çalışma zamanı ve COM + hizmetlerinin işleyebilir; Diğer senaryolarda yapamazlar. Aşağıdaki senaryolar bu gösterilmektedir:  
  
-   Hizmet verilen bileşenleri içeren aynı dizinde Dllhost.exe çalıştırmadığı bir COM + sunucu uygulamasında hizmet verilen bileşenleri için bileşenlerini içeren derleme genel derleme önbelleğinde olmalıdır.  
  
-   COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + hizmetlerinin geçerli dizinde arama yaparak bileşenlerini içeren derleme başvurusunu çözebilirsiniz. Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.  
  
-   Bir ASP.NET uygulamasında hizmet verilen bileşenleri için farklı bir durumdur. Hizmet verilen bileşenleri uygulamanın taban bin dizinindeki içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanırsanız, ASP.NET çalışma zamanı gölge özelliklerinden yararlanır çünkü derleme indirme önbelleğine gölge kopyalar olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemeler ve genel derleme önbelleği ile çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
