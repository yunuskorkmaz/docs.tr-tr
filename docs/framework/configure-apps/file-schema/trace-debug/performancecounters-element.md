---
title: '&lt;performanceCounters&gt; öğesi'
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
ms.openlocfilehash: 69d6deafb6aad88f5d379c7e8d4ac707e4c51815
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47209827"
---
# <a name="ltperformancecountersgt-element"></a>&lt;performanceCounters&gt; öğesi
Performans sayaçlarını birer paylaşılan genel bellek boyutunu belirtir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<performanceCounters >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<performanceCounters filemappingsize="524288" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|filemappingsize|Gerekli öznitelik.<br /><br /> Genel performans sayaçlarını birer paylaşılan belleğin bayt cinsinden boyutunu belirtir. 524288 varsayılandır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Performans sayaçları, performans verilerini yayınlamak için bellek eşlemeli dosya veya paylaşılan belleği'ni kullanın.  Tek seferde kaç tane kullanılabilir paylaşılan bellek boyutunu belirler.  Paylaşılan bellek iki tür vardır: Genel paylaşılan bellek ve ayrı bir paylaşılan bellek.  Genel paylaşılan bellek, .NET Framework sürümleri 1.0 veya 1.1 ile tüm performans sayacı kategorileri tarafından kullanılır.  .NET Framework sürüm 2.0 yüklü performans sayacı kategorileri ayrı paylaşılan bellek, her performans sayacı kategorisinin, kendi belleğe sahip kullanın.  
  
 Yalnızca bir yapılandırma dosyası ile genel paylaşılan bellek boyutunu ayarlayabilirsiniz.  Varsayılan boyutu 524.288 bEvet en büyük boyutu 33,554,432 bayt ve en düşük boyut 32.768 bayttır.  Genel paylaşılan bellek tüm işlemleri ve kategorileri tarafından paylaşılan olduğundan, ilk oluşturan boyutunu belirtir.  Uygulama yapılandırma dosyanızda boyutu tanımlarsanız, uygulamanızı yürütmek performans sayaçları neden olan ilk uygulama ise, boyutu yalnızca kullanılır.  Bu nedenle doğru konumu belirlemek için `filemappingsize` Machine.config dosyasının bir değerdir.  Çok sayıda performans sayacı örneklerinin farklı adlara sahip oluşturduysanız genel paylaşılan bellek bitti bireysel performans sayaçlarını birer, sonuç genel paylaşılan bellek bellekte bırakılamıyor.  
  
 Ayrı bir paylaşılan bellek boyutu için kayıt defteri DWORD FileMappingSize değerinde anahtar HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\*\<kategori adı >* \Performance başvuruluyor yapılandırma dosyasındaki genel paylaşılan bellek için belirtilen değer ilk olarak, arkasından. FileMappingSize değeri yok sonra ayrı bir paylaşılan bellek boyutu için bir dördüncü ayarlanır (1/4) yapılandırma dosyasındaki genel ayarı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Diagnostics.PerformanceCounter>  
 <xref:System.Diagnostics.PerformanceCounterCategory>  
 <xref:System.Diagnostics.PerformanceCounter.InstanceLifetime%2A>  
 <xref:System.Diagnostics.PerformanceCounterInstanceLifetime>
