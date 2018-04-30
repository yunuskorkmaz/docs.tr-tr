---
title: Sertifikalarla Çalışma
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
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3c023b27ace10919c51aa13e2635040d9d5b812b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="working-with-certificates"></a>Sertifikalarla Çalışma
Programa [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] güvenlik, X.509 dijital sertifikalar genellikle istemcilerin ve sunucuların kimliğini doğrulamak için kullanılan, şifrelemek ve iletileri dijital olarak imzala. Bu konu kısaca X.509 dijital sertifika özelliklerini ve bunların içinde nasıl kullanılacağını açıklamaktadır [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ve bu kavramları daha fazla açıklamak veya kullanarak ortak görevleri gerçekleştirmek nasıl Göster konulara bağlantılar içerir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve sertifikalar.  
  
 Kısaca, bir dijital sertifika bir parçası olan bir *ortak anahtar altyapısı* (PKI) sistemi dijital sertifikalar, sertifika yetkililerini ve geçerliliğini doğrulayan ve diğer yetkililerden olduğu Ortak anahtar şifrelemesi kullanılarak bir elektronik işlemde taraf her. Bir sertifika yetkilisi sertifikaları dağıtır ve her sertifikası gibi verileri içeren alanlar kümesi *konu* (sertifikanın verildiği varlık) geçerlilik tarihleri, veren ((sertifikanın olduğunda geçerli) Sertifikayı veren varlık) ve ortak anahtar. İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu özelliklerin her biri olarak işlenir bir <xref:System.IdentityModel.Claims.Claim>, ve her talep daha iki türlerine ayrılır: kimlik ve sağa. X.509 hakkında daha fazla bilgi için bkz: sertifikalar [X.509 ortak anahtar sertifikaları](http://go.microsoft.com/fwlink/?LinkId=209952)WCF görüyor talep yetkilendirme hakkında daha fazla bilgi için [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). Bir PKI uygulama hakkında daha fazla bilgi için bkz: [Windows Server 2008 R2 - Sertifika Hizmetleri](http://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Bir birincil sertifikanın başkalarına sertifika sahibinin kimliğini doğrulamak için işlevdir. Bir sertifikayı içeren *ortak anahtar* sahibi özel anahtarı tutarken sahibinin. Ortak anahtar sertifika sahibinin gönderilen iletileri şifrelemek için kullanılabilir. Sahibi özel anahtar erişimi yalnızca sahibi bu iletilerin şifresini çözebilir yalnızca bunu.  
  
 Sertifika bir üçüncü taraf veren sertifikalarının görülür bir sertifika yetkilisi tarafından verilmelidir. Bir Windows etki alanında bir sertifika yetkilisi dahil etki alanındaki bilgisayarların sertifika vermek için kullanılabilir.  
  
## <a name="viewing-certificates"></a>Sertifikaları görüntüleme  
 Sertifikalar ile çalışmak için genellikle bunları görüntülemek ve bunların özelliklerini incelemek gereklidir. Bu, Microsoft Yönetim Konsolu (MMC) ek bileşenini aracıyla kolayca gerçekleştirilir. Daha fazla bilgi için bkz: [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Sertifika depoları  
 Sertifika deposunda bulunamadı. Daha fazla alt depoları ayrılır iki ana deposu konum yok. Bir bilgisayarda yöneticisiyseniz, MMC ek bileşen aracını kullanarak her iki ana depoları görüntüleyebilirsiniz. Yönetici olmayanlar yalnızca geçerli kullanıcı deposunda görüntüleyebilirsiniz.  
  
-   **Yerel makinenin deposunu**. Bu gibi makine işlemler tarafından erişilen sertifikaları içeren [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. Bu konumu, istemcilerin sunucuya kimlik doğrulaması sertifikalarını depolamak için kullanır.  
  
-   **Geçerli kullanıcı deposunda**. Etkileşimli uygulamalar genellikle burada bilgisayarın geçerli kullanıcı için sertifikalar yerleştirin. Bir istemci uygulaması oluşturuyorsanız, genellikle bir kullanıcı bir hizmete kimlik doğrulaması sertifikaları nereye budur.  
  
 Bu iki depoları daha fazla alt depoları ayrılır. En fazla ile programlama olduğunda önemli bu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] içerir:  
  
-   **Güvenilen kök sertifika yetkilileri**. Sertifika yetkilisi sertifikası bu deposundaki geri izlenebilir sertifika zinciri oluşturmak için bu depolama alanındaki sertifikaları kullanabilirsiniz.  
  
    > [!IMPORTANT]
    >  Sertifika bir güvenilen üçüncü taraf sertifika yetkilisi gelmez olsa bile yerel bilgisayarda bu depolama alanındaki yerleştirilen herhangi bir sertifikayı örtük olarak güvenir. Bu nedenle, tam olarak veren güven ve sonuçlar anlamak sürece herhangi bir sertifikayı bu depoya yerleştirmeyin.  
  
-   **Kişisel**. Bu depo, bir bilgisayarın bir kullanıcıyla ilişkili sertifikalar için kullanılır. Genellikle bu depo güvenilen kök sertifika yetkilileri deposunda bulunan sertifika yetkilisi sertifikalarını biri tarafından verilen sertifikalar için kullanılır. Alternatif olarak, burada bulunan bir sertifika kendi kendine verilen ve bir uygulama tarafından güvenilir.  
  
 Sertifika depoları hakkında daha fazla bilgi için bkz: [sertifika depolarını](http://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Bir mağaza seçme  
 Bir sertifikanın depolanacağı yeri seçme bağlıdır nasıl ve ne zaman hizmeti veya istemci çalıştırır. Aşağıdaki genel kurallar geçerlidir:  
  
-   WCF hizmeti bir Windows hizmeti kullanımda barındırılıyorsa **yerel makine** depolar. Yerel makine deposuna sertifika yüklemek için yönetici ayrıcalıkları gerekli olduğunu unutmayın.  
  
-   Hizmet veya istemci bir kullanıcı hesabı altında çalışan bir uygulama ise, ardından kullanın **geçerli kullanıcı** depolar.  
  
### <a name="accessing-stores"></a>Depoları erişme  
 Depoları, bir bilgisayardaki klasörleri gibi erişim denetim listeleriyle (ACL) korunur. Internet Information Services (IIS) tarafından barındırılan bir hizmet oluştururken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] işlemi çalıştırılan altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hesabı. Hesabı sertifikaları içeren deposuna erişimine sahip olmalıdır, bir hizmet kullanır. Ana mağazaların her biri bir varsayılan erişim listesiyle korunur, ancak listeler değiştirilebilir. Bir deposuna erişim için ayrı bir rolü oluşturursanız, bu rolü erişim izni vermeniz gerekir. WinHttpCertConfig.exe aracını kullanarak erişimi listesini değiştirmek öğrenmek için bkz: [nasıl yapılır: geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). İstemci sertifikaları IIS'ye kullanma hakkında daha fazla bilgi için bkz: [kimlik doğrulaması için bir ASP.NET Web uygulaması ile bir istemci sertifikasını kullanarak bir Web hizmetini çağırmak nasıl](http://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Güven zinciri ve sertifika yetkilileri  
 Sertifikalar, her bir sertifika sertifika veren CA için burada bağlı olduğu bir hiyerarşideki oluşturulur. Bu CA'ın sertifikasını bağlantıdır. CA'ın sertifika sonra CA'ın yedeği sertifika veren CA bağlantılar. Kök CA'ın sertifikasını ulaşılana kadar bu işlem yinelenir. Doğası gereği güvenilir kök CA'ın sertifika yok.  
  
 Bir varlık olarak da adlandırılan bu hiyerarşi, bağlı olan kimlik doğrulaması için kullanılan dijital sertifikalar bir *güven zinciri*. Tüm sertifika zincirinin herhangi bir sertifikayı çift sonra tıklatarak MMC ek bileşenini kullanarak görüntüleyebilirsiniz **sertifika yolu** sekmesi. Sertifika yetkilisi için sertifika zincirleri alma hakkında daha fazla bilgi için bkz: [nasıl yapılır: sertifika yetkilisi sertifika zinciri kullanılan imzaları doğrulamak için belirtmek](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Tüm veren sertifikayı güvenilir kök yetkilisi sertifika deposunda yerleştirme tarafından güvenilen bir kök yetkilisi belirlenebilir.  
  
### <a name="disabling-chain-trust"></a>Zincir güven devre dışı bırakma  
 Yeni bir hizmet oluştururken, bir güvenilen kök sertifikası tarafından verilmemiş bir sertifika kullanıyor olabilir veya sertifikayı veren sertifika güvenilen kök sertifika yetkilileri deposunda olmayabilir. Yalnızca geliştirme amacıyla bir sertifika güven zinciri denetler mekanizması geçici olarak devre dışı bırakabilirsiniz. Bunu yapmak için ayarlayın `CertificateValidationMode` ya da özellik `PeerTrust` veya `PeerOrChainTrust`. Sertifika ya da (eş güven) kendi kendine verilebilmesi için her iki modda belirtir ya da bir güven zinciri parçası. Aşağıdaki sınıflar hiçbirinde özelliğini ayarlayabilirsiniz.  
  
|örneği|Özellik|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Yapılandırmayı kullanarak özelliği de ayarlayabilirsiniz. Aşağıdaki öğeler, doğrulama modunu belirtmek için kullanılır:  
  
-   [\<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Özel kimlik doğrulama  
 `CertificateValidationMode` Özelliği de sertifikaları nasıl doğrulanır özelleştirme olanak sağlar. Varsayılan olarak, düzeyini ayarlamak `ChainTrust`. Kullanılacak <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> değeri de ayarlamanız gerekir `CustomCertificateValidatorType` özniteliği bir derleme ve sertifikayı doğrulamak için kullanılan türü. Özel Doğrulayıcı sağlayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
 Özel bir kimlik doğrulayıcı oluştururken, geçersiz kılmak için en önemli yöntemdir <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi. Özel kimlik doğrulama bir örnek için bkz: [X.509 Sertifika Doğrulayıcı](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) örnek. Daha fazla bilgi için bkz: [özel kimlik bilgisi ve kimlik bilgileri doğrulaması](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-makecertexe-to-build-a-certificate-chain"></a>Bir sertifika zinciri oluşturmak için MakeCert.exe kullanma  
 Sertifika Oluşturma Aracı'nı (Makecert.exe) X.509 sertifikaları ve özel anahtarı/ortak anahtar çifti oluşturur. Disk ve vermek ve yeni sertifikaları imzalamak için kullanmak üzere özel anahtarı böylece zincirleme sertifika hiyerarşisini benzetimi kaydedebilirsiniz. Hizmetleri ve hiçbir zaman gerçek dağıtım sertifikalarını oluşturmak için kullanılması gereken geliştirme aracı yalnızca bir yardımcı olarak kullanıma yöneliktir. Geliştirirken bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet, bir Makecert.exe ile güven zinciri oluşturmak için aşağıdaki adımları kullanın.  
  
#### <a name="to-build-a-chain-of-trust-with-makecertexe"></a>Makecert.exe ile güven zinciri oluşturmak için  
  
1.  MakeCert.exe aracını kullanarak geçici kök yetkilisi (otomatik olarak imzalanan) bir sertifika oluşturun. Özel anahtarı, diske kaydedin.  
  
2.  Yeni sertifika, ortak anahtarı içeren başka bir sertifika vermek için kullanın.  
  
3.  Kök yetkilisi sertifikası güvenilen kök sertifika yetkilileri deposuna alın.  
  
4.  Adım adım yönergeler için bkz: [nasıl yapılır: geliştirme sırasında kullanmak için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Hangi sertifikanın kullanılacak?  
 Sertifikalar hakkında sık sorulan sorular, hangi sertifikanın kullanılacağını olan ve neden. Yanıt, istemci veya hizmet programlama üzerinde bağlıdır. Aşağıdaki bilgiler genel bir kılavuz sağlar ve bu soruların kapsamlı bir çözüm değildir.  
  
### <a name="service-certificates"></a>Hizmet sertifikaları  
 Hizmet sertifikaları istemcileri için sunucu kimlik doğrulaması birincil görevi vardır. Bir istemci bir sunucu kimlik doğrulaması gerçekleştirdiğinde ilk denetimlerden biridir değerini karşılaştırmak için **konu** alan Tekdüzen Kaynak Tanımlayıcısı (URI) için kullanılan hizmetiyle iletişim kurulamadı: hem DNS eşleşmesi gerekir. Örneğin, hizmet URI'si ise "http://www.contoso.com/endpoint/" sonra **konu** alan "www.contoso.com" değeri de içermesi gerekir.  
  
 Alan çeşitli değerleri içerebilir, her değeri belirtmek için bir başlatma önekli dikkat edin. En yaygın olarak, başlatma "CN =" ortak adı, örneğin, işlemi "CN = www.contoso.com". Ayrıca mümkündür **konu** ; bu durumda, boş olması için alan **konu diğer adı** alan içerebilir **DNS adı** değeri.  
  
 Ayrıca değerini not edin **Hedeflenen amaçlar** sertifikası alanı, "Sunucu kimlik doğrulaması" veya "İstemci kimlik doğrulaması" gibi uygun bir değer içermelidir.  
  
### <a name="client-certificates"></a>İstemci sertifikaları  
 İstemci sertifikaları genellikle bir üçüncü taraf sertifika yetkilisi tarafından verilen değil. Bunun yerine, geçerli kullanıcının konuma kişisel deposunda genellikle var. bir amacı "İstemci kimlik doğrulaması" ile bir kök yetkilisi tarafından yerleştirilen sertifikaları içerir. Karşılıklı kimlik doğrulaması gerekli olduğunda, istemcinin bu tür bir sertifika kullanabilirsiniz.  
  
## <a name="online-revocation-and-offline-revocation"></a>Çevrimiçi iptal ve çevrimdışı iptal etme  
  
### <a name="certificate-validity"></a>Sertifika geçerlilik  
 Her sertifika adlı süreyi yalnızca belirli bir süre için geçerlidir *geçerlilik süresi*. Geçerlilik süresi tarafından tanımlanan **geçerlilik** ve **için geçerli** alanları, bir X.509 sertifikası. Kimlik doğrulaması sırasında sertifikası hala geçerlilik süresi içinde olup olmadığını belirlemek için sertifika denetlenir.  
  
### <a name="certificate-revocation-list"></a>Sertifika iptal listesi  
 Geçerlilik süresi sırasında herhangi bir zamanda sertifika yetkilisi, sertifika iptal edebilirsiniz. Bu sertifikanın özel anahtarı güvenliğinin gibi birçok nedenlerle ortaya çıkabilir.  
  
 Bu durumda, iptal edilen sertifika Düzen zincirleri ayrıca geçersiz ve kimlik doğrulama yordamları sırasında güvenilir değildir. Hangi sertifikaların iptal bulmak için bir saat ve tarih-damgalı her veren yayımlar *sertifika iptal listesi* (CRL). Listenin ayarlayarak çevrimiçi iptal ya da çevrimdışı iptal kullanılarak denetlenebilir `RevocationMode` veya `DefaultRevocationMode` birine aşağıdaki sınıflar özelliğinin <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> numaralandırma değerlerinin: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> ve <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfları. Tüm özellikler için varsayılan değer `Online`.  
  
 Kullanılarak yapılandırma modu da ayarlayabilirsiniz `revocationMode` her iki öznitelik [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (biri [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) ve [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (biri [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>SetCertificate yöntemi  
 İçinde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], çoğunlukla bir sertifika belirtin veya bir hizmet sertifikalarının ayarlayın veya istemcidir şifrelemek veya bir ileti dijital olarak imzala doğrulamak için kullanılacak. Program aracılığıyla kullanarak bunu yapabilirsiniz `SetCertificate` X.509 sertifikalarını temsil eden çeşitli sınıflar yöntemi. Aşağıdaki sınıflar kullanım `SetCertificate` yöntemi bir sertifika belirtin.  
  
|örneği|Yöntem|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Yöntem çalışır bir depolama konumu ve depo, bir "Bul" türü belirterek (`x509FindType` parametresi) bir alan sertifikanın ve alanındaki bulmak için bir değer belirtir. Örneğin, aşağıdaki kod oluşturur bir <xref:System.ServiceModel.ServiceHost> örneği ve istemcilerle hizmete kimlik doğrulaması için kullanılan hizmet sertifikası ayarlar `SetCertificate` yöntemi.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Aynı değere sahip birden çok sertifika  
 Bir mağaza aynı konu adına sahip birden çok sertifika içerebilir. Bunun anlamı belirtirseniz `x509FindType` olan <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> veya <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>ve birden fazla sertifika aynı değere sahip, hangi sertifika gerekiyor ayırt etmek mümkün olduğundan özel durum oluşur. Bu ayarlayarak azaltmak `x509FindType` için <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Parmak izi alan belirli bir Sertifika Mağazası'nda bulmak için kullanılan benzersiz bir değer içerir. Kendi dezavantajı değiştirilirse: sertifika iptal veya yenilenmiş, `SetCertificate` parmak izi de kaldırılmıştır olduğundan yöntem başarısız olur. Veya, sertifika artık geçerli değilse, kimlik doğrulaması başarısız olur. Bu durumu iyileştirmek için ayarlanacak yoludur `x590FindType` parametresi <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> ve verenin adı belirtin. Belirli bir veren gerekiyorsa, ayrıca diğer birini ayarlayabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> gibi numaralandırma değerleri <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Sertifikaları yapılandırma  
 Yapılandırmayı kullanarak sertifikaları de ayarlayabilirsiniz. Bir hizmet oluşturuyorsanız, kimlik, sertifikalar dahil altında belirtilen [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Bir istemci programlamada sertifikaları altında belirtilen [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Bir kullanıcı hesabına bir sertifika eşlemesi  
 Bir IIS ve Active Directory bir Windows kullanıcı hesabı için bir sertifika eşleme özelliğini özelliğidir. Özelliği hakkında daha fazla bilgi için bkz: [sertifikaları kullanıcı hesaplarına eşleme](http://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Active Directory eşlemesi kullanma hakkında daha fazla bilgi için bkz: [dizin hizmeti eşlemesi ile eşleme istemci sertifikalarının](http://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Bu özelliği etkin, ayarladığınız <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> özelliği <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfının `true`. Yapılandırmada, ayarladığınız `mapClientCertificateToWindowsAccount` özniteliği [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesine `true`aşağıdaki kodda gösterildiği gibi.  
  
```xml  
<serviceBehaviors>  
 <behavior name="MappingBehavior">  
  <serviceCredentials>  
   <clientCertificate>  
    <authentication certificateValidationMode="None" mapClientCertificateToWindowsAccount="true" />  
   </clientCertificate>  
  </serviceCredentials>  
 </behavior>  
</serviceBehaviors>  
```  
  
 Bir Windows kullanıcı hesabı temsil eden belirteci için bir X.509 sertifikası eşleme, korunan kaynaklara erişim kazanmak için eşlenen sonra Windows belirteci kullanılabilir olduğundan, bir ayrıcalık kabul edilir. Bu nedenle, etki alanı ilkesi eşleme önce kendi ilkesiyle uyumlu uymak için X.509 sertifikası gerektirir. *SChannel* güvenlik paketi bu gereksinim zorlar.  
  
 Kullanırken [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya sonraki sürümlerde, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sertifika için bir Windows hesabı eşlenen önce etki alanı ilkesi uyumlu sağlar.  
  
 İlk sürümünde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], eşleme, etki alanı ilkesi danışmanlık olmadan yapılır. Bu nedenle ilk sürüm altında çalışırken çalışmak için kullanılan eski uygulamaları eşleme etkinleştirilmişse ve X.509 sertifikası etki alanı ilkesi karşılamadığı başarısız mümkündür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
