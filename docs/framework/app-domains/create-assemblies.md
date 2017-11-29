---
title: "Derlemeler Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- single-file assemblies
- assemblies [.NET Framework], creating
- multifile assemblies
ms.assetid: 54832ee9-dca8-4c8b-913c-c0b9d265e9a4
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f5aa4b8fa5422ae126a6027c5fe3358925873782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="creating-assemblies"></a>Derlemeler Oluşturma
Bir IDE kullanarak tek bir dosya veya birden çok dosya derlemeleri oluşturabilirsiniz [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)], veya derleyicileri ve de tarafından sağlanan araçları [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. En basit derleme basit bir ad ve tek bir uygulama etki alanına yüklü olduğu bir tek dosyadır. Bu derleme uygulama dizininin dışındaki diğer derlemelerden tarafından başvurulamaz ve sürüm denetimi uygulanabilecek değil. Derlemenin oluşan uygulamayı kaldırmak için yalnızca şu bulunduğu dizini silin. Birçok geliştiriciler için bu özelliklere sahip bir derleme bir uygulamayı dağıtmak için gereken tek şey.  
  
 Birkaç kod modülleri ve kaynak dosyaları, birden fazla dosya derlemesi oluşturabilirsiniz. Birden çok uygulama tarafından paylaşılan bir derleme de oluşturabilirsiniz. Paylaşılan bir derleme güçlü bir adı olması gerekir ve genel derleme önbelleğinde dağıtılabilir.  
  
 Kod modülleri ve kaynaklarına aşağıdaki etkenlere bağlı olarak derlemeler halinde gruplandırma, birkaç seçeneğiniz vardır:  
  
-   Sürüm oluşturma  
  
     Aynı sürüm bilgisini içermelidir Grup modüller.  
  
-   Dağıtım  
  
     Grup kod modülleri ve modelinizi dağıtım desteği kaynaklar.  
  
-   Yeniden kullanma  
  
     Bunlar mantıksal olarak birlikte bazı amaç için kullanılıp kullanılamayacağını modülleri grup. Örneğin, türleri ve seyrek program bakımı için kullanılan sınıflar oluşan bir derlemeyi aynı bütünleştirilmiş kodda beklemeye getirilebilir. Ayrıca, birden çok uygulama ile paylaşmak istiyorsanız türleri bir derlemeye gruplandırılmalıdır ve derleme tanımlayıcı bir ad ile oturum açmış olmanız gerekir.  
  
-   Güvenlik  
  
     Aynı güvenlik izinleri gerektiren türleri içeren Grup modüller.  
  
-   Kapsamı  
  
     Görünürlüğü aynı bütünleştirilmiş sınırlandırılmalıdır türleri içeren Grup modüller.  
  
 Ortak dil çalışma zamanı derlemeleri yönetilmeyen COM uygulamalarına yaparken özel konuları göz önünde bulundurulmalıdır. Yönetilmeyen kod ile çalışma hakkında daha fazla bilgi için bkz: [.NET Framework bileşenlerini COM'da gösterme](../../../docs/framework/interop/exposing-dotnet-components-to-com.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemelerle programlama](../../../docs/framework/app-domains/programming-with-assemblies.md)  
 [Derleme sürümü oluşturma](../../../docs/framework/app-domains/assembly-versioning.md)  
 [Nasıl yapılır: tek dosyalı derleme oluşturma](../../../docs/framework/app-domains/how-to-build-a-single-file-assembly.md)  
 [Nasıl yapılır: birden fazla dosya derleme](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Çalışma zamanı derlemeleri nasıl bulur](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Birden çok dosya derlemeleri](../../../docs/framework/app-domains/multifile-assemblies.md)
