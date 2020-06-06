---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: 5a4a4e8b645ee2c607988ac3031af537c93ca8c0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736749"
---
# <a name="message-of-netmsmqbinding"></a>\<message> / \<netMsmqBinding>

Bu bağlamada SOAP iletisi güvenlik ayarlarını tanımlar `netMsmqBinding` .

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netMsmqBinding>**](netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netmsmqbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  

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
|algorithmSuite|MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.<br /><br /> Varsayılan değer: `Aes256`. Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite> .|
|clientCredentialType|MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Geçerli değerler şunlardır:<br /><br /> -None: Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.<br />-Windows: Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.<br />-UserName: Bu, hizmetin, bir Kullanıcı adı kimlik bilgisi kullanılarak kimliğinin doğrulanmasını gerektirmesini sağlar. Bu durumda kimlik bilgisinin davranış biçimi kullanılarak belirtilmesi gerekir `clientCredentials` **:** Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parolayı kullanarak anahtar türemesini veya ileti güvenliği için bu anahtarları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar. Bu mod, hizmet sertifikasının, ve davranışı kullanılarak istemci tarafında belirtilmesini gerektirir `clientCredential` `serviceCertificate` . <br /><br /> -Certificate: Bu, hizmetin bir sertifika kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir. Bu durumda istemci kimlik bilgisinin davranış kullanılarak belirtilmesi gerekir `clientCredentials` . Bu durumda hizmet kimlik bilgilerinin `clientCredentials` , yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir `serviceCertificate` .<br />-CardSpace: Bu, hizmetin bir CardSpace kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar. `serviceCertificate`Davranışının sağlanması gerekir `clientCredential` .<br /><br /> Varsayılan değer: `Windows`. Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType> .|

### <a name="child-elements"></a>Alt Öğeler

Yok

### <a name="parent-elements"></a>Üst Öğeler

|Öğe|Açıklama|
|-------------|-----------------|
|[\<security>](security-of-netmsmqbinding.md)|Bağlama için güvenlik ayarlarını tanımlar.|

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
- [\<binding>](bindings.md)
