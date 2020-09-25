---
title: <dns>
ms.date: 03/30/2017
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
ms.openlocfilehash: adfd94365ceb0ddc3164a6baef838c16027b4bc3
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91190147"
---
# \<dns>

Sunucunun beklenen kimliğini belirtir. Sunucunun sertifikası aynı değere sahip bir DNS içeriyorsa, bu kimlik, x509 sertifika kimlik doğrulama modu için geçerlidir. SPN aynı değere sahipse, Windows kimlik doğrulama modu için de geçerlidir.  
  
Öğe değerini ayarlama hakkında daha fazla bilgi için bkz. [hizmet kimliği ve kimlik doğrulaması](../../../wcf/feature-details/service-identity-and-authentication.md).  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpoint>**](endpoint-of-client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<identity>**](identity.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dns>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<dns value = "String" />
```  
  
## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler  

 Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.  
  
### <a name="attributes"></a>Öznitelikler  
  
|Öznitelik|Açıklama|  
|---------------|-----------------|  
|değer|Sertifikanın DNS 'i. DNS, IP tabanlı bir ağdaki bilgisayarları bulmak için kullanılan sektör standardı bir protokoldür. Kullanıcılar, `https://go.microsoft.com/fwlink/?prd=10929` `https://go.microsoft.com/fwlink/?LinkID=96165` 207.46.131.137 gibi sayı tabanlı adreslerden daha kolay görünen adları anımsayabilir.|  
  
### <a name="child-elements"></a>Alt Öğeler  

 Yok.  
  
### <a name="parent-elements"></a>Üst Öğeler  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|[\<identity>](identity.md)|İstemci tarafından kimlik doğrulaması yapılacak hizmetin kimliğini belirtir.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki yapılandırma kodu bir sunucunun kimliğini doğrulamak için kullanılan bir X. 509.440 sertifikasının DNS 'sini belirtir.  
  
```xml  
<identity>
  <dns value = "www.cohowinery.com" />
</identity>
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IdentityElement>
- <xref:System.ServiceModel.EndpointAddress>
- <xref:System.ServiceModel.EndpointAddress.Identity%2A>
- <xref:System.ServiceModel.DnsEndpointIdentity>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [\<identity>](identity.md)
