---
title: '&lt;serviceActivations&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: 1a25ad517e26e037c588bb14844e38147e251d96
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; &lt;ekleme&gt;
Windows Communication Foundation (WCF) hizmetini türlerinizi eşlenen sanal hizmeti etkinleştirme ayarlarını tanımlamanızı sağlar bir yapılandırma öğesi. Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.  
  
 \<system.ServiceModel>  
\<ServiceHostingEnvironment >  
  
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
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Fabrika|Hizmeti etkinleştirme öğesi oluşturur Fabrika CLR türü adını belirten dize.|  
|hizmet|(Tam nitelikli Typename veya (App_Code klasörüne yerleştirilir olduğunda) kısa Typename. hizmeti uygulayan ServiceType|  
|relativeAddress|Geçerli bir IIS uygulama - örneğin "Service.svc" içinde göreli adresi. WCF 4. 0'göreli bu adresi bir bilinen dosya uzantılarını (.svc, .xamlx,...) içermesi gerekir. Fiziksel dosya için relativeUrl varolmak zorunda|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Etkinleştirme ayarlarını açıklayan bir yapılandırma bölümü.|  
  
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
 <xref:System.ServiceModel.Configuration.ServiceActivationElement>  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>  
 <xref:System.ServiceModel.ServiceHostingEnvironment>
