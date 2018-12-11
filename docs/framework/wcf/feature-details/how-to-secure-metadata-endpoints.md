---
title: 'Nasıl Yapılır: Meta veri uç noktalarını güvenli hale getirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
ms.openlocfilehash: e6fbaabb97e4a8de3e4bdbcc0c105b6cf999c0d5
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152197"
---
# <a name="how-to-secure-metadata-endpoints"></a>Nasıl Yapılır: Meta veri uç noktalarını güvenli hale getirme
Bir hizmet için meta veriler, kötü niyetli bir kullanıcı yararlanabilen uygulamanızla ilgili gizli bilgiler içerebilir. Hizmet tüketicileri, hizmetinizi hakkındaki meta verileri almak için güvenli bir mekanizma da gerektirebilir. Bu nedenle, bazen meta verilerinizi güvenli bir uç noktayı kullanarak yayımlamak gereklidir.  
  
 Meta veri uç noktalarını, genellikle uygulama uç noktaları güvenliğini sağlamak için Windows Communication Foundation (WCF) tanımlanan standart güvenlik mekanizmalarını kullanılarak güvenli hale getirilir. (Daha fazla bilgi için [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Bu konuda bir Güvenli Yuva Katmanı (SSL) sertifikası veya HTTPS uç noktası, diğer bir deyişle, güvenli bir uç nokta oluşturma adımları gösterilmektedir.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Kodda bir güvenli HTTPS GET meta veri uç noktası oluşturmak için  
  
1.  Bir bağlantı noktası uygun bir X.509 sertifikasıyla yapılandırın. Sertifika bir güvenilen yetkilisinden gelmelidir ve kullanım amacı, "Service yetkilendirme" olmalıdır Bağlantı noktası için sertifika eklemek için HttpCfg.exe Aracı'nı kullanmanız gerekir. Bkz: [nasıl yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Kendi etki alanı adı sistemi (DNS) veya sertifika konusunun bilgisayarın adı eşleşmelidir. HTTPS mekanizması gerçekleştirir ilk adımlarından biri sertifika için aynı Tekdüzen Kaynak Tanımlayıcısı (URI) çağırıldığı adresi verilir denetlemek için olduğundan, bu gereklidir.  
  
2.  Yeni bir örneğini oluşturma <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfının `true`.  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliğini uygun bir URL. Mutlak bir adres belirtirseniz, URL şeması "https://" ile başlamalıdır unutmayın. Göreli adres belirtirseniz, hizmet konağınız için bir HTTPS taban adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adresidir "", veya doğrudan hizmet için HTTPS temel adres.  
  
5.  Örnek davranışları koleksiyona ekleyin, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceDescription> döndürür, aşağıdaki kodda gösterildiği gibi sınıf.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Güvenli bir HTTPS GET meta veri uç yapılandırması oluşturmak için  
  
1.  Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) hizmetiniz için yapılandırma dosyasının öğesi.  
  
2.  Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
3.  Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesine `<serviceBehaviors>` öğesi.  
  
4.  Ayarlama `name` özniteliği `<behavior>` öğesi için uygun bir değer. `name` Özniteliği gereklidir. Aşağıdaki örnek değeri kullanır `mySvcBehavior`.  
  
5.  Ekleme bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) için `<behavior>` öğesi.  
  
6.  Ayarlama `httpsGetEnabled` özniteliği `<serviceMetadata>` öğesine `true`.  
  
7.  Ayarlama `httpsGetUrl` özniteliği `<serviceMetadata>` öğesi için uygun bir değer. Mutlak bir adres belirtirseniz, URL şeması "https://" ile başlamalıdır unutmayın. Göreli adres belirtirseniz, hizmet konağınız için bir HTTPS taban adresi sağlamanız gerekir. Bu özellik ayarlanmamışsa, varsayılan adresidir "", veya doğrudan hizmet için HTTPS temel adres.  
  
8.  Davranış hizmeti ile kullanmak için ayarlama `behaviorConfiguration` özniteliği [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) davranışı öğesinin ad özniteliği değeri öğesine. Aşağıdaki yapılandırma kod tam bir örnek gösterir.  
  
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
 Aşağıdaki örnek, bir örneğini oluşturur. bir <xref:System.ServiceModel.ServiceHost> sınıfı ve bir uç nokta ekler. Kodu daha sonra bir örneğini oluşturur <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı ve güvenli meta veri değişimi noktası oluşturmak üzere özellikleri ayarlar.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kod örneği, aşağıdaki ad alanlarını kullanır:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Nasıl Yapılır: Bir SSL sertifikası ile bir bağlantı noktası yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
