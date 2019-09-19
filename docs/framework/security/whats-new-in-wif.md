---
title: Windows Identity Foundation 4.5'teki Yenilikler
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
ms.openlocfilehash: 93631c1171f81ec8b8d94b56a56012343f6c3220
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045276"
---
# <a name="whats-new-in-windows-identity-foundation-45"></a>Windows Identity Foundation 4.5'teki Yenilikler
Windows Identity Foundation'ın (WIF) ilk sürümü tek başına bir indirme olarak gönderildi ve .NET 3.5 SP1 zaman çerçevesinde kullanıma sunulduğundan WIF 3.5 olarak bilinmekteydi. .NET 4.5 sürümünden itibaren WIF, .NET çerçevesinin bir parçası olmuştur. WıF sınıflarının doğrudan çerçevede kullanılabilir olması, .NET 'teki talep tabanlı kimliğin daha ayrıntılı bir şekilde tümleştirilmesini sağlayarak taleplerin kullanılmasını kolaylaştırır. WıF 3,5 için yazılan uygulamaların, yeni modelden faydalanmak için değiştirilmesi gerekir; bilgi için bkz. [wıf 3,5 kullanılarak oluşturulan bir uygulamayı wıf 4,5 ' e geçirmeye yönelik yönergeler](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Aşağıda, bazı önemli ana değişiklikleri bulabilirsiniz.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF Artık .NET Framework'ün Bir Parçasıdır  
 WIF sınıfları artık çok sayıda derlemeye `mscorlib`yayıldığında, ana `System.IdentityModel` `System.IdentityModel.Services`,, ve `System.ServiceModel`. Benzer şekilde, WIF sınıfları çeşitli ad alanlarına yayılır: <xref:System.Security.Claims?displayProperty=nameWithType>, çeşitli [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları ve. <xref:System.ServiceModel.Security?displayProperty=nameWithType> Ad alanı yeni <xref:System.Security.Claims.ClaimsPrincipal> ve<xref:System.Security.Claims.ClaimsIdentity> sınıfları içerir (aşağıya bakın). <xref:System.Security.Claims?displayProperty=nameWithType> .NET 'teki tüm sorumlular artık ' <xref:System.Security.Claims.ClaimsPrincipal>dan türetilir. WıF ad alanları ve içerdikleri sınıfların türleri hakkında daha ayrıntılı bilgi için bkz. [WıF API başvurusu](wif-api-reference.md). Ad alanlarının WıF 3,5 ile WıF 4,5 arasında nasıl eşlenmesiyle ilgili bilgi için, bkz. [wıf 3,5 Ile wıf 4,5 arasındaki ad alanı eşlemesi](namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Yeni Beyan Modeli ve Asıl Nesne  
 Beyanlar .NET Framework 4.5'in özündedir. Temel<xref:System.Security.Claims.Claim>talep sınıfları (, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal> <xref:System.Security.Claims.ClaimTypes>, `mscorlib` ve <xref:System.Security.Claims.ClaimValueTypes>) tamamen <xref:System.Security.Claims?displayProperty=nameWithType> ad alanında doğrudan içinde. Artık, .NET Identity sistemine talepler eklemek için arabirimleri kullanmak <xref:System.Security.Principal.WindowsPrincipal>gerekli değildir:, <xref:System.Security.Principal.GenericPrincipal>, ve <xref:System.Web.Security.RolePrincipal> artık ' den <xref:System.Security.Claims.ClaimsPrincipal>devralma; ve <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, ve <xref:System.Web.Security.FormsIdentity> şimdi devralma öğesinden <xref:System.Security.Claims.ClaimsIdentity>. Kısacası, her asıl sınıf bundan böyle beyanlar sunmaktadır. WIF 3,5 tümleştirme sınıfları ve arabirimleri`WindowsClaimsIdentity`(, `WindowsClaimsPrincipal`, `IClaimsPrincipal` `IClaimsIdentity`,) kaldırılmıştır. Ayrıca, <xref:System.Security.Claims.ClaimsIdentity> sınıfı artık kimliğin talep koleksiyonunu sorgulamayı kolaylaştıran yöntemler sunar.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>WIF 4.5 Visual Studio Deneyimine Yönelik Değişiklikler  
  
- **STS başvurusu Ekle..** . Visual Studio işlevselliği (komut satırı yardımcı programı FedUtil) artık yok; Bunun yerine, **Visual studio 2012 için yeni Visual Studio Uzantı kimliği ve erişim aracı**'nı kullanabilirsiniz. Bu size, varolan bir STS ile federasyon oluşturma veya çözümlerinizi test etmek için LocalSTS kullanma olanağı sağlar. Uzantıyı yükledikten sonra projenize sağ tıklayıp bağlam menüsünde **kimlik ve erişim** ' i bulabilirsiniz.  
  
- Beyanlar varolan ASP.Net, web siteleri ve WCF proje şablonlarında doğrudan kullanılabileceğinden, ASP.NET ve STS şablonları artık sağlanmamaktadır.  
  
- `Microsoft.IdentityModel.Web.Controls` Ad alanındaki (`SignInControl` ,`FederatedPassiveSignInControl`, ve`FederatedPassiveSignInStatus`) denetimler WIF 4,5 ' e taşınmaz.  
  
## <a name="changes-to-the-wif-45-api"></a>WIF 4.5 API'sine Yönelik Değişiklikler  
  
- Genel olarak, talep ile ilgili sınıflar <xref:System.Security.Claims?displayProperty=nameWithType> ad alanıdır; WCF ile ilgili sınıflar--WS-Trust senaryolarında <xref:System.ServiceModel.Security?displayProperty=nameWithType>kullanılan hizmet sözleşmeleri, kanallar, kanal fabrikaları ve hizmet ana bilgisayarları; ve diğer tüm WIF sınıfları farklı [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları genelinde yayıldığında, bunlar şunlardır: Örneğin, WS-* ve SAML yapıtları, belirteç işleyicileri ve ilgili sınıfları ve WS-Federation senaryolarında kullanılan sınıfları temsil eden sınıflar. Daha fazla bilgi için bkz. [wıf 3,5 Ile wıf 4,5](namespace-mapping-between-wif-3-5-and-wif-4-5.md) ve [WIF API başvurusu](wif-api-reference.md)arasında ad alanı eşleme.  
  
- Makine anahtarının, Web grubu senaryoları için oturum tanımlama bilgilerinde kullanımı sağlanmıştır. Daha fazla bilgi için bkz. [WIF ve Web grupları](wif-and-web-farms.md).  
  
- Artık [ \<System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğeleri altında WIF 'yi bildirimli olarak yapılandırırsınız. WıF yapılandırması hakkında daha fazla bilgi için bkz. [WIF yapılandırma başvurusu](wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>WFI'nin .NET tümleştirmesinin sağladığı diğer önemli .NET değişiklikleri veya özellikleri  
  
- Beyan tabanlı kimlik doğrulaması (CBAC) yapma potansiyeli artık .NET çerçevesinde tümleşiktir. Bir <xref:System.Security.Claims.ClaimsAuthorizationManager> nesne yapılandırabilir ve ardından kodunuzda zorunlu ve bildirime <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> dayalı <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> erişim denetimleri gerçekleştirmek için ve sınıflarını kullanabilirsiniz. CBAC, geleneksel rol tabanlı erişim denetimlerine (RBAC) göre daha fazla esneklik ve ayrıntı düzeyi sağlar. Ayrıca iş mantığı, erişim denetimini belirli bir talep veya talepler kümesi için temel almasına ve bu talepler için yetkilendirme ilkesi şu koşullarda bildirimli olarak yapılandırılabildiğinden, [ Yetkilendirmeilkesininişmantığınındahafazlaayrılmasınısağlar.\<ClaimsAuthorizationManager >](../configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesi.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>WIF tümleştirmesinin doğurduğu WCF değişiklikleri:  
  
- WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Bu,, ve <xref:System.IdentityModel.Claims?displayProperty=nameWithType> <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> ad alanlarındaki sınıfların <xref:System.IdentityModel.Policy?displayProperty=nameWithType>WIF sınıflarının kullanılması için bırakılması gereken anlamına gelir.  
  
- WIF, aşağıdaki XML 'de `useIdentityConfiguration` olduğu gibi `<behaviors>` / / `<system.serviceModel>` öğesi`<serviceCredentials>` üzerinde özniteliğini belirterek bir WCF hizmetinde etkin durumdadır: `<serviceBehaviors>` /  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     **Visual Studio 2012 için kimlik ve erişim aracı** 'nı kullandığınızda (Yukarıdaki **Visual Studio deneyimine yapılan değişikliklere** bakın), araç sizin için yapılandırma dosyasına ayarlanan `<serviceCredentials>` `useIdentityConfiguration` özniteliği içeren bir öğe ekler. Ayrıca, WIF yapılandırma ayarlarını içeren karşılık gelen [ \<bir System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) öğesi ekler ve seçtiğiniz STS 'ye kimlik doğrulaması için gereken bir bağlama ve diğer ayarları ekler.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri](guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)
- [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [WIF API Başvurusu](wif-api-reference.md)
- [WIF Yapılandırma Başvurusu](wif-configuration-reference.md)
