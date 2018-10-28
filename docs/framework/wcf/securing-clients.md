---
title: İstemcileri Güvenli Hale Getirme
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 7090d5e9cd4b44a6f894cc92ad69b34761356118
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188215"
---
# <a name="securing-clients"></a>İstemcileri Güvenli Hale Getirme
Windows Communication Foundation (WCF) hizmet istemciler için güvenlik gereksinimlerini belirler. Diğer bir deyişle, hizmeti kullanmak için hangi güvenlik modunu belirtir ve istemci bir kimlik bilgisi olup olmadığına sağlamalıdır. Bir istemciyi, bu nedenle, güvenli hale getirme işlem basittir: (yayımlanıyorsa) hizmetinden alınan meta verileri kullanın ve bir istemci oluşturun. Meta veriler istemci yapılandırma belirler. Hizmet istemci kimlik bilgileri sağlamanız gerekiyorsa, gereksinime uyan bir kimlik bilgisini edinmeniz gerekir. Bu konu başlığı altında daha ayrıntılı ele alınmaktadır. Güvenli bir hizmet oluşturma hakkında daha fazla bilgi için bkz. [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Güvenlik hizmeti belirtir  
 Varsayılan olarak, güvenlik özellikleri etkinleştirilmiş WCF bağlamaları vardır. (Özel durum <xref:System.ServiceModel.BasicHttpBinding>.) Bu nedenle, hizmeti devre dışı WCF kullanılarak oluşturulmuşsa, kimlik doğrulaması, gizliliği ve bütünlük emin olmak için güvenlik uygulamak için büyük bir olasılık yoktur. Bu durumda, sağladığı meta veriler güvenli bir iletişim kanalı kurmak için bunu gerektiren gösterir. Hizmet meta verileri tüm güvenlik gereksinimleriniz yoksa, bir güvenlik düzeni gibi Güvenli Yuva Katmanı (SSL) HTTP üzerinden bir hizmet üzerinde dayatmak için hiçbir yolu yoktur. Ancak, hizmet kimlik bilgilerini sağlamak istemci gerektiriyorsa İstemcinin hizmete kendi kimliğini doğrulamak için kullanacağı gerçek kimlik istemci geliştirici, dağıtıcı veya yönetici sağlamalısınız.  
  
## <a name="obtaining-metadata"></a>Meta veri alma  
 Bir istemci oluştururken ilk adım, istemcinin iletişim kuracağı hizmet için meta verileri elde edilir. Bu iki yolla yapılabilir. Hizmet meta veri değişimi (MEX) uç noktası yayımlar veya meta verilerini HTTP veya HTTPS üzerinden yapar, ilk olarak, meta verileri kullanarak indirebilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), her ikisi de oluşturduğu bir istemci ve bunun yanı sıra bir yapılandırma dosyası için kod dosyaları. (Aracı kullanma hakkında daha fazla bilgi için bkz. [WCF istemci kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Hizmet bir MEX uç noktasına yayın yapmaz ve ayrıca meta verilerini kullanılabilir HTTP veya HTTPS üzerinden yapmaz, güvenlik gereksinimleri ve meta verileri açıklayan belgeler için hizmet Oluşturucusu başvurmanız gerekir.  
  
> [!IMPORTANT]
>  Meta veriler için güvenilir bir kaynaktan geldiğini ve onu değiştirilmiş değil, önerilir. HTTP protokolü kullanılarak alınan meta verileri açık metin olarak gönderilir ve bozuabilir. Hizmet kullanıyorsa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özelliklerini kullanan hizmet Oluşturucusu sağlanan HTTPS protokolünü kullanarak verileri indirmek için URL.  
  
## <a name="validating-security"></a>Güvenlik doğrulama  
 Meta veri kaynakları iki geniş kategoriye ayrılabilir: güven kaynakları ve güvenilmeyen kaynakları. Bir kaynağa güveniyorsanız ve istemci oluşturabileceğinizi sonra istemci kodu ve diğer meta veriler, kaynağın güvenli MEX uç noktasından indirdikten, doğru kimlik bilgilerini sağlayın ve diğer hiçbir kaygılarıyla çalıştırın.  
  
 Ancak, istemci ve meta verileri hakkında az bildiğiniz bir kaynaktan indirin seçerseniz kod güvenlik önlemlerini doğrulamak emin olun. Örneğin, servis talepleri gizliliği ve bütünlüğü (en azından) sürece, bir hizmete kişisel veya finansal bilgilerinizi gönderen bir istemci yalnızca oluşturmamalıdır. Bu tür bilgiler gitmesini görünür olacağı için tür bilgilerin ifşa etmeye hazır olduğunuz için toplasa bile, hizmet sahibi güvenmelisiniz.  
  
 Bir kural olarak, bu nedenle, kod ve meta verileri güvenilmeyen bir kaynaktan kullanırken, kod ve ihtiyaç duyduğunuz güvenlik düzeyine karşıladığından emin olmak için meta verileri denetleyin.  
  
## <a name="setting-a-client-credential"></a>İstemci kimlik bilgilerini ayarlama  
 Bir istemcide istemci kimlik bilgilerini ayarlama, iki adımdan oluşur:  
  
1.  Belirlemek *istemci kimlik bilgisi türü* sağlayan bir hizmettir. Bu iki yöntemden biri tarafından gerçekleştirilir. İlk olarak, hizmet Oluşturucusu belgelerinden varsa, bu istemci kimlik bilgilerini belirtmelisiniz hizmeti türü (varsa) gerektirir. İkinci olarak, yalnızca Svcutil.exe araç tarafından oluşturulan bir yapılandırma dosyası varsa, hangi kimlik bilgisi türü gerekli olduğunu belirlemek için tek tek bağlamaları inceleyebilirsiniz.  
  
2.  Bir gerçek istemci kimlik bilgilerini belirtin. Gerçek istemci kimlik bilgisi adı verilen bir *istemci kimlik bilgisi değeri* türünden ayırmak için. Örneğin, bir sertifika istemci kimlik bilgileri türünü belirten bir sertifika yetkilisi tarafından hizmet verilen X.509 sertifikası sağlamanız gerekir güvenleri.  
  
### <a name="determining-the-client-credential-type"></a>İstemci kimlik bilgileri türünü belirleme  
 Oluşturulan Svcutil.exe aracını dosya, inceleyin yapılandırma varsa [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hangi istemci kimlik bilgisi türü gerekip gerekmediğini bölümü. Bölüm içinde güvenlik gereksinimlerini belirtin bağlama öğeleridir. Özellikle, inceleyin \<Güvenlik > her bağlama öğesi. Bu öğe içeren `mode` özniteliği üç değerlerden birine ayarlayın (`Message`, `Transport`, veya `TransportWithMessageCredential`). Öznitelik değeri modu belirler ve alt öğeleri önemli olduğu modu belirler.  
  
 `<security>` Öğesi ya da içerebilir bir `<transport>` veya `<message>` öğe veya her ikisi de. Önemli güvenlik modunu eşleşen bir öğedir. Örneğin, aşağıdaki kod güvenlik modunu belirtir `"Message"`ve kimlik bilgisi türü için istemci `<message>` öğesi `"Certificate"`. Bu durumda, `<transport>` öğesi yoksayıldı. Ancak, `<message>` öğeyi belirten bir X.509 sertifikası sağlanmalıdır.  
  
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
  
 Unutmayın `clientCredentialType` özniteliği `"Windows"`, aşağıdaki örnekte gösterildiği gibi gerçek kimlik değerini belirtmeniz gerekmez. İstemcisini çalıştıran kişinin gerçek kimlik bilgilerini (Kerberos belirteci) Windows tümleşik güvenliği sağlar olmasıdır.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>İstemci kimlik bilgisi değeri ayarlama  
 İstemci kimlik bilgileri sağlamanız gerekir belirlenirse istemciyi yapılandırmak için uygun yöntemi kullanın. Örneğin, bir istemci sertifikası ayarlamak için kullanın <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi.  
  
 Bir ortak kimlik bilgisi X.509 sertifikası biçimidir. Kimlik bilgisi iki şekilde sağlayabilirsiniz:  
  
-   İstemci kodunuz programlama tarafından (kullanarak `SetCertificate` yöntemi).  
  
 Ekleyerek bir [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) istemcisi için yapılandırma dosyasının ve kullanarak `clientCredentials` (aşağıda gösterildiği gibi).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ayarı bir \<clientCredentials > kod değeri  
 Ayarlanacak bir [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) değer kodda erişmesi gereken <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı. Özellik döndürür bir <xref:System.ServiceModel.Description.ClientCredentials> aşağıdaki tabloda gösterildiği gibi çeşitli kimlik bilgisi türlerinin erişim sağlayan nesne.  
  
|ClientCredential özelliği|Açıklama|Notlar|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Döndürür bir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Hizmete kendi kimliğini doğrulamak için istemci tarafından sağlanan bir X.509 sertifikası temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Döndürür bir <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Bir HTTP digest kimlik bilgileri temsil eder. Kimlik bilgisi, kullanıcı adı ve parola karmasıdır.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Döndürür bir <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Bir güvenlik belirteci Federasyon senaryolarında kullanılan hizmeti tarafından verilen bir özel güvenlik belirteci temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Döndürür bir <xref:System.ServiceModel.Security.PeerCredential>|Bir eş kimlik bilgisi bir Windows etki alanındaki bir eş kafes katılım temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Döndürür bir <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Bir bant dışı anlaşma hizmeti tarafından sağlanan bir X.509 sertifikası temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Döndürür bir <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Bir kullanıcı adı ve parola çiftini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Döndürür bir <xref:System.ServiceModel.Security.WindowsClientCredential>|Windows istemci kimlik bilgilerini (Kerberos kimlik bilgisi) temsil eder. Sınıf özellikleri salt okunurdur.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ayarı bir \<clientCredentials > yapılandırma değeri  
 Kimlik bilgisi değerleri belirtilen alt öğeleri olarak bir uç nokta davranışı kullanarak [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi. Kullanılan öğesi istemci kimlik bilgisi türüne bağlıdır. Örneğin, aşağıdaki örnek, bir X.509 sertifikası kullanarak ayarlamak için yapılandırma gösterir <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Yapılandırmada istemci kimlik bilgilerini ayarlamak için eklemek bir [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) yapılandırma dosyasına öğesi. Ayrıca, hizmet uç noktası için eklenen davranış öğesi bağlanmalıdır kullanarak `behaviorConfiguration` özniteliği [ \<uç noktası >](https://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) aşağıdaki örnekte gösterildiği gibi bir öğe. Değerini `behaviorConfiguration` özniteliği davranışı değerini eşleşmelidir `name` özniteliği.  
  
 `<configuration>`  
  
 `<system.serviceModel>`  
  
 `<client>`  
  
 `<endpoint address="http://localhost/servicemodelsamples/service.svc"`  
  
 `binding="wsHttpBinding"`  
  
 `bindingConfiguration="Binding1"`  
  
 `behaviorConfiguration="myEndpointBehavior"`  
  
 `contract="Microsoft.ServiceModel.Samples.ICalculator" />`  
  
 `</client>`  
  
 `</system.serviceModel>`  
  
 `</configuration>`  
  
> [!NOTE]
>  İstemci kimlik bilgileri değerlerini bazıları, uygulama yapılandırma dosyaları, örneğin kullanılarak küme, kullanıcı adı ve parola veya Windows kullanıcı ve parola değerlerini olamaz. Bu kimlik bilgileri değerlerini yalnızca kodda belirtilebilir.  
  
 İstemci kimlik bilgilerini ayarlama hakkında daha fazla bilgi için bkz. [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
> [!NOTE]
>  `ClientCredentialType` ne zaman göz ardı edilir `SecurityMode` ayarlanır `"TransportWithMessageCredential",` aşağıdaki örnek yapılandırmada gösterildiği gibi.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>  
 <xref:System.ServiceModel.ClientBase%601>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>  
 [\<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)  
 [Yapılandırma Düzenleme Aracı (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Hizmetleri Güvenli Hale Getirme](../../../docs/framework/wcf/securing-services.md)  
 [WCF İstemcisi Kullanarak Hizmetlere Erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)  
 [Nasıl yapılır: İstemci Kimlik Bilgileri Değerlerini Belirtme](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)  
 [ServiceModel Meta Veri Yardımcı Programı Aracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
 [Nasıl yapılır: İstemci Kimlik Bilgileri Türünü Belirtme](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
