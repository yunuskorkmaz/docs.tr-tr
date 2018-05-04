---
title: '&lt;performans sayaçları&gt; öğesi'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
- <perfomanceCounters> element
ms.assetid: a71f605b-c7d9-4501-a5c3-abcbb964a43f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cb4af08095c14c0c748a79f53104d8454d3dcd47
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltperformancecountersgt-element"></a>&lt;performans sayaçları&gt; öğesi
Performans sayaçları tarafından paylaşılan genel bellek boyutunu belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<performans sayaçları >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filemappingsize|Gerekli öznitelik.<br /><br /> Performans sayaçları tarafından paylaşılan genel belleğin bayt cinsinden boyutu belirtir. 524288 varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için kök öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Performans sayaçları, bellekle eşlenen dosya veya paylaşılan bellek performans verilerini yayınlamak için kullanın.  Kaç tane aynı anda kullanılabilir paylaşılan bellek boyutunu belirler.  Paylaşılan bellek iki tür vardır: Genel paylaşılan bellek ve ayrı bir paylaşılan bellek.  Genel paylaşılan bellek, .NET Framework sürüm 1.0 veya 1.1 ile tüm performans sayacı kategorileri tarafından kullanılır.  .NET Framework sürüm 2.0 ile birlikte yüklenen performans sayacı kategorileri ayrı paylaşılan bellek, her performans sayacı kategorisi kendi bellek sahip kullanın.  
  
 Genel paylaşılan bellek boyutu yalnızca bir yapılandırma dosyası ile ayarlayabilirsiniz.  Varsayılan boyutu 524.288 bEvet en büyük boyutu 33,554,432 bayt ve minimum boyut 32.768 bayttır.  Genel paylaşılan bellek tüm işlemleri ve kategorileri tarafından paylaşılan olduğundan, ilk oluşturan boyutunu belirtir.  Uygulama yapılandırma dosyasında boyutu tanımlarsanız, uygulamanız yürütmek performans sayaçları neden olan ilk uygulama ise bu boyut yalnızca kullanılır.  Bu nedenle belirtmek için doğru konuma `filemappingsize` Machine.config dosyasının bir değerdir.  Genel paylaşılan bellek bellek performans sayacı örnekleri farklı adlara sahip çok sayıda oluşturduysanız genel paylaşılan bellek tükendi tek tek performans sayaçları tarafından sonuç bırakılamıyor.  
  
 Ayrı bir paylaşılan bellek boyutu için anahtar DWORD FileMappingSize değeri kayıt defterinde HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<kategori adı >* \Performance başvurusu ilk olarak, genel paylaşılan bellek yapılandırma dosyası için belirtilen değer arkasından. FileMappingSize değer yok sonra bir dördüncü kümesi ayrı bir paylaşılan bellek boyutu (1/4) yapılandırma dosyasında genel ayar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
