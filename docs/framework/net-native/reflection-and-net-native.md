---
title: Yansıma ve .NET Yerel
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c92d71c9862dfbdace4de2e30cf48ace7becfd0b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59105863"
---
# <a name="reflection-and-net-native"></a>Yansıma ve .NET Yerel
.NET Framework'te yansıma API'si azaltılarak geliştirme destekleyen yönetilen. Yansıma, uygulama nesneleri incelemek, inceleme bulunan nesneler üzerinde yöntemleri çağırmak, çalışma zamanında yeni türler oluşturmak sağlar ve birçok diğer dinamik kod senaryolarını destekler. Serileştirme ve serisini kaldırma kalıcı yapılabilir ve daha sonra geri bir nesnenin alan değerlerini tanır de destekler. Tüm bu senaryolar için kullanılabilir meta verileri temel alarak yerel kod oluşturmak için .NET Framework just-ın-time (JIT) derleyici gerektirir.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Çalışma zamanı JIT derleyicisi içermez. Sonuç olarak, tüm gerekli yerel kodu önceden oluşturulmuş olmalıdır. Hangi kod oluşturulması belirlemek için buluşsal yöntem kümesi kullanılır, ancak bu buluşsal yöntemler, tüm olası azaltılarak senaryolar kapsamamaktadır.  Bu nedenle, ipuçları azaltılarak bu senaryolar için kullanarak sağlamanız gereken [çalışma zamanı yönergeleri](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). Gerekli meta veriler veya uygulama kodu çalışma zamanında kullanılabilir değilse, uygulamanızı oluşturur bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md), veya [ Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) özel durum. İki sorun gidericileri kullanılabilir özel durumu ortadan kaldıran çalışma zamanı yönergeleri dosyanız için uygun giriş oluşturacağını:  
  
-   [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
-   [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
> [!NOTE]
>  Arka plan üzerinde neden sağlayan .NET yerel derleme işlemine genel bakış için bir çalışma zamanı yönergeleri dosyası, bkz. gerekli [.NET Native ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).  
  
 Ayrıca, [!INCLUDE[net_native](../../../includes/net-native-md.md)] , .NET Framework Sınıf Kitaplığı'nın özel üyeler üzerinde yansıtacak şekilde izin vermez. Örneğin, bir çağrı <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> alanları bir .NET Framework sınıf kitaplığı türü döndürür yalnızca ortak veya korumalı alanı almak için özellik.  
  
 Aşağıdaki konular, kavramsal sağlayın ve başvuru yansıma ve Serileştirme uygulamalarınızı desteklemek için ihtiyacınız olan belgeleri:  
  
-   [Yansıma kullanan API'ler](../../../docs/framework/net-native/apis-that-rely-on-reflection.md)  
  
-   [Yansıma API'si Başvurusu](../../../docs/framework/net-native/net-native-reflection-api-reference.md)  
  
-   [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Yerel ile Uygulama Derleme](../../../docs/framework/net-native/index.md)
- [.NET Yerel ve Derleme](../../../docs/framework/net-native/net-native-and-compilation.md)
