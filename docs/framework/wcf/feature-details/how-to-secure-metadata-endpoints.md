---
title: 'Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: ee64e53f49e15059c91982f2e64879b9f4c76d78
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834687"
---
# <a name="how-to-secure-metadata-endpoints"></a>Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme

Bir hizmetin meta verileri, uygulamanız hakkında kötü niyetli bir kullanıcının yararlanabilen gizli bilgiler içerebilir. Hizmetinizin tüketicileri, hizmetinize ilişkin meta verileri almak için güvenli bir mekanizma da gerektirebilir. Bu nedenle, bazen güvenli bir uç nokta kullanarak meta verilerinizi yayımlamak gerekir.

Meta veri uç noktaları, uygulama uç noktalarını güvenli hale getirmek için Windows Communication Foundation (WCF) ' de tanımlanan standart güvenlik mekanizmaları kullanılarak genellikle güvenlidir. Daha fazla bilgi için bkz. [Güvenliğe genel bakış](security-overview.md).

Bu konu, bir Güvenli Yuva Katmanı (SSL) sertifikasıyla veya diğer bir deyişle, bir HTTPS uç noktası tarafından güvenliği sağlanmış bir uç nokta oluşturma adımlarını açıklar.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Kodda güvenli bir HTTPS GET meta veri uç noktası oluşturmak için

1. Uygun bir X. 509.440 sertifikası ile bir bağlantı noktası yapılandırın. Sertifika, güvenilir bir yetkilinizden gelmiş olmalı ve "hizmet yetkilendirmesi" kullanımı amaçlanan bir şekilde olmalıdır. Sertifikayı bağlantı noktasına iliştirmek için HttpCfg. exe aracını kullanmanız gerekir. Bkz. [nasıl yapılır: SSL sertifikası Ile bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).

    > [!IMPORTANT]
    > Sertifikanın konusu veya etki alanı adı sistemi (DNS) bilgisayarın adıyla eşleşmelidir. Bu, HTTPS mekanizmanın gerçekleştirdiği ilk adımlardan biri, sertifikanın çağrıldığı adresle aynı Tekdüzen Kaynak tanımlayıcısına (URI) verildiğine emin olmak için gereklidir.

2. @No__t-0 sınıfının yeni bir örneğini oluşturun.

3. @No__t-1 sınıfının <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> özelliğini `true` olarak ayarlayın.

4. @No__t-0 özelliğini uygun bir URL olarak ayarlayın. Mutlak bir adres belirtirseniz URL 'nin "https://" düzeniyle başlaması gerektiğini unutmayın. Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.

5. Aşağıdaki kodda gösterildiği gibi, örneği, <xref:System.ServiceModel.Description.ServiceDescription> sınıfının <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliğinin döndürdüğü davranış koleksiyonuna ekleyin.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Yapılandırmada güvenli bir HTTPS Al meta veri uç noktası oluşturmak için

1. Hizmetiniz için yapılandırma dosyasının [\<system. serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesine [\<davranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi ekleyin.

2. [@No__t-3davranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine [\<servicedavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) öğesi ekleyin.

3. @No__t-2 öğesine [\<behavior >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin.

4. @No__t-1 öğesinin `name` özniteliğini uygun bir değere ayarlayın. @No__t-0 özniteliği gereklidir. Aşağıdaki örnek `mySvcBehavior` değerini kullanır.

5. @No__t-2 öğesine [\<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ekleyin.

6. @No__t-1 öğesinin `httpsGetEnabled` özniteliğini `true` olarak ayarlayın.

7. @No__t-1 öğesinin `httpsGetUrl` özniteliğini uygun bir değere ayarlayın. Mutlak bir adres belirtirseniz URL 'nin "https://" düzeniyle başlaması gerektiğini unutmayın. Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.

8. Davranışını bir hizmetle birlikte kullanmak için, [\<service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesinin `behaviorConfiguration` özniteliğini davranış öğesinin Name özniteliğinin değeri olarak ayarlayın. Aşağıdaki yapılandırma kodu, bir örnek gösterir.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <configuration>
     <system.serviceModel>
      <behaviors>
       <serviceBehaviors>
        <behavior name="mySvcBehavior">
         <serviceMetadata httpsGetEnabled="true"
              httpsGetUrl="https://localhost:8036/calcMetadata" />
        </behavior>
       </serviceBehaviors>
      </behaviors>
     <services>
      <service behaviorConfiguration="mySvcBehavior"
            name="Microsoft.Security.Samples.Calculator">
       <endpoint address="http://localhost:8037/ServiceModelSamples/calculator"
       binding="wsHttpBinding" bindingConfiguration=""
       contract="Microsoft.Security.Samples.ICalculator" />
      </service>
     </services>
    </system.serviceModel>
    </configuration>
    ```

## <a name="example"></a>Örnek

Aşağıdaki örnek, <xref:System.ServiceModel.ServiceHost> sınıfının bir örneğini oluşturur ve bir uç nokta ekler. Kod daha sonra <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfının bir örneğini oluşturur ve güvenli bir meta veri değişim noktası oluşturmak için özellikleri ayarlar.

[!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
[!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]

## <a name="compiling-the-code"></a>Kod Derleniyor

Kod örneği aşağıdaki ad alanlarını kullanır:

- <xref:System.ServiceModel?displayProperty=nameWithType>

- <xref:System.ServiceModel.Description?displayProperty=nameWithType>

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
