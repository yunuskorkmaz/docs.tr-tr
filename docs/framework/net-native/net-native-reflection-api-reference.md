---
title: .NET Native Yansıtma API'si Başvurusu
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
ms.openlocfilehash: 01678ea6230a53416f213730ae6bb66e6bc057f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73128226"
---
# <a name="net-native-reflection-api-reference"></a>.NET Native Yansıtma API'si Başvurusu
.NET Native üç yeni özel durum türü içerir: [System. Runtime. CompilerServices. MissingInteropDataException](missinginteropdataexception-class-net-native.md), [System. Reflection. MissingMetadataException](missingmetadataexception-class-net-native.md)ve [System. Reflection. MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md). Üç özel durum türü hakkında aşağıdakilere göz önünde edin:  
  
 Bu türler yalnızca iç kullanım içindir.  
 Bu üç özel durum türü yalnızca .NET Native araç zincirinin kullanımı içindir. .NET Native araç zinciri, program yürütmenin devam etmesine izin verilmeyen eksik verileri algıladığında özel durumlar oluşur.  
  
 Kodunuzda bu özel durumları işlemeyin.  
 Bu özel durumlar, uygulamanız için gereken meta verilerin olmadığını ( [MissingInteropDataException](missinginteropdataexception-class-net-native.md) ve [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumları) veya uygulamanız için gereken uygulama kodunu eksik ( [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumu) olduğunu gösterir. Gerekli meta verileri veya uygulama kodunu çalışma zamanında kullanılabilir hale getirmek için bir çalışma zamanı yönergeleri (. RD. xml) dosyasını değiştirerek bu özel durum koşullarını düzeltebilirsiniz. Daha fazla bilgi için bkz. [çalışma zamanı yönergeleri (RD. xml) yapılandırma dosyası başvurusu](runtime-directives-rd-xml-configuration-file-reference.md). [MissingMetadataException](missingmetadataexception-class-net-native.md) ve [MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md) özel durumlarını ortadan kaldıracak çalışma zamanı yönergeleri dosyanız için uygun girişleri sağlayan iki sorun giderici mevcuttur:  
  
- Türler için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) .  
  
- Metotlar için [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) .  
  
> [!NOTE]
> Bu başvuru .NET Native için benzersiz olan üç özel durum türünü belgeler. .NET Framework Çekirdek yansıma API 'SI için başvuru belgeleri için, <xref:System.Reflection> <xref:System.Reflection.Context> ve ad alanları ' na bakın <xref:System.Reflection.Emit> . .NET Framework Çekirdek birlikte çalışma API 'SI için başvuru belgeleri için bkz <xref:System.Runtime.InteropServices> ..  
  
## <a name="systemreflection-namespace"></a>System. Reflection ad alanı  
 <xref:System.Reflection>Ad alanı, .NET Framework yansıma için kullanılan çekirdek türlerini içerir. .NET Native için Ayrıca iki yeni özel durum türü de içerir:  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|[MissingMetadataException](missingmetadataexception-class-net-native.md)|Mevcut olmayan meta verileri almak için yansıma kullanıldığında oluşturulan özel durum.|  
|[MissingRuntimeArtifactException](missingruntimeartifactexception-class-net-native.md)|Bir tür veya tür üyesi için meta veriler kullanılabilir olduğunda, ancak uygulanması kaldırıldığında oluşturulan özel durum.|  
  
 Bu ad alanındaki diğer türler hakkındaki belgeler için <xref:System.Reflection> .NET Framework belge kümesindeki başvuru sayfalarına bakın.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System. Runtime. CompilerServices Ad alanı  
 <xref:System.Runtime.CompilerServices>Ad alanı, dil derleyicileri tarafından Kullanıcı için tasarlanan türleri içerir. .NET Native için, yeni bir özel durum türü de içerir:  
  
|Sınıf|Açıklama|  
|-----------|-----------------|  
|[MissingInteropDataException](missinginteropdataexception-class-net-native.md)|Bir el ile sıralama yöntemi çağrıldığında oluşturulan özel durum, ancak bir türün meta verileri statik analiz veya çalışma zamanı yönergeleri dosyasında bulunamamıştır.|  
  
 Bu ad alanındaki diğer türler hakkındaki belgeler için <xref:System.Runtime.CompilerServices> .NET Framework belge kümesindeki başvuru sayfalarına bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MissingInteropDataException Sınıfı](missinginteropdataexception-class-net-native.md)
- [MissingMetadataException Sınıfı](missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](missingruntimeartifactexception-class-net-native.md)
- [Başlarken](getting-started-with-net-native.md)
