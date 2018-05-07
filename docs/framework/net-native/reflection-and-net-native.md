---
title: Yansıma ve .NET Yerel
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee56107c5d8760f69a29d9e4ad6e1bd445d4831d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
  
-   [Yansıma Kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Yansıma API'si Başvurusu](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [.NET Native ile Uygulama Derleme](../../../docs/framework/net-native/index.md)  
 [.NET Native ve Derleme](../../../docs/framework/net-native/net-native-and-compilation.md)
