---
title: '&lt;serviceThrottling&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a059684967af26c72aca48a3fa6bb10c2f26b0c5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicethrottlinggt"></a>&lt;serviceThrottling&gt;
Windows Communication Foundation (WCF) hizmetini azaltma mekanizmasını belirtir.  
  
 \<Sistem. ServiceModel >  
\<davranışları >  
\<serviceBehaviors >  
\<davranışı >  
\<serviceThrottling >  
  
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
|maxConcurrentCalls|Şu anda arasında işlem iletilerinin sayısını sınırlar pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost>. Sınırı aşan çağrıları kuyruğa alınır. Bu değerin 0 olarak ayarlanması, Int32.MaxValue olarak ayarlamaya eşittir. 16 varsayılandır * işlemci sayısı.|  
|MaxConcurrentInstances|Sayısını sınırlayan bir pozitif tamsayı <xref:System.ServiceModel.InstanceContext> arasında aynı anda yürütme nesneleri bir <xref:System.ServiceModel.ServiceHost>. Ek örnekleri oluşturmak için istekler kuyruğa alınır ve sınırın altındaki bir yuva kullanılabilir hale geldiğinde tamamlayın. Varsayılan maxConcurrentSessions ve MaxConcurrentCalls toplamıdır|  
|MaxConcurrentSessions|Oturum sayısını sınırlar pozitif bir tamsayı bir <xref:System.ServiceModel.ServiceHost> nesnesini kabul edebilir.<br /><br /> Hizmet sınırı aşan bağlantılarını kabul eder, ancak yalnızca sınırın altındaki kanalları etkin (kanaldan iletiler okunur). Bu değerin 0 olarak ayarlanması, Int32.MaxValue olarak ayarlamaya eşittir. Varsayılan değer 100'dür * işlemci sayısı.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<davranışı >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Bir davranış öğesi belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Azaltma denetimleri sınırlarını eşzamanlı çağrıları, örneği veya oturumları atlayarak kaynaklarının kullanımını engellemek için sayısına yerleştirin.  
  
 Özniteliklerin değeri ulaşıldığında her zaman bir izleme yazılır. İlk izleme uyarı olarak yazılır.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma örneği hizmet 2 ile 10 eşzamanlı örnek sayısı maksimum eşzamanlı çağrı sınırları belirtir. Bu örnekte çalışan ayrıntılı örnek için bkz: [azaltma](../../../../../docs/framework/wcf/samples/throttling.md).  
  
```xml  
<behaviors>   
  <serviceBehaviors>   
    <behavior name="CalculatorServiceBehavior">   
      <serviceDebug includeExceptionDetailInFaults="False" />   
      <serviceMetadata httpGetEnabled="True"/>   
      <!-- Specify throttling behavior -->  
      <serviceThrottling maxConcurrentCalls="2"   
           maxConcurrentInstances="10"/>   
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>  
 <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>  
 [WCF Hizmet Performansını Denetlemek için ServiceThrottlingBehavior Kullanma](../../../../../docs/framework/wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
