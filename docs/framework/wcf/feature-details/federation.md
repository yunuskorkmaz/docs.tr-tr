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
ms.openlocfilehash: 86c679af77f2b7b1960e7489e0e6e61b811e1bad
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185217"
---
# <a name="federation"></a>Federasyon
Bu konu federe güvenlik kavramına kısa bir genel bakış sağlar. Ayrıca, Windows Communication Foundation (WCF) federe güvenlik mimarilerinin dağıtılması için destek açıklar. Federasyonu gösteren örnek bir uygulama için [Federasyon Örneği'ne](../../../../docs/framework/wcf/samples/federation-sample.md)bakın.  
  
## <a name="definition-of-federated-security"></a>Federe Güvenliğin Tanımı  
 Federe güvenlik, istemcinin eriştisi olduğu hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamları arasında temiz ayrım yapılmasına olanak tanır. Federe güvenlik, farklı güven bölgelerindeki birden çok sistem, ağ ve kuruluş arasında işbirliğine de olanak sağlar.  
  
 WCF, federe güvenlik kullanan dağıtılmış sistemlerin oluşturulması ve dağıtılması için destek sağlar.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Federe Güvenlik Mimarisinin Unsurları  
 Federe güvenlik mimarisi, aşağıdaki tabloda açıklandığı gibi üç temel öğeye sahiptir.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Etki alanı/bölge|Güvenlik yönetimi veya güven tek bir birim. Tipik bir etki alanı tek bir kuruluş içerebilir.|  
|Federasyon|Güven oluşturmuş etki alanları topluluğu. Güven düzeyi değişebilir, ancak genellikle kimlik doğrulaması içerir ve hemen hemen her zaman yetkilendirme içerir. Tipik bir federasyon, bir dizi kaynağa paylaşılan erişim için güven oluşturmuş bir dizi kuruluş içerebilir.|  
|Güvenlik Belirteci Hizmeti (STS)|Güvenlik belirteçleri veren bir Web hizmeti; diğer bir şey, güvendiği kanıtlara dayanarak iddialarda yer almakta, kime güvenirse güvensin. Bu, etki alanları arasında güven aracılığı temelini oluşturur.|  
  
### <a name="example-scenario"></a>Örnek Senaryo  
 Aşağıdaki resimde federe güvenlik bir örnek gösterilmektedir:  
  
 ![Tipik bir federe güvenlik senaryosu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 Bu senaryo iki kuruluş içerir: A ve B Organizasyonu B'nin A organizasyonundaki bazı kullanıcıların değerli bulduğu bir Web kaynağı (Web hizmeti) vardır.  
  
> [!NOTE]
> Bu bölümde *kaynak,* *hizmet*ve *Web hizmeti* terimleri birbirinin yerine kullanılır.  
  
 Genellikle, B kuruluşu, A kuruluşundaki bir kullanıcının hizmete erişmeden önce geçerli bir kimlik doğrulama biçimi sağlamasını gerektirir. Buna ek olarak, kuruluş kullanıcısöz konusu belirli kaynağa erişmek için yetkili olmasını da gerektirebilir. Bu sorunu gidermenin ve A organizasyonundaki kullanıcıların B organizasyonundaki kaynağa erişmesini sağlamanın bir yolu aşağıdaki gibidir:  
  
- A kuruluşunun kullanıcıları kimlik bilgilerini (kullanıcı adı ve parola) B kuruluşuna kaydeder.  
  
- Kaynak erişimi sırasında, A organizasyonundaki kullanıcılar kimlik bilgilerini B kuruluşuna sunar ve kaynağa erişmeden önce kimlik doğrulaması yapılır.  
  
 Bu yaklaşımın üç önemli dezavantajı vardır:  
  
- B organizasyonu, yerel kullanıcılarının kimlik bilgilerini yönetmeye ek olarak A organizasyonundaki kullanıcıların kimlik bilgilerini yönetmek zorundadır.  
  
- Kuruluştaki kullanıcılar A, a organizasyonu içindeki kaynaklara erişmek için normalde kullandıkları kimlik bilgilerinin dışında ek bir kimlik bilgileri kümesi (diğer bir deyişle ek bir kullanıcı adı ve parolayı hatırlayın) tutmanız gerekir. Bu genellikle zayıf bir güvenlik önlemi olan birden çok hizmet sitelerinde aynı kullanıcı adı ve parolayı kullanma pratiğini teşvik eder.  
  
- Daha fazla kuruluş B organizasyonundaki kaynağı bir değerolarak algıladığı için mimari ölçeklenmez.  
  
 Daha önce bahsedilen sakıncaları gideren alternatif bir yaklaşım, federe güvenlik istihdam etmektir. Bu yaklaşımda, A ve B kuruluşları bir güven ilişkisi kurar ve kurulan güvenin aracılık etmesini sağlamak için Güvenlik Belirteci Hizmeti (STS) kullanır.  
  
 Federe güvenlik mimarisinde, A organizasyonundaki kullanıcılar B organizasyonundaki Web hizmetine erişmek istiyorlarsa, B organizasyonunda STS'den geçerli bir güvenlik belirteci sunmaları gerektiğini ve bu nedenle özel hizmet.  
  
 STS B ile iletişime geçerek, kullanıcılar STS ile ilişkili ilkeden başka bir yönlendirme düzeyi alır. STS B'nin onlara bir güvenlik belirteci verabilmesi için STS A'dan (diğer bir şekilde istemci güven diyarı) geçerli bir güvenlik belirteci sunmaları gerekir. Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sonucudur ve B kuruluşunun A organizasyonundaki kullanıcılar için kimlikleri yönetmesi gerekmediğini ima eder. Uygulamada, STS B genellikle bir `issuerAddress` `issuerMetadataAddress`null ve . Daha fazla bilgi için [bkz: Yerel İhraççı'yı yapılandırma.](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md) Bu durumda, istemci STS A'yı bulmak için yerel bir ilkeden başvurur. STS B STS A hakkında bilgi korumak zorunda değildir, çünkü bu yapılandırma *ev bölge federasyonu* denir ve daha iyi ölçekler.  
  
 Kullanıcılar daha sonra A organizasyonundaki STS ile iletişime geçer ve normalde A kuruluşundaki herhangi bir kaynağa erişmek için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu, kullanıcıların birden çok kimlik belgesi kümesini korumak veya birden çok hizmet sitesinde aynı kimlik bilgileri kümesini kullanmak zorunda kalma sorununu da hafifletir.  
  
 Kullanıcılar STS A'dan bir güvenlik belirteci aldıktan sonra, belirteci STS B. Organization B'ye sunarlar ve kullanıcıların isteklerinin yetkilendirmesini gerçekleştirmek için gelirler ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci verir. Kullanıcılar daha sonra belirteçlerini B kuruluşundaki kaynağa sunabilir ve hizmete erişebilir.  
  
## <a name="support-for-federated-security-in-wcf"></a>WCF'de Federe Güvenliğe Destek  
 WCF [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)aracılığıyla federe güvenlik mimarileri dağıtmak için anahtar teslimi destek sağlar.  
  
 wsFederationHttpBinding>öğesi, http'nin istek yanıtı iletişim stili için temel aktarım mekanizması olarak kullanılmasını gerektiren güvenli, güvenilir ve birlikte çalışabilir bir bağlama sağlar ve kodkodlama için tel biçimi olarak metin ve XML kullanır. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
  
 bir federe güvenlik senaryosunda wsFederationHttpBinding>kullanımı, aşağıdaki bölümlerde açıklandığı gibi, mantıksal olarak bağımsız iki aşamaya ayrıştırılabilir. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)  
  
### <a name="phase-1-design-phase"></a>Faz 1: Tasarım Aşaması  
 Tasarım aşamasında istemci [ServiceModel Metadata Utility Tool'u (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) hizmet bitiş noktasının ortaya çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için kullanır. Uygun vekiller, istemcide aşağıdaki federe güvenlik iletişimi deseni oluşturmak için oluşturulur:  
  
- İstemci güven alanında STS'den bir güvenlik belirteci edinin.  
  
- Belirteci hizmet güven alanında STS'ye sunun.  
  
- Hizmet güven alanında STS'den bir güvenlik belirteci edinin.  
  
- Hizmete erişmek için belirteci hizmete sunun.  
  
### <a name="phase-2-run-time-phase"></a>Aşama 2: Çalışma Zamanı Aşaması  
 Çalışma süresi aşamasında, istemci WCF istemci sınıfının bir nesnesini anında alar ve WCF istemcisini kullanarak arama yapar. WCF'nin temel çerçevesi, federe güvenlik iletişimi modelinde daha önce belirtilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde tüketmesini sağlar.  
  
## <a name="sample-implementation-using-wcf"></a>WCF kullanarak örnek uygulama  
 Aşağıdaki resimde, WCF'nin yerel desteğini kullanarak federe bir güvenlik mimarisi için örnek bir uygulama gösterilmektedir.  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Örnek MyService  
 `MyService` Hizmet, tek bir bitiş `MyServiceEndpoint`noktasını . Aşağıdaki resimde bitiş noktasıile ilişkili adres, bağlama ve sözleşme gösterilmektedir.  
  
 ![MyServiceEndpoint ayrıntılarını gösteren diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 Hizmet bitiş `MyServiceEndpoint` noktası [ \<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanır ve STS B tarafından verilen bir talep `accessAuthorized` ile geçerli bir Güvenlik İddiaları İşaretleme Dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimsel olarak belirtilir.  
  
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
> İnce bir nokta tarafından `MyService`gerekli iddiaları hakkında dikkat edilmelidir. İkinci şekil, `MyService` iddiaile bir SAML `accessAuthorized` belirteci gerektirdiğini gösterir. Daha kesin olmak gerekirse, bu `MyService` talep türünü belirtir. Bu talep türünün `http://tempuri.org:accessAuthorized` tam nitelikli adı ( ilişkili ad alanı ile birlikte), hizmet yapılandırma dosyasında kullanılır. Bu talebin değeri bu talebin varlığını gösterir ve `true` STS B tarafından ayarlanır varsayılır.  
  
 Çalışma zamanında, bu ilke `MyServiceOperationRequirement` bir parçası olarak uygulanan sınıf `MyService`tarafından zorlanır.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Aşağıdaki resimde STS B gösterilmektedir. Daha önce de belirtildiği gibi, bir güvenlik belirteç hizmeti (STS) aynı zamanda bir Web hizmetidir ve ilişkili uç noktalarına, ilkeye vb. sahip olabilir.  
  
 ![Güvenlik belirteci hizmetini gösteren diyagram B.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B, `STSEndpoint` güvenlik belirteçleri istemek için kullanilebilen tek bir uç noktayı ortaya çıkarır. Özellikle, STS B, hizmete erişmek `accessAuthorized` için `MyService` hizmet yerinde sunulabilecek olan saml belirteçlerini taleple birlikte verir. Ancak, STS B, kullanıcıların `userAuthenticated` STS A tarafından verilen ve talebi içeren geçerli bir SAML belirteci sunmasını gerektirir. Bu, STS yapılandırmasında bildirimsel olarak belirtilir.  
  
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
> Yine, `userAuthenticated` talep STS B tarafından gerekli olan talep türüdür. Bu talep türünün tam nitelikli `http://tempuri.org:userAuthenticated` adı (ilişkili ad alanı ile birlikte) STS yapılandırma dosyasında kullanılır. Bu talebin değeri bu talebin varlığını gösterir ve `true` STS A tarafından ayarlanır varsayılır.  
  
 Çalışma zamanında, `STS_B_OperationRequirement` sınıf STS B'nin bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Erişim denetimi açıksa, `accessAuthorized` STS B taleple birlikte bir SAML belirteci yayınlar.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Aşağıdaki resimde STS A gösterilmektedir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 STS B'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaç için tek bir bitiş noktasını ortaya çıkaran bir Web hizmetidir. Ancak, farklı bir bağlama`wsHttpBinding`kullanır ( ) ve kullanıcıların bir `emailAddress` talep ile geçerli bir CardSpace sunmak için gerektirir. Yanıt olarak, `userAuthenticated` iddia ile SAML belirteçleri sorunları. Bu, hizmet yapılandırmasında bildirimsel olarak belirtilir.  
  
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
  
 Çalışma zamanında sınıf, `STS_A_OperationRequirement` STS A'nın bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Erişim ise, `true`STS A talep ile `userAuthenticated` bir SAML belirteci sorunları.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>A Organizasyonunda İstemci  
 Aşağıdaki resimde, A organizasyonundaki istemci ve bir `MyService` servis çağrısı yapma yla ilgili adımlar gösterilmektedir. Diğer fonksiyonel bileşenler de bütünlük için dahildir.  
  
 ![MyService servis çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Özet  
 Federe güvenlik, temiz bir sorumluluk bölümü sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur. Dağıtılmış uygulamalar oluşturmak ve dağıtmak için bir platform olarak WCF, federe güvenliğin uygulanması için yerel destek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
