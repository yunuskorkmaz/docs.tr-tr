---
title: Federasyon
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
caps.latest.revision: "26"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 71b685b372edc99ffa8ea00180cdf622c5e48632
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="federation"></a>Federasyon
Bu konu, Federasyon güvenlik kavramı kısa bir genel bakış sağlar. Ayrıca açıklanır [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] destek federe güvenlik mimarileri dağıtmak için. Federasyon gösteren örnek bir uygulama için bkz: [Federasyon örnek](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Federasyon güvenlik tanımı  
 Bir istemci erişim hizmeti ile ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında temiz ayırmayı federe güvenlik sağlar. Federasyon güvenlik işbirliği birden çok sistemler, ağlar ve farklı güven bölgelerinde kuruluşlarda üzerinden de sağlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]oluşturma ve dağıtma federe güvenlik işe dağıtılmış sistemler için destek sağlar.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Öğeleri bir federe güvenlik mimarisi  
 Federasyon güvenlik mimarisi aşağıdaki tabloda açıklandığı gibi üç temel öğeleri vardır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Etki alanı/bölge|Güvenlik yönetimi ya da güven tek bir birimi. Tipik bir etki alanı tek bir kurumun içerebilir.|  
|Federasyon|Güven etki alanı topluluğu. Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve neredeyse her zaman yetkilendirme içerir. Tipik bir federasyon güveni bir kaynak kümesi için paylaşılan erişim için kuruluş sayısı içerebilir.|  
|Güvenlik Belirteci Hizmeti (STS)|Güvenlik belirteçleri Web hizmeti; diğer bir deyişle, sağlanmayacağını güvendiği, çok güvendiği kanıt üzerinde temel onaylar kolaylaştırır. Bu, etki alanı arasında güven aracılığı yapmaktan temelini oluşturur.|  
  
### <a name="example-scenario"></a>Örnek senaryo  
 Aşağıdaki çizimde bir federe güvenlik örneği gösterilmektedir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Bu senaryo iki kuruluş içerir: A ve b kuruluş B sahip bir kuruluştaki bazı kullanıcılar değerli Bul bir Web kaynağını (Web hizmeti).  
  
> [!NOTE]
>  Bu bölümde koşullarını kullanır *kaynak*, *hizmet*, ve *Web hizmeti* birbirinin yerine.  
  
 Genellikle, kuruluş B, A kuruluştan bir kullanıcı geçerli çeşit hizmet erişmeden önce kimlik doğrulaması sağlaması gerekir. Ayrıca, kuruluş ayrıca kullanıcının söz konusu belirli kaynağa erişmek için yetkili gerekebilir. Bu sorunu gidermek ve kuruluştaki B kaynağa erişmek için bir kuruluştaki kullanıcılar etkinleştirmek için bir yolu aşağıdaki gibidir:  
  
-   Bir kuruluştan kullanıcıların kimlik bilgilerini (kullanıcı adı ve parola) kuruluşunuza B. kaydedin.  
  
-   Kaynak erişim sırasında kullanıcıların bir kuruluştan kuruluşa B kimlik bilgilerini sunmak ve kaynağa erişmeden önce kimlik doğrulaması.  
  
 Bu yaklaşımın üç önemli sakıncaları vardır:  
  
-   Kullanıcılar için kimlik bilgilerini yerel kullanıcı kimlik bilgilerini yönetmeye ek olarak bir kuruluştan yönetmek kuruluşun B vardır.  
  
-   Bir kuruluştaki kullanıcılar gereken ek bir kimlik bilgileri kümesini korumak (diğer bir deyişle, bir ek kullanıcı adı ve parola unutmayın) normalde A. kuruluşunuzdaki kaynaklara erişmek için kullandıkları kimlik dışında Bu genellikle zayıf güvenlik önlemi olduğu birden çok hizmet sitede aynı kullanıcı adı ve parola kullanarak uygulama teşvik eder.  
  
-   Daha fazla kuruluşlar bazı değeri olarak B kuruluşu kaynak bakışını gibi mimarisi ölçeklenmez.  
  
 Yukarıda açıklanan belirli sakıncaları adresleri, alternatif bir yaklaşım federe güvenlik kullanmayı ' dir. Bu yaklaşımda kuruluşlar A ve B bir güven ilişkisi oluşturmak ve güvenlik belirteci hizmeti (oluşturulan güven aracılığı yapmaktan etkinleştirmek için STS) kullanan.  
  
 B kuruluştaki kimliğini doğrular ve kendi erişimini yetkilendirir geçerli güvenlik uygulamasından bir belirteç kuruluştaki B STS sunmalıdır Web hizmeti erişim vermek istiyorsanız bir federe güvenlik mimaride kullanıcılar bir kuruluştan biliyor belirli hizmet.  
  
 STS B başvurarak üzerinde kullanıcılar yöneltmesi başka bir düzeyi STS ile ilişkili ilkesinden alır. Geçerli bir güvenlik sunması gerekir (yani, güven istemcisinin) STS A'dan belirteci STS B bunları bir güvenlik belirteci yayımlayabilmesi. Bu iki kuruluş arasında bir güven ilişkisi corollary ve kuruluş B A. kuruluştan kullanıcılar için kimlikleri yönetme yok anlamına gelir Uygulamada, STS B null sahip `issuerAddress` ve `issuerMetadataAddress`. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nasıl yapılır: yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Bu durumda, istemci STS A. bulmak için bir yerel ilke başvurur Bu yapılandırma olarak adlandırılır *giriş bölgesi Federasyon* ve STS B STS A. hakkındaki bilgileri tutmak sahip olmadığından daha iyi ölçeklenir  
  
 Kullanıcıların sonra kuruluştaki bir STS başvurun ve normalde A. kuruluştaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama bilgilerini sunarak bir güvenlik belirteci alın Bu aynı zamanda birden çok kimlik bilgileri kümesi bakımını yapmak zorunda veya birden çok hizmet sitede aynı kimlik bilgileri kümesini kullanarak kullanıcı sorununu ortadan kaldırır.  
  
 Kullanıcılar bir güvenlik belirteci STS A'dan edindikten sonra kullanıcıların isteklerin yetkilendirme gerçekleştirmek üzere STS B. kuruluş B kazançlar belirtece sunmak ve kullanıcılara kendi güvenlik belirteçlerini kümesinden bir güvenlik belirteci verir. Kullanıcılar kendi belirteci kaynağa B kuruluştan sunmak ve hizmete erişim.  
  
## <a name="support-for-federated-security-in-wcf"></a>Wcf'de güvenlik desteği  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Federasyon güvenlik mimarileri üzerinden dağıtmak için anahtar teslimi desteği sağlar [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) istek-yanıt iletişim stili temelindeki iletim mekanizması olarak HTTP kullanımını kapsar güvenli, güvenilir ve birlikte çalışabilir bağlama öğesi sağlar metin ve XML kodlama için kablo biçimi olarak kullanan.  
  
 Kullanımını [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Federasyon güvenliğinde senaryo iki mantıksal olarak bağımsızdır aşamaya, aşağıdaki bölümlerde açıklandığı gibi ayrılmış.  
  
### <a name="phase-1-design-phase"></a>1. Aşama: Tasarım aşaması  
 Tasarım aşamasında, istemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet uç noktasını kullanıma sunar ilkesini okuyun ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerine toplamak için. Uygun proxy'leri istemcide aşağıdaki federe güvenlik iletişim düzeni oluşturmak üzere oluşturulur:  
  
-   İstemci güven bölge içinde STS ile bir güvenlik belirteci alın.  
  
-   Belirteç Hizmeti güven bölge içinde STS sunar.  
  
-   Bir güvenlik belirteci hizmeti güven bölge içinde STS almak.  
  
-   Belirteç hizmetine erişmek için hizmet sunar.  
  
### <a name="phase-2-run-time-phase"></a>2. Aşama: Çalışma zamanında aşaması  
 Çalışma zamanı aşamasında, istemci bir nesneyi başlatır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci sınıfı ve kullanarak bir çağrı yapar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] istemci. Temel alınan çerçevesinin [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] federe güvenlik iletişim düzeni yukarıda açıklanan adımları işler ve sorunsuz bir şekilde hizmeti kullanmak istemci sağlar.  
  
## <a name="sample-implementation-using-wcf"></a>WCF kullanarak örnek uygulama  
 Yerel Destek'ten kullanarak bir Federasyon güvenlik mimarisi için bir örnek uygulama aşağıda gösterilmiştir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 ![WCF güvenliğinde Federasyon](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Örnek MyService  
 Hizmet `MyService` tek bir uç noktası aracılığıyla kullanıma sunan `MyServiceEndpoint`. Aşağıdaki çizimde, adresi, bağlama ve uç noktasıyla ilişkili sözleşme gösterir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")  
  
 Hizmet uç noktası `MyServiceEndpoint` kullanan [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve geçerli bir güvenlik onaylar biçimlendirme dili (SAML) belirteci ile gerektiren bir `accessAuthorized` STS B. tarafından verilen talep Bu hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.MyService"      
        behaviorConfiguration='MyServiceBehavior'>  
        <endpoint address=""  
            binding=" wsFederationHttpBinding"  
            bindingConfiguration='MyServiceBinding'  
            contract="Federation.IMyService" />  
   </service>  
  </services>  
  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by MyService. It redirects   
    clients to STS-B. -->  
      <binding name='MyServiceBinding'>  
        <security mode="Message">  
           <message issuedTokenType=  
"http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
           <issuer address="http://localhost/FederationSample/STS-B/STS.svc" />  
            <issuerMetadata   
           address=  
"http://localhost/FederationSample/STS-B/STS.svc/mex" />  
         <requiredClaimTypes>  
            <add claimType="http://tempuri.org:accessAuthorized" />  
         </requiredClaimTypes>  
        </message>  
      </security>  
      </binding>  
    </wsFederationHttpBinding>  
  </bindings>  
  
  <behaviors>  
    <behavior name='MyServiceBehavior'>  
      <serviceAuthorization   
operationRequirementType="FederationSample.MyServiceOperationRequirement, MyService" />  
       <serviceCredentials>  
         <serviceCertificate findValue="CN=FederationSample.com"  
         x509FindType="FindBySubjectDistinguishedName"  
         storeLocation='LocalMachine'  
         storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Bir ince noktası gerektirdiği talepler hakkında unutulmamalıdır `MyService`. İkinci şekil belirten `MyService` bir SAML belirteci gerektirir `accessAuthorized` talep. Daha kesin olacak şekilde bu talep türü belirtir `MyService` gerektirir. Bu talep türünün tam adını (birlikte ilişkili ad alanı), hizmet yapılandırma dosyasında kullanılan http://tempuri.org:accessAuthorized ' dir. Bu talep değerini bu talep durumunu gösteren ve ayarlamak için kabul `true` STS B. tarafından  
  
 Çalışma zamanında, bu ilke tarafından uygulanan `MyServiceOperationRequirement` parçası olarak uygulanan sınıfı `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 STS B. aşağıda gösterilmektedir Daha önce belirtildiği gibi bir güvenlik belirteci hizmeti (STS) de bir Web hizmetidir ve ilişkili uç noktaları, ilke ve benzeri olabilir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B adlı tek bir uç noktasını kullanıma sunar `STSEndpoint` isteği güvenlik belirteçleri kullanımına olabilir. Özellikle, STS B SAML ile belirteçleri `accessAuthorized` talep, hangi konumunda sunulabilir `MyService` hizmete erişim için hizmet sitesi. Ancak, STS B içeren STS A verilen geçerli bir SAML belirteci sunmak kullanıcılara gerektirir `userAuthenticated` talep. Bu STS yapılandırmasında bildirimli olarak belirtilir.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_B" behaviorConfiguration=  
     "STS-B_Behavior">  
    <endpoint address=""  
              binding="wsFederationHttpBinding"  
              bindingConfiguration='STS-B_Binding'  
      contract="FederationSample.ISts" />  
    </service>  
  </services>  
  <bindings>  
    <wsFederationHttpBinding>  
    <!-- This is the binding used by STS-B. It redirects clients to   
         STS-A. -->  
      <binding name='STS-B_Binding'>  
        <security mode='Message'>  
          <message issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
          <issuer address='http://localhost/FederationSample/STS-A/STS.svc' />  
          <issuerMetadata address='http://localhost/FederationSample/STS-A/STS.svc/mex'/>  
          <requiredClaimTypes>  
            <add claimType='http://tempuri.org:userAuthenticated'/>  
          </requiredClaimTypes>  
          </message>  
        </security>  
    </binding>  
   </wsFederationHttpBinding>  
  </bindings>  
  <behaviors>  
  <behavior name='STS-B_Behavior'>  
    <serviceAuthorization   operationRequirementType='FederationSample.STS_B_OperationRequirement, STS_B' />  
    <serviceCredentials>  
      <serviceCertificate findValue='CN=FederationSample.com'  
      x509FindType='FindBySubjectDistinguishedName'  
       storeLocation='LocalMachine'  
       storeName='My' />  
     </serviceCredentials>  
   </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
> [!NOTE]
>  Yeniden `userAuthenticated` talep olduğu STS B. tarafından gerekli talep türü Bu talep türünün tam adını STS yapılandırma dosyasında kullanılan http://tempuri.org:userAuthenticated (birlikte ilişkili ad alanı), ' dir. Bu talep değerini bu talep durumunu gösteren ve ayarlamak için kabul `true` STS A. tarafından  
  
 Çalışma zamanında `STS_B_OperationRequirement` sınıfı STS B. bir parçası olarak uygulanan bu ilkeyi zorlar  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Erişim denetimi boş olduğunda, bir SAML belirteci STS B sorunları `accessAuthorized` talep.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 STS A. aşağıda gösterilmektedir  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 STS B, STS A Ayrıca güvenlik belirteçleri sağlar ve bu amaç için tek bir uç nokta gösteren bir Web hizmeti benzer. Ancak, başka bir bağlama kullanır (`wsHttpBinding`) ve geçerli bir sunmak kullanıcıların gerektiren [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ile bir `emailAddress` talep. SAML belirteçleri ile verdiği yanıt olarak `userAuthenticated` talep. Bu hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
```xml  
<system.serviceModel>  
  <services>  
    <service type="FederationSample.STS_A" behaviorConfiguration="STS-A_Behavior">  
      <endpoint address=""  
                binding="wsHttpBinding"  
                bindingConfiguration="STS-A_Binding"  
                contract="FederationSample.ISts">  
       <identity>  
       <certificateReference findValue="CN=FederationSample.com"    
                       x509FindType="FindBySubjectDistinguishedName"  
                       storeLocation="LocalMachine"   
                       storeName="My" />  
       </identity>  
    <endpoint>  
  </service>  
</services>  
  
<bindings>  
  <wsHttpBinding>  
  <!-- This is the binding used by STS-A. It requires users to present  
   a CardSpace. -->  
    <binding name='STS-A_Binding'>  
      <security mode='Message'>  
        <message clientCredentialType="CardSpace" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
  
<behaviors>  
  <behavior name='STS-A_Behavior'>  
    <serviceAuthorization operationRequirementType=  
     "FederationSample.STS_A_OperationRequirement, STS_A" />  
      <serviceCredentials>  
  <serviceCertificate findValue="CN=FederationSample.com"  
                     x509FindType='FindBySubjectDistinguishedName'  
                     storeLocation='LocalMachine'  
                     storeName='My' />  
      </serviceCredentials>  
    </behavior>  
  </behaviors>  
</system.serviceModel>  
```  
  
 Çalışma zamanında `STS_A_OperationRequirement` sınıfı STS A. bir parçası olarak uygulanan bu ilkeyi zorlar  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Erişim ise `true`, STS A sorunları SAML belirteci ile `userAuthenticated` talep.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Kuruluşun bir istemcide  
 Aşağıdaki çizimde istemci kuruluşta A adımlarını birlikte yapma gösterir bir `MyService` hizmet çağrısı. Bir işlev bileşenleri de bütünlük açısından dahil edilmiştir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Özet  
 Federasyon güvenlik sorumluluk temiz bölme sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur. Derleme ve dağıtılmış uygulamaları dağıtmak için bir platform olarak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] federe güvenlik uygulamak için yerel destek sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
