---
title: "&lt;gcAllowVeryLargeObjects&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- gcAllowVeryLargeObjects element
- <gcAllowVeryLargeObjects> element
ms.assetid: 5c7ea24a-39ac-4e5f-83b7-b9f9a1b556ab
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5db777f147e2eca7644d5b5f1a4bc18c8401ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltgcallowverylargeobjectsgt-element"></a>&lt;gcAllowVeryLargeObjects&gt; öğesi
64-bit platformlarda toplam boyutu 2 gigabayttan (GB) büyük olan dizileri etkinleştirir.  
  
 \<Yapılandırma > öğesi  
\<çalışma zamanı > öğesi  
\<gcAllowVeryLargeObjects > öğesi  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<gcAllowVeryLargeObjects    
   enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> Toplam boyutu 2 GB'tan büyük dizilerin 64-Bit platformlarda etkinleştirilip etkinleştirilmeyeceğini belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|Toplam boyutu 2 GB'den büyük diziler etkin değildir. Bu varsayılandır.|  
|`true`|Toplam boyutu 2 GB'den büyük diziler 64-bit platformlarda etkindir.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Çalışma zamanı başlatma seçenekleri hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulama yapılandırma dosyanızda bu öğenin kullanılması, boyutu 2 GB'tan büyük dizileri etkinleştirir, ancak nesne boyutu veya dizi boyutundaki diğer sınırlamaları değiştirmez:  
  
-   Bir dizideki öğelerin sayısı en fazla şudur: <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.  
  
-   Bir bayt dizisi ve tek baytlı yapı dizileri için herhangi tek bir boyuttaki en büyük dizin 2,147,483,591 (0x7FFFFFC7), diğer türler için ise 2,146,435,071'dir (0X7FEFFFFF).  
  
-   Dizeler ve dizi olmayan diğer nesnelerin en büyük boyutu değiştirilmez.  
  
> [!CAUTION]
>  Bu özelliği etkinleştirmeden önce uygulamanızın, tüm dizilerin 2 GB'dan daha küçük olduğunu varsayan güvenli olmayan kod içermediğinden emin olun. Örneğin, dizileri arabellek olarak kullanan güvenilir olmayan kod, dizilerin 2 GB boyutunu geçmeyeceği varsayımıyla yazılmışsa arabellek aşımlarına maruz kalabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir uygulama için bu özelliğin nasıl etkinleştirileceğini göstermektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <gcAllowVeryLargeObjects enabled="true" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
