---
title: '&lt;transactedBatching&gt;'
ms.date: 03/30/2017
ms.assetid: 2f790a0d-8f03-4b86-81b5-ce1bc1a6c575
ms.openlocfilehash: 2f89a1a6c2cc110a4695b792c5aa801b516393be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566001"
---
# <a name="lttransactedbatchinggt"></a>&lt;transactedBatching&gt;
Hareket işlem grubu oluşturma için desteklenip desteklenmediğini belirtir alma işlemleri.  
  
 \<system.ServiceModel>  
\<davranışlar >  
\<endpointBehaviors>  
\<davranışı >  
\<transactedBatching >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<transactedBatching maxBatchSize="Integer" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|`maxBatchSize`|En fazla sayısını belirten bir tamsayı gruplanabilecek operations birlikte tek bir işlemle alırsınız. Varsayılan değer 0'dır.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir uç nokta davranışı belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Birkaç batch girişimleri toplu işlem ile yapılandırılmış bir taşıma işlemlerini tek bir işleme alırsınız. Bunu, bir işlem oluşturmak ve bunu yapmadan görece yüksek maliyeti yaparak her alma işlemi engellenir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, bir hizmet yapılandırma dosyasında işlenen toplu işleme davranışını eklemek gösterilmektedir.  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- Define NetMsmqEndpoint -->
      <endpoint address="net.msmq://localhost/private/ServiceModelSamples"
                binding="netMsmqBinding"
                contract="Microsoft.ServiceModel.Samples.IQueueCalculator" />
      <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <behaviors>
    <endpointBehaviors>
      <behavior name="endpointBehavior">
        <transactedBatching maxBatchSize="10" />
      </behavior>
    </endpointBehaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="true" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.TransactedBatchingElement>
- <xref:System.ServiceModel.Description.TransactedBatchingBehavior>
