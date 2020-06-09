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
ms.openlocfilehash: c31c2612b595e627b0c4c2d7fbb3a359b19ee704
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595498"
---
# <a name="federation"></a>Federasyon
Bu konuda, Federe güvenlik kavramıyla ilgili kısa bir genel bakış sunulmaktadır. Federasyon güvenlik mimarilerini dağıtmaya yönelik Windows Communication Foundation (WCF) desteğini de açıklar. Federasyonu gösteren örnek bir uygulama için bkz. [Federasyon örneği](../samples/federation-sample.md).  
  
## <a name="definition-of-federated-security"></a>Federal Güvenlik tanımı  
 Federasyon güvenliği, bir istemcinin eriştiği hizmet ile ilişkili kimlik doğrulama ve yetkilendirme yordamlarına kadar temiz ayrım sağlar. Federasyon güvenliği, farklı güven bölgelerinde birden fazla sistem, ağ ve kuruluşta işbirliği yapılmasını de mümkün.  
  
 WCF, Federasyon güvenliği kullanan dağıtılmış sistemler oluşturmak ve dağıtmak için destek sağlar.  
  
### <a name="elements-of-a-federated-security-architecture"></a>Federasyon güvenlik mimarisinin öğeleri  
 Federasyon güvenlik mimarisinin aşağıdaki tabloda açıklandığı gibi üç anahtar öğesi vardır.  
  
|Öğe|Açıklama|  
|-------------|-----------------|  
|Etki alanı/bölge|Tek bir güvenlik yönetimi veya güven birimi. Tipik bir etki alanı tek bir kuruluş içerebilir.|  
|Federasyon|Güvenine sahip bir etki alanı koleksiyonu. Güven düzeyi farklılık gösterebilir, ancak genellikle kimlik doğrulaması içerir ve neredeyse her zaman yetkilendirmeyi içerir. Tipik bir Federasyon, bir dizi kaynağa paylaşılan erişim için güven oluşturmuş bir sayıda kuruluş içerebilir.|  
|Güvenlik Belirteci Hizmeti (STS)|Güvenlik belirteçleri veren bir Web hizmeti; diğer bir deyişle, bu, güvendiğini ve güvenmesini sağlayan kanıtları temel alarak onaylamaları yapar. Bu, etki alanları arasındaki güven aracılığı temelini oluşturur.|  
  
### <a name="example-scenario"></a>Örnek Senaryo  
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
  
 Bir Federasyon güvenlik mimarisinde, kuruluşlardaki kullanıcılar B kuruluşunda Web hizmetine erişmek istiyorlarsa, bu, belirli bir hizmete erişiminin kimliğini doğrulayan ve bu hizmetin kimliğini doğrulayan B kuruluşunda bulunan STS 'den geçerli bir güvenlik belirteci sunması gerektiğini bilir.  
  
 STS B ile iletişim kurulurken, kullanıcılar STS ile ilişkili ilkeden başka bir yöneltme düzeyi alır. STS B 'nin bir güvenlik belirteci vermesini gerektiren STS A 'nın (yani, istemci güven bölgesi) geçerli bir güvenlik belirteci sunması gerekir. Bu, iki kuruluş arasında kurulan güven ilişkisinin bir sahibi olabilir ve B kuruluşunun, A kuruluşundan kullanıcılar için kimlikleri yönetmesi gerekmez. Pratikte STS B genellikle null `issuerAddress` ve içerir `issuerMetadataAddress` . Daha fazla bilgi için bkz. [nasıl yapılır: yerel veren yapılandırma](how-to-configure-a-local-issuer.md). Bu durumda, istemci STS A 'nın yerini bulmak için yerel bir ilke danışmanlar. Bu yapılandırma, *Ev bölgesi Federasyonu* olarak ADLANDıRıLıR ve STS B 'nin STS hakkındaki bilgileri saklamak zorunda olmadığından daha iyi ölçeklendirilir.  
  
 Kullanıcılar A kurumunda STS ile iletişim kurun ve normal olarak kuruluş içindeki diğer kaynaklara erişim kazanmak için kullandıkları kimlik doğrulama kimlik bilgilerini sunarak bir güvenlik belirteci elde eder. Bu Ayrıca, kullanıcıların birden çok kimlik bilgisi kümesini sürdürmek veya birden çok hizmet sitesinde aynı kimlik bilgilerini kullanmasını sağlamak zorunda konuma almayı azaltır sorununu da ortadan koyar.  
  
 Kullanıcılar STS A 'dan bir güvenlik belirteci aldıktan sonra, bu belirteci STS 'ye sunar. B. kuruluş, kullanıcıların isteklerini yetkilendirmeyi gerçekleştirmeye devam eder ve kendi güvenlik belirteçleri kümesinden kullanıcılara bir güvenlik belirteci yayınlar. Kullanıcılar daha sonra belirtecini B kuruluşunda kaynağa sunabilir ve hizmete erişebilir.  
  
## <a name="support-for-federated-security-in-wcf"></a>WCF 'de Federal güvenlik desteği  
 WCF, aracılığıyla Federal Güvenlik mimarileri dağıtmaya yönelik anahtar desteği sağlar [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) .  
  
 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Öğesi, istek-yanıt iletişim stili için temel alınan aktarım mekanizması olarak http kullanımını gerektiren güvenli, güvenilir ve birlikte çalışabilen bir bağlama sağlar. Bu, kodlama için Tel biçimi olarak metin ve xml kullanır.  
  
 [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)Bir Federasyon güvenlik senaryosunda kullanımı, aşağıdaki bölümlerde açıklandığı gibi, mantıksal olarak bağımsız iki aşamaya ayrılabilir.  
  
### <a name="phase-1-design-phase"></a>1. Aşama: Tasarım aşaması  
 Tasarım aşamasında istemci, hizmet uç noktasının açığa çıkardığı ilkeyi okumak ve hizmetin kimlik doğrulama ve yetkilendirme gereksinimlerini toplamak için [ServiceModel meta veri yardımcı programı aracını (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) kullanır. İstemci üzerinde aşağıdaki Federasyon güvenliği iletişim modelini oluşturmak için uygun proxy 'ler oluşturulur:  
  
- İstemci güven bölgesindeki STS 'den bir güvenlik belirteci alın.  
  
- Belirteci hizmet güven bölgesindeki STS 'ye sunun.  
  
- Hizmet güven bölgesindeki STS 'den bir güvenlik belirteci alın.  
  
- Hizmete erişmek için belirteci hizmete sunun.  
  
### <a name="phase-2-run-time-phase"></a>2. Aşama: çalışma zamanı aşaması  
 Çalışma zamanı aşamasında istemci, WCF istemci sınıfının bir nesnesini başlatır ve WCF istemcisini kullanarak bir çağrı yapar. WCF 'nin temel alınan çatısı, Federasyon güvenliği iletişim düzeninde daha önce bahsedilen adımları işler ve istemcinin hizmeti sorunsuz bir şekilde kullanmasına olanak sağlar.  
  
## <a name="sample-implementation-using-wcf"></a>WCF kullanarak örnek uygulama  
 Aşağıdaki çizimde, WCF 'den yerel destek kullanan bir Federasyon güvenlik mimarisine yönelik örnek bir uygulama gösterilmektedir.  
  
 ![Örnek bir Federasyon güvenlik uygulamasını gösteren diyagram.](./media/federation/federated-security-implementation.gif)  
  
### <a name="example-myservice"></a>Örnek hizmetim  
 Hizmet `MyService` aracılığıyla tek bir uç nokta sunar `MyServiceEndpoint` . Aşağıdaki çizimde bitiş noktasıyla ilişkili adres, bağlama ve anlaşma gösterilmektedir.  
  
 ![MyServiceEndpoint ayrıntılarının gösterildiği diyagram.](./media/federation/myserviceendpoint-details.gif)  
  
 Hizmet uç noktası `MyServiceEndpoint` ' nı kullanır [\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ve `accessAuthorized` STS B tarafından verilen talebe sahip geçerli bir güvenlik onaylama işlemi BIÇIMLENDIRME dili (SAML) belirteci gerektirir. Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
> İçin gereken talepler hakkında bir hafif nokta not edilmelidir `MyService` . İkinci şekil, `MyService` talebe sahip BIR SAML belirteci gerektirdiğini gösterir `accessAuthorized` . Daha kesin olması için bu, gereken talep türünü belirtir `MyService` . Bu talep türünün tam adı, `http://tempuri.org:accessAuthorized` hizmet yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte). Bu talebin değeri, bu talebin varlığını gösterir ve `true` STS B tarafından ayarlandığı varsayılır.  
  
 Çalışma zamanında, bu ilke `MyServiceOperationRequirement` öğesinin bir parçası olarak uygulanan sınıfı tarafından zorlanır `MyService` .  
  
 [!code-csharp[C_Federation#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#0)]
 [!code-vb[C_Federation#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#0)]  
[!code-csharp[C_Federation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#1)]
[!code-vb[C_Federation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#1)]  
  
#### <a name="sts-b"></a>STS B  
 Aşağıdaki çizimde STS B gösterilmektedir. Daha önce belirtildiği gibi, bir güvenlik belirteci hizmeti (STS) da bir Web hizmetidir ve ilişkili uç noktaları, ilkesi vb. olabilir.  
  
 ![Güvenlik belirteci hizmeti B 'yi gösteren diyagram.](./media/federation/myservice-security-token-service-b.gif)  
  
 STS B, `STSEndpoint` güvenlik belirteçleri istemek için kullanılabilecek adlı tek bir uç nokta sunar. Özellikle STS B, `accessAuthorized` `MyService` servis sitesinde hizmete erişmek için sunulabilen, talebe sahip SAML belirteçleri verir. Ancak STS B, kullanıcıların talebi içeren STS tarafından verilen geçerli bir SAML belirteci sunmasını gerektirir `userAuthenticated` . Bu, STS yapılandırmasında bildirimli olarak belirtilir.  
  
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
> `userAuthenticated`Bu talep, STS B için gereken talep türüdür. Bu talep türünün tam adı, `http://tempuri.org:userAuthenticated` STS yapılandırma dosyasında kullanılan (ilişkili ad alanıyla birlikte). Bu talebin değeri, bu talebin varlığını gösterir ve `true` STS A tarafından ayarlandığı varsayılır.  
  
 Çalışma zamanında, `STS_B_OperationRequirement` sınıfı STS 'nin bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#2)]
 [!code-vb[C_Federation#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#2)]  
  
 Erişim denetimi net ise STS B, talebe sahip bir SAML belirteci yayınlar `accessAuthorized` .  
  
 [!code-csharp[C_Federation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#3)]
 [!code-vb[C_Federation#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#3)]  
  
#### <a name="sts-a"></a>STS A  
 Aşağıdaki çizimde STS A gösterilmektedir.  
  
 ![Federasyon](media/sts-b.gif "STS_B")  
  
 STS B 'ye benzer şekilde, STS A da güvenlik belirteçleri veren ve bu amaçla tek bir uç nokta sunan bir Web hizmetidir. Ancak, farklı bir bağlama () kullanır `wsHttpBinding` ve kullanıcıların bir talep ile geçerli bir CardSpace sunmasını gerektirir `emailAddress` . Yanıt ' da, talebe sahip SAML belirteçleri verir `userAuthenticated` . Bu, hizmet yapılandırmasında bildirimli olarak belirtilir.  
  
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
    </endpoint>  
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
  
 Çalışma zamanında, `STS_A_OperationRequirement` sınıfı STS 'Nin bir parçası olarak uygulanan bu ilkeyi zorlar.  
  
 [!code-csharp[C_Federation#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#4)]
 [!code-vb[C_Federation#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#4)]  
  
 Erişim ise `true` , STS, talebe sahip BIR SAML belirteci yayınlar `userAuthenticated` .  
  
 [!code-csharp[C_Federation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federation/cs/source.cs#5)]
 [!code-vb[C_Federation#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federation/vb/source.vb#5)]  
  
### <a name="client-at-organization-a"></a>Kuruluşunda istemci A  
 Aşağıdaki çizimde, bir hizmet çağrısı yapma ile ilgili adımlarla birlikte A kuruluşunda istemci gösterilmektedir `MyService` . Diğer işlevsel bileşenler de ayrıca tamamlana için de eklenmiştir.  
  
 ![Bir hizmetim hizmeti çağrısındaki adımları gösteren diyagram.](./media/federation/federation-myservice-service-call-process.gif)  
  
## <a name="summary"></a>Özet  
 Federal güvenlik, daha temiz bir sorumluluk bölmesi sağlar ve güvenli, ölçeklenebilir hizmet mimarileri oluşturmaya yardımcı olur. WCF, dağıtılmış uygulamalar oluşturmaya ve dağıtmaya yönelik bir platform olarak, Federasyon güvenliği uygulamak için yerel destek sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Güvenlik](security.md)
