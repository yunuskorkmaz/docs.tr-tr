---
title: İstemcileri Güvenli Hale Getirme
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
caps.latest.revision: 22
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 7d06df1a9c4ef5a7cb64f71d2f7afc77c41a0e6f
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="securing-clients"></a>İstemcileri Güvenli Hale Getirme
İçinde [!INCLUDE[indigo1](../../../includes/indigo1-md.md)], istemciler için güvenlik gereksinimlerini hizmet belirler. Diğer bir deyişle, hizmeti kullanmak için hangi güvenlik modunu belirtir ve istemci bir kimlik bilgisi olup olmadığına sağlamanız gerekir. Bir istemci, bu nedenle, güvenli hale getirme işlemi basittir: bir istemciyi derlemek ve (yayımlanırsa) hizmetinden alınan meta veriler kullanın. Meta veriler istemcisinin nasıl yapılandırılacağını belirtir. Hizmet istemci kimlik bilgileri sağlamanız gerektiriyorsa, gereksinime uyan bir kimlik bilgisi edinmeniz gerekir. Bu konuda daha ayrıntılı ele alınmaktadır. Güvenli bir hizmet oluşturma hakkında daha fazla bilgi için bkz: [Hizmetleri güvenli hale getirme](../../../docs/framework/wcf/securing-services.md).  
  
## <a name="the-service-specifies-security"></a>Güvenlik hizmeti belirtir  
 Varsayılan olarak, [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] bağlamaları etkin güvenlik özellikleri vardır. (Özel durum <xref:System.ServiceModel.BasicHttpBinding>.) Bu nedenle, hizmetin kullanarak oluşturduysanız [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], kimlik doğrulaması, gizliliği ve bütünlük sağlamak için güvenlik uygulamak büyük bir olasılığı yüksektir. Bu durumda, hizmeti sağlayan meta verileri hangi güvenli bir iletişim kanalı kurulamadı gerektirdiğini gösterir. Hizmet meta verileri tüm güvenlik gereksinimleriniz içermiyorsa, güvenlik, bir düzeni gibi Güvenli Yuva Katmanı (SSL) HTTP üzerinden bir hizmete koymak için yolu yoktur. Ancak, hizmet bir kimlik bilgisi sağlamak istemci gerektiriyorsa, istemci hizmete kendi kimliğini doğrulamak için kullanacağınız gerçek kimlik bilgisi istemci geliştirici, dağıtıcı veya yönetici sağlamalısınız.  
  
## <a name="obtaining-metadata"></a>Meta veri alma  
 Bir istemci oluştururken ilk adımı istemci iletişim hizmet için meta verileri elde edilir. Bu iki yolla yapılabilir. Hizmet meta veri değişimi (MEX) uç noktası yayımlar veya meta verilerini HTTP veya HTTPS üzerinden yapar, ilk olarak, meta verileri kullanarak indirebilirsiniz [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md), hangi oluşturur hem de bir istemci ve bunun yanı sıra bir yapılandırma dosyası için kod dosyaları. (Aracını kullanma hakkında daha fazla bilgi için bkz: [bir WCF istemcisi kullanarak hizmetlere erişme](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md).) Hizmet MEX bitiş noktası yayımlamaz ve ayrıca meta verilerini kullanılabilir HTTP veya HTTPS üzerinden yapmaz, güvenlik gereksinimleri ve meta verileri tanımlayan belgelerine hizmeti oluşturan başvurmanız gerekir.  
  
> [!IMPORTANT]
>  Meta veriler güvenilir bir kaynaktan geldiğini ve onu değiştirilmiş değil, önerilir. HTTP protokolü kullanılarak alınan meta veriler düz metin olarak gönderilir ve ile değiştirilmiş. Hizmet kullanıyorsa <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> ve <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> özellikleri, hizmet Oluşturucusu sağlanan verileri HTTPS protokolünü kullanarak indirmek için URL kullanın.  
  
## <a name="validating-security"></a>Güvenlik doğrulama  
 Meta veri kaynakları iki geniş kategorilere ayrılmış: kaynakları ve güvenilir olmayan kaynaklardan güven. Bir kaynağına güveniyorsanız ve istemci derleme sonra istemci kodu ve diğer meta verileri bu kaynağın güvenli MEX uç noktasından indirmiş, doğru kimlik bilgilerini sağlayın ve diğer hiçbir sorunları ile çalıştırın.  
  
 Ancak, bir istemci ve meta verileri hakkında çok az bildiğiniz bir kaynaktan indirin almak isterseniz, kodu kullanan güvenlik önlemlerini doğrulamak emin olun. Örneğin, hizmet gizliliği ve bütünlük (en azından) talep sürece kişisel veya finansal bilgilerinizi bir hizmete gönderir istemci yalnızca oluşturmamalıdır. Bu tür bilgileri gibi bilgileri verip müdürün görünür olacağı için ifşa etmeye hazır olduğunuz toplasa bile hizmet sahibi güvenmelisiniz.  
  
 Bir kural olarak, bu nedenle, kod ve ihtiyaç duyduğunuz güvenlik düzeyine karşıladığından emin olmak için meta veriler kodu ve meta verileri güvenilmeyen bir kaynaktan kullanırken, kontrol edin.  
  
## <a name="setting-a-client-credential"></a>İstemci kimlik bilgilerini ayarlama  
 Bir istemcide istemci kimlik bilgilerini ayarlama iki adımdan oluşur:  
  
1.  Belirlemek *istemci kimlik bilgisi türü* hizmeti gerektirir. Bu iki yöntemden birini kullanarak gerçekleştirilir. İlk olarak, hizmet Oluşturucusu belgelerinden varsa, bu istemci kimlik bilgileri belirtmelisiniz hizmet türü (varsa) gerektirir. İkinci olarak, yalnızca Svcutil.exe aracı tarafından oluşturulan bir yapılandırma dosyası varsa, hangi kimlik bilgisi türü gerekli olduğunu belirlemek için tek tek bağlamaları inceleyebilirsiniz.  
  
2.  Gerçek istemci kimlik bilgilerini belirtin. Gerçek istemci kimlik bilgisi olarak adlandırılan bir *istemci kimlik bilgisi değeri* türünden ayırt etmek için. Örneğin, istemci kimlik bilgisi türü bir sertifika belirtiyorsa, bir sertifika yetkilisi tarafından hizmet verilen bir X.509 sertifikası sağlamanız gerekir güvenleri.  
  
### <a name="determining-the-client-credential-type"></a>İstemci kimlik bilgileri türünü belirleme  
 Oluşturulan Svcutil.exe aracı dosya, inceleyin yapılandırmanız varsa [ \<bağlamaları >](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) hangi istemci kimlik bilgisi türü gerekli olduğunu belirlemek için bölüm. Bölüm içinde güvenlik gereksinimlerini belirtin bağlama öğelerdir. Özellikle, inceleyin \<Güvenlik > her bağlamanın öğesi. Bu öğe içeren `mode` üç değerlerden birine ayarlayın özniteliği (`Message`, `Transport`, veya `TransportWithMessageCredential`). Özniteliğin değerini modunu belirler ve alt öğelerini önemli olduğu modu belirler.  
  
 `<security>` Öğesi içerebilir ya da bir `<transport>` veya `<message>` öğesi ya da her ikisini de. Önemli güvenlik modunu eşleşen bir öğedir. Örneğin, aşağıdaki kodu güvenlik modunu belirtir `"Message"`ve türü için kimlik bilgisi istemci `<message>` öğesi `"Certificate"`. Bu durumda, `<transport>` öğesi yoksayıldı. Ancak, `<message>` öğesi belirttiğinden bir X.509 sertifikası sağlanmalıdır.  
  
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
  
 Unutmayın `clientCredentialType` özniteliği `"Windows"`, aşağıdaki örnekte gösterildiği gibi gerçek kimlik bilgisi değer sağlamanız gerekmez. Windows tümleşik güvenliği istemci çalışan kişinin gerçek kimlik bilgisi (Kerberos belirteci) sağlamasından kaynaklanır.  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>İstemci kimlik bilgisi değeri ayarlama  
 İstemci bir kimlik bilgisi sağlamalısınız belirlenir, istemciyi yapılandırmak için uygun yöntemi kullanın. Örneğin, bir istemci sertifikası ayarlamak için kullanın <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> yöntemi.  
  
 Ortak kimlik bilgisi X.509 sertifikası biçimidir. İki yolla kimlik bilgileri sağlayabilir:  
  
-   İstemci kodunuzda programlama tarafından (kullanarak `SetCertificate` yöntemi).  
  
 Ekleyerek bir [ \<davranışları >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) istemci yapılandırma dosyasının ve kullanarak `clientCredentials` öğesi (aşağıda gösterilen).  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>Ayarı bir \<clientCredentials > kod değeri  
 Ayarlamak için bir [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) değeri kodda erişmesi gereken <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> özelliği <xref:System.ServiceModel.ClientBase%601> sınıfı. Özellik döndürür bir <xref:System.ServiceModel.Description.ClientCredentials> aşağıdaki tabloda gösterildiği gibi çeşitli kimlik bilgisi türlerinin erişimi veren nesnesi.  
  
|ClientCredential özelliği|Açıklama|Notlar|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|Döndürür bir <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|Hizmete kendi kimliğini doğrulamak için istemci tarafından sağlanan bir X.509 sertifikası temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|Döndürür bir <xref:System.ServiceModel.Security.HttpDigestClientCredential>|Bir HTTP digest kimlik bilgileri temsil eder. Kimlik bilgisi, kullanıcı adı ve parola karmasıdır.|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|Döndürür bir <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|Bir güvenlik belirteci Federasyon senaryolarında kullanılan hizmeti tarafından verilmiş bir özel güvenlik belirteci temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|Döndürür bir <xref:System.ServiceModel.Security.PeerCredential>|Bir Windows etki alanındaki bir eş kafes katılım için eş kimlik bilgilerini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|Döndürür bir <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|Bir bant dışı anlaşma hizmeti tarafından sağlanan bir X.509 sertifikası temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|Döndürür bir <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|Bir kullanıcı adı ve parola çiftini temsil eder.|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|Döndürür bir <xref:System.ServiceModel.Security.WindowsClientCredential>|Bir Windows istemcisi kimlik bilgisi (Kerberos kimlik bilgisi) temsil eder. Sınıfının özelliklerine salt okunurdur.|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>Ayarı bir \<clientCredentials > yapılandırma değeri  
 Kimlik bilgileri değerlerini belirtilen bir uç noktası davranışı alt öğeleri olarak kullanarak [ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) öğesi. Kullanılan öğe istemci kimlik bilgisi türüne bağlıdır. Örneğin, aşağıdaki örnekte bir X.509 sertifikası kullanarak ayarlamak için yapılandırma gösterilir <[\<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).  
  
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
  
 Yapılandırmada istemci kimlik bilgilerini ayarlamak için ekleme bir [ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md) yapılandırma dosyası öğesi. Ayrıca, hizmetin uç noktasına eklenen davranışı öğesi bağlanmalıdır kullanarak `behaviorConfiguration` özniteliği [ \<uç noktası >](http://msdn.microsoft.com/library/13aa23b7-2f08-4add-8dbf-a99f8127c017) aşağıdaki örnekte gösterildiği gibi öğesi. Değeri `behaviorConfiguration` özniteliği davranışı değerini eşleşmelidir `name` özniteliği.  
  
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
>  Bazı istemci kimlik bilgisi değerleri kümesi uygulama yapılandırma dosyaları, örneğin kullanarak, kullanıcı adı ve parola veya Windows kullanıcı ve parola değerlerini olamaz. Bu kimlik bilgisi değerleri yalnızca kodda belirtilebilir.  
  
 İstemci kimlik bilgileri ayarlama hakkında daha fazla bilgi için bkz: [nasıl yapılır: istemci kimlik bilgileri değerlerini belirtme](../../../docs/framework/wcf/how-to-specify-client-credential-values.md).  
  
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
