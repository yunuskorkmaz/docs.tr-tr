---
title: .NET Native Yansıtma API'si Başvurusu
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a2a27f788fa84c41ccb818266fffc816237bb48
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44139286"
---
# <a name="net-native-reflection-api-reference"></a>.NET Native Yansıtma API'si Başvurusu
[!INCLUDE[net_native](../../../includes/net-native-md.md)] üç yeni özel durum türleri içerir: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), ve [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Tüm üç özel durum türleri hakkında aşağıdakileri unutmayın:  
  
 Bu tür, yalnızca dahili kullanım içindir.  
 Bu üç özel durum türleri için kullanımını olan [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri. Ne zaman özel durumlar [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri, program yürütme işleminin devam etmesini izin vermeyen eksik veri algılar.  
  
 Bu özel durumlar, kodunuzda işleyemez.  
 Bu özel durumlar uygulamanızın ihtiyaç duyduğu ya da bu meta veri eksik olduğunu belirten ( [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) ve [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumlar) veya ilgili uygulama kodu Gerekli uygulama eksik ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum). Bir çalışma zamanı yönergeleri değiştirerek bu özel durum koşullarını düzeltin (. rd.xml) gerekli meta veriler veya uygulama kodu çalışma zamanında kullanılabilir hale getirmek için dosya. Daha fazla bilgi için [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). İki sorun gidericileri kullanılabilir uygun girişleri ortadan kaldıracak çalışma zamanı yönergeleri dosyanız için tedarik [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar:  
  
-   [MissingMetadataException sorun giderici](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
-   [MissingMetadataException sorun giderici](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
> [!NOTE]
>  Bu başvuru için benzersiz olan üç özel durum türlerini belgeleri [!INCLUDE[net_native](../../../includes/net-native-md.md)]. .NET Framework Çekirdek yansıma API'si için başvuru belgeleri için bkz. [System.Reflection ad alanlarında](https://msdn.microsoft.com/library/gg145033.aspx). .NET Framework Çekirdek birlikte çalışma API'si için başvuru belgeleri için bkz. <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>System.Reflection ad alanı  
 <xref:System.Reflection> Ad alanı, .NET Framework'te yansıma için kullanılan temel türleri içerir. İçin [!INCLUDE[net_native](../../../includes/net-native-md.md)], iki yeni özel durum türlerini de içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Yansıma mevcut olmayan meta verilerini almak için kullanıldığında oluşan özel durum.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Bir tür veya üye türü için meta veriler kullanılabilir olduğunda oluşturulan özel durum ancak uygulanması kaldırıldı.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla bilgi için bkz <xref:System.Reflection> .NET Framework dokümantasyon setinde sayfalarında başvuru.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices ad alanı  
 <xref:System.Runtime.CompilerServices> Ad alanı için kullanıcı, dil derleyiciler tarafından tasarlanmış türleri içerir. İçin [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayrıca yeni bir özel durum türü içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Yöntem hazırlama el ile olarak adlandırılır, ancak bir türü için meta verileri statik analiz tarafından veya bir çalışma zamanı yönergeleri dosyası bulunamadıysa oluşturulan özel durum.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla bilgi için bkz <xref:System.Runtime.CompilerServices> .NET Framework dokümantasyon setinde sayfalarında başvuru.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MissingInteropDataException Sınıfı](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [MissingMetadataException Sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [MissingRuntimeArtifactException Sınıfı](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
