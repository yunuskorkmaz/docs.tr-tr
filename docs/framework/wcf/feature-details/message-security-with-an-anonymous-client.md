---
title: Anonim İstemci ile İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: cad53e1a-b7c9-4064-bc87-508c3d1dce49
ms.openlocfilehash: fccdd021e392e6c37615a9091ce13f0e94167246
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76211999"
---
# <a name="message-security-with-an-anonymous-client"></a>Anonim İstemci ile İleti Güvenliği

Aşağıdaki senaryoda, Windows Communication Foundation (WCF) ileti güvenliği ile güvenliği sağlanmış bir istemci ve hizmet gösterilmektedir. Bir tasarım hedefi, aktarım güvenliği yerine ileti güvenliği kullanmak ve ileride daha zengin bir talep tabanlı modeli destekleyebilmesi için kullanılır. Yetkilendirme için zengin talepler kullanma hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md).

Örnek bir uygulama için bkz. [Ileti güvenliği anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md).

![Anonim bir istemciyle ileti güvenliği](../../../../docs/framework/wcf/feature-details/media/b361a565-831c-4c10-90d7-66d8eeece0a1.gif "b361a565-831c-4c10-90d7-66d8eeece0a1")

|Özellikler|Açıklama|
|--------------------|-----------------|
|Güvenlik modu|İleti|
|Birlikte Çalışabilirlik|Yalnızca WCF|
|Kimlik doğrulaması (sunucu)|İlk anlaşma sunucu kimlik doğrulaması gerektirir, ancak istemci kimlik doğrulaması gerektirmez|
|Kimlik doğrulaması (Istemci)|Yok.|
|Bütünlük|Evet, paylaşılan güvenlik bağlamını kullanma|
|Gizlilik|Evet, paylaşılan güvenlik bağlamını kullanma|
|Aktarma|HTTP|

## <a name="service"></a>Hizmet

Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Aşağıdakilerden birini yapın:

- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.

- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.

### <a name="code"></a>Kod

Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktasının nasıl oluşturulacağını göstermektedir.

[!code-csharp[C_SecurityScenarios#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#8)]
[!code-vb[C_SecurityScenarios#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#8)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki yapılandırma kod yerine kullanılabilir. Hizmet davranışı öğesi, istemciye hizmetin kimliğini doğrulamak için kullanılan bir sertifika belirtmek için kullanılır. Hizmet öğesi `behaviorConfiguration` özniteliğini kullanarak davranışı belirtmelidir. Bağlama öğesi, istemci kimlik bilgisi türünün `None`olduğunu belirtir ve anonim istemcilerin hizmeti kullanmasına izin verir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior name="ServiceCredentialsBehavior">
          <serviceCredentials>
            <serviceCertificate findValue="contoso.com"
                                storeLocation="LocalMachine"
                                storeName="My" />
          </serviceCredentials>
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <services>
      <service behaviorConfiguration="ServiceCredentialsBehavior"
               name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="CalculatorService"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>İstemci

Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Aşağıdakilerden birini yapın:

- Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).

- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın. Örneğin:

    [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
    [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

Aşağıdaki kod, istemcisinin bir örneğini oluşturur. Bağlama ileti modu güvenliği kullanır ve istemci kimlik bilgisi türü None olarak ayarlanır.

[!code-csharp[C_SecurityScenarios#15](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#15)]
[!code-vb[C_SecurityScenarios#15](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#15)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki kod istemcisini yapılandırır.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://machineName/Calculator"
        binding="wsHttpBinding"
        bindingConfiguration="WSHttpBinding_ICalculator"
        contract="ICalculator"
        name="WSHttpBinding_ICalculator">
        <identity>
          <dns value="contoso.com" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Dağıtılan Uygulama Güvenliği](../../../../docs/framework/wcf/feature-details/distributed-application-security.md)
- [İleti Güvenliği Anonim](../../../../docs/framework/wcf/samples/message-security-anonymous.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
