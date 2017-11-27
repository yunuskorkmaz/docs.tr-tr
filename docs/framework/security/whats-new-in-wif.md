---
title: '&#39; teki Windows Identity Foundation 4.5''deki yenilikler'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3b381f04-593b-471f-bd33-0362be1aade5
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 19116aba3049dce6612ca1a7170030f7ced6705e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="what39s-new-in-windows-identity-foundation-45"></a>&#39; teki Windows Identity Foundation 4.5'deki yenilikler
Windows Identity Foundation'ın (WIF) ilk sürümü tek başına bir indirme olarak gönderildi ve .NET 3.5 SP1 zaman çerçevesinde kullanıma sunulduğundan WIF 3.5 olarak bilinmekteydi. .NET 4.5 sürümünden itibaren WIF, .NET çerçevesinin bir parçası olmuştur. Framework'te doğrudan kullanılabilen WIF sınıfları sahip talep tabanlı kimlik talepleri kullanan kolaylaştırma .NET içinde çok derin tümleştirme sağlar. WIF 3.5 için yazılmış uygulamalar için yeni model yararlanmak için değiştirilmesi gerekir; bilgi için bkz: [bir uygulama yerleşik kullanarak WIF 3.5 WIF 4.5 sürümüne geçirmek için yönergeler](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md).  
  
 Aşağıda, bazı önemli ana değişiklikleri bulabilirsiniz.  
  
## <a name="wif-is-now-part-of-the-net-framework"></a>WIF Artık .NET Framework'ün Bir Parçasıdır  
 WIF sınıf artık birkaç derlemeler arasında ana olanları yayılan olan `mscorlib`, `System.IdentityModel`, `System.IdentityModel.Services`, ve `System.ServiceModel`. Benzer şekilde, WIF sınıfları birkaç ad alanları arasında yayılır: <xref:System.Security.Claims?displayProperty=nameWithType>, birkaç [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) ad alanları, ve <xref:System.ServiceModel.Security?displayProperty=nameWithType>. <xref:System.Security.Claims?displayProperty=nameWithType> Ad alanı içeren yeni <xref:System.Security.Claims.ClaimsPrincipal> ve <xref:System.Security.Claims.ClaimsIdentity> sınıfları (aşağıya bakın). .NET içinde tüm Sorumlular şimdi öğesinden türetilen <xref:System.Security.Claims.ClaimsPrincipal>. WIF ad alanları ve içerdikleri sınıfları türleri hakkında daha ayrıntılı bilgi için bkz: [WIF API Başvurusu](../../../docs/framework/security/wif-api-reference.md). Ad alanları WIF 3.5 ve WIF 4.5 arasında nasıl eşleme hakkında daha fazla bilgi için bkz: [Namespace eşleme WIF 3.5 ve WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
## <a name="new-claims-model-and-principal-object"></a>Yeni Beyan Modeli ve Asıl Nesne  
 Beyanlar .NET Framework 4.5'in özündedir. Temel sınıflar talep (<xref:System.Security.Claims.Claim>, <xref:System.Security.Claims.ClaimsIdentity>, <xref:System.Security.Claims.ClaimsPrincipal>, <xref:System.Security.Claims.ClaimTypes>, ve <xref:System.Security.Claims.ClaimValueTypes>) tüm Canlı doğrudan `mscorlib` içinde <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı. Artık .NET kimlik sisteme talep bağlama için arabirimleri kullanmak gerekli değildir: <xref:System.Security.Principal.WindowsPrincipal>, <xref:System.Security.Principal.GenericPrincipal>, ve <xref:System.Web.Security.RolePrincipal> şimdi devralınmalıdır <xref:System.Security.Claims.ClaimsPrincipal>; ve <xref:System.Security.Principal.WindowsIdentity>, <xref:System.Security.Principal.GenericIdentity>, ve <xref:System.Web.Security.FormsIdentity> şimdi devral gelen <xref:System.Security.Claims.ClaimsIdentity>. Kısacası, her asıl sınıf bundan böyle beyanlar sunmaktadır. WIF 3.5 tümleştirme sınıflar ve arabirimler (`WindowsClaimsIdentity`, `WindowsClaimsPrincipal`, `IClaimsPrincipal`, `IClaimsIdentity`) böylece kaldırıldı. Ayrıca, <xref:System.Security.Claims.ClaimsIdentity> kolaylaştırmak çıkarır yöntemleri kimliğin sorgu artık sınıfı talep koleksiyonu.  
  
## <a name="changes-to-the-wif-45-visual-studio-experience"></a>WIF 4.5 Visual Studio Deneyimine Yönelik Değişiklikler  
  
-   **STS Başvurusu Ekle...** Visual Studio işlevselliği (komut satırı yardımcı programı FedUtil) artık yoktur; Bunun yerine, yeni Visual Studio uzantısı kullanabileceğiniz **kimlik ve erişim aracı Visual Studio 2012 için**. Bu size, varolan bir STS ile federasyon oluşturma veya çözümlerinizi test etmek için LocalSTS kullanma olanağı sağlar. Uzantıyı yükledikten sonra projeye sağ tıklayın ve Ara **kimlik ve erişim** bağlam menüsünde.  
  
-   Beyanlar varolan ASP.Net, web siteleri ve WCF proje şablonlarında doğrudan kullanılabileceğinden, ASP.NET ve STS şablonları artık sağlanmamaktadır.  
  
-   Denetimleri `Microsoft.IdentityModel.Web.Controls` ad alanı (`SignInControl`, `FederatedPassiveSignInControl`, ve `FederatedPassiveSignInStatus`) WIF 4.5 taşınır değil.  
  
## <a name="changes-to-the-wif-45-api"></a>WIF 4.5 API'sine Yönelik Değişiklikler  
  
-   Genel olarak, talep ilgili olarak sınıflardır <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı; WCF ilgili sınıflar – - hizmet sözleşmeler, Kanallar, kanal fabrikaları ve WS-Trust senaryoları için--kullanılan hizmet konakları olan <xref:System.ServiceModel.Security?displayProperty=nameWithType>; ve diğer tüm WIF sınıfları çeşitli arasında yayılır [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) ad alanları – bunlar, örneğin, WS - temsil eden sınıfları * SAML yapıları belirteci işleyicileri ve ilgili sınıfları ve WS-Federasyon senaryolarında kullanılan sınıfları ve. Daha fazla bilgi için bkz: [Namespace eşleme WIF 3.5 ve WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md) ve [WIF API Başvurusu](../../../docs/framework/security/wif-api-reference.md).  
  
-   Makine anahtarının, Web grubu senaryoları için oturum tanımlama bilgilerinde kullanımı sağlanmıştır. Daha fazla bilgi için bkz: [WIF ve Web grupları](../../../docs/framework/security/wif-and-web-farms.md).  
  
-   Şimdi bildirimli olarak WIF altında yapılandırdığınız [ \<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) öğeleri. WIF yapılandırma hakkında daha fazla bilgi için bkz: [WIF yapılandırma başvurusu](../../../docs/framework/security/wif-configuration-reference.md).  
  
## <a name="other-notable-net-changes-or-features-that-are-caused-by-the-integration-of-wif-into-net"></a>WFI'nin .NET tümleştirmesinin sağladığı diğer önemli .NET değişiklikleri veya özellikleri  
  
-   Beyan tabanlı kimlik doğrulaması (CBAC) yapma potansiyeli artık .NET çerçevesinde tümleşiktir. Yapılandırabileceğiniz bir <xref:System.Security.Claims.ClaimsAuthorizationManager> nesnesi ve ardından <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> ve <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> kodunuzda kesinlik temelli ve bildirim temelli erişim denetimleri gerçekleştirmek için sınıflar. CBAC, geleneksel rol tabanlı erişim denetimlerine (RBAC) göre daha fazla esneklik ve ayrıntı düzeyi sağlar. Ayrıca yetkilendirme ilkesi büyük ayrılması iş mantığı gelen iş mantığı belirli bir talep üzerinde erişim denetimi temel alabilir veya grup talepleri ve bu talepleri yetkilendirme ilkesi yapılandırılabilir bildirimli olarak altındaolduğundantanır[ \<claimsAuthorizationManager >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md) öğesi.  
  
## <a name="wcf-changes-as-a-result-of-wif-integration"></a>WIF tümleştirmesinin doğurduğu WCF değişiklikleri:  
  
-   WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıflar Bunun anlamı <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType> ad alanları bırakılan WIF sınıflarını kullanarak lehinde.  
  
-   WIF şu anda etkin bir WCF Hizmeti belirterek `useIdentityConfiguration` özniteliği `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` olduğu gibi aşağıdaki XML öğesi:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
     Kullandığınızda **kimlik ve erişim aracı Visual Studio 2012 için** (bkz **değiştirir Visual Studio deneyimine** yukarıda), aracı ekler bir `<serviceCredentials>` öğeyle `useIdentityConfiguration` özniteliği ayarlamak sizin için yapılandırma dosyası. Ayrıca bir karşılık gelen ekler [ \<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) WIF yapılandırma ayarlarını içeren ve bağlama ve kimlik doğrulama, seçilen STS için dış kaynak sağlamak gerekli diğer ayarları ekler öğesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamayı geçirmek için yönergeler](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)  
 [WIF 3.5 ve WIF 4.5 arasında Namespace eşleme](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [WIF API Başvurusu](../../../docs/framework/security/wif-api-reference.md)  
 [WIF yapılandırma başvurusu](../../../docs/framework/security/wif-configuration-reference.md)
