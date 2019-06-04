---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26fed0a10b9a25f25a580c7ac9a468cbedeb3671
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66489476"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Element
PerfCounter.dll CategoryOptions kayıt defteri ayarı bir .NET Framework sürüm 1.1 uygulamasında kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için kullanıp kullanmayacağını belirtir.  
  
 \<Yapılandırma >  
\<çalışma zamanı >  
\<forcePerformanceCounterUniqueSharedMemoryReads>  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> PerfCounter.dll kategoriye özgü paylaşılan bellek ya da genel bellek performans sayacı verilerini yüklemek karar vermek için CategoryOptions kayıt defteri ayarı kullanıp kullanmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|PerfCounter.dll CategoryOptions kullanmayan kayıt defteri ayarı bu varsayılan değerdir.|  
|`true`|PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanın.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4 önce .NET Framework sürümlerinde, işlemde yüklü çalışma zamanı sürümü yüklendi PerfCounter.dll corresponded. Bir bilgisayar hem de .NET Framework sürüm 1.1 sahip olduğu ve [!INCLUDE[dnprdnlong](../../../../../includes/dnprdnlong-md.md)] yüklü .NET Framework 1.1 uygulama PerfCounter.dll .NET Framework 1.1 sürümü yüklenir. .NET Framework 4 ile başlayarak, PerfCounter.dll en yeni yüklü sürümü yüklendi. Başka bir deyişle, bilgisayarda .NET Framework 4 yüklü değilse .NET Framework 1.1 uygulama PerfCounter.dll .NET Framework 4 sürümünü yükler.  
  
 Performans sayaçları tüketildiğinde .NET Framework 4 ile başlayarak, paylaşılan bellek kategorisi özel veya genel paylaşılan bellek gözükmelidir olup olmadığını belirlemek her bir sağlayıcı CategoryOptions kayıt defteri girişini PerfCounter.dll denetler. Kategori özgü paylaşılan bellek farkında olmadığından System.Numerics.vectors.dll o kayıt defteri girdisini .NET Framework 1.1 PerfCounter.dll okumaz; her zaman, paylaşılan genel bellekten okur.  
  
 Geriye dönük uyumluluk için bir .NET Framework 1.1 uygulamasında çalışırken CategoryOptions kayıt defteri girdisini .NET Framework 4 PerfCounter.dll denetlemez. Yalnızca, .NET Framework 1.1 PerfCounter.dll gibi genel paylaşılan bellek kullanır. Ancak, kayıt defteri ayarı etkinleştirerek denetlemek için .NET Framework 4 PerfCounter.dll söyleyebilirsiniz `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi.  
  
> [!NOTE]
>  Etkinleştirme `<forcePerformanceCounterUniqueSharedMemoryReads>` öğesi kategorisi özgü paylaşılan bellek kullanılacak garantilemez. Ayar için etkin `true` PerfCounter.dll CategoryOptions kayıt defteri ayarı başvurmak yalnızca neden olur. Kategori özgü paylaşılan bellek kullanmasına CategoryOptions için varsayılan ayar olan; Ancak, genel paylaşılan bellek kullanılması gerektiğini belirtmek için CategoryOptions değiştirebilirsiniz.  
  
 HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services CategoryOptions ayarları içeren kayıt defteri anahtarıdır\\< categoryName\>\Performance. Varsayılan olarak, CategoryOptions 3'e hangi PerfCounter.dll bildirir kategoriye özgü paylaşılan bellek kullanacak şekilde ayarlanır. CategoryOptions 0 olarak ayarlarsanız, PerfCounter.dll genel paylaşılan bellek kullanır. Örnek verileri yeniden oluşturulan örneğinin adını yeniden kullanılıyor örnekle aynı ise kullanılabilir. Tüm sürümler kategorisine yazma mümkün olacaktır. CategoryOptions 1 olarak ayarlarsanız, genel paylaşılan bellek kullanılır, ancak aynı uzunlukta yeniden kullanılıyor kategorisi kategori adı ise, örnek verileri yeniden kullanılabilir.  
  
 0 ile 1 ayarları, bellek sızıntılarını ve yukarı doldurmanın performans sayacı bellek neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, PerfCounter.dll kategoriye özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için CategoryOptions kayıt defteri girdisini başvurmalıdır belirtmek gösterilmektedir.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Yapılandırma Dosyası Şeması](../../../../../docs/framework/configure-apps/file-schema/index.md)
