---
title: 'Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: c6439187560e15ec10f1eea4e1731421904e8643
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045293"
---
# <a name="how-to-secure-metadata-endpoints"></a>Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme

Bir hizmetin meta verileri, uygulamanız hakkında kötü niyetli bir kullanıcının yararlanabilen gizli bilgiler içerebilir. Hizmetinizin tüketicileri, hizmetinize ilişkin meta verileri almak için güvenli bir mekanizma da gerektirebilir. Bu nedenle, bazen güvenli bir uç nokta kullanarak meta verilerinizi yayımlamak gerekir.

Meta veri uç noktaları, uygulama uç noktalarını güvenli hale getirmek için Windows Communication Foundation (WCF) ' de tanımlanan standart güvenlik mekanizmaları kullanılarak genellikle güvenlidir. (Daha fazla bilgi için bkz. [Güvenliğe genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md).)

Bu konu, bir Güvenli Yuva Katmanı (SSL) sertifikasıyla veya diğer bir deyişle, bir HTTPS uç noktası tarafından güvenliği sağlanmış bir uç nokta oluşturma adımlarını açıklar.

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Kodda güvenli bir HTTPS GET meta veri uç noktası oluşturmak için

1. Uygun bir X. 509.440 sertifikası ile bir bağlantı noktası yapılandırın. Sertifika, güvenilir bir yetkilinizden gelmiş olmalı ve "hizmet yetkilendirmesi" kullanımı amaçlanan bir şekilde olmalıdır. Sertifikayı bağlantı noktasına iliştirmek için HttpCfg. exe aracını kullanmanız gerekir. Bkz [. nasıl yapılır: SSL sertifikası](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)Ile bir bağlantı noktası yapılandırın.

    > [!IMPORTANT]
    > Sertifikanın konusu veya etki alanı adı sistemi (DNS) bilgisayarın adıyla eşleşmelidir. Bu, HTTPS mekanizmanın gerçekleştirdiği ilk adımlardan biri, sertifikanın çağrıldığı adresle aynı Tekdüzen Kaynak tanımlayıcısına (URI) verildiğine emin olmak için gereklidir.

2. <xref:System.ServiceModel.Description.ServiceMetadataBehavior> Sınıfının yeni bir örneğini oluşturun.

3. Sınıfının özelliğini olarak`true`ayarlayın. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

4. <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> Özelliği uygun bir URL olarak ayarlayın. Mutlak bir adres belirtirseniz URL 'nin "https://" düzeniyle başlaması gerektiğini unutmayın. Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.

5. Aşağıdaki kodda gösterildiği gibi, örneği, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> <xref:System.ServiceModel.Description.ServiceDescription> sınıfının özelliğinin döndürdüğü davranışlar koleksiyonuna ekleyin.

    [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
    [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]

### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Yapılandırmada güvenli bir HTTPS Al meta veri uç noktası oluşturmak için

1. Hizmetiniz için yapılandırma dosyasının [ \<System. ServiceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) öğesine [ davranışlar>öğesiekleyin.\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

2. Davranışlar > öğesine bir [ \<servicedavranışlar >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) öğesi [ekleyin. \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)

3. `<serviceBehaviors>` Öğeye bir [ \<davranış >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesi ekleyin.

4. `<behavior>` Öğesinin özniteliğini `name` uygun bir değere ayarlayın. `name` Özniteliği gereklidir. Aşağıdaki örnek, değerini `mySvcBehavior`kullanır.

5. `<behavior>` Öğesine bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) ekleyin.

6. Ayarlama `httpsGetEnabled` özniteliği `<serviceMetadata>` öğesine `true`.

7. `<serviceMetadata>` Öğesinin özniteliğini `httpsGetUrl` uygun bir değere ayarlayın. Mutlak bir adres belirtirseniz URL 'nin "https://" düzeniyle başlaması gerektiğini unutmayın. Göreli bir adres belirtirseniz, hizmet ana bilgisayarınız için bir HTTPS temel adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adres "" veya doğrudan hizmetin HTTPS taban adresidir.

8. Davranışını bir hizmetle birlikte kullanmak için, [ \<Service >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) öğesinin `behaviorConfiguration` özniteliğini davranış öğesinin Name özniteliğinin değeri olarak ayarlayın. Aşağıdaki yapılandırma kodu, bir örnek gösterir.

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

Aşağıdaki örnek bir <xref:System.ServiceModel.ServiceHost> sınıfın örneğini oluşturur ve bir uç nokta ekler. Daha sonra kod, <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfının bir örneğini oluşturur ve güvenli bir meta veri değişim noktası oluşturmak için özellikleri ayarlar.

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
- [Nasıl yapılır: SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)
- [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)
- [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
