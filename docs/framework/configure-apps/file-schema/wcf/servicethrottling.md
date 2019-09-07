---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399570"
---
# <a name="servicethrottling"></a>\<serviceThrottling>
Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.  
  
[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Servicedavranışlar >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Serviceazaltma >**  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|maxConcurrentCalls|Üzerinde şu anda işleyen ileti sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.ServiceHost>. Sınırın fazla olan çağrıları sıraya alınır. Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir. Varsayılan değer 16 * işlemci sayısıdır.|  
|maxConcurrentInstances|Bir defada bir <xref:System.ServiceModel.InstanceContext> <xref:System.ServiceModel.ServiceHost>kez yürütülen nesne sayısını sınırlayan pozitif bir tamsayı. Ek örnek oluşturma istekleri sıraya alınır ve sınırın altına bir yuva kullanılabilir hale geldiğinde tamamlanır. Varsayılan değer, maxConcurrentSessions ve Maxconcurrentçağrılarının toplamıdır|  
|maxConcurrentSessions|Bir <xref:System.ServiceModel.ServiceHost> nesnenin kabul edebileceği oturum sayısını sınırlayan pozitif bir tamsayı.<br /><br /> Hizmet sınırı aşan bağlantıları kabul eder, ancak yalnızca sınırın altındaki kanallar etkin olur (iletiler kanaldan okur). Bu değerin 0 olarak ayarlanması, Int32. MaxValue olarak ayarlanmasına eşdeğerdir. Varsayılan değer 100 * işlemci sayısıdır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranış >](behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Azaltma denetimleri, kaynakların aşırı kullanımını önlemeye yönelik eşzamanlı çağrı, örnek veya oturum sayısına yönelik sınırlar yerleştirir.  
  
 Her öznitelik değeri her ulaşıldığında bir izleme yazılır. İlk izleme uyarı olarak yazılmıştır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği, hizmetin maksimum eşzamanlı çağrı sayısını 2 ' ye ve en fazla eşzamanlı örnek sayısını 10 ' a sınırlandırdığından emin olarak belirtir. Bu örneği çalıştırmanın ayrıntılı bir örneği için bkz. [azaltma](../../../wcf/samples/throttling.md).  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
