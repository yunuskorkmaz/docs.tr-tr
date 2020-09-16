---
title: Sertifikalarla Çalışma
description: X. 509.952 dijital sertifika özellikleri ve bunların WCF 'de nasıl kullanılacağı hakkında bilgi edinin. Bu makaledeki kaynaklar, bu kavramları daha ayrıntılı bir şekilde açıklayabilir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates [WCF]
ms.assetid: 6ffb8682-8f07-4a45-afbb-8d2487e9dbc3
ms.openlocfilehash: a12e723c763cdc3b9cf2105df9d0ee601f8bda1a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90559024"
---
# <a name="working-with-certificates"></a>Sertifikalarla Çalışma

Program Windows Communication Foundation (WCF) güvenliği, X. 509.440 dijital sertifikalar genellikle istemcilerin ve sunucuların kimliğini doğrulamak, iletileri şifrelemek ve dijital olarak imzalamak için kullanılır. Bu konu, X. 509.952 dijital sertifika özelliklerini ve WCF 'de nasıl kullanılacağını kısaca açıklar ve bu kavramları açıklayan konuların bağlantılarını ve WCF ve sertifikaları kullanarak genel görevlerin nasıl gerçekleştirileceğini gösterir.

Kısaca dijital sertifika, bir *genel anahtar altyapısının* (PKI) bir parçasıdır. Bu, bir dijital sertifikalar, sertifika yetkilileri ve genel anahtar şifrelemesi kullanılarak elektronik bir işlemde yer alan her bir tarafın geçerliliğini doğrulayan ve doğrulayan diğer kayıt yetkililerinden oluşur. Sertifika yetkilisi sertifikaları ve her sertifika, *Konu* (sertifikanın verildiği varlık), geçerlilik tarihleri (sertifika geçerli olduğunda), veren (sertifikayı veren varlık) ve ortak anahtar gibi verileri içeren alanlar kümesine sahiptir. WCF 'de, bu özelliklerin her biri bir olarak işlenir <xref:System.IdentityModel.Claims.Claim> ve her talep iki türe ayrılır: kimlik ve sağ. X. 509.440 sertifikaları hakkında daha fazla bilgi için bkz. [x. 509.440 ortak anahtar sertifikaları](/windows/desktop/SecCertEnroll/about-x-509-public-key-certificates). WCF 'de talepler ve yetkilendirme hakkında daha fazla bilgi için bkz. [kimlik modeliyle talepleri ve Yetkilendirmeyi Yönetme](managing-claims-and-authorization-with-the-identity-model.md). PKI uygulama hakkında daha fazla bilgi için bkz. [Windows Server 2012 R2 Ile kurumsal pkı Active Directory Sertifika Hizmetleri](/archive/blogs/yungchou/enterprise-pki-with-windows-server-2012-r2-active-directory-certificate-services-part-1-of-2).

Bir sertifikanın birincil işlevi, sertifika sahibinin kimliğini başkalarına doğrulamasıdır. Bir sertifika, sahibin *ortak anahtarını* içerir, ancak sahibi özel anahtarı korur. Ortak anahtar, sertifikanın sahibine gönderilen iletileri şifrelemek için kullanılabilir. Yalnızca sahibi özel anahtara erişebilir, bu nedenle yalnızca sahip bu iletilerin şifresini çözebilir.

Sertifikalar, genellikle bir üçüncü taraf sertifika veren olan bir sertifika yetkilisi tarafından verilmelidir. Bir Windows etki alanında, etki alanındaki bilgisayarlara sertifika vermek için kullanılabilecek bir sertifika yetkilisi bulunur.

## <a name="viewing-certificates"></a>Sertifikaları görüntüleme

Sertifikalarla çalışmak için genellikle bunları görüntülemeniz ve özelliklerini incelemesi gerekir. Bu, Microsoft Yönetim Konsolu (MMC) ek bileşeni aracıyla kolayca yapılır. Daha fazla bilgi için bkz. [nasıl yapılır: MMC ek bileşeni Ile sertifikaları görüntüleme](how-to-view-certificates-with-the-mmc-snap-in.md).

## <a name="certificate-stores"></a>Sertifika depoları

Sertifikalar mağazalarda bulunur. Alt depolara daha fazla bölündüğü iki ana depo konumu vardır. Bir bilgisayarda yöneticisiyseniz, her iki ana deposu da MMC ek bileşeni aracını kullanarak görüntüleyebilirsiniz. Yönetici olmayanlar yalnızca geçerli kullanıcı deposunu görüntüleyebilir.

- **Yerel makine deposu**. Bu, ASP.NET gibi makine işlemlerinin eriştiği sertifikaları içerir. Sunucu kimlik doğrulaması yapan sertifikaları istemcilere depolamak için bu konumu kullanın.

- **Geçerli kullanıcı deposu**. Etkileşimli uygulamalar, genellikle bilgisayarın geçerli kullanıcısı için sertifikaları buraya yerleştirir. Bir istemci uygulaması oluşturuyorsanız, bu, genellikle bir kullanıcının kimliğini doğrulamak için sertifikalar yerleştirdiğiniz yerdir.

Bu iki depo daha fazla alt depolarına bölünmüştür. WCF ile programlama yaparken bunların en önemlileri şunlardır:

- **Güvenilen kök sertifika yetkilileri**. Bu depodaki sertifikaları, bu depodaki bir sertifika yetkilisi sertifikasına geri izleyebileceğiniz bir sertifika zinciri oluşturmak için kullanabilirsiniz.

  > [!IMPORTANT]
  > Sertifika, güvenilen bir üçüncü taraf sertifika yetkilisinden gelmese de, yerel bilgisayar bu depoya yerleştirilmiş herhangi bir sertifikaya dolaylı olarak güvenir. Bu nedenle, verenle tam olarak güvenmediğiniz ve sonuçları anlamadığınız müddetçe bu depoya herhangi bir sertifika yerleştirmeyin.

- **Kişisel**. Bu depo, bir bilgisayarın kullanıcısı ile ilişkili sertifikalar için kullanılır. Genellikle bu mağaza, güvenilen kök sertifika yetkilileri deposunda bulunan sertifika yetkilisi sertifikalarından biri tarafından verilen sertifikalar için kullanılır. Alternatif olarak, burada bulunan bir sertifika bir uygulama tarafından kendine verilmiş ve güvenilir olabilir.

Sertifika depoları hakkında daha fazla bilgi için bkz. [sertifika depoları](/windows/desktop/secauthn/certificate-stores).

### <a name="selecting-a-store"></a>Mağaza seçme

Bir sertifikanın depolanacağı yeri seçme, hizmet veya istemcinin nasıl ve ne zaman çalıştığını bağlıdır. Aşağıdaki genel kurallar geçerlidir:

- WCF hizmeti bir Windows hizmetinde barındırılıyorsa **yerel makine** deposunu kullanın. Sertifikaları yerel makine deposuna yüklemek için yönetici ayrıcalıklarının gerekli olduğunu unutmayın.

- Hizmet veya istemci, bir kullanıcı hesabı altında çalışan bir uygulama ise, **Geçerli Kullanıcı** deposunu kullanın.

### <a name="accessing-stores"></a>Mağazalara erişme

Depolar, tıpkı bir bilgisayardaki klasörler gibi erişim denetim listeleriyle (ACL 'Ler) korunur. Internet Information Services (IIS) tarafından barındırılan bir hizmet oluştururken ASP.NET işlemi ASP.NET hesabı altında çalışır. Bu hesabın, bir hizmetin kullandığı sertifikaları içeren mağazaya erişimi olmalıdır. Ana mağazaların her biri varsayılan bir erişim listesiyle korunur, ancak listeler değiştirilebilir. Bir depoya erişmek için ayrı bir rol oluşturursanız, bu rol erişim iznini vermeniz gerekir. WinHttpCertConfig.exe aracını kullanarak erişim listesini değiştirme hakkında bilgi edinmek için bkz. [nasıl yapılır: geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="chain-trust-and-certificate-authorities"></a>Zincir güveni ve sertifika yetkilileri

Sertifikalar, her ayrı sertifikanın sertifikayı veren CA 'ya bağlandığı bir hiyerarşide oluşturulur. Bu bağlantı, CA 'nın sertifikasına ait olur. CA 'nın sertifikası, özgün CA 'nın sertifikasını veren CA 'ya bağlanır. Bu işlem, kök CA sertifikasına ulaşılana kadar yinelenir. Kök CA 'nın sertifikası, doğal olarak güvenilirdir.

Dijital sertifikalar, *güven zinciri*olarak da adlandırılan bu hiyerarşiye bağlı olarak bir varlığın kimliğini doğrulamak için kullanılır. Herhangi bir sertifikaya çift tıklayarak ve ardından **sertifika yolu** sekmesine TıKLAYARAK, MMC ek bileşenini kullanarak herhangi bir sertifikanın zincirini görüntüleyebilirsiniz. Bir sertifika yetkilisi için sertifika zincirlerini alma hakkında daha fazla bilgi için bkz. [nasıl yapılır: Imzaları doğrulamak Için kullanılan sertifika yetkilisi sertifika zincirini belirtme](specify-the-certificate-authority-chain-verify-signatures-wcf.md).

> [!NOTE]
> Herhangi bir veren, verenin sertifikasını Güvenilen kök yetkili sertifika deposuna yerleştirerek güvenilen bir kök yetkilisi belirlenebilir.

### <a name="disabling-chain-trust"></a>Zincir güvenini devre dışı bırakma

Yeni bir hizmet oluştururken, güvenilen kök sertifika tarafından verilmemiş bir sertifika kullanıyor olabilirsiniz veya veren sertifika, güvenilen kök sertifika yetkilileri deposunda bulunmayabilir. Yalnızca geliştirme amacıyla, bir sertifika için güven zincirini denetleyen mekanizmayı geçici olarak devre dışı bırakabilirsiniz. Bunu yapmak için, özelliğini ya `CertificateValidationMode` da olarak ayarlayın `PeerTrust` `PeerOrChainTrust` . Her iki mod da, sertifikanın kendi kendine yayınlanan (eş güven) veya bir güven zincirinin parçası olduğunu belirtir. Özelliğini aşağıdaki sınıfların herhangi birinde ayarlayabilirsiniz.

|Sınıf|Özellik|
|-----------|--------------|
|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>|<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>|<xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication.CertificateValidationMode%2A?displayProperty=nameWithType>|
|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential>|<xref:System.ServiceModel.Security.IssuedTokenServiceCredential.CertificateValidationMode%2A?displayProperty=nameWithType>|

Özelliği yapılandırma kullanarak da ayarlayabilirsiniz. Doğrulama modunu belirtmek için aşağıdaki öğeler kullanılır:

- [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)

- [\<peerAuthentication>](../../configure-apps/file-schema/wcf/peerauthentication-element.md)

- [\<messageSenderAuthentication>](../../configure-apps/file-schema/wcf/messagesenderauthentication-element.md)

## <a name="custom-authentication"></a>Özel kimlik doğrulaması

`CertificateValidationMode`Özelliği, sertifikaların nasıl doğrulandığını özelleştirmenize de olanak sağlar. Varsayılan olarak, düzeyi olarak ayarlanır `ChainTrust` . Değerini kullanmak için <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom> , `CustomCertificateValidatorType` bir derlemeyi ve sertifikayı doğrulamak için kullanılan türünü de özniteliğini ayarlamanız gerekir. Özel Doğrulayıcı oluşturmak için soyut sınıftan devralması gerekir <xref:System.IdentityModel.Selectors.X509CertificateValidator> .

Özel bir Authenticator oluştururken, geçersiz kılmak için en önemli Yöntem <xref:System.IdentityModel.Selectors.X509CertificateValidator.Validate%2A> yöntemidir. Özel kimlik doğrulama örneği için bkz. [X. 509.440 sertifika Doğrulayıcısı](../samples/x-509-certificate-validator.md) örneği. Daha fazla bilgi için bkz. [özel kimlik bilgileri ve kimlik bilgisi doğrulaması](../extending/custom-credential-and-credential-validation.md).

## <a name="using-the-powershell-new-selfsignedcertificate-cmdlet-to-build-a-certificate-chain"></a>Bir sertifika zinciri oluşturmak için PowerShell New-SelfSignedCertificate cmdlet 'Ini kullanma

PowerShell New-SelfSignedCertificate cmdlet 'i X. 509.952 sertifikaları ve özel anahtar/ortak anahtar çiftleri oluşturur. Özel anahtarı diske kaydedebilir ve ardından yeni sertifikalar vermek ve imzalamak için kullanabilir ve böylece zincirleme sertifikaların bir hiyerarşisinin benzetimini yapabilirsiniz. Cmdlet 'i, yalnızca hizmet geliştirirken bir yardım olarak kullanılmak üzere tasarlanmıştır ve gerçek dağıtıma yönelik sertifikalar oluşturmak için asla kullanılmamalıdır. Bir WCF hizmeti geliştirirken, New-SelfSignedCertificate cmdlet 'i ile bir güven zinciri oluşturmak için aşağıdaki adımları kullanın.

#### <a name="to-build-a-chain-of-trust-with-the-new-selfsignedcertificate-cmdlet"></a>New-SelfSignedCertificate cmdlet 'i ile bir güven zinciri oluşturmak için

1. New-SelfSignedCertificate cmdlet 'ini kullanarak geçici bir kök yetkilisi (otomatik imzalı) sertifikası oluşturun. Özel anahtarı diske kaydedin.

2. Ortak anahtarı içeren başka bir sertifika vermek için yeni sertifikayı kullanın.

3. Kök yetkilisi sertifikasını Güvenilen kök sertifika yetkilileri deposuna aktarın.

4. Adım adım yönergeler için bkz. [nasıl yapılır: geliştirme sırasında kullanılmak üzere geçici sertifikalar oluşturma](how-to-create-temporary-certificates-for-use-during-development.md).

## <a name="which-certificate-to-use"></a>Hangi sertifikayı kullanacak?

Sertifikalar hakkında sık sorulan sorular, hangi sertifikanın kullanılacağı ve neden. Yanıt, bir istemciyi veya hizmeti programlayıp programlamanıza bağlı olarak değişir. Aşağıdaki bilgiler genel bir kılavuz sağlar ve bu sorulara kapsamlı bir yanıt değildir.

### <a name="service-certificates"></a>Hizmet sertifikaları

Hizmet sertifikalarında, istemcilerin istemci kimliğini doğrulama birincil görevi vardır. İlk denetimlerden biri, bir istemcinin sunucu kimliğini doğruladığında, **Konu** alanının değerini hizmetle iletişim kurmak Için kullanılan Tekdüzen Kaynak tanımlayıcısı (URI) ile karşılaştırmaktır: her IKISININ de DNS eşleşmesi gerekir. Örneğin, hizmetin URI 'SI `http://www.contoso.com/endpoint/` daha sonra **Konu** alanının da değeri içermesi gerekir `www.contoso.com` .

Alanın, her biri değeri belirtmek için bir başlatma ile birlikte birden çok değer içerebileceğini unutmayın. En yaygın olarak, başlatma, örneğin, ortak ad için "CN" dir `CN = www.contoso.com` . **Konu** alanının boş olması da mümkündür, bu durumda **konu alternatif adı** alanı **DNS ad** değerini içerebilir.

Ayrıca, sertifikanın **amaçlanan amaçlar** alanının değeri, "sunucu kimlik doğrulaması" veya "Istemci kimlik doğrulaması" gibi uygun bir değer içermelidir.

### <a name="client-certificates"></a>İstemci Sertifikaları

İstemci sertifikaları genellikle üçüncü taraf bir sertifika yetkilisi tarafından verilmez. Bunun yerine, geçerli kullanıcı konumunun kişisel deposu genellikle, "Istemci kimlik doğrulaması" amacını taşıyan bir kök yetkilisi tarafından verilen sertifikaları içerir. İstemci, karşılıklı kimlik doğrulaması gerektiğinde böyle bir sertifikayı kullanabilir.

## <a name="online-revocation-and-offline-revocation"></a>Çevrimiçi Iptal ve çevrimdışı Iptal

### <a name="certificate-validity"></a>Sertifika geçerliliği

Her sertifika, *geçerlilik süresi*olarak adlandırılan belirli bir süre için geçerlidir. Geçerlilik süresi, bir X. 509.952 sertifikası tarafından **geçerli olan** ve **geçerli** bir alan tarafından tanımlanır. Kimlik doğrulama sırasında sertifika, sertifikanın hala geçerlilik süresi içinde olup olmadığını belirlemekte denetlenir.

### <a name="certificate-revocation-list"></a>Sertifika Iptal listesi

Geçerlilik süresi boyunca herhangi bir zamanda, sertifika yetkilisi bir sertifikayı iptal edebilir. Bu, sertifikanın özel anahtarıyla ilgili bir uzlaşma olması gibi birçok nedenden kaynaklanabilir.

Bu gerçekleştiğinde, iptal edilen sertifikadan gelen tüm zincirler de geçersiz olur ve kimlik doğrulama yordamları sırasında güvenilir değildir. Hangi sertifikaların iptal edildiğini öğrenmek için, her veren bir zaman ve Tarih damgalı *sertifika iptal listesi* (CRL) yayınlar. Liste, `RevocationMode` aşağıdaki sınıfların veya özelliği sabit listesi değerlerinden birine ayarlanarak çevrimiçi iptal veya çevrimdışı iptali kullanılarak denetlenebilir `DefaultRevocationMode` <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> : <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> , <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> , <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication> ve <xref:System.ServiceModel.Security.IssuedTokenServiceCredential> sınıfları. Tüm özellikler için varsayılan değer `Online` .

Ayrıca, yapılandırma modunu `revocationMode` hem [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) (öğesinin) hem de (öğesinin) özniteliğini kullanarak ayarlayabilirsiniz [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md) [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .

## <a name="the-setcertificate-method"></a>SetCertificate yöntemi

WCF 'de, bir hizmet veya istemcinin bir iletiyi doğrulamak, şifrelemek veya dijital olarak imzalamak için kullanması gereken bir sertifikayı veya sertifika kümesini belirtmeniz gerekir. Bunu, `SetCertificate` X. 509.440 sertifikalarını temsil eden çeşitli sınıfların yöntemini kullanarak programlı bir şekilde yapabilirsiniz. Aşağıdaki sınıflar, `SetCertificate` bir sertifika belirtmek için yöntemini kullanır.

|Sınıf|Yöntem|
|-----------|------------|
|<xref:System.ServiceModel.Security.PeerCredential>|<xref:System.ServiceModel.Security.PeerCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>|<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential>|
|<xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.SetCertificate%2A>|

`SetCertificate`Yöntemi, bir depo konumu ve mağaza tanımlayarak çalışarak, sertifikanın alanını belirten bir "Find" türü ( `x509FindType` parametre) ve alanda bulunacak bir değer. Örneğin, aşağıdaki kod bir <xref:System.ServiceModel.ServiceHost> örnek oluşturur ve hizmeti kimlik doğrulaması için kullanılan hizmet sertifikasını yöntemiyle istemcilere ayarlar `SetCertificate` .

[!code-csharp[c_WorkingWithCertificates#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_workingwithcertificates/cs/source.cs#1)]
[!code-vb[c_WorkingWithCertificates#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_workingwithcertificates/vb/source.vb#1)]

### <a name="multiple-certificates-with-the-same-value"></a>Aynı değere sahip birden fazla sertifika

Bir mağaza aynı konu adına sahip birden çok sertifika içerebilir. Yani, `x509FindType` <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectName> veya <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindBySubjectDistinguishedName> ' nin aynı değere sahip olduğunu belirtirseniz, hangi sertifikanın gerekli olduğunu ayırt etmenin bir yolu olmadığından bir özel durum oluşturulur. ' A ayarlayarak bunu azaltabilirsiniz `x509FindType` <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> . Parmak izi alanı, bir depodaki belirli bir sertifikayı bulmak için kullanılabilecek benzersiz bir değer içerir. Bununla birlikte, bunun kendi dezavantajı vardır: sertifika iptal edildiğinde veya yenilendiğinde, `SetCertificate` parmak izi de geçmiş olduğundan yöntem başarısız olur. Ya da sertifika artık geçerli değilse, kimlik doğrulaması başarısız olur. Bunu hafifletmenin yolu, `x590FindType` parametresini olarak ayarlamak <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByIssuerName> ve verenin adını belirtmektir. Belirli bir veren gerekmiyorsa, gibi diğer numaralandırma değerlerinden birini de ayarlayabilirsiniz <xref:System.Security.Cryptography.X509Certificates.X509FindType> <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByTimeValid> .

## <a name="certificates-in-configuration"></a>Yapılandırmadaki sertifikalar

Sertifikaları, yapılandırma kullanarak da ayarlayabilirsiniz. Bir hizmet oluşturuyorsanız, Sertifikalar dahil olmak üzere kimlik bilgileri altında belirtilir [\<serviceBehaviors>](../../configure-apps/file-schema/wcf/servicebehaviors.md) . Bir istemciyi programlarken, sertifikalar altında belirtilir [\<endpointBehaviors>](../../configure-apps/file-schema/wcf/endpointbehaviors.md) .

## <a name="mapping-a-certificate-to-a-user-account"></a>Bir sertifikayı bir kullanıcı hesabıyla eşleme

IIS ve Active Directory özelliği bir sertifikayı Windows Kullanıcı hesabına eşleyebilme yeteneğidir. Özelliği hakkında daha fazla bilgi için bkz. [sertifikaları kullanıcı hesaplarıyla eşleme](/previous-versions/windows/it-pro/windows-server-2003/cc736706(v=ws.10)).

Active Directory eşleme kullanma hakkında daha fazla bilgi için bkz. [Istemci sertifikalarını dizin hizmeti eşleme Ile eşleme](/previous-versions/windows/it-pro/windows-server-2003/cc758484(v=ws.10)).

Bu özellik etkin olduğunda, <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication.MapClientCertificateToWindowsAccount%2A> <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> sınıfının özelliğini olarak ayarlayabilirsiniz `true` . Yapılandırma bölümünde, `mapClientCertificateToWindowsAccount` [\<authentication>](../../configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md) öğesinin özniteliğini `true` aşağıdaki kodda gösterildiği gibi olarak ayarlayabilirsiniz.

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

Bir Windows Kullanıcı hesabını temsil eden belirtece bir X. 509.440 sertifikası eşleme, bir ayrıcalık yükselmesi olarak değerlendirilir, çünkü eşlendikten sonra, korunan kaynaklara erişim kazanmak için Windows belirteci kullanılabilir. Bu nedenle, etki alanı ilkesi, eşleme öncesinde, X. 509.440 sertifikasının ilkeyle uyumlu olmasını gerektirir. *Schannel* güvenlik paketi bu gereksinimi zorlar.

WCF, .NET Framework 3,5 veya sonraki sürümleri kullanırken, sertifikanın bir Windows hesabına eşlenmesini sağlamak için etki alanı ilkesine uymasını sağlar.

WCF 'nin ilk sürümünde, eşleme etki alanı ilkesine danışmadan yapılır. Bu nedenle, ilk sürüm altında çalışırken çalışmak için kullanılan eski uygulamalar, eşleme etkinse ve X. 509.440 sertifikası etki alanı ilkesini karşılamazsa başarısız olur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels>
- <xref:System.ServiceModel.Security>
- <xref:System.ServiceModel>
- <xref:System.Security.Cryptography.X509Certificates.X509FindType>
- [Hizmet ve İstemcileri Güvenli Hale Getirme](securing-services-and-clients.md)
