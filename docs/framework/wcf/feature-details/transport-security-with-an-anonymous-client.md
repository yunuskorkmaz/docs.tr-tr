---
title: Anonim bir istemciyle aktarım güvenliği
description: İstemcinin güvendiği bir sertifika kullanarak bir sunucunun kimliğini doğrulamak için aktarım güvenliği kullanan bu WCF senaryosunu inceleyin. İstemcinin kimliği doğrulanmadı.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
ms.openlocfilehash: 08cfb8c1a5581f17a251224430018764bed80b0f
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245017"
---
# <a name="transport-security-with-an-anonymous-client"></a>Anonim bir istemciyle aktarım güvenliği

Bu Windows Communication Foundation (WCF) senaryosu gizlilik ve bütünlük sağlamak için taşıma güvenliği (HTTPS) kullanır. Sunucunun kimlik doğrulamasının Güvenli Yuva Katmanı (SSL) sertifikasıyla doğrulanması ve istemcilerin sunucunun sertifikasına güvenmesi gerekir. İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.

Örnek bir uygulama için bkz. [WS Transport Security](../samples/ws-transport-security.md). Taşıma güvenliği hakkında daha fazla bilgi için bkz. [Aktarım güvenliğine genel bakış](transport-security-overview.md).

Hizmeti olan bir sertifika kullanma hakkında daha fazla bilgi için bkz. [sertifikalarla çalışma](working-with-certificates.md) ve bir [SSL sertifikası Ile bağlantı noktası yapılandırma](how-to-configure-a-port-with-an-ssl-certificate.md).

![Anonim bir istemciyle taşıma güvenliğini kullanma](./media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif)

|Özellik|Description|
|--------------------|-----------------|
|Güvenlik modu|Aktarım|
|Birlikte çalışabilirlik|Mevcut Web Hizmetleri ve istemcilerle|
|Kimlik doğrulaması (sunucu)<br /><br /> Kimlik doğrulaması (Istemci)|Yes<br /><br /> Uygulama düzeyi (WCF desteği yok)|
|Bütünlük|Yes|
|Gizlilik|Yes|
|Aktarım|HTTPS|
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Hizmet

Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:

- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.

- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.

### <a name="code"></a>Kod

Aşağıdaki kod, taşıma güvenliği kullanarak bir uç noktanın nasıl oluşturulacağını gösterir:

[!code-csharp[c_SecurityScenarios#5](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
[!code-vb[c_SecurityScenarios#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki kod, yapılandırma kullanarak aynı uç noktayı ayarlar. İstemcinin kimliği herhangi bir mekanizma tarafından doğrulanır ve bu nedenle anonimdir.

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

Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:

- Kodu kullanarak tek başına istemci oluşturun (ve istemci kodu).

- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın. Örneğin:

     [!code-csharp[C_SecurityScenarios#0](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

[!code-csharp[c_SecurityScenarios#6](~/samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
[!code-vb[c_SecurityScenarios#6](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]

### <a name="configuration"></a>Yapılandırma

Hizmeti ayarlamak için aşağıdaki yapılandırma kod yerine kullanılabilir.

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

- [Güvenliğe genel bakış](security-overview.md)
- [WS Taşıma Güvenliği](../samples/ws-transport-security.md)
- [Aktarım Güvenliğine Genel Bakış](transport-security-overview.md)
- [Windows Server App Fabric için güvenlik modeli](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))
