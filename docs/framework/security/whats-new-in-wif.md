---
title: Hangi&#39;s Windows Identity Foundation 4.5'deki yenilikler
ms.date: 03/30/2017
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a275c32caefb54b11cc605c1339526465c8319a
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269338"
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>Hangi&#39;s Windows Identity Foundation 4.5'deki yenilikler
Windows Identity Foundation'ın (WIF) ilk sürümü tek başına bir indirme olarak gönderildi ve .NET 3.5 SP1 zaman çerçevesinde kullanıma sunulduğundan WIF 3.5 olarak bilinmekteydi. .NET 4.5 sürümünden itibaren WIF, .NET çerçevesinin bir parçası olmuştur. WIF sınıflarının doğrudan çerçevede kullanılabilir olması beyana dayalı kimliğin taleplerin kullanılmasını kolaylaştırır NET'te çok daha ayrıntılı bir tümleştirme sağlar. WIF 3.5 için yazılmış uygulamalar için yeni modelin avantajlarından yararlanmak için değiştirilmesi gerekecektir; bilgi için [WIF 4.5 için bir Application Built Using WIF 3.5 geçirme yönergeleri](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Aşağıda, bazı önemli ana değişiklikleri bulabilirsiniz.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF Artık .NET Framework'ün Bir Parçasıdır  
 WIF sınıfları artık çeşitli derlemeler geneline yayılmakta yayılan olan `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, ve `System.ServiceModel`. Benzer şekilde, WIF sınıfları çeşitli ad alanları geneline yayılmaktadır: <xref:System.Security.Claims?displayProperty=nameWithType>, birkaç [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları ve <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Ad alanı içeren yeni <xref:System.Security.Claims.ClaimsPrincipal> ve <xref:System.Security.Claims.ClaimsIdentity> sınıfları (aşağıya bakın). . NET'te tüm ilkeleri artık öğesinden türetilen <xref:System.Security.Claims.ClaimsPrincipal>. WIF ad alanları ve içerdikleri sınıfların türleri hakkında daha ayrıntılı bilgi için bkz: [WIF API Reference](../../../docs/framework/security/wif-api-reference.md). Ad alanları, WIF 3.5 ile WIF 4.5 arasında nasıl eşleştiği hakkında daha fazla bilgi için bkz: [Namespace eşleme WIF 3.5 ile WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Yeni Beyan Modeli ve Asıl Nesne  
 Beyanlar .NET Framework 4.5'in özündedir. Taban beyan sınıflarının (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, ve <xref:System.Security.Claims.ClaimValueTypes>) tüm Canlı doğrudan `mscorlib` içinde <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı. Artık arabirimleri talep .NET kimlik sistemine bağlama noktasına sahip olmak için gerekli değildir: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, ve <xref:System.Web.Security.RolePrincipal> artık devralınacak <xref:System.Security.Claims.ClaimsPrincipal>; ve <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, ve <xref:System.Web.Security.FormsIdentity> artık devral gelen <xref:System.Security.Claims.ClaimsIdentity>. Kısacası, her asıl sınıf bundan böyle beyanlar sunmaktadır. WIF 3.5 tümleştirme sınıfları ve arabirimleri (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) bu nedenle kaldırılmıştır. Ayrıca, <xref:System.Security.Claims.ClaimsIdentity> sınıfı için kolaylaştıran yöntemleri şimdi kimliğin beyan koleksiyonunu.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>WIF 4.5 Visual Studio Deneyimine Yönelik Değişiklikler  
  
-   **STS Başvurusu Ekle...** Visual Studio işlevselliği (cmdline yardımcı programı FedUtil) artık mevcut; Bunun yerine yeni Visual Studio uzantısı kullanabileceğiniz **kimlik ve erişim aracı Visual Studio 2012 için**. Bu size, varolan bir STS ile federasyon oluşturma veya çözümlerinizi test etmek için LocalSTS kullanma olanağı sağlar. Uzantıyı yükledikten sonra projenize sağ tıklayın ve aranacak **kimlik ve erişim** bağlam menüsünde.  
  
-   Beyanlar varolan ASP.Net, web siteleri ve WCF proje şablonlarında doğrudan kullanılabileceğinden, ASP.NET ve STS şablonları artık sağlanmamaktadır.  
  
-   Denetimlerde `Microsoft.IdentityModel.Web.Controls` ad alanı (`SignInControl`, `FederatedPassiveSignInControl`, ve `FederatedPassiveSignInStatus`) WIF 4. 5 ' taşınmaz.  
  
## <a name="changes-to-the-wif-45-api"></a>WIF 4.5 API'sine Yönelik Değişiklikler  
  
-   Talep ilgili sınıflar bulunan genel olarak, <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı; WCF ilgili sınıflar – - Hizmet sözleşmeleri, Kanallar, kanal fabrikaları ve WS-Güven senaryoları için--kullanılan hizmet konakları bulunduğunuz <xref:System.ServiceModel.Security?displayProperty=nameWithType>; ve tüm diğer WIF sınıfları çeşitli arasında yayılır [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları – bunlar, örneğin, WS - temsil eden sınıfları * ve SAML yapılarını belirteç işleyicileri ve ilgili sınıfları ve WS-Federasyon senaryolarında kullanılan sınıfları. Daha fazla bilgi için [Namespace eşleme WIF 3.5 ile WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) ve [WIF API Reference](../../../docs/framework/security/wif-api-reference.md).  
  
-   Makine anahtarının, Web grubu senaryoları için oturum tanımlama bilgilerinde kullanımı sağlanmıştır. Daha fazla bilgi için [WIF ve Web grupları](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Artık bildirimli olarak WIF altında yapılandırdığınız [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğeleri. WIF yapılandırması hakkında daha fazla bilgi için bkz. [WIF Configuration Reference](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>WFI'nin .NET tümleştirmesinin sağladığı diğer önemli .NET değişiklikleri veya özellikleri  
  
-   Beyan tabanlı kimlik doğrulaması (CBAC) yapma potansiyeli artık .NET çerçevesinde tümleşiktir. Yapılandırabileceğiniz bir <xref:System.Security.Claims.ClaimsAuthorizationManager> nesnesi ve ardından <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ve <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> kodunuzda zorunlu ve beyana dayalı erişim denetimleri gerçekleştirmek için sınıflar. CBAC, geleneksel rol tabanlı erişim denetimlerine (RBAC) göre daha fazla esneklik ve ayrıntı düzeyi sağlar. Ayrıca yetkilendirme ilkesinin iş mantığından daha fazla ayrılmasını çünkü iş mantığı erişim denetimini belirli bir talep temel alabilir veya talepleri ve bu talepleri yetkilendirme ilkesi yapılandırılabilir bildirimli olarak altında sağlar[ \<claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesi.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>WIF tümleştirmesinin doğurduğu WCF değişiklikleri:  
  
-   WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıflar Bunun anlamı <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> ad alanları, WIF sınıflarını kullanmak lehine bırakılmalıdır.  
  
-   WIF artık etkin bir WCF Hizmeti belirterek `useIdentityConfiguration` özniteliği `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` öğesi aşağıdaki XML'de olduğu gibi:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Kullanırken **kimlik ve erişim aracı Visual Studio 2012 için** (bkz **değiştirir Visual Studio deneyimine** yukarıda), aracı ekler bir `<serviceCredentials>` öğeyle `useIdentityConfiguration` özniteliği ayarlayın sizin için yapılandırma dosyası. Karşılık gelen de ekler [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) öğesi WIF yapılandırması ayarlarını içeren ve bir bağlama ve kimlik doğrulaması tercih ettiğiniz sts'ye dış kaynak için gerekli diğer ayarları ekler.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [WIF API Başvurusu](../../../docs/framework/security/wif-api-reference.md)  
 [WIF Yapılandırma Başvurusu](../../../docs/framework/security/wif-configuration-reference.md)
