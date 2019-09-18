---
title: .NET Native Yansıtma API'si Başvurusu
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c1fbef46231fed3af0d335e9396b301fe503254
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71049391"
---
# <a name="net-native-reflection-api-reference"></a>.NET Native Yansıtma API'si Başvurusu
.NET Native üç yeni özel durum türü içerir: [System. Runtime. CompilerServices. MissingInteropDataException](missinginteropdataexception-class-net-native.md), [System. Reflection. MissingMetadataException](missingmetadataexception-class-net-native.md)ve [System. Reflection. MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). Üç özel durum türü hakkında aşağıdakilere göz önünde edin:  
  
 Bu türler yalnızca iç kullanım içindir.  
 Bu üç özel durum türü yalnızca .NET Native araç zincirinin kullanımı içindir. .NET Native araç zinciri, program yürütmenin devam etmesine izin verilmeyen eksik verileri algıladığında özel durumlar oluşur.  
  
 Kodunuzda bu özel durumları işlemeyin.  
 Bu özel durumlar, uygulamanız için gereken meta verilerin olmadığını ( [MissingInteropDataException](missinginteropdataexception-class-net-native.md) ve [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumları) veya uygulamanız için [gereken uygulama kodunu eksik olduğunu belirtir ( MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu). Gerekli meta verileri veya uygulama kodunu çalışma zamanında kullanılabilir hale getirmek için bir çalışma zamanı yönergeleri (. RD. xml) dosyasını değiştirerek bu özel durum koşullarını düzeltebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md). [MissingMetadataException](missingmetadataexception-class-net-native.md) ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlarını ortadan kaldıracak çalışma zamanı yönergeleri dosyanız için uygun girişleri sağlayan iki sorun giderici mevcuttur:  
  
- Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
  
- Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Bu başvuru .NET Native için benzersiz olan üç özel durum türünü belgeler. .NET Framework Çekirdek yansıma API 'si için başvuru belgeleri için, ve <xref:System.Reflection> <xref:System.Reflection.Emit> ad alanları <xref:System.Reflection.Context> ' na bakın. .NET Framework Çekirdek birlikte çalışma API 'SI için başvuru belgeleri için bkz <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>System. Reflection ad alanı  
 Ad <xref:System.Reflection> alanı, .NET Framework yansıma için kullanılan çekirdek türlerini içerir. .NET Native için Ayrıca iki yeni özel durum türü de içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[MissingMetadataException](missingmetadataexception-class-net-native.md)|Mevcut olmayan meta verileri almak için yansıma kullanıldığında oluşturulan özel durum.|  
|[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)|Bir tür veya tür üyesi için meta veriler kullanılabilir olduğunda, ancak uygulanması kaldırıldığında oluşturulan özel durum.|  
  
 Bu ad alanındaki diğer türler hakkındaki belgeler için .NET Framework belge kümesindeki <xref:System.Reflection> başvuru sayfalarına bakın.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System. Runtime. CompilerServices Ad alanı  
 Ad <xref:System.Runtime.CompilerServices> alanı, dil derleyicileri tarafından Kullanıcı için tasarlanan türleri içerir. .NET Native için, yeni bir özel durum türü de içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[MissingInteropDataException](missinginteropdataexception-class-net-native.md)|Bir el ile sıralama yöntemi çağrıldığında oluşturulan özel durum, ancak bir türün meta verileri statik analiz veya çalışma zamanı yönergeleri dosyasında bulunamamıştır.|  
  
 Bu ad alanındaki diğer türler hakkındaki belgeler için .NET Framework belge kümesindeki <xref:System.Runtime.CompilerServices> başvuru sayfalarına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MissingInteropDataException Sınıfı](missinginteropdataexception-class-net-native.md)
- [MissingMetadataException Sınıfı](missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](missingruntimeartifactexception-class-net-native.md)
- [Başlarken](getting-started-with-net-native.md)
