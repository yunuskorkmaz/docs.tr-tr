---
title: Yansıma ve .NET Yerel
ms.date: 03/30/2017
ms.assetid: 91c9eae4-c641-476c-a06e-d7ce39709763
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 17b567fe0f476e689a9775c5c73ebf068424e840
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049281"
---
# <a name="reflection-and-net-native"></a>Yansıma ve .NET Yerel
.NET Framework yönetilen geliştirme, yansıma API 'SI aracılığıyla meta programlamayı destekler. Yansıma, bir uygulamadaki nesneleri incelemenize, İnceleme aracılığıyla bulunan nesnelerde Yöntemler çağırmasına, çalışma zamanında yeni türler oluşturmanıza ve diğer birçok dinamik kod senaryosunu desteketmenize olanak tanır. Ayrıca, bir nesnenin alan değerlerinin kalıcı olmasını ve daha sonra geri yüklenmesini sağlayan serileştirme ve serisini kaldırma de desteklenir. Bu senaryoların hepsi, kullanılabilir meta verilere dayalı yerel kod oluşturmak için .NET Framework tam zamanında (JıT) derleyicisi gerektirir.  
  
 .NET Native çalışma zamanı bir JıT derleyicisi içermez. Sonuç olarak, gerekli tüm yerel kodun önceden oluşturulması gerekir. Hangi kodun oluşturulması gerektiğini belirlemek için bir buluşsal yöntem kümesi kullanılır, ancak bu buluşsal yöntemler olası tüm meta programlama senaryolarını kapsamaz.  Bu nedenle, [çalışma zamanı yönergeleri](runtime-directives-rd-xml-configuration-file-reference.md)kullanarak bu meta programlama senaryolarına yönelik ipuçları sağlamalısınız. Gerekli meta veriler veya uygulama kodu çalışma zamanında kullanılabilir değilse, uygulamanız bir [MissingMetadataException](missingmetadataexception-class-net-native.md), [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)veya [MissingInteropDataException](missinginteropdataexception-class-net-native.md) özel durumu oluşturur. Çalışma zamanı yönergeleri dosyası için özel durumu ortadan kaldıran uygun girişi oluşturacak iki sorun giderici mevcuttur:  
  
- Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
  
- Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Çalışma zamanı yönergeleri dosyasının neden gerekli olduğuna ilişkin arka plan sağlayan .NET Native derleme işlemine genel bakış için, bkz. [.NET Native ve derleme](net-native-and-compilation.md).  
  
 Ayrıca .NET Native, .NET Framework sınıf kitaplığının özel üyelerini yansıtmasına izin vermez. Örneğin, bir .NET Framework sınıf kitaplığı türünün <xref:System.Reflection.TypeInfo.DeclaredFields%2A?displayProperty=nameWithType> alanlarını almak için özelliğine yapılan bir çağrı yalnızca ortak veya korumalı alanları döndürür.  
  
 Aşağıdaki konular, uygulamalarınızda yansıma ve Serileştirmeyi desteklemek için ihtiyacınız olan kavramsal ve başvuru belgelerini sağlar:  
  
- [Yansıma Kullanan API'ler](apis-that-rely-on-reflection.md)  
  
- [Yansıma API'si Başvurusu](net-native-reflection-api-reference.md)  
  
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET Native ile Uygulama Derleme](index.md)
- [.NET Native ve Derleme](net-native-and-compilation.md)
