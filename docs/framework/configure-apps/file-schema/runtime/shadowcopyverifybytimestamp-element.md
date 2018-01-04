---
title: "&lt;shadowCopyVerifyByTimestamp&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bae98c91c8a9b68ec7c21b142bc9f004c7bc1394
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltshadowcopyverifybytimestampgt-element"></a>&lt;shadowCopyVerifyByTimestamp&gt; öğesi
Gölge kopyalama sunulan varsayılan başlangıç davranışını kullanıp kullanmadığını belirtir [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], veya .NET Framework'ün önceki sürümlerinde başlangıç davranışını döner.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<shadowCopyVerifyByTimestamp > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Etkin|Gerekli öznitelik.<br /><br /> Gölge kopyalama kullanan uygulama etki alanları derleme zaman damgaları, bir derlemeyi derleme kopyalama gölge önce güncelleştirilmiş olup olmadığını belirlemek için başlangıç karşılaştırmak olup olmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|true|Başlangıçta, yalnızca son gölge kopya dizinine kopyalanan bu yana güncelleştirilen derlemeleri kopyalar. Bunun için varsayılan değer [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].|  
|false|.NET Framework'ün önceki sürümlerini başlangıç davranışını Başlangıçta tüm dosyaları kopyalamak için olduğu döner.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], derlemeler yalnızca kendi zaman damgaları gölge kopya dizinine son kopyalanan sonra bunlar değişmiş gösteriyorsa gölge olan. Bu açıklandığı gibi gölge kopyalama, kullanmak pek çok uygulama başlatma sürelerini artırır [gölge kopyalama derlemeleri](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md). Yüksek yüzdesi ve derleme güncelleştirmelerinin sıklığını uygulamaları bu davranış değişikliği yararlı değil. Bu durumda, .NET Framework'ün önceki sürümlerini davranışını geri yüklemek için bu öğeyi kullanın.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, gölge kopyalama varsayılan başlangıç davranışını devre dışı bırakma gösterir [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]ve .NET Framework'ün önceki sürümlerini başlangıç davranışını dönebilirsiniz.  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Gölge Kopyalama Bütünleştirilmiş Kodları](../../../../../docs/framework/app-domains/shadow-copy-assemblies.md)
