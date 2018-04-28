---
title: 'Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 9f71b6ae-737c-4382-8d89-0a7b1c7e182b
caps.latest.revision: 13
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 50a62366063123de9e1773b2926f79b76a1b1c3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-secure-metadata-endpoints"></a>Nasıl yapılır: Meta Veri Uç Noktalarını Güvenli Hale Getirme
Bir hizmet için meta verileri, kötü niyetli bir kullanıcının yararlanabilirsiniz uygulamanız ile ilgili gizli bilgiler içerebilir. Hizmetinizin Tüketiciler, hizmetiniz hakkındaki meta verileri almak için güvenli bir mekanizma de gerektirebilir. Bu nedenle, bazen kullanarak güvenli bir uç noktası, meta verilerini yayımlamak gereklidir.  
  
 Meta veri uç noktaları genellikle güvenli tanımlanan standart güvenlik mekanizmalarını kullanarak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] uygulama uç noktalarını güvenli hale getirmek için. (Daha fazla bilgi için bkz: [güvenliğine genel bakış](../../../../docs/framework/wcf/feature-details/security-overview.md).)  
  
 Bu konuda bir Güvenli Yuva Katmanı (SSL) sertifikası veya bir HTTPS uç noktası tarafından diğer bir deyişle, güvenli bir uç nokta oluşturmak için adım adım anlatılmaktadır.  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-code"></a>Güvenli bir HTTPS alma meta veri uç kodu oluşturmak için  
  
1.  Bir bağlantı noktası uygun bir X.509 sertifikası ile yapılandırın. Sertifika güvenilir bir yetkiliden gelmesi gerekir ve bir kullanım amacı "Hizmetinin yetkilendirmesi" olması gerekir Bağlantı noktasına sertifika eklemek için HttpCfg.exe aracını kullanmanız gerekir. Bkz: [nasıl yapılır: bir SSL sertifikası ile bir bağlantı noktası yapılandırın](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
    > [!IMPORTANT]
    >  Sertifika veya kendi etki alanı adı sistemi (DNS) bilgisayarın adı eşleşmelidir. Sertifika için aynı Tekdüzen Kaynak Tanımlayıcısı (URI) bağlı çağrılır adresi olarak verilmeden denetlemek için HTTPS mekanizması gerçekleştirir ilk adımlarından biri olduğu için bu önemlidir.  
  
2.  Yeni bir örneğini oluşturmak <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı.  
  
3.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> özelliği <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfının `true`.  
  
4.  Ayarlama <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> uygun bir URL'ye özelliği. Mutlak bir adres belirtirseniz, URL şeması "https://" ile başlamalıdır unutmayın. Göreli bir adresi belirtirseniz, hizmet konağınız için bir HTTPS temel adresi girmeniz gerekir. Bu özellik ayarlanmamışsa varsayılan adresidir "", veya doğrudan hizmeti için HTTPS temel adres.  
  
5.  Örnek davranışları koleksiyona eklemek, <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> özelliği <xref:System.ServiceModel.Description.ServiceDescription> aşağıdaki kodda gösterildiği gibi sınıf döndürür.  
  
     [!code-csharp[c_HowToSecureEndpoint#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#1)]
     [!code-vb[c_HowToSecureEndpoint#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#1)]  
  
### <a name="to-create-a-secure-https-get-metadata-endpoint-in-configuration"></a>Güvenli bir HTTPS alma meta veri uç yapılandırmasında oluşturmak için  
  
1.  Ekleme bir [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesine [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) hizmetiniz için yapılandırma dosyası öğesi.  
  
2.  Ekleme bir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md) öğesine [ \<davranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) öğesi.  
  
3.  Ekleme bir [ \<davranışı >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-servicebehaviors.md) öğesine `<serviceBehaviors>` öğesi.  
  
4.  Ayarlama `name` özniteliği `<behavior>` uygun bir değere öğesi. `name` Özniteliği gereklidir. Aşağıdaki örnek değeri kullanır `mySvcBehavior`.  
  
5.  Ekleme bir [ \<serviceMetadata >](../../../../docs/framework/configure-apps/file-schema/wcf/servicemetadata.md) için `<behavior>` öğesi.  
  
6.  Ayarlama `httpsGetEnabled` özniteliği `<serviceMetadata>` öğesine `true`.  
  
7.  Ayarlama `httpsGetUrl` özniteliği `<serviceMetadata>` uygun bir değere öğesi. Mutlak bir adres belirtirseniz, URL şeması "https://" ile başlamalıdır unutmayın. Göreli bir adresi belirtirseniz, hizmet konağınız için bir HTTPS temel adresi girmeniz gerekir. Bu özellik ayarlanmamışsa varsayılan adresidir "", veya doğrudan hizmeti için HTTPS temel adres.  
  
8.  Bir hizmetle davranışı kullanmak üzere ayarlanmış `behaviorConfiguration` özniteliği [ \<hizmet >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) davranışı öğesinin ad özniteliği değeri öğesine. Aşağıdaki yapılandırma kodunu tam bir örnek gösterilir.  
  
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
 Aşağıdaki örnek, bir örneğini oluşturur. bir <xref:System.ServiceModel.ServiceHost> sınıfı ve bir uç nokta ekler. Kod sonra bir örneğini oluşturur <xref:System.ServiceModel.Description.ServiceMetadataBehavior> sınıfı ve bir güvenli meta verileri exchange noktası oluşturmak için özellikleri ayarlar.  
  
 [!code-csharp[c_HowToSecureEndpoint#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtosecureendpoint/cs/source.cs#0)]
 [!code-vb[c_HowToSecureEndpoint#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtosecureendpoint/vb/source.vb#0)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Kod örneği, şu ad alanlarından kullanır:  
  
-   <xref:System.ServiceModel?displayProperty=nameWithType>  
  
-   <xref:System.ServiceModel.Description?displayProperty=nameWithType>  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [Nasıl Yapılır: SSL Sertifikası ile Bir Bağlantı Noktasını Yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Sertifikalarla Çalışma](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Meta Veriler Hakkında Güvenlik Konuları](../../../../docs/framework/wcf/feature-details/security-considerations-with-metadata.md)  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
