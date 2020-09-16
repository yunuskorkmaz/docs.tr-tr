---
title: Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: fc07a26c-cbee-41c5-8fb0-329085fef749
ms.openlocfilehash: 3e5838c474a4f13136ed29baab440dc1559b95f5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551099"
---
# <a name="message-security-with-a-windows-client-without-credential-negotiation"></a>Windows İstemcisi ile Kimlik Bilgileri Görüşmesi Olmadan İleti Güvenliği

Aşağıdaki senaryoda Kerberos protokolüyle güvenliği sağlanmış bir Windows Communication Foundation (WCF) istemcisi ve hizmeti gösterilmektedir.

Hem hizmet hem de istemci aynı etki alanında veya güvenilen etki alanlarında.

> [!NOTE]
> Bu senaryo ve [Windows Istemcisiyle Ileti güvenliği](message-security-with-a-windows-client.md) arasındaki fark, bu senaryonun uygulama iletisini göndermeden önce hizmet kimlik bilgilerini anlaşamayacağı bir uygulamadır. Buna ek olarak, Kerberos protokolünü gerektirdiğinden bu senaryo bir Windows etki alanı ortamı gerektirir.

![Kimlik bilgisi anlaşması olmadan ileti güvenliği](media/0c9f9baa-2439-4ef9-92f4-43c242d85d0d.gif "0c9f9baa-2439-4ef9-92f4-43c242d85d0d")

|Özellik|Description|
|--------------------|-----------------|
|Güvenlik modu|İleti|
|Birlikte Çalışabilirlik|Evet, WS-Kerberos belirteci ile profil uyumlu istemcilerle güvenlik|
|Kimlik doğrulaması (sunucu)|Sunucu ve istemcinin karşılıklı kimlik doğrulaması|
|Kimlik doğrulaması (Istemci)|Sunucu ve istemcinin karşılıklı kimlik doğrulaması|
|Bütünlük|Yes|
|Gizlilik|Yes|
|Aktarım|HTTP|
|Bağlama|<xref:System.ServiceModel.WSHttpBinding>|

## <a name="service"></a>Hizmet

Aşağıdaki kod ve yapılandırma bağımsız olarak çalışacak şekilde tasarlanmıştır. Şunlardan birini yapın:

- Yapılandırma olmadan kodu kullanarak tek başına bir hizmet oluşturun.

- Sağlanan yapılandırmayı kullanarak bir hizmet oluşturun, ancak herhangi bir uç nokta tanımlamaz.

### <a name="code"></a>Kod

Aşağıdaki kod, ileti güvenliği kullanan bir hizmet uç noktası oluşturur. Kod, hizmet kimlik bilgileri anlaşmasını ve güvenlik bağlamı belirtecinin (SCT) kurulmasını devre dışı bırakır.

> [!NOTE]
> Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmetin Kullanıcı hesabının Active Directory etki alanına kayıtlı hizmet asıl adına (SPN) erişimi olmalıdır. Bunu iki şekilde yapabilirsiniz:

1. `NetworkService` `LocalSystem` Hizmetini çalıştırmak için veya hesabını kullanın. Makine Active Directory etki alanına katıldığında, bu hesapların kurulduğu makine SPN 'sine erişimi olduğundan, WCF otomatik olarak hizmetin meta verilerinde (Web Hizmetleri Açıklama Dili veya WSDL) uygun SPN öğesini otomatik olarak oluşturur.

2. Hizmetinizi çalıştırmak için rastgele bir Active Directory etki alanı hesabı kullanın. Bu durumda, bu etki alanı hesabı için bir SPN oluşturmanız gerekir. Bunu yapmanın bir yolu Setspn.exe yardımcı program aracını kullanmaktır. Hizmet hesabı için SPN oluşturulduktan sonra, bu SPN 'YI, meta verileri (WSDL) aracılığıyla hizmetin istemcilerine yayımlamak üzere WCF 'yi yapılandırın. Bu, bir uygulama yapılandırma dosyası veya kodu gibi, gösterilen uç nokta için uç nokta kimliği ayarlanarak yapılır. Aşağıdaki örnek, kimliği programlı olarak yayımlar.

SPN 'Ler, Kerberos protokolü ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](/previous-versions/msp-n-p/ff649429(v=pandp.10)). Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md).

[!code-csharp[C_SecurityScenarios#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#12)]
[!code-vb[C_SecurityScenarios#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#12)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki yapılandırma kod yerine kullanılabilir.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <behaviors />
    <services>
      <service behaviorConfiguration="" name="ServiceModel.Calculator">
        <endpoint address="http://localhost/Calculator"
                  binding="wsHttpBinding"
                  bindingConfiguration="KerberosBinding"
                  name="WSHttpBinding_ICalculator"
                  contract="ServiceModel.ICalculator"
                  listenUri="net.tcp://localhost/metadata" >
         <identity>
            <servicePrincipalName value="service_spn_name" />
         </identity>
        </endpoint>
      </service>
    </services>
    <bindings>
      <wsHttpBinding>
        <binding name="KerberosBinding">
          <security>
            <message negotiateServiceCredential="false"
                     establishSecurityContext="false" />
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

- Herhangi bir uç nokta adresi tanımlamayan bir istemci oluşturun. Bunun yerine, yapılandırma adını bağımsız değişken olarak alan istemci oluşturucusunu kullanın. Örnek:

  [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
  [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]

### <a name="code"></a>Kod

Aşağıdaki kod istemcisini yapılandırır. Güvenlik modu Ileti olarak ayarlanır ve istemci kimlik bilgisi türü Windows olarak ayarlanır. <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A>Ve <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> özelliklerinin olarak ayarlandığını unutmayın `false` .

> [!NOTE]
> Windows kimlik bilgisi türünü anlaşma olmadan kullanmak için, hizmet ile iletişim kurmadan önce istemcinin hizmetin hesap SPN 'si ile yapılandırılması gerekir. İstemci, kimlik doğrulaması yapmak ve hizmetle iletişimin güvenliğini sağlamak için Kerberos belirtecini almak üzere SPN 'YI kullanır. Aşağıdaki örnek, istemcisinin hizmetin SPN 'si ile nasıl yapılandırılacağını gösterir. İstemciyi oluşturmak için [ServiceModel meta veri yardımcı programı aracını (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanıyorsanız, hizmetin meta verileri bu bilgileri IÇERIYORSA hizmetin SPN 'si otomatik olarak hizmetin meta VERILERINDEN (wsdl) istemciye yayılır. Hizmetin meta verilerine SPN 'yi dahil etmek için hizmeti yapılandırma hakkında daha fazla bilgi için, bu konunun devamındaki "hizmet" bölümüne bakın.
>
> SPN 'Ler, Kerberos ve Active Directory hakkında daha fazla bilgi için bkz. [Windows Için Kerberos teknik eki](/previous-versions/msp-n-p/ff649429(v=pandp.10)). Uç nokta kimlikleri hakkında daha fazla bilgi için bkz. [SecurityBindingElement Kimlik doğrulama modları](securitybindingelement-authentication-modes.md) konusu.

[!code-csharp[C_SecurityScenarios#19](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#19)]
[!code-vb[C_SecurityScenarios#19](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#19)]

### <a name="configuration"></a>Yapılandırma

Aşağıdaki kod istemcisini yapılandırır. [\<servicePrincipalName>](../../configure-apps/file-schema/wcf/serviceprincipalname.md)Öğesinin, Active Directory etki alanındaki hizmet hesabı için kayıtlı olarak hizmetin SPN 'sine eşleşecek şekilde ayarlanması gerektiğini unutmayın.

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
  <system.serviceModel>
    <bindings>
      <wsHttpBinding>
        <binding name="WSHttpBinding_ICalculator" >
          <security mode="Message">
            <message clientCredentialType="Windows"
                     negotiateServiceCredential="false"
                     establishSecurityContext="false" />
          </security>
        </binding>
      </wsHttpBinding>
    </bindings>
    <client>
      <endpoint address="http://localhost/Calculator"
                binding="wsHttpBinding"
                bindingConfiguration="WSHttpBinding_ICalculator"
                contract="ICalculator"
                name="WSHttpBinding_ICalculator">
        <identity>
          <servicePrincipalName value="service_spn_name" />
        </identity>
      </endpoint>
    </client>
  </system.serviceModel>
</configuration>
```

## <a name="see-also"></a>Ayrıca bkz.

- [Güvenliğe genel bakış](security-overview.md)
- [Kimlik Doğrulama ile Hizmet Kimliği](service-identity-and-authentication.md)
- [Windows Server App Fabric için güvenlik modeli](/previous-versions/appfabric/ee677202(v=azure.10))
