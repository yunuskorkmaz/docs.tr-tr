---
title: İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: bfb980e629ffb8f8543937a1850430c9bf6e9199
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183129"
---
# <a name="securing-clients"></a>İstemcileri Güvenli Hale Getirme
Windows Communication Foundation'da (WCF) hizmet, istemcilerin güvenlik gereksinimlerini belirler. Diğer bir de, hizmet hangi güvenlik modunu kullanacağını ve istemcinin bir kimlik bilgisi sağlaması gerekip gerekmediğini belirtir. Bu nedenle, bir istemciyi güvence altına alma işlemi basittir: hizmetten elde edilen meta verileri kullanın (yayınlanırsa) ve bir istemci oluşturun. Meta veriler istemcinin nasıl yapılandırılabildiğini belirtir. Hizmet, istemcinin bir kimlik bilgisi sağlamasını gerektiriyorsa, gereksinime uygun bir kimlik bilgisi edinmeniz gerekir. Bu konu süreci daha ayrıntılı olarak ele alatır. Güvenli bir hizmet oluşturma hakkında daha fazla bilgi için, [Güvenlik Hizmetleri'ne](securing-services.md)bakın.  
  
## <a name="the-service-specifies-security"></a>Hizmet Güvenliği Belirtir  
 Varsayılan olarak, WCF bağlamaları güvenlik özelliklerine sahiptir. (Özel durum.) <xref:System.ServiceModel.BasicHttpBinding> Bu nedenle, hizmet WCF kullanılarak oluşturulduysa, kimlik doğrulaması, gizliliği ve bütünlüğü sağlamak için güvenliği uygulama olasılığı daha yüksektir. Bu durumda, hizmetin sağladığı meta veriler, güvenli bir iletişim kanalı oluşturmak için ne gerektiğini gösterir. Hizmet meta verileri herhangi bir güvenlik gereksinimi içermiyorsa, http üzerinden Güvenli Soketkatmanı (SSL) gibi bir güvenlik düzenini bir hizmete empoze etmenin bir yolu yoktur. Ancak, hizmet istemcinin bir kimlik bilgisi sağlamasını gerektiriyorsa, istemci geliştirici, dağıtıcı veya yönetici, istemcinin kendisini hizmete doğrulamak için kullanacağı gerçek kimlik belgesini sağlaması gerekir.  
  
## <a name="obtaining-metadata"></a>Meta veri edinme  
 İstemci oluştururken, ilk adım istemciile iletişim kuracağı hizmet için meta veri elde etmektir. Bu iki şekilde yapılabilir. İlk olarak, hizmet bir meta veri değişimi (MEX) bitiş noktası yayımlarsa veya meta verilerini HTTP veya HTTPS üzerinden kullanılabilir hale getirirse, meta verileri, istemci nin yanı sıra yapılandırma dosyası için her iki kod dosyasını da oluşturan [ServiceModel Metadata Utility Tool (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)kullanarak indirebilirsiniz. (Aracı kullanma hakkında daha fazla bilgi için [wcf istemcisi kullanarak Hizmetlere Erişim'e](accessing-services-using-a-wcf-client.md)bakın.) Hizmet bir MEX bitiş noktası yayımlamıyorsa ve meta verilerini HTTP veya HTTPS üzerinden de kullanıma sunmuyorsa, güvenlik gereksinimlerini ve meta verileri açıklayan belgeler için hizmet oluşturucuya başvurmanız gerekir.  
  
> [!IMPORTANT]
> Meta verilerin güvenilir bir kaynaktan gelmesi ve değiştirilmemesi önerilir. HTTP protokolü kullanılarak alınan meta veriler açık metin olarak gönderilir ve kurcalanabilir. Hizmet özellikleri ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini kullanıyorsa, https protokolünü kullanarak verileri indirmek için hizmet oluşturucusu tarafından sağlanan URL'yi kullanın.  
  
## <a name="validating-security"></a>Güvenliği Doğrulama  
 Meta veri kaynakları iki geniş kategoriye ayrılabilir: güven kaynakları ve güvenilmeyen kaynaklar. Bir kaynağa güveniyorsanız ve istemci kodunu ve diğer meta verileri bu kaynağın güvenli MEX bitiş noktasından indirdiyseniz, istemciyi oluşturabilir, doğru kimlik bilgilerini sağlayabilir ve başka bir endişeolmadan çalıştırabilirsiniz.  
  
 Ancak, hakkında çok az şey bildiğiniz bir kaynaktan bir istemci ve meta veri indirmeyi seçerseniz, kodun kullandığı güvenlik önlemlerini doğruladığınızdan emin olun. Örneğin, hizmet gizlilik ve bütünlük talep etmediği sürece (en azından) kişisel veya finansal bilgilerinizi bir hizmete gönderen bir istemci oluşturmamalısınız. Bu tür bilgiler onlar tarafından görülebileceğinden, hizmetin sahibine bu tür bilgileri ifşa etmeye istekli olduğunuz ölçüde güvenmelisiniz.  
  
 Bu nedenle, kural olarak, güvenilmeyen bir kaynaktan gelen kod ve meta verileri kullanırken, gereksinim duyduğunuz güvenlik düzeyini karşıladığından emin olmak için kodu ve meta verileri denetleyin.  
  
## <a name="setting-a-client-credential"></a>İstemci Kimlik Bilgileri Ayarlama  
 İstemci üzerinde istemci kimlik bilgisi ayarlama iki adımdan oluşur:  
  
1. Hizmetin gerektirdiği *istemci kimlik bilgisi türünü* belirleyin. Bu iki yöntemden biri ile gerçekleştirilir. İlk olarak, hizmet oluşturucudan belgeleriniz varsa, hizmetin gerektirdiği istemci kimlik bilgisi türünü (varsa) belirtmelidir. İkinci olarak, Yalnızca Svcutil.exe aracı tarafından oluşturulan bir yapılandırma dosyanız varsa, hangi kimlik bilgisi türünün gerekli olduğunu belirlemek için tek tek bağlamaları inceleyebilirsiniz.  
  
2. Gerçek bir istemci kimlik bilgisi belirtin. Gerçek istemci kimlik bilgisi, türden ayırt etmek için *istemci kimlik bilgisi değeri* olarak adlandırılır. Örneğin, istemci kimlik bilgisi türü bir sertifika belirtirse, hizmetin güvendiği bir sertifika yetkilisi tarafından verilen bir X.509 sertifikası sağlamanız gerekir.  
  
### <a name="determining-the-client-credential-type"></a>İstemci Kimlik Türünü Belirleme  
 Svcutil.exe aracının oluşturduğu yapılandırma dosyasına sahipseniz, hangi istemci kimlik bilgisi türünün gerekli olduğunu belirlemek için [ \<bağlama>](../configure-apps/file-schema/wcf/bindings.md) bölümünü inceleyin. Bölümde güvenlik gereksinimlerini belirten bağlayıcı öğeler vardır. Özellikle, her \<bağlayıcının güvenlik> Öğesini inceleyin. Bu öğe, `mode` üç olası değerden birine ayarlayabileceğiniz`Message`özniteliği içerir ( , , `Transport`veya `TransportWithMessageCredential`). Öznitelik değeri modu belirler ve mod hangi alt öğelerin önemli olduğunu belirler.  
  
 Öğe `<security>` bir `<transport>` veya `<message>` öğe veya her ikisini de içerebilir. Önemli öğe, güvenlik moduyla eşleşen öğedir. Örneğin, aşağıdaki kod güvenlik modu `"Message"`olduğunu belirtir ve `<message>` öğe için istemci kimlik bilgisi `"Certificate"`türü . Bu durumda, `<transport>` öğe yoksayılabilir. Ancak, `<message>` öğe bir X.509 sertifikası sağlanması gerektiğini belirtir.  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"
                      realm="" />  
           <message clientCredentialType="Certificate"
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 `clientCredentialType` Öznitelik `"Windows"`, aşağıdaki örnekte gösterildiği gibi ayarlanırsa, gerçek bir kimlik bilgisi değeri sağlamanız gerekmediğini unutmayın. Bunun nedeni, Windows tümleşik güvenliğinin istemciyi çalıştıran kişinin gerçek kimlik belgesini (Kerberos belirteci) sağlamasıdır.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>İstemci Kimlik Değerini Ayarlama  
 İstemcinin bir kimlik bilgisi sağlaması gerektiği tespit edilirse, istemciyi yapılandırmak için uygun yöntemi kullanın. Örneğin, istemci sertifikası ayarlamak için <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi kullanın.  
  
 X.509 sertifikası, ortak bir kimlik bilgisi biçimidir. Kimlik bilgisiiki şekilde sağlayabilirsiniz:  
  
- İstemci kodunuzda programlayarak `SetCertificate` (yöntemi kullanarak).  
  
 İstemci için yapılandırma dosyasının>bölümüne [ \<davranışlar](../configure-apps/file-schema/wcf/behaviors.md) ekleyerek ve öğeyi `clientCredentials` kullanarak (aşağıda gösterilmiştir).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>\<Kodda Müşteri Kimlik Bilgilerini> Değeri Ayarlama  
 [Bir istemci kimlik bilgilerini koddaki değer>ayarlamak için sınıfın özelliğine erişmeniz gerekir. \<](../configure-apps/file-schema/wcf/clientcredentials.md) <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> <xref:System.ServiceModel.ClientBase%601> Özellik, aşağıdaki <xref:System.ServiceModel.Description.ClientCredentials> tabloda gösterildiği gibi çeşitli kimlik bilgisi türlerine erişim sağlayan bir nesne döndürür.  
  
|ClientCredential Özellik|Açıklama|Notlar|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Bir verir<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Hizmete kendini doğrulamak için istemci tarafından sağlanan bir X.509 sertifikasını temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Bir verir<xref:System.ServiceModel.Security.HttpDigestClientCredential>|Bir HTTP özet kimlik belgesini temsil eder. Kimlik bilgisi, kullanıcı adı ve parolanın bir karmasidur.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Bir verir<xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Bir Güvenlik Belirteci Hizmeti tarafından verilen ve genellikle federasyon senaryolarında kullanılan özel bir güvenlik belirteci temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Bir verir<xref:System.ServiceModel.Security.PeerCredential>|Windows etki alanında eş örgüsüne katılmak için Bir Peer kimlik belgesini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Bir verir<xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Bant dışı bir anlaşmada hizmet tarafından sağlanan X.509 sertifikasını temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Bir verir<xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Kullanıcı adı ve parola çiftini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Bir verir<xref:System.ServiceModel.Security.WindowsClientCredential>|Windows istemci kimlik belgesini (Kerberos kimlik bilgisi) temsil eder. Sınıfın özellikleri salt okunur.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Yapılandırmada \<müşteri kimlik bilgilerini> Değer Ayarlama  
 Kimlik bilgileri değerleri, [ \<istemci Kimlik Bilgileri>](../configure-apps/file-schema/wcf/clientcredentials.md) öğesinin alt öğeleri olarak bir uç nokta davranışı kullanılarak belirtilir. Kullanılan öğe istemci kimlik bilgisi türüne bağlıdır. Örneğin, aşağıdaki örnek, <[ \<istemci Sertifikası>](../configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)kullanarak bir X.509 sertifikası ayarlamak için yapılandırmayı gösterir.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>
      </endpointBehaviors>
    </behaviors>
  </system.serviceModel>  
</configuration>  
```  
  
 İstemci kimlik bilgisini yapılandırmada ayarlamak için, yapılandırma dosyasına [ \<bir uç nokta davranışı>](../configure-apps/file-schema/wcf/endpointbehaviors.md) öğesi ekleyin. Ayrıca, eklenen davranış öğesi, aşağıdaki örnekte gösterildiği gibi `behaviorConfiguration` [ \< \<istemci>](../configure-apps/file-schema/wcf/endpoint-of-client.md) öğesinin bitiş noktası> özniteliğini kullanarak hizmetin bitiş noktasına bağlanmalıdır. Özniteliğin `behaviorConfiguration` değeri davranış `name` özniteliğinin değeriyle eşleşmelidir.  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> İstemci kimlik bilgileri değerlerinden bazıları, kullanıcı adı ve parola veya Windows kullanıcı ve parola değerleri gibi uygulama yapılandırma dosyaları kullanılarak ayarlanamaz. Bu tür kimlik bilgileri yalnızca kodolarak belirtilebilir.  
  
 İstemci kimlik bilgilerini ayarlama hakkında daha fazla bilgi için [bkz: İstemci kimlik bilgilerini belirtin.](how-to-specify-client-credential-values.md)  
  
> [!NOTE]
> `ClientCredentialType`aşağıdaki örnek `SecurityMode` yapılandırmada `"TransportWithMessageCredential",` gösterildiği gibi ayarlandığında göz ardı edilir.  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"
               establishSecurityContext="false"
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<>](../configure-apps/file-schema/wcf/bindings.md)
- [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](configuration-editor-tool-svcconfigeditor-exe.md)
- [Hizmetleri Güvenli Hale Getirme](securing-services.md)
- [WCF İstemcisi Kullanarak Hizmetlere Erişme](accessing-services-using-a-wcf-client.md)
- [Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme](how-to-specify-client-credential-values.md)
- [ServiceModel Meta Veri Yardımcı Programracı (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme](how-to-specify-the-client-credential-type.md)
