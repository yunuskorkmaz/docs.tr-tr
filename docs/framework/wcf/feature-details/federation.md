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
ms.openlocfilehash: 2331e484f22be7e3154a4cff981ee320a9b143a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948155"
---
# <a name="federation"></a>Federasyon
Bu konuda, Federe güvenlik kavramıyla ilgili kısa bir genel bakış sunulmaktadır. Federasyon güvenlik mimarilerini dağıtmaya yönelik Windows Communication Foundation (WCF) desteğini de açıklar. Federasyonu gösteren örnek bir uygulama için bkz. [Federasyon örneği](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Federal Güvenlik tanımı  
 Federasyon güvenliği, bir istemcinin eriştiği hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamlarına kadar temiz ayrım sağlar. Federasyon güvenliği, farklı güven bölgelerinde birden fazla sistem, ağ ve kuruluşta işbirliği yapılmasını de mümkün.  
  
 WCF, Federasyon güvenliği kullanan dağıtılmış sistemler oluşturmak ve dağıtmak için destek sağlar.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Federasyon güvenlik mimarisinin öğeleri  
 Federasyon güvenlik mimarisinin aşağıdaki tabloda açıklandığı gibi üç anahtar öğesi vardır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Etki alanı/bölge|Tek bir güvenlik yönetimi veya güven birimi. Tipik bir etki alanı tek bir kuruluş içerebilir.|  
|Federasyon|Güvenine sahip bir etki alanı koleksiyonu. Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve hemen her zaman yetkilendirme içerir. Tipik bir federasyon güveni için bir kaynak kümesi için paylaşılan erişim kuruluşların sayısı içerebilir.|  
|Güvenlik Belirteci Hizmeti (STS)|Güvenlik belirteçleri veren bir Web hizmeti; diğer bir deyişle, bu, güvendiğini ve güvenmesini sağlayan kanıtları temel alarak onaylamaları yapar. Bu, etki alanları arasındaki güven aracılığı temelini oluşturur.|  
  
### <a name="example-scenario"></a>Örnek senaryo  
 Aşağıdaki çizimde bir Federasyon güvenliği örneği gösterilmektedir:  
  
 ![Tipik bir Federasyon güvenlik senaryosunu gösteren diyagram.](./media/federation/typical-federated-security-scenario.gif)  
  
 Bu senaryo iki kuruluş içerir: A ve B. kuruluş B, kuruluşlardaki bazı kullanıcıların önemli bulabileceği bir web kaynağına (Web hizmeti) sahiptir.  
  
> [!NOTE]
> Bu bölümde, *kaynak*, *hizmet*ve *Web hizmeti* 'nin birbirlerinin yerine kullanıldığı terimler kullanılmaktadır.  
  
 Genellikle kuruluş B, bir kullanıcının, hizmet erişmeden önce geçerli bir kimlik doğrulama biçimi sağlamasını gerektirir. Ayrıca, kuruluş, kullanıcının söz konusu kaynağa erişmek için yetkilendirilmesini de gerektirebilir. Bu sorunu ele almanın ve kuruluşlardaki kullanıcıların B kuruluşunda kaynağa erişmesi için bir yol aşağıdaki gibidir:  
  
- Kuruluştaki kullanıcılar, kimlik bilgilerini (Kullanıcı adı ve parola) B kuruluşuna kaydeder.  
  
- Kaynak erişimi sırasında, kuruluşlardaki kullanıcılar kimlik bilgilerini B kuruluşuna sunmadan, kaynağa erişmeden önce kimlik doğrulamasından geçer.  
  
 Bu yaklaşım üç önemli dezavantaja sahiptir:  
  
- B kuruluşunun, yerel kullanıcılarının kimlik bilgilerini yönetmeye ek olarak, kuruluşlarındaki kullanıcıların kimlik bilgilerini yönetmesi vardır.  
  
- Kuruluştaki kullanıcıların, normalde bir kuruluş içindeki kaynaklara erişim kazanmak için kullandıkları kimlik bilgilerinden ayrı bir ek kimlik bilgileri (yani, ek Kullanıcı adı ve parola hatırlamaları) olması gerekir. Bu genellikle, çok sayıda hizmet sitesinde aynı Kullanıcı adı ve parolayı kullanma ve zayıf bir güvenlik ölçüsü olan uygulamayı teşvik eder.  
  
- Daha fazla kuruluş, B kuruluşunda kaynağı bir değer olduğu gibi algılamaz mimari ölçeklenmez.  
  
 Daha önce bahsedilen dezavantajları ele veren alternatif bir yaklaşım, Federe güvenlik kullanmaktır. Bu yaklaşımda, A ve B kuruluşları bir güven ilişkisi kurar ve kurulan güvenin aracılı hale getirmesini sağlamak için güvenlik belirteci hizmeti (STS) benimseme.  
  
 Bir Federasyon güvenlik mimarisinde, kuruluşlardaki kullanıcılar b kuruluşunda Web hizmetine erişmek istiyorlarsa, b kuruluşunda bulunan STS 'den geçerli bir güvenlik belirteci sunması gerektiğini ve bunlara erişimini doğrulayan ve belirli bir hizmet.  
  
 STS B ile iletişim kurulurken, kullanıcılar STS ile ilişkili ilkeden başka bir yöneltme düzeyi alır. STS B 'nin bir güvenlik belirteci vermesini gerektiren STS A 'nın (yani, istemci güven bölgesi) geçerli bir güvenlik belirteci sunması gerekir. Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sahibi olabilir ve B kuruluşunun, A kuruluşundan kullanıcılar için kimlikleri yönetmesi gerekmez. Pratikte STS B genellikle null `issuerAddress` ve `issuerMetadataAddress`içerir. Daha fazla bilgi için [nasıl yapılır: Yerel bir veren](../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)yapılandırın. Bu durumda, istemci STS A 'nın yerini bulmak için yerel bir ilke danışmanlar. Bu yapılandırma, *Ev bölgesi Federasyonu* olarak ADLANDıRıLıR ve STS B 'nin STS hakkındaki bilgileri saklamak zorunda olmadığından daha iyi ölçeklendirilir.  
  
 Kullanıcılar A kurumunda STS ile iletişim kurun ve normal olarak kuruluş içindeki diğer kaynaklara erişim kazanmak için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu Ayrıca, kullanıcıların birden çok kimlik bilgisi kümesini sürdürmek veya birden çok hizmet sitesinde aynı kimlik bilgilerini kullanmasını sağlamak zorunda konuma almayı azaltır sorununu da ortadan koyar.  
  
 Kullanıcılar STS A 'dan bir güvenlik belirteci aldıktan sonra, bu belirteci STS 'ye sunar. B. kuruluş, kullanıcıların isteklerini yetkilendirmeyi gerçekleştirmeye devam eder ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci yayınlar. Kullanıcılar daha sonra belirtecini B kuruluşunda kaynağa sunabilir ve hizmete erişebilir.  
  
## <a name="support-for-federated-security-in-wcf"></a>WCF 'de Federal güvenlik desteği  
 WCF, [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)aracılığıyla Federe güvenlik mimarilerini dağıtmaya yönelik anahtar desteği sağlar.  
  
 WSFederationHttpBinding > öğesi, istek-yanıt iletişim stili için temel alınan aktarım mekanizması olarak http kullanımını gerektiren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kodlama için tel biçimlendirme.  
  
 Bir Federasyon güvenlik senaryosunda [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanımı, aşağıdaki bölümlerde açıklandığı gibi iki mantıksal bağımsız aşamaya ayrılabilir.  
  
### <a name="phase-1-design-phase"></a>1\. Aşama: Tasarım aşaması  
 Tasarım aşamasında istemci, hizmet uç noktasının açığa çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. İstemci üzerinde aşağıdaki Federasyon güvenliği iletişim modelini oluşturmak için uygun proxy 'ler oluşturulur:  
  
- İstemci güven bölgesindeki STS 'den bir güvenlik belirteci alın.  
  
- Belirteci hizmet güven bölgesindeki STS 'ye sunun.  
  
- Hizmet güven bölgesindeki STS 'den bir güvenlik belirteci alın.  
  
- Hizmete erişmek için belirteci hizmete sunun.  
  
### <a name="phase-2-run-time-phase"></a>2\. Aşama: Çalışma zamanı aşaması  
 Çalışma zamanı aşamasında istemci, WCF istemci sınıfının bir nesnesini başlatır ve WCF istemcisini kullanarak bir çağrı yapar. WCF 'nin temel alınan çatısı, Federasyon güvenliği iletişim düzeninde daha önce bahsedilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde kullanmasına olanak sağlar.  
  
## <a name="sample-implementation-using-wcf"></a>WCF kullanarak örnek uygulama  
 Aşağıdaki çizimde, WCF 'den yerel destek kullanan bir Federasyon güvenlik mimarisine yönelik örnek bir uygulama gösterilmektedir.  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Örnek hizmetim  
 Hizmet `MyService` aracılığıyla`MyServiceEndpoint`tek bir uç nokta sunar. Aşağıdaki çizimde bitiş noktasıyla ilişkili adres, bağlama ve anlaşma gösterilmektedir.  
  
 ![MyServiceEndpoint ayrıntılarının gösterildiği diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 Hizmet uç noktası `MyServiceEndpoint` [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) kullanır ve STS B tarafından verilen `accessAuthorized` talebe sahip geçerli bir güvenlik onaylama işlemi biçimlendirme dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
> İçin gereken `MyService`talepler hakkında bir hafif nokta not edilmelidir. İkinci şekil, `accessAuthorized` talebe sahip `MyService` bir SAML belirteci gerektirdiğini gösterir. Daha kesin olması için bu, gereken talep türünü `MyService` belirtir. Bu talep türünün `http://tempuri.org:accessAuthorized` tam adı, hizmet yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte). Bu talebin değeri, bu talebin varlığını gösterir ve STS B `true` tarafından ayarlandığı varsayılır.  
  
 Çalışma zamanında, bu ilke `MyServiceOperationRequirement` `MyService`öğesinin bir parçası olarak uygulanan sınıfı tarafından zorlanır.  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Aşağıdaki çizimde STS B gösterilmektedir. Daha önce belirtildiği gibi, bir güvenlik belirteci hizmeti (STS) da bir Web hizmetidir ve ilişkili uç noktaları, ilkesi vb. olabilir.  
  
 ![Güvenlik belirteci hizmeti B 'yi gösteren diyagram.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B, güvenlik belirteçleri istemek için kullanılabilecek `STSEndpoint` adlı tek bir uç nokta sunar. Özellikle STS B, servis sitesinde hizmete erişmek için `accessAuthorized` sunulabilen `MyService` , talebe sahip SAML belirteçleri verir. Ancak STS B, kullanıcıların `userAuthenticated` talebi içeren STS tarafından verilen geçerli bir SAML belirteci sunmasını gerektirir. Bu, STS yapılandırmasında bildirimli olarak belirtilir.  
  
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
> Bu `userAuthenticated` talep, STS B için gereken talep türüdür. Bu talep türünün `http://tempuri.org:userAuthenticated` tam adı, STS yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte). Bu talebin değeri, bu talebin varlığını gösterir ve STS A `true` tarafından ayarlandığı varsayılır.  
  
 Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Erişim denetimi net ise STS B, `accessAuthorized` talebe sahip bir SAML belirteci yayınlar.  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Aşağıdaki çizimde STS A gösterilmektedir.  
  
 ![Federasyon](../../../../docs/framework/wcf/feature-details/media/sts-b.gif "STS_B")  
  
 STS B 'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaçla tek bir uç nokta sunan bir Web hizmetidir. Ancak, farklı bir bağlama (`wsHttpBinding`) kullanır ve kullanıcıların bir `emailAddress` talep ile geçerli bir CardSpace sunmasını gerektirir. Yanıt ' da, `userAuthenticated` talebe sahip SAML belirteçleri verir. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
  
 Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Erişim ise `true`, STS, talebe sahip `userAuthenticated` bir SAML belirteci yayınlar.  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Kuruluşunda istemci A  
 Aşağıdaki çizimde, bir `MyService` hizmet çağrısı yapma ile ilgili adımlarla birlikte a kuruluşunda istemci gösterilmektedir. Diğer işlevsel bileşenler de ayrıca tamamlana için de eklenmiştir.  
  
 ![Bir hizmetim hizmeti çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Özet  
 Federal güvenlik, daha temiz bir sorumluluk bölmesi sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur. WCF, dağıtılmış uygulamalar oluşturmaya ve dağıtmaya yönelik bir platform olarak, Federasyon güvenliği uygulamak için yerel destek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](../../../../docs/framework/wcf/feature-details/security.md)
