---
title: '&lt;serviceActivations&gt; &lt;ekleme&gt;'
ms.date: 03/30/2017
ms.assetid: e5b01fc8-ee84-48b7-95fd-95ab54fa871f
ms.openlocfilehash: d0e1f45cc8ff5b544eff5ff5dae33d5989aaf405
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587641"
---
# <a name="ltaddgt-of-ltserviceactivationsgt"></a>&lt;serviceActivations&gt; &lt;ekleme&gt;
Windows Communication Foundation (WCF) hizmet türlerinizi eşleştiren sanal hizmet aktivasyon ayarlarını tanımlamanıza olanak sağlayan bir yapılandırma öğesi. Bu WAS içinde barındırılan hizmetleri etkinleştirmeniz mümkün kılar / IIS .svc dosyası olmadan.  
  
 \<system.ServiceModel>  
\<serviceHostingEnvironment >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<serviceHostingEnvironment>
    <serviceActivations>
      <add factory="String"
           service="String" />
  </serviceActivations>
</serviceHostingEnvironment>
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|Fabrika|Bir hizmet aktivasyon öğesini üreten üretici CLR tür adını belirten dize.|  
|hizmet|(Tam nitelikli tür adı veya kısa Typename (App_Code klasörü içinde yerleştirilir olduğunda). hizmeti uygulayan ServiceType|  
|relativeAddress|Geçerli bir IIS uygulama - örneğin "Service.svc" içinde göreli adresi. WCF 4. 0'göreli bu adresi bir bilinen dosya uzantıları (.svc .xamlx,...) içeren var. Fiziksel dosya için relativeUrl var olması|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<serviceHostingEnvironment >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|Aktivasyon ayarlarını tanımlayan bir yapılandırma bölümü.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki örnekte, web.config dosyasında etkinleştirme ayarlarının nasıl yapılandırılacağı gösterilmektedir.  
  
```xml  
<configuration>
  <system.serviceModel>
    <serviceHostingEnvironment>
      <serviceActivations>
        <add service="GreetingService" />
      </serviceActivations>
    </serviceHostingEnvironment>
  </system.serviceModel>
</configuration>
```  
  
 Bu yapılandırmayı kullanarak .svc dosyası kullanmadan GreetingService etkinleştirebilirsiniz.  
  
 Unutmayın `<serviceHostingEnvironment>` uygulama düzeyinde yapılandırma. Yerleştirmek sahip olduğunuz `web.config` sanal uygulama kökü altındaki yapılandırmasını içeren. Ayrıca, `serviceHostingEnvironment` machinetoApplication devralınabilir bölümüdür. Tek bir hizmette makine kökündeki kaydolursanız, uygulamadaki her hizmet bu hizmeti devralır.  
  
 Yapılandırma temelli etkinleştirme, etkinleştirme hem http hem de olmayan http protokolü üzerinden destekler. Yani .svc, .xoml veya .xamlx relatativeAddress uzantılarında gerektiriyor. Sonra hizmeti uzantıyı etkinleştirmek üzere olanak sağlayacak bilinen buildProviders kendi uzantılarınızı eşleyebilirsiniz. Çakışma, bağlı `<serviceActivations>` bölüm .svc kayıtları geçersiz kılar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Configuration.ServiceActivationElement>
- <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>
- <xref:System.ServiceModel.ServiceHostingEnvironment>
