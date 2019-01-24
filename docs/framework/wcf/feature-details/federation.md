---
title: Federasyon
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation [WCF]
ms.assetid: 2f1e646f-8361-48d4-9d5d-1b961f31ede4
ms.openlocfilehash: f05d4a9348c12a29dc3cd7b93334ab1134eeb1a3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709396"
---
# <a name="federation"></a>Federasyon
Bu konuda birleşik güvenliği kavramını kısa bir genel bakış sağlar. Ayrıca, Federasyon güvenlik mimariyi dağıtmak için Windows Communication Foundation (WCF) desteği açıklanmaktadır. Federasyon gösteren örnek bir uygulama için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Federasyon güvenlik tanımı  
 Birleşik güvenliği bir istemci erişim hizmeti ve ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında ayrım sağlar. Birleşik güvenliği ayrıca birden fazla sistemler, ağlar ve farklı güven bölgelerinde kuruluşta işbirliği sağlar.  
  
 WCF oluştururken ve dağıtırken, Federasyon güvenlik kullanan dağıtılmış sistemler için destek sağlar.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Öğeleri bir Federasyon güvenlik mimarisi  
 Birleşik güvenliği mimari, aşağıdaki tabloda açıklandığı gibi üç anahtar öğelerin sahiptir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Domain/realm|Güvenlik yönetimi ya da güven tek bir birim. Tipik bir etki alanı, tek bir kuruma içerebilir.|  
|Federasyon|Güveni olan etki alanları koleksiyonu. Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve hemen her zaman yetkilendirme içerir. Tipik bir federasyon güveni için bir kaynak kümesi için paylaşılan erişim kuruluşların sayısı içerebilir.|  
|Güvenlik Belirteci Hizmeti (STS)|Güvenlik belirteçleri bir Web hizmeti; diğer bir deyişle, onaylamalar yanınızda güvendiği, çok güvendiği kanıta göre yapar. Bu, etki alanı arasında güven aracılığı yapmaktan'ın temelini oluşturur.|  
  
### <a name="example-scenario"></a>Örnek senaryo  
 Birleşik güvenliği örneği aşağıda gösterilmiştir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/typicalfederatedsecurityscenario.gif "TypicalFederatedSecurityScenario")  
  
 Bu senaryo, iki kuruluş içerir: A ve b kuruluş, bir kuruluştaki bazı kullanıcılar değerli bulduğunuz bir Web kaynağı (bir Web hizmeti) sahip.  
  
> [!NOTE]
>  Bu bölümde terimler kullanılmaktadır *kaynak*, *hizmet*, ve *Web hizmeti* birbirinin yerine.  
  
 Genellikle, kuruluş B, A kuruluştan bir kullanıcı geçerli çeşit hizmet erişmeden önce kimlik doğrulaması sağlaması gerekir. Ayrıca, kuruluş Ayrıca kullanıcı söz konusu belirli kaynağa erişim yetkisi olması gerekebilir. Bu sorunu gidermek ve kuruluştaki B kaynağa erişmek için bir kuruluştaki kullanıcılara etkinleştirmek için bir yol aşağıdaki gibidir:  
  
-   Bir kuruluşun kullanıcıları, kimlik bilgilerini (kullanıcı adı ve parola) kuruluş b ile kaydedin.  
  
-   Kaynak erişim sırasında bir kuruluşun kullanıcıları kuruluş B için kimlik bilgilerini sunmak ve kaynağa erişmeden önce kimlikleri doğrulanır.  
  
 Bu yaklaşım, üç önemli engelleri vardır:  
  
-   Yerel kullanıcı kimlik bilgilerini yönetmenin yanı sıra bir kuruluştan kullanıcılar için kimlik bilgilerini yönetmek B kuruluş var.  
  
-   Bir kuruluştaki kullanıcılara ek bir kimlik bilgileri kümesini bulundurmak gerekir (diğer bir deyişle, bir ek kullanıcı adınızı ve parolanızı hatırlayacağınızdan) dışında normalde A. kuruluşundaki kaynaklara erişmek için kullandıkları kimlik bilgileri Bu genellikle zayıf güvenlik önlemi olduğu birden çok hizmet sitede aynı kullanıcı adı ve parola kullanarak uygulama teşvik eder.  
  
-   Kaynak kuruluşta B bazı değeri olarak kuruluşların algılar gibi mimarisi ölçeklenmez.  
  
 Daha önce bahsedilen dezavantajları adresleri, alternatif bir yaklaşım, Federasyon güvenlik görevlendirmek sağlamaktır. Bu yaklaşım, kuruluşların A ve B bir güven ilişkisi kurmak ve güvenlik belirteci hizmeti (kurulan güven aracılığı yapmaktan etkinleştirmek için STS) kullanın.  
  
 İsterseniz kuruluşunuzdaki B kimlik doğrulamasından geçiren ve kullanıcıların erişimini yetkilendirir bir geçerli güvenlik belirtecine kuruluştaki B, STS sunması gerekir Web hizmetine erişmek birleşik güvenliği mimaride, bir kuruluşun kullanıcıları biliyor belirli hizmet.  
  
 STS B başvurarak üzerinde bir STS ile ilişkili ilkeden başka bir yöneltme düzeyi kullanıcıları alır. Geçerli bir güvenlik sunması gerekir (diğer bir deyişle, istemci güven bölge) STS A'dan belirteci STS B bir güvenlik belirteci vermeden önce. Bu iki kuruluş arasında bir güven ilişkisi bir corollary ve kuruluş B A. kuruluştan kullanıcılar için kimlikleri yönetme yok anlamına gelir. Uygulamada, STS B null olan `issuerAddress` ve `issuerMetadataAddress`. Daha fazla bilgi için [nasıl yapılır: Yerel yayımlayan yapılandırma](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md). Bu durumda, istemci STS A. bulmak için yerel bir ilke başvurur Bu yapılandırma olarak adlandırılır *giriş bölge Federasyon* ve STS B STS A. hakkındaki bilgileri tutmak sahip olmadığından, daha iyi ölçeklendirir.  
  
 Kullanıcılar ardından kuruluştaki bir STS ile iletişime geçin ve normalde A. kuruluştaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama bilgileri sunarak bir güvenlik belirteci elde Bu, birden çok kimlik bilgileri kümesi sürdürmek zorunda veya birden çok hizmet sitede aynı kimlik bilgileri kümesini kullanarak kullanıcı sorununu da azaltır.  
  
 Kullanıcılar bir güvenlik belirteci STS A'dan edindikten sonra kullanıcıların isteklerin yetkilendirme gerçekleştirmeye STS B. kuruluş B kazançlar belirtece sunmak ve kendi güvenlik belirteçlerini kümesinden kullanıcılar için bir güvenlik belirteci verir. Kullanıcılar kimliklerini belirteci kaynağa B kuruluştan sunmak ve hizmete erişim.  
  
## <a name="support-for-federated-security-in-wcf"></a>Wcf'de güvenlik için destek  
 WCF güvenlik mimariler aracılığıyla dağıtmaya yönelik kullanıma hazır destek sağlar [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) istek-yanıt iletişim stil temelindeki iletim mekanizması olarak HTTP kullanımını gerektirir güvenli, güvenilir ve birlikte çalışabilen bir bağlama öğesi sağlar metin ve XML olarak kodlamak için kablo biçimini kullanan.  
  
 Kullanımını [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Federasyon security'de senaryo iki mantıksal olarak bağımsızdır aşamaya, aşağıdaki bölümlerde açıklandığı gibi ölçeklendirilebilmeleri.  
  
### <a name="phase-1-design-phase"></a>1. Aşama: Tasarım aşaması  
 Tasarım aşamasında, istemcinin kullandığı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet uç noktasını kullanıma sunar politikasını okuyun ve hizmetin kimlik doğrulaması ve yetkilendirme gereksinimlerine toplanacak. İstemcide aşağıdaki güvenlik iletişim düzeni oluşturmak için uygun proxy oluşturulur:  
  
-   Bir güvenlik belirteci istemcisinin güven içinde STS almak.  
  
-   Belirteç sts'ye hizmet güven bölgedeki sunar.  
  
-   Bir güvenlik belirteci hizmeti güven bölge içinde STS almak.  
  
-   Hizmete erişmek için hizmet belirteci sunar.  
  
### <a name="phase-2-run-time-phase"></a>2. Aşama: Çalışma zamanı aşaması  
 Çalıştırma aşamasında, istemci bir WCF istemcisi sınıfı nesnesinin örneğini oluşturur ve WCF istemcisi kullanarak bir çağrı yapar. WCF temel çerçevesinde, Federasyon güvenlik iletişim deseni yukarıda açıklanan adımları işler ve sorunsuz bir şekilde hizmeti kullanmak ve istemcinin sağlar.  
  
## <a name="sample-implementation-using-wcf"></a>WCF kullanan örnek uygulama  
 Aşağıdaki çizim bir örnek uygulama için yerel destek WCF kullanarak Federasyon güvenlik mimarisi gösterilmektedir.  
  
 ![Wcf'de güvenlik Federasyon](../../../../docs/framework/wcf/feature-details/media/federatedsecurityinwcf.gif "FederatedSecurityInWCF")  
  
### <a name="example-myservice"></a>Örnek MyService  
 Hizmet `MyService` tek bir uç nokta aracılığıyla kullanıma sunan `MyServiceEndpoint`. Aşağıdaki çizim, adres, bağlamayı ve uç noktası ile ilişkili sözleşme gösterir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/myservice.gif "MyService")  
  
 Hizmet uç noktası `MyServiceEndpoint` kullanır [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve geçerli bir güvenlik onaylama işaretleme dili (SAML) belirteçle gerektiren bir `accessAuthorized` STS b tarafından verilen talep Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
>  Bir ince noktası gerektirdiği taleplerle ilgili unutulmamalıdır `MyService`. İkinci şekil belirten `MyService` bir SAML belirteci gerektirir `accessAuthorized` talep. Daha kesin olacak şekilde bu talep türü belirtir `MyService` gerektirir. Bu talep türü tam adı `http://tempuri.org:accessAuthorized` (ilişkili ad alanı ile birlikte), hizmet yapılandırma dosyasında kullanılır. Bu talep değerini bu talep varlığını gösterir ve ayarlanması varsayılır `true` STS b tarafından  
  
 Çalışma zamanında Bu ilke tarafından zorunlu `MyServiceOperationRequirement` parçası olarak uygulanan sınıfı `MyService`.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Aşağıdaki çizim STS b gösterir Daha önce belirtildiği gibi bir güvenlik belirteci hizmeti (STS) de bir Web hizmetidir ve kendi ilişkili uç noktaları, ilke ve benzeri olabilir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/msservicestsb.gif "MsServiceSTSB")  
  
 STS B adlı tek bir uç noktasını kullanıma sunar `STSEndpoint` isteği güvenlik belirteçleri kullanmak olabilir. Özellikle, STS B SAML ile belirteçleri `accessAuthorized` talep, hangi konumunda sunulabilir `MyService` hizmete erişmek için hizmet sitesi. Ancak, kullanıcıların içeren STS A verilen geçerli bir SAML belirteç sunmasını STS B gerektirir `userAuthenticated` talep. Bu, STS yapılandırmada bildirimli olarak belirtilir.  
  
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
>  Yeniden `userAuthenticated` talep olduğunu STS b tarafından gerekli talep türü Bu talep türü tam adı `http://tempuri.org:userAuthenticated` (ilişkili ad alanı ile birlikte), STS'ye yapılandırma dosyasında kullanılır. Bu talep değerini bu talep varlığını gösterir ve ayarlanması varsayılır `true` STS a tarafından  
  
 Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS b bir parçası olarak uygulanan bu ilkeyi zorlar  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Erişim denetimi açık ise, STS B ile bir SAML belirteci verir. `accessAuthorized` talep.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Aşağıdaki çizim STS A. gösterir  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 STS B, STS A de güvenlik belirteçleri sağlar ve bu amaç için tek bir uç noktayı kullanıma sunan bir Web hizmeti benzer. Ancak, farklı bir bağlama kullanır (`wsHttpBinding`) ve geçerli bir sunmak kullanıcıların gerektirir [!INCLUDE[infocard](../../../../includes/infocard-md.md)] ile bir `emailAddress` talep. İsteğe bağlı olarak yanıtta ile SAML belirteçlerini çıkartan `userAuthenticated` talep. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
  
 Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS a'nın bir parçası olarak uygulanan bu ilkeyi zorlar  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Erişim ise `true`, STS bir SAML belirteci ile sorunları `userAuthenticated` talep.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Bir kuruluştaki istemci  
 Aşağıdaki çizimde istemci kuruluşta A yer alan adımların yanı sıra yapma gösterir bir `MyService` hizmet çağrısı. İşlev diğer bileşenleri de bütünlük açısından dahil edilir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/federationclienta.gif "FederationClientA")  
  
## <a name="summary"></a>Özet  
 Birleşik güvenliği sorumluluk temiz bir bölme sağlar ve güvenli, ölçeklenebilir hizmet mimarisi oluşturmak için yardımcı olur. Dağıtılmış uygulama oluşturup dağıtırken için bir platform, WCF, Federasyon güvenlik uygulamak için yerel destek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
