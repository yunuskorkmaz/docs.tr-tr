---
title: <sharedListeners> Öğesi
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 56a4111f2e0fd290321756c43c7f245e46044b02
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254945"
---
# <a name="sharedlisteners-element"></a>\<sharedListeners > öğesi
Herhangi bir kaynak veya trace ögesi başvurabilirsiniz dinleyicileri içerir.  Dinleyiciler, varsayılan olarak tüm izlemeleri almaz ve çalışma zamanında bu dinleyicileri almak mümkün değildir. Paylaşılan dinleyiciler tanımlanan dinleyicileri adına göre kaynakları veya izlemeleri eklenebilir.  
  
 \<Yapılandırma >  
\<System.Diagnostics >  
\<sharedListeners >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<sharedListeners>   
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Ekle >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-listeners-for-trace.md)|Bir ekler `sharedListeners` koleksiyonu.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|`Configuration`|Her yapılandırma dosyasında yer alan ve ortak dil çalışma zamanı ve .NET Framework uygulamaları tarafından kullanılan kök öğe.|  
|`system.diagnostics`|ASP.NET yapılandırma bölümü için olan kök öğesini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Paylaşılan dinleyici koleksiyonuna bir dinleyici etkin dinleyici yapmaz. Bunu hala bir izleme kaynağı veya bir izleme ekleyerek eklenmelidir `Listeners` izleme öğe için bir koleksiyon. .NET Framework'teki dinleyici sınıflar türetilen <xref:System.Diagnostics.TraceListener> sınıfı.  
  
 Bu öğe, makine yapılandırma dosyası (Machine.config) ve uygulama yapılandırma dosyasında kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek nasıl kullanılacağını gösterir `<sharedListeners>` dinleyici eklemek için öğe `console` için `Listeners` hem de koleksiyonu <xref:System.Diagnostics.TraceSource> ve <xref:System.Diagnostics.Trace> sınıfları. Konsol iz dinleyicisi izleme bilgilerini ya da yapılan çağrılar aracılığıyla konsola yazar. <xref:System.Diagnostics.TraceSource> veya <xref:System.Diagnostics.Trace>.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration></system.diagnostics>   
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Diagnostics.TraceListener>
- [İzleme ve Hata Ayıklama Ayarları Şeması](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [İzleme Dinleyicileri](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
