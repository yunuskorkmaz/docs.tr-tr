---
title: Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache), serviced components
- serviced components, global assembly cache
- global assembly cache, serviced components
ms.assetid: 3423e5d9-234c-4571-8161-e35f6d130128
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 703e71661c7a679b85e60726f53b275fce1a4d6a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753358"
---
# <a name="using-serviced-components-with-the-global-assembly-cache"></a>Genel Derleme Önbelleği ile Hizmet Verilen Bileşenleri Kullanma
Hizmet verilen bileşenleri (yönetilen kod COM + bileşenleri), Genel Derleme Önbelleği'nde moduna geçirmelisiniz. Bazı senaryolarda, Genel Derleme Önbelleği'nde olmayan hizmet verilen bileşenler Ortak dil çalışma zamanı ve COM + hizmetlerinin işleyebilir; Diğer senaryolarda yapamazlar. Aşağıdaki senaryolar bu gösterilmektedir:  
  
-   Hizmet verilen bileşenleri içeren aynı dizinde Dllhost.exe çalıştırmadığı bir COM + sunucu uygulamasında hizmet verilen bileşenleri için bileşenlerini içeren derleme Genel Derleme Önbelleği'olmalıdır.  
  
-   COM + kitaplık uygulamasında hizmet verilen bileşenleri için çalışma zamanı ve COM + hizmetlerinin geçerli dizinde arama yaparak bileşenlerini içeren derleme başvurusunu çözebilirsiniz. Bu durumda, derleme genel derleme önbelleğinde olması gerekmez.  
  
-   Bir ASP.NET uygulamasında hizmet verilen bileşenleri için farklı bir durumdur. Hizmet verilen bileşenleri uygulamanın taban bin dizinindeki içeren derlemenin yerleştirin ve isteğe bağlı kayıt kullanırsanız, ASP.NET çalışma zamanı gölge özelliklerinden yararlanır çünkü derleme indirme önbelleğine gölge kopyalar olacaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bütünleştirilmiş Kodlar ve Genel Derleme Önbelleği ile Çalışma](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Gacutil.exe (Genel Derleme Önbelleği Aracı)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)
