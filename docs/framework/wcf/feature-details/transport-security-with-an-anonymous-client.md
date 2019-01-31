---
title: Anonim istemci - WCF ile Aktarım güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 20d7e59ba2b4b9dedc0b0daff1c1aa9c5210e61b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260391"
---
# <a name="transport-security-with-an-anonymous-client"></a>Anonim istemci ile Aktarım güvenliği

Windows Communication Foundation (WCF) Bu senaryo, gizliliği ve bütünlüğü sağlamak için Aktarım güvenliği (HTTPS) kullanır. Sunucu bir Güvenli Yuva Katmanı (SSL) sertifikası ile doğrulanması gerekir ve istemcilerin sunucu sertifikasına güvenmelidir. İstemci tarafından herhangi bir mekanizma doğrulanmaz ve, bu nedenle, anonimdir.

Örnek bir uygulama için bkz: [WS aktarım güvenliği](../samples/ws-transport-security.md). Aktarım güvenliği hakkında daha fazla bilgi için bkz: [aktarım güvenliğine genel bakış](transport-security-overview.md).

Bir sertifika bir hizmetle kullanma hakkında daha fazla bilgi için bkz. [Working with Certificates](working-with-certificates.md) ve [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).

![Anonim istemci ile Aktarım güvenliği kullanarak](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Özelliği|Açıklama|
|--------------------|-----------------|
|Güvenlik modu|Taşıma|
|Birlikte Çalışabilirlik|Mevcut Web Hizmetleri ve istemcileri ile|
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (istemci)|Evet<br /><br /> Uygulama düzeyinde (WCF desteği)|
|Bütünlüğü|Evet|
|Gizliliği|Evet|
|Taşıma|HTTPS|
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Hizmet

Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:

- Kod ile yapılandırma kullanarak tek başına bir hizmet oluşturun.

- Sağlanan Yapılandırması'nı kullanarak bir hizmet oluşturma, ancak tüm uç noktalar tanımlamaz.

### <a name="code"></a>Kod

Aşağıdaki kod, aktarım güvenliği kullanarak bir uç nokta oluşturma işlemi gösterilmektedir:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki kod, yapılandırma kullanarak aynı uç noktasını ayarlar. İstemci, herhangi bir mekanizma tarafından doğrulanmaz ve bu nedenle anonimdir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="ServiceModel.Calculator">
        <endpoint address="https://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="WSHttpBinding_ICalculator"
                  name="SecuredByTransportEndpoint"
                  contract="ServiceModel.ICalculator" />
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator">
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client />
  </system.serviceModel>
</configuration>
```

## <a name="client"></a>İstemci

Aşağıdaki kod ve yapılandırma, bağımsız olarak çalışmaya yöneliktir. Aşağıdakilerden birini yapın:

- Bir tek başına istemci kodu (ve istemci kodu) kullanarak oluşturun.

- Herhangi bir uç nokta adresi tanımlamıyor bir istemci oluşturun. Bunun yerine, yapılandırma adı bağımsız değişkeni olarak alan İstemci Oluşturucu kullanın. Örneğin:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki yapılandırmayı kod yerine barındırılan hizmeti kurmak için kullanılabilir.

```xml
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Transport">
            <transport clientCredentialType="None" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="https://machineName/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe Genel Bakış](security-overview.md)
- [WS Aktarım Güvenliği](../samples/ws-transport-security.md)
- [Aktarım Güvenliğine Genel Bakış](transport-security-overview.md)
- [Windows Server AppFabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))