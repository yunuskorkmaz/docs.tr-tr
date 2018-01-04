---
title: "&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NetFx45_CultureAwareComparerGetHashCode_LongStrings element
- <NetFx45_CultureAwareComparerGetHashCode_LongStrings> element
- GetHashCode method
- hash codes, calculating
ms.assetid: 3a5f38d1-ebc8-44de-aaeb-2929f6e6b48f
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1c370bc9ea5f8c3cdbf8690c7e22788b1224f4df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltnetfx45cultureawarecomparergethashcodelongstringsgt-element"></a>&lt;NetFx45_CultureAwareComparerGetHashCode_LongStrings&gt; öğesi
Çalışma zamanı için karma kodları hesaplamak için sabit miktarlı bellek kullanıp kullanmadığını belirtir <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
< NetFx45_CultureAwareComparerGetHashCode_LongStrings >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml
<NetFx45_CultureAwareComparerGetHashCode_LongStrings enabled="0|1">  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Ortak dil çalışma zamanının karma kodları hesaplarken sabit miktarda bellek ayırıp ayırmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|0|Ortak dil çalışma zamanı bir değişken için bellek miktarı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodlarını hesaplamak için yöntem. Bu varsayılandır.|  
|1.|Sabit miktarlı bellek için ortak dil çalışma zamanı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> karma kodlarını hesaplamak için yöntem.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, ortak dil çalışma zamanı bir değişken için bellek miktarı ayırır <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi bir <xref:System.ArgumentException> yöntemi (birkaç milyon karakterden uzun) çok büyük dizeleri karma kodunu işlem girişiminde bulunduğunda oluşur. Bu öğe bir uygulama yapılandırma dosyası ve ayarı ekleyerek kendi `enabled` özniteliği, belirtin "1", <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> yöntemi karma kodlarını hesaplama için sabit miktarlı bellek ayırır alternatif bir algoritma kullanır.  
  
> [!IMPORTANT]
>  `<NetFx45_CultureAwareComparerGetHashCode_LongStrings>` Öğesi kullanılan değil [!INCLUDE[win8](../../../../../includes/win8-md.md)] ve sonraki sürümler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
