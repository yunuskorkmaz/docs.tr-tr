---
title: .NET Native Yansıtma API'si Başvurusu
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 833d31c48220e2d2b5d07ee482325df090714329
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66052416"
---
# <a name="net-native-reflection-api-reference"></a>.NET Native Yansıtma API'si Başvurusu
.NET native üç yeni özel durum türleri içerir: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), ve [System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) . Tüm üç özel durum türleri hakkında aşağıdakileri unutmayın:  
  
 Bu tür, yalnızca dahili kullanım içindir.  
 Bu üç özel durum türleri yalnızca .NET Native araç zincirinin kullanım içindir. .NET Native araç zinciri, program yürütme işleminin devam etmesini izin vermeyen eksik veri algıladığında özel durumlar.  
  
 Bu özel durumlar, kodunuzda işleyemez.  
 Bu özel durumlar uygulamanızın ihtiyaç duyduğu ya da bu meta veri eksik olduğunu belirten ( [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) ve [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumlar) veya ilgili uygulama kodu Gerekli uygulama eksik ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum). Bir çalışma zamanı yönergeleri değiştirerek bu özel durum koşullarını düzeltin (. rd.xml) gerekli meta veriler veya uygulama kodu çalışma zamanında kullanılabilir hale getirmek için dosya. Daha fazla bilgi için [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). İki sorun gidericileri kullanılabilir uygun girişleri ortadan kaldıracak çalışma zamanı yönergeleri dosyanız için tedarik [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar:  
  
- [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
- [MissingMetadataException sorun giderici](https://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
> [!NOTE]
>  .NET Native için benzersiz olan üç özel durum türleri bu başvuru belgeleri. .NET Framework Çekirdek yansıma API'si için başvuru belgeleri için bkz. <xref:System.Reflection>, <xref:System.Reflection.Context> ve <xref:System.Reflection.Emit> ad alanları. .NET Framework Çekirdek birlikte çalışma API'si için başvuru belgeleri için bkz. <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>System.Reflection ad alanı  
 <xref:System.Reflection> Ad alanı, .NET Framework'te yansıma için kullanılan temel türleri içerir. .NET Native için de iki yeni özel durum türlerini içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Yansıma mevcut olmayan meta verilerini almak için kullanıldığında oluşan özel durum.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Bir tür veya üye türü için meta veriler kullanılabilir olduğunda oluşturulan özel durum ancak uygulanması kaldırıldı.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla bilgi için bkz <xref:System.Reflection> .NET Framework dokümantasyon setinde sayfalarında başvuru.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices ad alanı  
 <xref:System.Runtime.CompilerServices> Ad alanı için kullanıcı, dil derleyiciler tarafından tasarlanmış türleri içerir. .NET Native için de yeni bir özel durum türü içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Yöntem hazırlama el ile olarak adlandırılır, ancak bir türü için meta verileri statik analiz tarafından veya bir çalışma zamanı yönergeleri dosyası bulunamadıysa oluşturulan özel durum.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla bilgi için bkz <xref:System.Runtime.CompilerServices> .NET Framework dokümantasyon setinde sayfalarında başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [MissingInteropDataException Sınıfı](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)
- [MissingMetadataException Sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)
- [MissingRuntimeArtifactException Sınıfı](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)
- [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
