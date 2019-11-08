---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736749"
---
# <a name="message-of-netmsmqbinding"></a>\<netMsmqBinding > \<ileti >

Bu `netMsmqBinding` bağlamasındaki SOAP iletisi güvenlik ayarlarını tanımlar.

[ **\<configuration >** ](../configuration-element.md) \
&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) \
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlamaları >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netMsmqBinding >** ](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** \
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<güvenlik >** ](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<ileti >**  

## <a name="syntax"></a>Sözdizimi

```xml
<netMsmqBinding>
  <binding>
    <security>
      <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
               clientCredentialType="None/Windows/UserName/Certificate/CardSpace" />
    </security>
  </binding>
</netMsmqBinding>
```

## <a name="attributes-and-elements"></a>Öznitelikler ve Öğeler

Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.

### <a name="attributes"></a>Öznitelikler

|Öznitelik|Açıklama|
|---------------|-----------------|
|algorithmSuite|MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.<br /><br /> Varsayılan değer `Aes256` şeklindedir. Bu öznitelik <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>türündedir.|
|clientCredentialType|MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -None: Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.<br />-Windows: Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.<br />-UserName: Bu, hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak kimliğinin doğrulanmasını gerektirmesini sağlar. Bu durumda kimlik bilgisinin **`clientCredentials` davranışı kullanılarak belirtilmesi gerekir. Windows Communication Foundation** (WCF) parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya ileti güvenliği için bu anahtarları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar. Bu mod, hizmet sertifikasının istemci tarafında `clientCredential` davranış ve `serviceCertificate`kullanılarak belirtilmesini gerektirir. <br /><br /> -Certificate: Bu, hizmetin bir sertifika kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir. Bu durumda istemci kimlik bilgisinin `clientCredentials` davranışı kullanılarak belirtilmesi gerekir. Bu durumda hizmet kimlik bilgisinin, `serviceCertificate`belirtilerek `clientCredentials` davranışı kullanılarak belirtilmesi gerekir.<br />-CardSpace: Bu, hizmetin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar. `serviceCertificate` `clientCredential` davranışının sağlanması gerekir.<br /><br /> Varsayılan değer `Windows` şeklindedir. Bu öznitelik <xref:System.ServiceModel.MessageCredentialType>türündedir.|

### <a name="child-elements"></a>Alt Öğeler

Yok.

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<Güvenlik >](security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Configuration.MessageSecurityOverMsmqElement>
- <xref:System.ServiceModel.Configuration.NetMsmqSecurityElement.Message%2A>
- <xref:System.ServiceModel.NetMsmqSecurity.Message%2A>
- <xref:System.ServiceModel.MessageSecurityOverMsmq>
- [WCF'de Kuyruklar](../../../wcf/feature-details/queues-in-wcf.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../wcf/feature-details/securing-services-and-clients.md)
- [Bağlamalar](../../../wcf/bindings.md)
- [Sistem Tarafından Sağlanan Bağlamaları Yapılandırma](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Hizmetler ve İstemcileri Yapılandırmak için Bağlamaları Kullanma](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\< bağlama >](bindings.md)
