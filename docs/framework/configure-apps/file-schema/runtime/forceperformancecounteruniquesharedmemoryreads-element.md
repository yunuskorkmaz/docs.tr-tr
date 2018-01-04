---
title: "&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; öğesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 602359b713adfd4adf90d3e18f5f434d50c92ef4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltforceperformancecounteruniquesharedmemoryreadsgt-element"></a>&lt;forcePerformanceCounterUniqueSharedMemoryReads&gt; öğesi
PerfCounter.dll CategoryOptions kayıt defteri ayarını bir .NET Framework sürüm 1.1 uygulamasında kategoriye özel paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemeye karar vermek için kullanıp kullanmadığını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<forcePerformanceCounterUniqueSharedMemoryReads >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads   
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> PerfCounter.dll kategoriye özel paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemeye karar vermek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|PerfCounter.dll CategoryOptions kullanmaz kayıt defteri ayarı bu varsayılan değerdir.|  
|`true`|PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Önce .NET Framework sürümlerinde [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], işlemde yüklendi çalışma zamanı yüklendi PerfCounter.dll sürümü corresponded. Bir bilgisayar hem de .NET Framework sürüm 1.1 sahip ve [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] yüklü .NET Framework 1.1 uygulamayı PerfCounter.dll .NET Framework 1.1 sürümünü yüklemek. İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], PerfCounter.dll yüklü en son sürümü yüklendi. Bir .NET Framework 1.1 uygulamasını yükleyecek yani [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll sürümü varsa [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] bilgisayara yüklendi.  
  
 İle başlayarak [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], performans sayaçları kullanırken PerfCounter.dll CategoryOptions kayıt defteri girdisini paylaşılan bellek kategoriye özel veya genel paylaşılan bellek gözükmelidir olup olmadığını belirlemek her bir sağlayıcı için denetler. .NET Framework 1.1 PerfCounter.dll kategoriye özel paylaşılan bellek farkında olmadığından bu kayıt defteri girişi okumaz; her zaman, genel Paylaşılan bellekten okur.  
  
 Geriye dönük uyumluluk için [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] PerfCounter.dll bir .NET Framework 1.1 uygulamasında çalıştırırken CategoryOptions kayıt defteri girdisini denetlemez. Bu, yalnızca .NET Framework 1.1 PerfCounter.dll gibi genel paylaşılan bellek kullanır. Ancak, söyleyebilirsiniz [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] kayıt defteri ayarını etkinleştirerek denetlemek için PerfCounter.dll `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi.  
  
> [!NOTE]
>  Etkinleştirme `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi garanti etmez kategoriye özel paylaşılan bellek kullanılacak. Ayar için etkin `true` yalnızca CategoryOptions kayıt defteri ayarı başvurmak PerfCounter.dll neden olur. CategoryOptions için varsayılan ayar kategorisi özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan bellek kullanılması gerektiğini belirtmek için CategoryOptions değiştirebilirsiniz.  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services CategoryOptions ayarını içeren kayıt defteri anahtarıdır\\< categoryName\>\Performance. Varsayılan olarak, CategoryOptions 3, hangi PerfCounter.dll bildirir kategoriye özel paylaşılan bellek kullanmak üzere ayarlanmış. CategoryOptions 0 olarak ayarlarsanız, PerfCounter.dll genel paylaşılan bellek kullanır. Oluşturulan örneğinin adını yeniden kullanılıyor örneğine aynı ise örnek verileri yeniden kullanılabilir. Tüm sürümleri için kategori yazma kuramaz. CategoryOptions 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak aynı uzunlukta yeniden kullanılıyor kategorisi kategori adı ise, örnek verileri yeniden kullanılabilir.  
  
 0 ve 1 ayarları bellek sızıntıları ve yukarı doldurma performans sayacı bellek yol açabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, PerfCounter.dll kategori özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için CategoryOptions kayıt defteri girdisini başvurmalısınız belirtin gösterilmektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
