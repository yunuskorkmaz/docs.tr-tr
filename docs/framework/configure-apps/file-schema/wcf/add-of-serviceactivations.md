---
title: '&lt;serviceActivations&gt; &lt;ekleme&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c49845169265e48b232963ed5a2e6215be75d3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; &lt;ekleme&gt;
Eşlenen sanal hizmeti etkinleştirme ayarlarını tanımlamanızı sağlar bir yapılandırma öğesi, [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet türleri. Bu WAS içinde barındırılan hizmetlere etkinleştirmek mümkün kılar / IIS .svc dosyası olmadan.  
  
 \<Sistem. ServiceModel >  
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
