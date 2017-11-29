---
title: "WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamayı geçirmek için yönergeler"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: fc5554193d93f2a88fd9e6d1c1af7923a23b2280
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamayı geçirmek için yönergeler
## <a name="applies-to"></a>Uygulandığı öğe:  
  
-   Microsoft® Windows® Identity Foundation (WIF) 3.5 ve 4.5.  
  
## <a name="overview"></a>Genel Bakış  
 Windows Identity Foundation (WIF) .NET 3.5 SP1 zaman çerçevesinde ilk olarak yayımlanmıştır. WIF sürümünün WIF 3.5 adlandırılır. Ayrı çalışma zamanı ve SDK'sı, ama WIF etkin bir uygulama çalıştırıldığı her bilgisayarda yüklü WIF çalışma zamanı olması gerekiyordu ve geliştiriciler Visual Studio şablonları ve etkinleştirilmiş tooling almak için WIF SDK'sını yükleyip gerekiyordu amacı yayımlanan WIF kullanan uygulamaları geliştirme. .NET 4. 5'ile başlayan, WIF tam olarak .NET Framework'e tümleştirilmiştir. Ayrı bir çalışma zamanı artık gerekli değildir ve WIF araçları Visual Studio 2012'de Visual Studio uzantıları Yöneticisi kullanılarak yüklenebilir. Bu sürümü WIF WIF 4.5 adlandırılır.  
  
 .NET WIF tümleştirilmesi WIF API yüzeyi birkaç değişiklikleri olmaması. WIF 4.5 yeni ad alanları, bazı değişiklikler yapılandırma öğeleri ve Visual Studio için yeni araçları içerir. Bu konu WIF 4.5 WIF 3.5 kullanılarak oluşturulan uygulamalar geçirmenize yardımcı olması için kullanabileceğiniz yönergeler sağlar. Windows 8 veya Windows Server 2012 çalıştıran bilgisayarlara WIF 3.5 kullanılarak oluşturulan eski uygulamaları çalıştırmak gereken senaryolar olabilir. Bu konu aynı zamanda bu işletim sistemleri için WIF 3.5 etkinleştirme hakkında yönergeler sağlar.  
  
## <a name="changes-required-for-wif-45"></a>WIF 4.5 için gerekli değişiklikleri  
 Bu bölümde WIF 4.5 WIF 3.5 uygulamaya geçirmek için gereken değişiklikleri açıklar.  
  
### <a name="assembly-and-namespace-changes"></a>Derleme ve Namespace değişiklikleri  
 WIF 3. 5'da, tüm WIF sınıfları içinde yer alan `Microsoft.IdentityModel` derleme (microsoft.identitymicrosoft.identitymodel.dll). Aşağıdaki derlemeler arasında WIF 4.5 içinde WIF sınıfları böl: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) ve `System.ServiceModel` (System.ServiceModel.dll ).  
  
 WIF 3.5 sınıfları tüm birinde yer `Microsoft.IdentityModel` ad alanları; örneğin, `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`ve benzeri. WIF 4.5 içinde WIF sınıfları şimdi arasında yayılır [System.IdentityModel](http://go.microsoft.com/fwlink/?LinkId=272004) ad alanları, <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı ve <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanı. Bu düzenlenmesi ek olarak, bazı WIF 3.5 sınıfları WIF 4.5 bırakıldı.  
  
 Aşağıdaki tabloda bazı daha önemli WIF 4.5 ad alanları ve sınıfları içerdikleri türünü gösterir. Daha ayrıntılı ve ad alanları WIF 3.5 ve WIF 4.5 arasında nasıl harita hakkında ad alanları ve WIF 4.5 bırakılan sınıfları hakkında bilgi için [Namespace eşleme WIF 3.5 ve WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).  
  
|WIF 4.5 Namespace|Açıklama|  
|-----------------------|-----------------|  
|<xref:System.IdentityModel?displayProperty=nameWithType>|Tanımlama bilgisi dönüşümler, güvenlik belirteci Hizmetleri ve özel XML sözlük okuyucular temsil eden sınıfları içerir. Aşağıdaki WIF 3.5 ad sınıflardan içerir: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, ve `Microsoft.IdentityModel.Threading`.|  
|<xref:System.Security.Claims?displayProperty=nameWithType>|Talepler, talep tabanlı kimlik, talep tabanlı ilkeleri ve diğer talep tabanlı kimlik modeli yapıları temsil eden sınıfları içerir. Sınıflardan içeren `Microsoft.IdentityModel.Claims` ad alanı.|  
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Güvenlik belirteçleri, güvenlik belirteci işleyicileri ve diğer güvenlik belirteci yapıları temsil eden sınıfları içerir. Aşağıdaki WIF 3.5 ad sınıflardan içerir: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, ve `Microsoft.IdentityModel.Tokens.Saml2`.|  
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir. Sınıflardan içeren `Microsoft.IdentityModel.Web` ad alanı.|  
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|WCF sözleşmeleri, kanalları, hizmet konakları ve etkin (WS-Trust) senaryolarında kullanılır diğer yapıları temsil eden sınıflar bu ad alanında sunulmuştur. Bu sınıfların WIF 3. 5'bulunduğunuz `Microsoft.IdentityModel.Protocols.WSTrust` ad alanı.|  
  
> [!IMPORTANT]
>  Aşağıdaki `System.IdentityModel` ad alanları içeren WCF beyana dayalı kimlik modelinde uygulayan sınıflar: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıflar bu üç ad alanlarında WIF tabanlı çözümler oluştururken kullanmamanız gerekir.  
  
### <a name="changes-due-to-net-integration"></a>.NET tümleştirme nedeniyle değişiklikler  
 WIF şimdi .NET Framework'e tümleşiktir. Çoğu .NET kimlik ve asıl sınıfları şimdi öğesinden türetilen <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. WIF 4.5 aşağıdaki değişiklikleri sonuçlanır:  
  
-   Talepler, kimlik ve ilkeleri artık temsil eden WIF sınıflar mevcut <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı.  
  
    > [!IMPORTANT]
    >  <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Ad alanı, WCF beyana dayalı kimlik modelinde yapıları temsil eden sınıfları içerir. Bu sınıfların çoğu WIF sınıflar olarak aynı adlara sahip; Örneğin, `Claims`. Bu sınıfların WIF tabanlı çözümler oluştururken kullanmayın.  
  
-   .NET kimlik ve asıl sınıfları şimdi türetilen doğrudan <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, talep tabanlı kimlik ve ilkeleri gösterir. Bu nedenle, WIF 3.5 arabirimleri `IClaimsIdentity` ve `IClaimsPrincipal` artık gerekli değildir ve WIF 4.5 kullanılabilir değil.  
  
-   Because.NET kimlik ve asıl sınıflar gibi <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> şimdi türetin <xref:System.Security.Claims.ClaimsIdentity> ve <xref:System.Security.Claims.ClaimsPrincipal>, talep işlevselliği yerleşik sahiptirler. Bu nedenle, talep özgü kimlik ve asıl sınıfları gibi `WindowsClaimsIdentity` ve `WindowsClaimsPrincipal` , WIF 3.5 mevcut artık gerekli değildir ve WIF 4.5 içinde yok.  
  
### <a name="other-changes-to-wif-functionality"></a>Başka WIF işlev değişiklikleri  
 Ad alanı değişiklikleri ve .NET ile tümleştirme değişikliklerinin ek olarak, aşağıdaki genel değişiklikler WIF işlevine WIF 4.5 gerçekleşir.  
  
-   `Microsoft.IdentityModel.ExceptionMapper` Belirli SOAP hataları için özel durumlar eşleştirmek etkin işlevselliği sağlayan, sınıf kaldırılır.  
  
-   Özel durum yüzeyini önemli ölçüde azalır.  
  
-   Birçok protokolü veya WS - tanımlı sınıfların * belirli sabitleri kaldırılmış; Örneğin, `Microsoft.IdentityModel.WSAddressing10Constants` WS adresleme 1.0 ilgili sabitleri tanımlı sınıfı.  
  
-   Windows Belirteç Hizmeti (c2wts) için talep ve onun ilişkili sınıfları `Microsoft.IdentityModel.WindowsTokenService` ad alanı kaldırılır.  
  
### <a name="wif-configuration-changes"></a>WIF yapılandırma değişiklikleri  
 Yapılandırma dosyasındaki değişiklikleri çoğunu WIF 4.5 ad alanı güncelleştirmelerinde olmuş. Örneğin, aşağıdaki WIF 3.5 girdisinde göz önünde bulundurun `<httpModules>` WS-Federasyon kimlik doğrulama Yöneticisi'ni bir uygulama eklemek için bölüm:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />  
```  
  
 Bu girdi yeni ad alanları ve derleme sürümü içerecek şekilde WIF 4.5 içinde güncelleştirildi:  
  
```xml  
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>  
```  
  
 Aşağıdaki listede yapılandırma dosyasının önemli değişiklikler için WIF 4.5 numaralandırır.  
  
-   `<microsoft.identityModel>` Bölümdür şimdi [ \<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) bölümü.  
  
-   `<service>` Öğesidir şimdi [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.  
  
-   Yeni bir bölüm [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), pasif (WS-Federation) senaryolarında davranışını denetleyen ayarları belirtmek için eklendi.  
  
-   [ \<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) öğesi ve kendi alt öğelerini taşınır gelen `<service>` WIF 3.5 öğesinde yeni `<system.identityModel.services>` öğesi.  
  
-   Hizmet düzeyi doğrudan altında konumunda belirtilen çeşitli öğeleri `<service>` WIF 3.5 öğesinde altında belirtilen için sınırlı olduğu [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi. (Altında hala belirtilebilir [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) WIF 4.5 öğesinde geriye dönük uyumluluk için.)  
  
 WIF 4.5 yapılandırma öğelerini tam bir listesi için bkz: [WIF yapılandırma şeması](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).  
  
### <a name="visual-studio-tooling-changes"></a>Visual Studio Araçları değişiklikleri  
 Bir tek başına Federasyon yardımcı programı WIF 3.5 SDK'sı sunulan (FedUtil) FedUtil.exe WIF etkin uygulamalarda bir güvenlik belirteci hizmeti (STS) için Kimlik Yönetimi dış kaynak sağlamak için kullanabilirsiniz. Bu aracı WIF ayarları bir veya daha fazla Sts'ler güvenlik belirteçleri almak için uygulama etkinleştirmek için uygulama yapılandırma dosyasına eklendi ve Visual Studio ortaya **STS hizmet Başvurusu Ekle** düğmesi. FedUtil WIF 4.5 ile birlikte gelmez. Bunun yerine, uygulamanızın yapılandırma dosyasına bir STS için Kimlik Yönetimi dış kaynak sağlamak için gerekli WIF ayarları değiştirmek için kullanabileceğiniz Visual Studio 2012 için kimlik ve erişim aracı adlı yeni bir Visual Studio uzantısı WIF 4.5 destekler. Kimlik ve erişim aracı WIF etkinleştirilmiş uygulamalarınızı test etmek için kullanabileceğiniz yerel STS olarak adlandırılan bir STS de uygular. Çoğu durumda, bu özellik genellikle WIF 3.5 çözümleri geliştirme altında test etmek için gerekli özel Sts'ler oluşturmaya gerek obviates. Bu nedenle, STS şablonları artık Visual Studio 2012'de desteklenir; Ancak, Sts'ler geliştirme destekleyen sınıfları WIF 4.5 içinde hala kullanılabilir durumdadır.  
  
 Uzantılar ve güncelleştirmeler Yöneticisi'nde Visual Studio kimlik ve erişim aracı yükleyebilir veya kod Galerisi aşağıdaki sayfasından indirebilirsiniz: [kimlik ve erişim aracı kod Galerisi üzerinde Visual Studio 2012 için](http://go.microsoft.com/fwlink/?LinkID=245849). Visual Studio Araçları değişiklikler aşağıdaki listede özetlenmiştir:  
  
-   STS hizmet Başvurusu Ekle işlevselliği kaldırılır. Kimlik ve erişim aracı yerini alır.  
  
-   Visual Studio STS şablonları kaldırılır. Kimlik ve erişim aracı ile WIF geliştirmek kimlik çözümleri test etmek için aracılığıyla kullanılabilir yerel STS kullanabilirsiniz. Yerel STS yapılandırma sunduğu talep özelleştirmek için değiştirilebilir.  
  
-   Tek başına Federasyon yardımcı programı'nı (FedUtil), WIF 4.5 içinde kullanılamaz. Yapılandırma dosyalarınızın bir STS için Kimlik Yönetimi dış değiştirmek için kimlik ve erişim Aracı'nı kullanabilirsiniz.  
  
 Kimlik ve erişim aracı hakkında daha fazla bilgi için bkz: [kimlik ve erişim aracı Visual Studio 2012 için](../../../docs/framework/security/identity-and-access-tool-for-vs.md)  
  
<a name="BKMK_ToolingChanges"></a>   
### <a name="passive-ws-federation-scenarios"></a>Pasif (WS-Federation) senaryolar:  
  
-   Pasif senaryolarını destekleyen sınıfları taşınır için <xref:System.IdentityModel.Services?displayProperty=nameWithType> ad alanı. Bu sınıfların WIF 3.5 bulunduğunuz `Microsoft.IdentityModel.Web` ad alanı.  
  
-   Sınıflarda `Microsoft.IdentityModel.Web.Configuration` ad alanı taşınır için <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Bu sınıfların nesneleri belirli pasif senaryolarda yapılandırmasını temsil eder.  
  
-   `FederatedPasssiveSignInControl` Artık desteklenmemektedir; tüm sınıflarda `Microsoft.IdentityModel.Web.Controls` ad alanı WIF 4.5'ten kaldırıldı.  
  
-   WS-Federasyon kimlik doğrulama Modülü (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) oturum kapatma işlevselliği WIF 3.5 farklı. WIF 4.5 içinde oturum kapatma nasıl çalıştığı hakkında daha fazla ayrıntı için bkz: <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıfı konu.  
  
### <a name="active-wcfws-trust-scenarios"></a>Etkin (WCF/WS-Trust) senaryolar:  
  
-   `Microsoft.IdentityModel.Protocols.WSTrust` Ad alanı bölme çoğunlukla WIF 4.5 iki ad alanları içine. WS-Trust protokole özgü yapıları temsil eden sınıflar şimdi olan <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Bu gibi sınıflara içerir <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Hizmet sözleşmeleri, kanalları, hizmet konakları ve WS-Trust WCF uygulamaları kullanarak söz konusu diğer yapıları temsil eden sınıflar taşınır için <xref:System.ServiceModel.Security?displayProperty=nameWithType>; Örneğin, <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> arabirimi.  
  
-   WIF kullanan bir WCF uygulaması yapılandırma büyük ölçüde basitleştirilmiştir. Daha önce `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` davranış uzantısı eklenmesi gerekiyordu ve bu işlevselliği belirterek hizmet davranışı WIF Kama için kullanılan bir `<federatedServiceHostConfiguration>` öğesi. WIF 4.5, WCF ile daha sıkı bir şekilde tümleştirilmiştir. WIF belirterek bir WCF hizmetini etkinleştirin artık `useIdentityConfiguration` özniteliği `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` olduğu gibi aşağıdaki XML öğesi:  
  
    ```xml  
    <serviceCredentials useIdentityConfiguration="true">  
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->  
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />  
    </serviceCredentials>  
    ```  
  
-   WIF 4.5 hizmetin bir etkin (WCF) hizmeti tarafından kullanılan sertifika hizmeti konakta belirtilmesi gerekir. Yapılandırmada üzerinden bunu yapabilirsiniz `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` önceki örnekte gösterildiği gibi öğesi. WIF 3.5 aracılığıyla hizmet sertifikası belirtilebilir `<serviceCertificate>` WIF alt öğesi `<service>` öğesi. Bu işlev WIF 4.5 yok; belirtin `<serviceCertificate>` öğesinin altında `<serviceCredentials>` öğesi yerine.  
  
-   WIF 3.5 WCF artık Kama için kullanılan sınıflar mevcut. Bu aşağıdaki sınıflarda içerir `Microsoft.IdentityModel.Tokens` ad alanı: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, ve `IdentityModelServiceAuthorizationManager`, yanı sıra `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` sınıfı.  
  
## <a name="enabling-wif-35-in-windows-8"></a>WIF 3.5 Windows 8'de etkinleştirme  
 WIF 4.5 .NET 4.5 parçası olduğundan, Windows 8 ve Windows Server 2012 çalıştıran bilgisayarlarda otomatik olarak etkinleştirilir ve WIF 4.5 kullanılarak oluşturulan uygulamalar varsayılan olarak Windows 8 veya Windows Server 2012 altında çalışacaktır. Ancak, Windows 8 veya Windows Server 2012 çalıştıran bir bilgisayarda WIF 3.5 kullanılarak geliştirilmiş uygulamaları çalıştırmak gerekebilir. Bu durumda, hedef bilgisayarda WIF 3.5 etkinleştirmeniz gerekir. Windows 8 çalıştıran bir bilgisayarda olan Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) aracını kullanarak bunu yapabilirsiniz. Windows Server 2012 çalıştıran bir bilgisayarda, DISM aracını kullanın ya da Windows PowerShell'i kullanabilirsiniz `Add-WindowsFeature` cmdlet'i. Komut satırında veya uygun komutları her iki durumda da çağrılabilir Windows PowerShell ortamı içindeki.  
  
 Aşağıdaki komutlar komut satırından veya gelen DISM aracının nasıl kullanılacağını göstermektedir Windows PowerShell ortamı içindeki. Varsayılan olarak, DISM PowerShell modülü Windows 8 ve Windows Server 2012'de bulunan ve aktarılması gerekmez. Windows PowerShell ile DISM kullanma hakkında daha fazla bilgi için bkz: [kullanım DISM Windows PowerShell'de nasıl](http://go.microsoft.com/fwlink/?LinkId=254419).  
  
 WIF 3.5 DISM'yi kullanarak etkinleştirmek için:  
  
```  
dism /online /enable-feature:windows-identity-foundation  
```  
  
 WIF 3.5 DISM'yi kullanarak devre dışı bırakmak için:  
  
```  
dism /online /disable-feature:windows-identity-foundation  
```  
  
 Hangi özelliklerin etkinleştirilir veya DISM kullanarak devre dışı denetlemek için:  
  
```  
dism /online /get-features  
```  
  
 Alternatif olarak, Windows Server 2012 çalıştıran bilgisayarlarda, WIF 3.5 Windows PowerShell kullanarak etkinleştirebilirsiniz `Add-WindowsFeature` cmdlet'i. Komut satırından Bunu yapmak için aşağıdaki komutu girebilirsiniz:  
  
```  
powershell "add-windowsfeature windows-identity-foundation"  
```  
  
 Windows PowerShell ortamın içinde komut doğrudan girebilirsiniz:  
  
```  
add-windowsfeature windows-identity-foundation  
```  
  
> [!NOTE]
>  Aynı adı paylaştığından, birlikte WIF 3.5 ve WIF 4.5 kullanırken WIF 3.5 ve WIF 4.5 sınıfların çoğu tam sınıf adları kullanın ya da WIF 3.5 sınıflarda WIF 4.5 arasında ayrım yapmak için ad alanı diğer adlar kullanın emin olun.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WIF yapılandırma şeması](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)  
 [WIF 3.5 ve WIF 4.5 arasında Namespace eşleme](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)  
 [Windows Identity Foundation 4.5 yenilikler nelerdir?](../../../docs/framework/security/whats-new-in-wif.md)  
 [Kimlik ve erişim aracı Visual Studio 2012 için](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
