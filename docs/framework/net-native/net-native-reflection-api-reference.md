---
title: .NET Native Yansıtma API'si Başvurusu
ms.date: 03/30/2017
ms.assetid: 0429c049-22a3-4ba1-9cc8-f6ee91e31d9c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea47b8402f1bd2f66c957ff9126c8dff094a7ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="net-native-reflection-api-reference"></a>.NET Native Yansıtma API'si Başvurusu
[!INCLUDE[net_native](../../../includes/net-native-md.md)] üç yeni özel durum türleri içerir: [System.Runtime.CompilerServices.MissingInteropDataException](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md), [System.Reflection.MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md), ve [ System.Reflection.MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md). Tüm üç özel durum türleri hakkında aşağıdakileri unutmayın:  
  
 Bu tür yalnızca dahili kullanım içindir.  
 Bu üç özel durum türleri için kullanımı olan [!INCLUDE[net_native](../../../includes/net-native-md.md)] aracı yalnızca zinciri. Ne zaman özel durumlar [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri program yürütme devam etmek izin verme eksik veri algılar.  
  
 Bu özel durumlar, kodunuzda işleyemez.  
 Bu özel durumları, uygulama tarafından gerek duyulan ya da bu meta verileri yok belirtmek ( [Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md) ve [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumlar) ya da bu uygulama kodu gerekli uygulamanızı eksik ( [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durum). Çalışma zamanı yönergeleri değiştirerek bu özel durumları düzeltmek (. rd.xml) gerekli meta veri veya uygulama kodu çalışma zamanında kullanılabilmesi için dosya. Daha fazla bilgi için bkz: [çalışma zamanı yönergeleri (rd.xml) yapılandırma dosyası başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md). İki sorun gidericileri kullanılabilir ortadan kaldırır, çalışma zamanı yönergeleri dosyanızı için uygun girdileri tedarik [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) ve [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md) özel durumlar:  
  
-   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/type.html) türleri için.  
  
-   [MissingMetadataException sorun gidericisini](http://dotnet.github.io/native/troubleshooter/method.html) yöntemleri için.  
  
> [!NOTE]
>  Bu başvuru özgü üç özel durum türleri belgeleri [!INCLUDE[net_native](../../../includes/net-native-md.md)]. .NET Framework Çekirdek yansıma API başvuru belgeleri için bkz [System.Reflection ad alanlarında](http://msdn.microsoft.com/library/gg145033.aspx). .NET Framework Çekirdek birlikte çalışma API başvuru belgeleri için bkz: <xref:System.Runtime.InteropServices>.  
  
## <a name="systemreflection-namespace"></a>System.Reflection ad alanı  
 <xref:System.Reflection> Ad alanı, .NET Framework'te yansıma için kullanılan çekirdek türleri içerir. İçin [!INCLUDE[net_native](../../../includes/net-native-md.md)], ayrıca iki yeni özel durum türleri içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)|Yansıma yer almayan meta verilerini almak için kullanılan olmadığında oluşan özel durum.|  
|[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)|Meta veri türü veya tür üyesi için kullanılabilir olmadığında oluşan özel durum ancak uygulaması kaldırıldı.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla belgeler için bkz: <xref:System.Reflection> başvuru sayfaları için .NET Framework belgeleri kümesi içinde.  
  
## <a name="systemruntimecompilerservices-namespace"></a>System.Runtime.CompilerServices ad alanı  
 <xref:System.Runtime.CompilerServices> Ad alanı, kullanıcı için dil derleyicileri tarafından tasarlanmış türleri içerir. İçin [!INCLUDE[net_native](../../../includes/net-native-md.md)], yeni bir özel durum türü de içerir:  
  
|örneği|Açıklama|  
|-----------|-----------------|  
|[Missingınteropdataexception](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)|Yöntemi hazırlama el ile çağrıldı, ancak meta veri türü için statik çözümleme tarafından veya bir çalışma zamanı yönergeleri dosyasında bulunamadığını zaman oluşturulur özel durum.|  
  
 Bu ad alanındaki diğer türleri hakkında daha fazla belgeler için bkz: <xref:System.Runtime.CompilerServices> başvuru sayfaları için .NET Framework belgeleri kümesi içinde.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [MissingInteropDataException Sınıfı](../../../docs/framework/net-native/missinginteropdataexception-class-net-native.md)  
 [MissingMetadataException Sınıfı](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)  
 [MissingRuntimeArtifactException Sınıfı](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
