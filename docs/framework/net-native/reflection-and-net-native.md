---
title: "Yansıma ve .NET Yerel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d9e4bdc26815feab7910e7518f7cd691a1f4dece
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="reflection-and-net-native"></a>Yansıma ve .NET Yerel
.NET Framework geliştirme destekler API yansıma yoluyla meta yönetilen. Yansıma uygulama nesneleri inceleyin, inceleme bulunan nesnelerin yöntemleri çağırmak, çalışma zamanında yeni türleri oluşturmak olanak tanır ve diğer birçok dinamik kodu senaryolarını destekler. Seri hale getirme ve kalıcı ve daha sonra geri nesnenin alan değerlerini sağlayan seri durumdan çıkarma de destekler. Bu senaryolar tüm kullanılabilir meta verileri temel alarak yerel kodu oluşturmak için .NET Framework tam zamanında (JIT) derleyici gerektirir.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı JIT Derleyici içermez. Sonuç olarak, tüm gerekli yerel kod önceden oluşturulmuş olması gerekir. Buluşsal yöntemler kümesi hangi kod oluşturulması belirlemek için kullanılır, ancak bu buluşsal yöntemler tüm olası meta senaryolarını kapsamak olamaz.  Bu nedenle, ipuçlarını bu meta senaryolar için kullanarak sağlamanız gereken [çalışma zamanı yönergeleri](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Gerekli meta veri veya uygulama kodu çalışma zamanında kullanılabilir durumda değilse, uygulamanızı oluşturur bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), veya [ Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) özel durum. İki sorun gidericileri kullanılabilir özel ortadan kaldırır, çalışma zamanı yönergeleri dosyanızı uygun girişini üretir:  
  
-   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
-   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
> [!NOTE]
>  Arka plan üzerinde neden sağlar .NET yerel derleme işlemine genel bakış için bir çalışma zamanı yönergeleri dosyası, bkz: gerekli [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Ayrıca, [!INCLUDE[net_native](../../../includes/net-native-md.md)] özel üyeleri .NET Framework sınıf kitaplığı yansıtacak şekilde izin vermiyor. Örneğin, bir çağrı <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> özelliği bir .NET Framework sınıf kitaplığı Türü alanlarının döndürür yalnızca genel veya korumalı alanlar alınamadı.  
  
 Aşağıdaki konular kavramsal sağlamak ve yansıma ve seri hale getirme uygulamalarınızla desteklemeniz gereken belgelerine başvuru:  
  
-   [Yansıma kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Yansıtma API'si başvurusu](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET yerel ile uygulama derleme](../../../docs/framework/net-native/index.md)  
 [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md)
