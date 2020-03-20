---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 742b444c445ba67d6977b622e615a6a8f591826e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154146"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
PerfCounter.dll'nin kategoriye özgü paylaşılan bellekten veya genel bellekten performans sayacı verilerini yükleyip yüklemeyeceğini belirlemek için bir .NET Framework sürüm 1.1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmayacağını belirtir.  
  
[**\<yapılandırma>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<çalışma zamanı>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
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
|`enabled`|Gerekli öznitelik.<br /><br /> PerfCounter.dll'nin kategoriye özgü paylaşılan bellekten veya genel bellekten performans sayacı verilerini yükleyip yüklemeyeceğini belirlemek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını gösterir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|PerfCounter.dll CategoryOptions kayıt defteri ayarı bu varsayılan kullanmaz.|  
|`true`|PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  
 .NET Framework 4'ten önceki .NET Framework sürümlerinde, yüklenilen PerfCounter.dll sürümü, işlemde yüklenen çalışma süresine karşılık gelir. Bir bilgisayarda hem .NET Framework sürüm 1.1 hem de .NET Framework 2.0 yüklü olsaydı, bir .NET Framework 1.1 uygulaması PerfCounter.dll'nin .NET Framework 1.1 sürümünü yükler. .NET Framework 4'ten başlayarak, PerfCounter.dll'nin en yeni yüklü sürümü yüklenir. Bu, bilgisayara .NET Framework 4 yüklenirse ,NET Framework 1.1 uygulamasının PerfCounter.dll'nin .NET Framework 4 sürümünü yükleyeceği anlamına gelir.  
  
 Performans sayaçlarını tüketirken .NET Framework 4'ten başlayarak PerfCounter.dll, kategoriye özgü paylaşılan bellekten mi yoksa genel paylaşılan bellekten mi okunması gerektiğini belirlemek için her sağlayıcı için CategoryOptions kayıt defteri girişini denetler. .NET Framework 1.1 PerfCounter.dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, kayıt defteri girişini okumaz; her zaman genel paylaşılan bellekten okur.  
  
 Geriye dönük uyumluluk için .NET Framework 4 PerfCounter.dll, .NET Framework 1.1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez. Sadece .NET Framework 1.1 PerfCounter.dll gibi, küresel paylaşılan bellek kullanır. Ancak, .NET Framework 4 PerfCounter.dll öğesini etkinleştirerek kayıt defteri `<forcePerformanceCounterUniqueSharedMemoryReads>` ayarını denetlemesi için talimat verebilirsiniz.  
  
> [!NOTE]
> Öğeyi `<forcePerformanceCounterUniqueSharedMemoryReads>` etkinleştirmek, kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez. Yalnızca PerfCounter.dll'nin CategoryOptions kayıt defteri ayarına başvurmasına neden olacak şekilde etkinleştirildi. `true` CategoryOptions için varsayılan ayar kategoriye özgü paylaşılan bellek kullanmaktır; ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions'ı değiştirebilirsiniz.  
  
 CategoryOptions ayarını içeren kayıt defteri anahtarı\\ HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\><categoryName \Performance'tır. Varsayılan olarak, CategoryOptions 3 olarak ayarlanır ve bu da PerfCounter.dll'ye kategoriye özgü paylaşılan belleği kullanmasını bildirir. CategoryOptions 0 olarak ayarlanmışsa, PerfCounter.dll genel paylaşılan bellek kullanır. Örnek veriler, yalnızca oluşturulan örneğin adı yeniden kullanılan örnekle aynıysa yeniden kullanılır. Tüm sürümler kategoriye yazabilecektir. CategoryOptions 1 olarak ayarlanmışsa, genel paylaşılan bellek kullanılır, ancak kategori adı yeniden kullanılan kategoriyle aynı uzunluktaysa örnek verileri yeniden kullanılabilir.  
  
 0 ve 1 ayarları bellek sızıntılarına ve performans sayacı belleği doldurmasına neden olabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, PerfCounter.dll'nin kategoriye özgü paylaşılan bellek kullanıp kullanmaması gerektiğini belirlemek için CategoryOptions kayıt defteri girişine başvurması gerektiğinin nasıl belirtilen bir şekilde belirtilen.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı Ayarları Şeması](index.md)
- [Yapılandırma Dosyası Şeması](../index.md)
