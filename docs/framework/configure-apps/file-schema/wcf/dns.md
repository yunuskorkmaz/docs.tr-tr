---
title: '&lt;DNS&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6994069ca57a078e3d8236739ecf091d9e179455
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltdnsgt"></a>&lt;DNS&gt;
Sunucu beklenen kimliğini belirtir. Bu kimlik X509 için geçerli olduğundan sunucu sertifikasının aynı değere sahip bir DNS içeriyorsa, sertifika kimlik doğrulama modu. SPN aynı değere sahipse, aynı zamanda Windows kimlik doğrulama modu için geçerlidir.  
  
 Öğe değerini ayarlama hakkında daha fazla bilgi için bkz: [hizmet kimliği ve kimlik doğrulama](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
 \<Kimliği >  
\<DNS >  
  
## <a name="syntax"></a>Sözdizimi  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  
 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|value|Sertifika DNS. DNS IP tabanlı bir ağda bilgisayarlar bulmak için kullanılan, endüstri standardı bir protokoldür. Kullanıcılar unutmayın görünen adları gibi [http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929) veya [http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165), 207.46.131.137 gibi sayı tabanlı adreslerini daha kolay.|  
  
### <a name="child-elements"></a>Alt Öğeler  
 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|İstemci tarafından doğrulanmasını hizmetin kimliğini belirtir.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki yapılandırma kodunu bir sunucu kimliğini doğrulaması için kullanılan bir X.509 sertifikası DNS belirtir.  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [Hizmet kimliği ve kimlik doğrulaması](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<Kimliği >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
