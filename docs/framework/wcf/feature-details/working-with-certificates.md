---
title: Sertifikalarla Çalışma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: 147de1cdde79ee29f8f316399ba2e41f93921073
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44361608"
---
# <a name="working-with-certificates"></a>Sertifikalarla Çalışma
Windows Communication Foundation (WCF) güvenlik programlamak için X.509 dijital sertifikalar sık iletileri dijital olarak imzala istemcilere ve sunuculara kimlik doğrulaması ve şifreleme için kullanılır. Bu konuda kısaca X.509 dijital sertifika özellikleri ve bunların WCF'de nasıl kullanılacağını açıklar ve WCF ve sertifikaları kullanarak yaygın görevlerin nasıl yerine getirileceğini gösteren ya da, bu kavramları daha açıklayan konulara bağlantılar içerir.  
  
 Kısaca, bir dijital sertifika bir parçası olan bir *ortak anahtar altyapısı* (PKI) bir sistem dijital sertifikalar, sertifika yetkililerini ve geçerliliğini doğrulayan ve diğer yetkililerden olduğu Ortak anahtar şifrelemesi kullanarak elektronik bir işlemde katılan her iki taraf. Bir sertifika yetkilisi sertifikaları dağıtır ve her sertifika gibi verileri içeren bir alanlar kümesine sahiptir *konu* (sertifikanın verildiği varlık) geçerlilik tarihleri, veren ((sertifikanın olduğunda geçerli) Sertifikayı veren varlığı) ve ortak anahtar. WCF'de, bu özelliklerin her biri olarak işlenir bir <xref:System.IdentityModel.Claims.Claim>, ve her talep daha iki türe ayrılır: kimlik ve sağ. X.509 hakkında daha fazla bilgi için bkz: sertifikaları [X.509 ortak anahtar sertifikaları](https://go.microsoft.com/fwlink/?LinkId=209952). Beyanlar ve yetkilendirmeyi WCF hakkında daha fazla bilgi için bkz. [yönetme beyanlar ve yetkilendirmeyi kimlik modeliyle](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md). Bir PKI uygulama hakkında daha fazla bilgi için bkz. [Windows Server 2008 R2 - Sertifika Hizmetleri](https://go.microsoft.com/fwlink/?LinkId=209949).  
  
 Diğer sertifika sahibinin kimliğini doğrulamak için bir sertifika birincil işlevi olduğu. Bir sertifika içerir *ortak anahtar* sahibi özel anahtarı tutarken sahip. Ortak anahtar sertifika sahibine gönderilen iletileri şifrelemek için kullanılabilir. Özel anahtarına erişime sahip yalnızca bunu yalnızca sahibi bu iletilerin şifresini çözebilir.  
  
 Sertifikaları çoğunlukla sertifika bir üçüncü taraf veren olduğu bir sertifika yetkilisi tarafından verilmiş olması gerekir. Bir Windows etki alanında sertifika yetkilisi dahildir etki alanındaki bilgisayar sertifikaları için kullanılabilir.  
  
## <a name="viewing-certificates"></a>Sertifikaları görüntüleme  
 Sertifikalar ile çalışmak için genellikle bunları görüntülemek ve bunların özelliklerini incelemek gereklidir. Bu, Microsoft Yönetim Konsolu (MMC) ek bileşenini aracıyla kolayca gerçekleştirilir. Daha fazla bilgi için [nasıl yapılır: MMC ek bileşeni ile sertifikaları görüntüleme](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="certificate-stores"></a>Sertifika depoları  
 Sertifika deposunda bulunamadı. Daha fazla alt depolarına bölünür iki ana depo konum yok. Bilgisayarda yöneticiyseniz MMC ek bileşenini aracını kullanarak her iki ana depoları görüntüleyebilirsiniz. Yönetici olmayan kullanıcılar, yalnızca geçerli kullanıcı deposu görüntüleyebilirsiniz.  
  
-   **Yerel makine deposuna**. Bu gibi makine işlemler tarafından erişilen sertifikaları içeren [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)]. İstemcilerin sunucuya kimlik doğrulaması sertifikalarını depolamak için bu konumu kullanır.  
  
-   **Geçerli kullanıcı deposu**. Etkileşimli uygulamalar genellikle bilgisayarın geçerli kullanıcı için sertifikalar buraya yerleştirin. Bir istemci uygulaması oluşturuyorsanız, genellikle bir kullanıcı bir hizmete kimlik doğrulaması sertifikaları yerleştirdiğiniz budur.  
  
 Bu iki depoları daha fazla alt depolarına bölünür. Bunların en önemlisi, WCF ile programlama içerir:  
  
-   **Güvenilen kök sertifika yetkilileri**. Bu depodaki bir sertifika yetkilisi sertifikasına geri izlenebilir sertifikalarını da zinciri oluşturmak için bu depoda sertifikaları kullanabilirsiniz.  
  
    > [!IMPORTANT]
    >  Bile güvenilir bir üçüncü taraf sertifika yetkilisinden sertifika gelmez yerel bilgisayar, örtük olarak bu depoda yer herhangi bir sertifika güvenir. Bu nedenle, tam olarak veren kişiye güvendiğiniz ve sonuçları anladığınızdan sürece herhangi bir sertifika bu deposuna yerleştirmeyin.  
  
-   **Kişisel**. Bu depo, bir bilgisayarın bir kullanıcıyla ilişkili sertifikaları için kullanılır. Genellikle bu depo, sertifika yetkilisi sertifikaları Güvenilen kök sertifika yetkilileri deposunda bulunan biri tarafından verilen sertifikaların kullanılır. Alternatif olarak, burada bulunan bir sertifika kendi kendine verilmesi ve bir uygulama tarafından güvenilen.  
  
 Sertifika depoları hakkında daha fazla bilgi için bkz. [sertifika depolarını](https://go.microsoft.com/fwlink/?LinkId=88912).  
  
### <a name="selecting-a-store"></a>Bir Store seçme  
 Bir sertifikanın depolanacağı yeri seçilmesi bağlıdır nasıl ve ne zaman hizmet veya istemcinin çalıştırır. Aşağıdaki genel kurallar geçerlidir:  
  
-   WCF hizmeti bir Windows hizmeti kullanımda barındırılıyorsa **yerel makine** depolayın. Yerel makine deposuna sertifika yüklemek için yönetici ayrıcalıkları gerekli olduğunu unutmayın.  
  
-   Hizmet veya istemcinin bir kullanıcı hesabı altında çalışan bir uygulama ise, ardından kullanın **geçerli kullanıcının** depolayın.  
  
### <a name="accessing-stores"></a>Depoları erişme  
 Depoları, bir bilgisayardaki klasörler gibi erişim denetim listeleri (ACL'ler) korunur. Internet Information Services (IIS) tarafından barındırılan hizmet oluşturulurken [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] işlemini çalıştıran altında [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] hesabı. Hesabı sertifikaları içeren depoya erişimine sahip olmalıdır, bir hizmeti kullanır. Ana mağazaların her biri varsayılan erişim listesi ile korunuyor, ancak liste değiştirilebilir. Bir mağazaya erişmek için ayrı bir rol oluşturursanız, bu rolü erişim izni vermeniz gerekir. WinHttpCertConfig.exe aracını kullanarak erişimi listesini değiştirme konusunda bilgi almak için bkz: [nasıl yapılır: kullanım sırasında geliştirme için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md). IIS ile istemci sertifikaları kullanma hakkında daha fazla bilgi için bkz. [nasıl bir ASP.NET Web uygulaması kimlik doğrulaması için bir istemci sertifikasını kullanarak bir Web hizmeti çağırmak amacıyla](https://go.microsoft.com/fwlink/?LinkId=88914).  
  
## <a name="chain-trust-and-certificate-authorities"></a>Güven zinciri ve sertifika yetkilileri  
 Sertifikalar, bir hiyerarşideki her bir sertifika sertifikayı veren CA'ya burada bağlı oluşturulur. Bu CA'ın sertifikasını bağlantıdır. CA'ın ardından bağlantıları özgün CA'ın sertifika veren CA sertifikası. Kök CA sertifikasını ulaşılana kadar bu işlem tekrarlanır. Kök CA sertifikasını kendiliğinden güveniliyor.  
  
 Varlık olarak da adlandırılan bu hiyerarşide bağlı olarak kimlik doğrulaması için kullanılan dijital sertifikalar bir *güven zinciri*. Tüm sertifika zincirinin herhangi bir sertifikayı çift tıklayıp tıklayarak MMC ek bileşenini kullanarak görüntüleyebileceğiniz **sertifika yolu** sekmesi. Sertifika yetkilisi için sertifika zincirleri içeri aktarma hakkında daha fazla bilgi için bkz. [nasıl yapılır: sertifika yetkilisi sertifika zinciri kullanılan imzaları doğrulamak için belirtin](../../../../docs/framework/wcf/feature-details/specify-the-certificate-authority-chain-verify-signatures-wcf.md).  
  
> [!NOTE]
>  Verenin sertifika güvenilir kök yetkilisi sertifika deposuna yerleştirerek veren herhangi bir güvenilir kök yetkilisi belirlenebilir.  
  
### <a name="disabling-chain-trust"></a>Güven zinciri devre dışı bırakma  
 Yeni bir hizmet oluştururken, bir güvenilen kök sertifika tarafından verilmemiş bir sertifika kullanıyor olabilir veya sertifikayı veren sertifika güvenilen kök sertifika yetkilileri deposunda olmayabilir. Yalnızca geliştirme amacıyla bir sertifika güven zinciri denetleyen mekanizmayı geçici olarak devre dışı bırakabilirsiniz. Bunu yapmak için ayarlanmış `CertificateValidationMode` ya da özellik `PeerTrust` veya `PeerOrChainTrust`. Sertifika ya da (eş güven) Self verilebilir, her iki modda belirtir ya da bir güven zinciri parçası. Aşağıdaki sınıflar hiçbirini özelliği ayarlayabilirsiniz.  
  
|örneği|Özellik|  
|-----------|--------------|  
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|  
  
 Ayrıca, yapılandırma özelliğini ayarlayabilirsiniz. Aşağıdaki öğeler, doğrulama modunu belirtmek için kullanılır:  
  
-   [\<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)  
  
-   [\<peerAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)  
  
-   [\<messageSenderAuthentication >](../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)  
  
## <a name="custom-authentication"></a>Özel kimlik doğrulama  
 `CertificateValidationMode` Özelliği de sertifika kimlik doğrulaması nasıl yapılır özelleştirme olanak sağlar. Varsayılan olarak, düzeyi `ChainTrust`. Kullanılacak <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> değeri ayarlamanız gerekir `CustomCertificateValidatorType` öznitelik bir bütünleştirilmiş kod ve sertifikayı doğrulamak için kullanılan tür. Özel Doğrulayıcı sağlayıcısı oluşturmak için Özet devralmalıdır <xref:System.IdentityModel.Selectors.X509CertificateValidator> sınıfı.  
  
 Özel bir kimlik doğrulayıcı oluştururken, geçersiz kılmak için en önemli yöntemdir <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemi. Özel kimlik doğrulama örneği için bkz: [X.509 Sertifika Doğrulayıcı](../../../../docs/framework/wcf/samples/x-509-certificate-validator.md) örnek. Daha fazla bilgi için [özel kimlik bilgileri ve kimlik bilgisi doğrulaması](../../../../docs/framework/wcf/extending/custom-credential-and-credential-validation.md).  
  
## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Bir sertifika zinciri oluşturmak için yeni Powershell-SelfSignedCertificate cmdlet'ini kullanarak  
 New-SelfSignedCertificate Powershell cmdlet'i, X.509 sertifikaları ve özel anahtarı/genel anahtar çifti oluşturur. Disk ve vermek ve yeni sertifikaları imzalamak için kullanmak üzere özel anahtarı böylece Zincirli sertifikalar hiyerarşisini benzetimi kaydedebilirsiniz. Geliştirme Hizmetleri ve gerçek dağıtımı için sertifikaları oluşturmak için asla kullanılmamalıdır cmdlet'i yalnızca yardımcı olarak kullanıma yöneliktir. Bir WCF Hizmeti geliştirirken, bir New-SelfSignedCertificate cmdlet'i ile bir güven zinciri oluşturmak için aşağıdaki adımları kullanın.  
  
#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>New-SelfSignedCertificate cmdlet'i ile bir güven zinciri oluşturmak için  
  
1.  New-SelfSignedCertificate cmdlet'ini kullanarak bir geçici kök yetkilisi (otomatik olarak imzalanan) bir sertifika oluşturun. Özel anahtarı, diske kaydedin.  
  
2.  Yeni sertifikanın ortak anahtarı içeren başka bir sertifika kullanın.  
  
3.  Kök yetkilisi sertifikası güvenilen kök sertifika yetkilileri deposuna aktarın.  
  
4.  Adım adım yönergeler için bkz: [nasıl yapılır: kullanım sırasında geliştirme için geçici sertifikalar oluşturma](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
## <a name="which-certificate-to-use"></a>Hangi sertifikanın kullanılacağını?  
 Sertifikaları hakkında sık sorulan sorular, hangi sertifikanın kullanılacağını, olan ve neden. Yanıt, istemci veya hizmet programlama üzerinde bağlıdır. Aşağıdaki bilgileri, genel bir kılavuz sağlar ve bu soruların kapsamlı bir çözüm değildir.  
  
### <a name="service-certificates"></a>Hizmet sertifikaları  
 Hizmet sertifikalarını istemcilere sunucu kimliği birincil görevi vardır. Bir sunucuya bir istemci kimlik doğrulamasını gerçekleştirdiğinde ilk denetimler biri değerini karşılaştırmak için **konu** alanı Tekdüzen Kaynak Tanımlayıcısı (URI) için kullanılan hizmetiyle iletişim kurma: her iki DNS eşleşmelidir. Örneğin, hizmet URI'si ise `http://www.contoso.com/endpoint/` sonra **konu** alan değeri de içermelidir `www.contoso.com`.  
  
 Alan birden fazla değer içerebilir, her değeri belirtmek için bir başlatma ile önek dikkat edin. En yaygın olarak, "CN =" ortak adı, örneğin, bir başlatmadır `CN = www.contoso.com`. De mümkündür **konu** durumda boş olacak şekilde alan **konu alternatif adı** alanı içerebilir **DNS adı** değeri.  
  
 Ayrıca değerini not edin **Hedeflenen amaçlar** sertifikasının alanı, "Sunucu kimlik doğrulaması" veya "İstemci kimlik doğrulaması" gibi uygun bir değer içermelidir.  
  
### <a name="client-certificates"></a>İstemci sertifikaları  
 İstemci sertifikaları genellikle bir üçüncü taraf sertifika yetkilisi tarafından verilen değil. Bunun yerine, geçerli kullanıcının konuma alanı kişisel mağazasında genellikle var. bir amacı "İstemci kimlik doğrulaması" ile bir kök yetkilisi tarafından yerleştirilen sertifikaları içerir. Karşılıklı kimlik doğrulaması gerekli olduğunda, istemcinin bu tür bir sertifika kullanabilirsiniz.  
  
## <a name="online-revocation-and-offline-revocation"></a>İptal çevrimiçi ve çevrimdışı iptal etme  
  
### <a name="certificate-validity"></a>Sertifika geçerlilik  
 Her sertifikanın zaman çağrılır, yalnızca belirli bir süre için geçerli olduğundan *geçerlilik süresi*. Geçerlilik süresi tarafından tanımlanan **geçerlilik** ve **geçerlilik sonu** alanlarının bir X.509 sertifikası. Sertifika geçerlilik süresi hala olup olmadığını belirlemek için sertifika kimlik doğrulaması sırasında denetlenir.  
  
### <a name="certificate-revocation-list"></a>Sertifika iptal listesi  
 Geçerlilik süresi boyunca herhangi bir zamanda bir sertifika yetkiliyi iptal edebilirsiniz. Bu sertifikanın özel anahtarı'nın güvenliğinin gibi birçok nedenden dolayı ortaya çıkabilir.  
  
 Böyle bir durumda, iptal edilen sertifika Düzen herhangi zincirleri ayrıca geçersizdir ve kimlik doğrulama yordamları sırasında güvenilir değildir. Hangi sertifikaların iptal bulmak için bir saat ve tarih-damgalı her veren yayımlar *sertifika iptal listesi* (CRL). Listenin ayarlayarak çevrimiçi iptal ya da çevrimdışı iptal kullanarak denetlenebilir `RevocationMode` veya `DefaultRevocationMode` özelliği aşağıdaki sınıflarının biri olarak <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> numaralandırma değerlerinin: <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>, <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>, <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> ve <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfları. Tüm özellikler için varsayılan değer `Online`.  
  
 Kullanılarak yapılandırma modunu ayarlayabilirsiniz `revocationMode` her iki öznitelik [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (biri [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)) ve [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (biri [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)).  
  
## <a name="the-setcertificate-method"></a>SetCertificate yöntemi  
 Wcf'de, genellikle bir sertifika belirtin veya bir hizmet sertifikalarının ayarlayın veya istemci kimlik doğrulaması, şifreleme veya imzalamak için kullanmaktır. Program aracılığıyla kullanarak bunu yapabilirsiniz `SetCertificate` X.509 sertifikaları temsil eden çeşitli sınıf yöntemi. Aşağıdaki sınıflar kullanım `SetCertificate` bir sertifika belirtmek için yöntemi.  
  
|örneği|Yöntem|  
|-----------|------------|  
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|  
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|  
  
 `SetCertificate` Yöntem çalışır bir depolama konumu ve depolama, bir "Bul" türü atayarak (`x509FindType` parametresi) sertifika alanını bulmak için bir değer ve bir alan belirtir. Örneğin, aşağıdaki kod oluşturur bir <xref:System.ServiceModel.ServiceHost> örneği ve hizmet sertifikası ile istemcilere hizmet kimliğini doğrulamak için kullanılan ayarlar `SetCertificate` yöntemi.  
  
 [!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
 [!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]  
  
### <a name="multiple-certificates-with-the-same-value"></a>Aynı değere sahip birden çok sertifika  
 Bir depolama aynı konu adına sahip birden çok sertifika içeriyor olabilir. Bunun anlamı, belirtirseniz `x509FindType` olduğu <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> veya <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName>ve birden fazla sertifika aynı değere sahip, hangi sertifikanın gereklidir ayırt etmek için hiçbir yolu olmadığından bir özel durum oluşturulur. Bu ayarlayarak azaltabilirsiniz `x509FindType` için <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>. Parmak izi alan belirli bir Sertifika Mağazası'nda bulmak için kullanılan benzersiz bir değer içerir. Ancak, bunun kendi dezavantajı vardır: sertifika iptal edilmiş ya da yenilenmesi, `SetCertificate` yöntem, parmak izini de gitmiş olduğundan başarısız. Veya sertifika artık geçerli değilse, kimlik doğrulaması başarısız olur. Bunu azaltmak için ayarlanacak yoludur `x590FindType` parametresi <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> verenin adını belirtin. Hiçbir belirli veren gerekiyorsa, ayrıca diğer birini ayarlayabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> gibi sabit listesi değerleri <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid>.  
  
## <a name="certificates-in-configuration"></a>Sertifikaları yapılandırma  
 Sertifikaları yapılandırmayı kullanarak da ayarlayabilirsiniz. Bir hizmeti oluşturuyorsanız, kimlik, sertifikalar dahil altında belirtilir [ \<serviceBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md). Bir istemci programlama yaparken sertifikalar altında belirtilir [ \<endpointBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md).  
  
## <a name="mapping-a-certificate-to-a-user-account"></a>Bir kullanıcı hesabına bir sertifika eşlemesi  
 IIS ve Active Directory bir Windows kullanıcı hesabına bir sertifika eşleme özelliğini özelliğidir. Bu özellik hakkında daha fazla bilgi için bkz. [sertifikaları kullanıcı hesaplarına harita](https://go.microsoft.com/fwlink/?LinkId=88917).  
  
 Active Directory eşlemesi kullanma hakkında daha fazla bilgi için bkz. [dizin hizmeti eşlemesi ile eşleme istemci sertifikaları](https://go.microsoft.com/fwlink/?LinkId=88918).  
  
 Bu özellik sayesinde etkin ayarlayabilirsiniz <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> özelliği <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfının `true`. Yapılandırması'nda ayarlayabileceğiniz `mapClientCertificateToWindowsAccount` özniteliği [ \<kimlik doğrulama >](../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesine `true`aşağıdaki kodda gösterildiği gibi.  
  
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
  
 Korunan kaynaklara erişim elde etmek için eşlenmiş sonra Windows belirteci kullanılabilir olduğundan, bir Windows kullanıcı hesabı temsil eden bir belirteci için bir X.509 sertifikası eşleme ayrıcalık kabul edilir. Bu nedenle, etki alanı ilkesi eşleme önce kendi ilkesine uyması için X.509 sertifikası gerektirir. *SChannel* güvenlik paketi, bu gereksinim zorlar.  
  
 Kullanırken [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] veya daha sonra sertifikayı uygun etki alanı ilkesi için bir Windows hesabı eşlenmeden önce WCF sağlar.  
  
 WCF ilk sürümde, etki alanı ilkesi danışmadan eşleme gerçekleştirilir. Bu nedenle ilk sürüm altında çalışırken çalışmak için kullanılan eski uygulamaları eşleme etkinleştirilmişse ve X.509 Sertifika, etki alanı ilkesini karşılamadığı başarısız mümkündür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels>  
 <xref:System.ServiceModel.Security>  
 <xref:System.ServiceModel>  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType>  
 [Hizmet ve İstemcileri Güvenli Hale Getirme](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
