---
title: <add> / <issuerChannelBehaviors>
ms.date: 03/30/2017
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
ms.openlocfilehash: cf7ac2691ad1c641352a8047373ced538b19e983
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398327"
---
# <a name="add-of-issuerchannelbehaviors"></a>\<\<ıssuerchanneldavranışların > ekleyin >

STS ile iletişim kurulurken kullanılacak bir uç nokta davranışı ekler.

> [!NOTE]
> Herhangi bir uç nokta davranışı bir [ \<ClientCredentials >](clientcredentials.md) öğesi içeriyorsa, bir özel durum oluşturulur.

[ **\<Yapılandırma >** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<IssuedToken >** ](issuedtoken.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ıssuerchanneldavranışlar >** ](issuerchannelbehaviors-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**  

## <a name="syntax"></a>Sözdizimi

```xml
<add issuerAddress="string"
     behaviorConfiguration="string" />
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Aşağıdaki bölümlerde öznitelikler, alt öğeler ve üst öğeler açıklanır

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|IssuerAddress|İletişim kuracak güvenlik belirteci verenin URI 'SI.|
|behaviorConfiguration|Aynı yapılandırma dosyasında tanımlanan bir uç nokta davranışı adı.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<ıssuerchanneldavranışlar >](issuerchannelbehaviors-element.md)|Belirtilen hizmet belirteci hizmetleriyle iletişim kurulurken kullanılacak bir Windows Communication Foundation (WCF) istemci uç nokta davranışı koleksiyonu içerir.|

## <a name="remarks"></a>Açıklamalar

`issuerAddress`istemcinin iletişim kurmak istediği güvenlik belirteci hizmetinin URI 'sini içerir. `behaviorConfiguration`uygulamanın, güvenlik belirteci hizmetlerinden verilen belirteçleri almak için Windows Communication Foundation (WCF) tarafından oluşturulan kanallarda kullandığı bir uç nokta davranışına işaret eder.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>
- <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>
- <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../wcf/feature-details/service-identity-and-authentication.md)
- [Güvenlik Davranışları](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [İstemcileri Güvenli Hale Getirme](../../../wcf/securing-clients.md)
- [Nasıl yapılır: Federe Istemci oluşturma](../../../wcf/feature-details/how-to-create-a-federated-client.md)
- [Nasıl yapılır: Yerel veren yapılandırma](../../../wcf/feature-details/how-to-configure-a-local-issuer.md)
- [Federasyon ve Verilen Belirteçler](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<ıssuerchanneldavranışlar >](issuerchannelbehaviors-element.md)
