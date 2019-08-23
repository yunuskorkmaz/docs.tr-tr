---
title: <message> / <netMsmqBinding>
ms.date: 03/30/2017
ms.assetid: 6ebf0240-d7be-4493-b0fe-f00fd5989d77
ms.openlocfilehash: b163dcb08e9656e3bde9c7fbb71fa1c92c9957ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931510"
---
# <a name="message-of-netmsmqbinding"></a>\<\<NetMsmqBinding > ileti >

Bu `netMsmqBinding` bağlamada soap iletisi güvenlik ayarlarını tanımlar.

```xml
<system.ServiceModel>
  <bindings>
    <netMsmqBinding>
      <binding>
        <security>
          <message>
```

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
|algorithmSuite|MSMQ aktarımı üzerinden gönderilen iletiler için ileti tabanlı güvenlik elde etmek üzere kullanılan ileti şifrelemesini ve anahtar sarması algoritmalarını ayarlar.<br /><br /> Varsayılan değer `Aes256` şeklindedir. Bu öznitelik türü <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.|
|clientCredentialType|MSMQ aktarımı üzerinden gönderilen iletiler için istemci kimlik doğrulaması gerçekleştirirken kullanılacak kimlik bilgisinin türünü belirtir. Geçerli değerler şunlardır:<br /><br /> Seçim Bu, hizmetin anonim istemcilerle etkileşime geçmesini sağlar. Ne hizmet ne de istemci bir kimlik bilgisi gerektirmez.<br />Pencerelerin Bu, SOAP değişimlerinin bir Windows kimlik bilgisinin kimliği doğrulanmış bağlamı altında olmasını sağlar. Bu, her zaman Kerberos tabanlı kimlik doğrulaması gerçekleştirir.<br />Nitelen Bu, hizmetin Kullanıcı adı kimlik bilgisi kullanarak kimlik doğrulaması yapmasını zorunlu kılabilir. Bu durumda kimlik bilgisinin, `clientCredentials` davranış uyarısı kullanılarak belirtilmesi gerekir **:**  Windows Communication Foundation (WCF) parola özetinin gönderilmesini veya parola kullanarak anahtar türemesini veya ileti güvenliği için bu tuşları kullanmayı desteklemez. Bu nedenle, WCF, Kullanıcı adı kimlik bilgileri kullanılırken Exchange 'in güvenliğinin sağlanmasını zorunlu kılar. Bu mod, hizmet sertifikasının, ve `clientCredential` `serviceCertificate`davranışı kullanılarak istemci tarafında belirtilmesini gerektirir. <br /><br /> Sertifika Bu, hizmetin bir sertifika kullanarak kimliğinin doğrulanmasını gerektirmesini sağlar. Bu durumda istemci kimlik bilgisinin `clientCredentials` davranış kullanılarak belirtilmesi gerekir. Bu durumda hizmet kimlik bilgilerinin, `clientCredentials` `serviceCertificate`yöntemi belirtilerek davranışı kullanılarak belirtilmesi gerekir.<br />Rağmen Bu, hizmetin bir CardSpace kullanarak istemcinin kimliğinin doğrulanmasını gerektirmesini sağlar. Davranışınınsağlanması`clientCredential` gerekir `serviceCertificate` .<br /><br /> Varsayılan değer `Windows` şeklindedir. Bu öznitelik türü <xref:System.ServiceModel.MessageCredentialType>.|

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
- [\<bağlama >](../../../misc/binding.md)
