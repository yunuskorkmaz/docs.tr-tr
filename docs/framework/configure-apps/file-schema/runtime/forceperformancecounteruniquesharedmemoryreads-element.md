---
title: <forcePerformanceCounterUniqueSharedMemoryReads> Öğesi
ms.date: 03/30/2017
helpviewer_keywords:
- forcePerformanceCounterUniqueSharedMemoryReads element
- <forcePerformanceCounterUniqueSharedMemoryReads> element
ms.assetid: 91149858-4810-4f65-9b48-468488172c9b
ms.openlocfilehash: 719448ba3de2aca0621fc17b9fadbdd3b8588f2e
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178248"
---
# <a name="forceperformancecounteruniquesharedmemoryreads-element"></a>\<forcePerformanceCounterUniqueSharedMemoryReads> Öğesi

PerfCounter.dll, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mı yoksa genel bellekten mi yükleneceğini öğrenmek için, .NET Framework sürüm 1,1 uygulamasında CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<forcePerformanceCounterUniqueSharedMemoryReads>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<forcePerformanceCounterUniqueSharedMemoryReads
enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`enabled`|Gerekli öznitelik.<br /><br /> PerfCounter.dll, performans sayacı verilerinin kategoriye özgü paylaşılan bellekten mi yoksa genel bellekten mi yükleneceğini öğrenmek için CategoryOptions kayıt defteri ayarını kullanıp kullanmadığını belirtir.|  
  
## <a name="enabled-attribute"></a>etkin Öznitelik  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`false`|PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanmaz. bu varsayılan ayardır.|  
|`true`|PerfCounter.dll CategoryOptions kayıt defteri ayarını kullanır.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`runtime`|Derleme bağlama ve atık toplama hakkında bilgi içerir.|  
  
## <a name="remarks"></a>Açıklamalar  

 .NET Framework 4 ' ün öncesindeki .NET Framework sürümlerinde, yüklenmiş olan PerfCounter.dll sürümü, işleme yüklenmiş çalışma zamanına karşılık gelen sürümüdür. Bir bilgisayarda .NET Framework sürüm 1,1 ve .NET Framework 2,0 yüklüyse, bir .NET Framework 1,1 uygulaması PerfCounter.dll .NET Framework 1,1 sürümünü yükler. .NET Framework 4 ' te başlayarak, PerfCounter.dll en yeni yüklü sürümü yüklenir. Bu, .NET Framework 1,1 uygulamasının, bilgisayarda .NET Framework 4 yüklüyse PerfCounter.dll .NET Framework 4 sürümünü yükleyemeyeceği anlamına gelir.  
  
 .NET Framework 4 ' ten başlayarak, performans sayaçlarını tüketerek, PerfCounter.dll kategoriye özgü paylaşılan bellekten veya genel paylaşılan bellekten okunup okunmayacağını öğrenmek için her bir sağlayıcı için CategoryOptions kayıt defteri girişini denetler. .NET Framework 1,1 PerfCounter.dll, kategoriye özgü paylaşılan belleğin farkında olmadığından, bu kayıt defteri girişini okummıyor; her zaman genel paylaşılan bellekten okur.  
  
 Geriye dönük uyumluluk için .NET Framework 4 PerfCounter.dll, bir .NET Framework 1,1 uygulamasında çalışırken CategoryOptions kayıt defteri girişini denetlemez. Yalnızca .NET Framework 1,1 PerfCounter.dll gibi genel paylaşılan belleği kullanır. Ancak, .NET Framework 4 PerfCounter.dll öğesini etkinleştirerek kayıt defteri ayarını kontrol edebilirsiniz `<forcePerformanceCounterUniqueSharedMemoryReads>` .  
  
> [!NOTE]
> Öğesinin etkinleştirilmesi, `<forcePerformanceCounterUniqueSharedMemoryReads>` kategoriye özgü paylaşılan belleğin kullanılacağını garanti etmez. Enabled ayarı `true` yalnızca PerfCounter.dll CategoryOptions kayıt defteri ayarına başvuracak. CategoryOptions için varsayılan ayar, kategoriye özgü paylaşılan bellek kullanmaktır; Ancak, genel paylaşılan belleğin kullanılması gerektiğini belirtmek için CategoryOptions ' ı değiştirebilirsiniz.  
  
 CategoryOptions ayarını içeren kayıt defteri anahtarı HKEY_LOCAL_MACHINE \System\CurrentControlSet\Services \\<CategoryName \> \ performanceşeklindedir. Varsayılan olarak, CategoryOptions 3 olarak ayarlanır, bu da kategoriye özgü paylaşılan belleği kullanmak PerfCounter.dll bildirir. CategoryOptions 0 olarak ayarlandıysa, PerfCounter.dll genel paylaşılan belleği kullanır. Örnek verileri yalnızca oluşturulan örneğin adı, yeniden kullanılan örnekle aynıysa yeniden kullanılır. Tüm sürümler kategoriye yazabilecektir. Kategorili olarak 1 olarak ayarlanırsa, genel paylaşılan bellek kullanılır, ancak kategori adı, yeniden kullanılan kategoriyle aynı uzunluktadır sonra örnek verileri yeniden kullanılabilir.  
  
 0 ve 1 ayarları, bellek sızıntılarına ve performans sayacı belleğinin doldurulmasına yol açabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, kategoriye özgü paylaşılan bellek kullanması gerekip gerekmediğini belirlemek için PerfCounter.dll kategorili kayıt defteri girişine başvurması gerektiğini nasıl belirleyeceğini gösterir.  
  
```xml  
<configuration>  
  <runtime>  
    <forcePerformanceCounterUniqueSharedMemoryReads enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma zamanı ayarları şeması](index.md)
- [Yapılandırma dosyası şeması](../index.md)
