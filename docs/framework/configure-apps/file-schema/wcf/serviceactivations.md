---
title: '&lt;serviceActivations&gt;'
ms.date: 03/30/2017
ms.assetid: 97e665b6-1c51-410b-928a-9bb42c954ddb
ms.openlocfilehash: c62f2bd1a34aca31ea9f9d5de17840f2967b269c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748535"
---
# <a name="ltserviceactivationsgt"></a>&lt;serviceActivations&gt;
Windows Communication Foundation (WCF) hizmetini türlerinizi eşlenen sanal hizmeti etkinleştirme ayarlarını tanımla ayarları eklemenize izin verir bir yapılandırma öğesi. Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
\<serviceActivations >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment>   
   <serviceActivations>  
      <add factory="String"  
           service="String"/>  
   </serviceActivations>  
</serviceHostingEnvironment>  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
 Yok.  
  
### <a name="child-elements"></a>Alt Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<ekleme >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-serviceactivations.md)|Bir hizmet uygulaması etkinleştirme belirten bir yapılandırma öğesi ekler.|  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Belirli bir barındırma ortamı hizmeti başlatır türü tanımlar.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağını gösterir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <serviceHostingEnvironment>  
      <serviceActivations>  
        <add service="GreetingService"/>  
      </serviceActivations>  
    </serviceHostingEnvironment>  
  </system.serviceModel>  
</configuration>  
```  
  
 Bu yapılandırmayı kullanarak, bir .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.  
  
 Unutmayın `<serviceHostingEnvironment>` uygulama düzeyi yapılandırması. Yerleştirmek zorunda `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren. Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür. Tek bir hizmeti makinenin kök dizininde kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.  
  
 Yapılandırma temelli etkinleştirme hem http hem de http olmayan protokolü üzerinden etkinleştirmeyi destekler. Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektirir. Ardından, uzantıyı hizmeti etkinleştirmek üzere olanak tanır bilinen buildProviders kendi uzantıları eşleyebilirsiniz. Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtlar geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.ServiceActivationElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
