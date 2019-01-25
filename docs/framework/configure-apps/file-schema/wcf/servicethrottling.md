---
title: '&lt;serviceThrottling&gt;'
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ebef29360f661c77f51557ae4c9ca0bdf8177b99
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54689487"
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Bir Windows Communication Foundation (WCF) hizmetinin azaltma mekanizmasını belirtir.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<serviceBehaviors>  
\<davranışı >  
\<serviceThrottling>  
  
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
|maxConcurrentCalls|Şu anda üzerinde işlem iletilerinin sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost>. Sınırı aşan çağrıları kuyruğa alınır. Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir. Varsayılan değer 16 * işlemci sayısı.|  
|maxConcurrentInstances|Sayısını sınırlayan pozitif bir tamsayı <xref:System.ServiceModel.InstanceContext> arasında aynı anda yürütmek nesneleri bir <xref:System.ServiceModel.ServiceHost>. Ek örnekleri oluşturmak için istekler kuyruğa alınır ve sınırın altına bir yuva kullanıma sunulduğunda tamamlayın. Varsayılan maxConcurrentSessions ve MaxConcurrentCalls toplamıdır|  
|maxConcurrentSessions|Oturumlarının sayısını sınırlayan pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost> nesneyi kabul edebilir.<br /><br /> Hizmet sınırı aşan bağlantılar kabul eder, ancak yalnızca kanalları sınırın altına etkin (kanaldan iletiler okunur). Bu değerin 0 olarak ayarlanması, bu Int32.MaxValue olarak ayarlamaya eşittir. Varsayılan değer 100'dür * işlemci sayısı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Azaltma denetimleri sınırlarını eşzamanlı çağrıları, örnekleri veya oturumları kaynakların aşırı kullanımını önlemek için sayısına yerleştirin.  
  
 Özniteliklerin değerini ulaşıldığında her zaman bir izleme yazılır. İlk izleme, uyarı olarak yazılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örnek hizmet 2 ve en fazla 10 eş zamanlı örnekleri sayısı en fazla eşzamanlı çağrıların limitleri belirtir. Bu örneği çalıştırmadan ayrıntılı örnek için bkz. [azaltma](../../../../../docs/framework/wcf/samples/throttling.md).  
  
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
- [WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
