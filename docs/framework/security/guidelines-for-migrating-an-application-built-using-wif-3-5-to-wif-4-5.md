---
title: WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamayı geçirme yönergeleri
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: ad8ff2b6daaaf48975b86c637435b31fa1869e1d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370026"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>WIF 4.5 WIF 3.5 kullanılarak oluşturulan bir uygulamayı geçirme yönergeleri

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WIF) 3.5 ve 4.5.

## <a name="overview"></a>Genel Bakış

Windows Identity Foundation (WIF) ilk .NET 3.5 SP1 zaman çerçevesinde kullanıma sunuldu. WIF sürümünün WIF 3.5 adlandırılır. Ayrı çalışma zamanını ve SDK'sı, ama bir WIF özelliği etkinleştirilmiş uygulamanın çalıştırıldığı her bilgisayarda yüklü olan WIF çalışma zamanı gerekti ve geliştiriciler Visual Studio şablonları ve etkinleştirilmiş araç almak için WIF SDK'sını indirip olduğu anlamına geliyordu yayımlanmıştır WIF özelliği etkinleştirilmiş uygulamaların geliştirilmesini. .NET 4.5 ile başlayarak, WIF tam .NET Framework'e tümleştirilmiştir. Ayrı bir çalışma zamanı artık gerekli değil ve Visual Studio Uzantı Yöneticisi'ni kullanarak, WIF araçları Visual Studio 2012'de yüklenebilir. WIF bu sürümü, WIF 4.5 adlandırılır.

WIF API yüzeyi, bazı değişiklikler tümleştirmesinin .NET olmaması. WIF 4.5, yeni ad alanları, yapılandırma öğelerini ve yeni araçları Visual Studio için bazı değişiklikler içerir. Bu konuda, WIF 3.5 to WIF 4.5 kullanılarak oluşturulan uygulamalar geçirmenize yardımcı olması için kullanabileceğiniz bir kılavuz sağlar. Windows 8 veya Windows Server 2012 çalıştıran bilgisayarlara WIF 3.5 kullanılarak oluşturulan eski uygulamaları çalıştırmak gereken senaryolar olabilir. Bu konu aynı zamanda bu işletim sistemleri için WIF 3.5 etkinleştirme hakkında yönergeler sağlar.

## <a name="changes-required-for-wif-45"></a>WIF 4.5 için gerekli değişiklikleri

Bu bölümde, bir WIF 4.5 WIF 3.5 uygulamasına geçirmek için gereken değişiklikleri açıklar.

### <a name="assembly-and-namespace-changes"></a>Derleme ve Namespace değişiklikleri

WIF 3.5 içinde WIF sınıflarının tüm içinde bulunan `Microsoft.IdentityModel` derleme (microsoft.identitymicrosoft.identitymodel.dll). Aşağıdaki derlemeler arasında WIF 4.5 içinde WIF sınıflara bölme: `mscorlib` (mscorlib.dll) `System.IdentityModel` (System.IdentityModel.dll) `System.IdentityModel.Services` (System.IdentityModel.Services.dll) ve `System.ServiceModel` (System.ServiceModel.dll ).

WIF 3.5 sınıfları tüm birinde bulunan `Microsoft.IdentityModel` ad; örneğin, `Microsoft.IdentityModel`, `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Web`ve benzeri. WIF 4.5 içinde WIF sınıfları artık arasında yayılır [System.IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları, <xref:System.Security.Claims?displayProperty=nameWithType> ad alanını ve <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanı. Bu yeniden yapılanma yanı sıra bazı WIF 3.5 sınıflar WIF 4.5 içinde bırakıldı.

Aşağıdaki tabloda bazı önemli WIF 4.5 ad alanları ve içerdikleri sınıfların türü gösterilmektedir. Daha ayrıntılı ve ad alanları, WIF 3.5 ile WIF 4.5 arasında nasıl eşleştiği hakkında ad alanları ve WIF 4.5 bırakılmış olan sınıfları hakkında bilgi için [Namespace eşleme WIF 3.5 ile WIF 4.5 arasında](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|WIF 4.5 Namespace|Açıklama|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Tanımlama bilgisi dönüşümler ve güvenlik belirteci hizmetlerine özel XML sözlük okuyucularına temsil eden sınıfları içerir. Aşağıdaki WIF 3.5 ad alanından sınıfları içerir: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`, ve `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Talepler, beyana dayalı kimlikler, talep tabanlı ilkeleri ve diğer beyana dayalı kimlik modeli yapıları temsil eden sınıfları içerir. Sınıflardan içeren `Microsoft.IdentityModel.Claims` ad alanı.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Güvenlik belirteçleri, güvenlik belirteci işleyicileri ve diğer güvenlik belirteci yapılarını temsil eden sınıfları içerir. Aşağıdaki WIF 3.5 ad alanından sınıfları içerir: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`, ve `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir. Sınıflardan içeren `Microsoft.IdentityModel.Web` ad alanı.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|WCF sözleşmeleri, Kanallar, hizmet konakları ve active (WS-Trust) senaryolarında kullanılan diğer yapıları temsil eden sınıfları, artık bu ad alanında görüntülenir. Bu sınıflar WIF 3.5 içinde bulunduğunuz `Microsoft.IdentityModel.Protocols.WSTrust` ad alanı.|

> [!IMPORTANT]
> Aşağıdaki `System.IdentityModel` WCF beyana dayalı kimlik modeli uygulayan sınıflar ad alanlarında bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. Sınıfları bu üç ad alanı üzerinde WIF tabanlı çözümler oluştururken kullanmamanız gerekir.

### <a name="changes-due-to-net-integration"></a>.NET tümleştirme nedeniyle değişiklikler

WIF artık .NET Framework'e tümleşiktir. Çoğu .NET kimlik ve asıl sınıf artık öğesinden türetilen <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>. WIF 4.5 aşağıdaki değişiklikleri sonuçları:

- Talepler, kimlik ve ilkeleri artık temsil eden WIF sınıfları var <xref:System.Security.Claims?displayProperty=nameWithType> ad alanı.

    > [!IMPORTANT]
    > <xref:System.IdentityModel.Claims?displayProperty=nameWithType> Ad alanı, WCF beyana dayalı kimlik modeli içindeki yapıları temsil eden sınıfları içerir. Bu sınıfların çoğu, WIF sınıfları aynı adlara sahip olması; Örneğin, `Claims`. Bu sınıflar WIF tabanlı çözümler oluşturma sırasında kullanmayın.

- Artık .NET kimlik ve asıl sınıf türetmek doğrudan <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>, beyana dayalı kimlikler ve ilkeleri gösterir. Bu nedenle, WIF 3.5 arabirimleri `IClaimsIdentity` ve `IClaimsPrincipal` artık gerekmeyen ve WIF 4.5 içinde kullanılabilir değil.

- Because.NET kimlik ve asıl sınıflar gibi <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> ve <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> artık türetilmesi <xref:System.Security.Claims.ClaimsIdentity> ve <xref:System.Security.Claims.ClaimsPrincipal>, talep işlevselliğini yerleşik sahiptirler. Bu nedenle, talep özgü kimlik ve asıl sınıflarını gibi `WindowsClaimsIdentity` ve `WindowsClaimsPrincipal` , WIF 3.5 mevcut artık gerekmeyen ve WIF 4.5 içinde mevcut değildir.

### <a name="other-changes-to-wif-functionality"></a>Diğer WIF işlev değişiklikleri

Ad değişiklikleri ve .NET ile tümleştirme nedeniyle değişiklikler ek olarak, aşağıdaki genel değişiklikler WIF işlevine WIF 4.5 içinde gerçekleşir.

- `Microsoft.IdentityModel.ExceptionMapper` Özel durumlar için özel SOAP hataları eşlemek etkinleştirdiğiniz işlevselliği sağlanan sınıfı kaldırılır.

- Özel durum surface büyük ölçüde azalttı.

- Birçok protokolü veya WS - tanımlanan sınıfların * belirli sabitleri kaldırıldı; Örneğin, `Microsoft.IdentityModel.WSAddressing10Constants` WS-Addressing 1.0 ilgili sabitleri tanımlanan sınıfı.

- Windows Belirteç Hizmeti (c2wts) için talep ve onun ilişkili sınıfları `Microsoft.IdentityModel.WindowsTokenService` ad alanı kaldırılır.

### <a name="wif-configuration-changes"></a>WIF yapılandırma değişiklikleri

Birçok yapılandırma dosyasındaki değişiklikleri WIF 4.5 ad alanı güncelleştirmeleri olmuş. Örneğin, aşağıdaki WIF 3.5 girişini düşünün `<httpModules>` bölüm WS-Federasyon kimlik doğrulama Yöneticisi bir uygulamaya eklemek için:

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Bu giriş WIF 4.5 içinde yeni ad alanları ve bütünleştirilmiş kod sürümü içerecek şekilde güncelleştirildi:

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

Aşağıdaki listede yapılandırma dosyasının önemli değişiklikler için WIF 4.5 numaralandırır.

- `<microsoft.identityModel>` Bölümü, artık [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) bölümü.

- `<service>` Öğedir artık [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi.

- Yeni bir bölüm [ \<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md), pasif (WS-Federation) senaryolarında davranışını denetleyen ayarları belirtmek için eklendi.

- [ \<Federationconfiguration'a >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) gelen öğeyi ve onun alt öğelerini taşındı `<service>` WIF 3.5 öğesinde yeni `<system.identityModel.services>` öğesi.

- Hizmet düzeyinde-doğrudan altında belirtilmesi çeşitli öğelerin `<service>` WIF 3.5 öğesinde altında belirtilen için sınırlı olduğu [ \<securityTokenHandlerConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğe. (Altında hala belirtilebilir [ \<identityConfiguration >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) geriye dönük uyumluluk için WIF 4.5 öğesinde.)

WIF 4.5 yapılandırma öğelerini tam bir listesi için bkz. [WIF yapılandırma şeması](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Visual Studio Araçları değişiklikleri

WIF 3.5 SDK'sı bir tek başına Federasyon yardımcı programı, sunulan kimlik yönetimi için güvenlik belirteci hizmeti (STS) WIF özelliği etkinleştirilmiş uygulamalarında dış kullanabileceğinizi FedUtil.exe (FedUtil). Bu araç, WIF ayarları bir veya daha fazla Sts'ler güvenlik belirteçleri elde etmek için uygulamaya etkinleştirmek için uygulama yapılandırma dosyasına eklenir ve Visual Studio aracılığıyla yaşanan **STS hizmet Başvurusu Ekle** düğmesi. FedUtil WIF 4.5 ile birlikte gelmez. Bunun yerine, WIF 4.5, uygulamanızın yapılandırma dosyasına dış bir sts'ye kimlik yönetimi için gereken WIF ayarları değiştirmek için kullanabileceğiniz Visual Studio 2012 için kimlik ve erişim aracı adlı yeni bir Visual Studio uzantısı destekler. Kimlik ve erişim aracı, WIF özelliği etkinleştirilmiş uygulamalarınızı test etmek için kullanabileceğiniz yerel STS olarak adlandırılan bir STS de uygular. Çoğu durumda, bu özellik genellikle WIF 3.5, geliştirme aşamasındaki çözümlerini test etmek için gerekli özel Sts'ler oluşturma gerek obviates. Bu nedenle, STS şablonları artık Visual Studio 2012'de desteklenir; Ancak, Sts'ler geliştirilmesini destekleyen sınıflar WIF 4. 5 ' yine kullanılabilir durumdadır.

Uzantılar ve güncelleştirmeler Yöneticisi'nde Visual Studio kimlik ve erişim aracı yükleyebilirsiniz veya kod Galerisi'nde şu sayfadan indirebilirsiniz: [Kimlik ve erişim aracı kod galerisindeki Visual Studio 2012 için](https://go.microsoft.com/fwlink/?LinkID=245849). Visual Studio Araçları değişiklikleri aşağıda özetlenmiştir:

- STS hizmet Başvurusu Ekle işlevselliğini kaldırılır. Bu değişiklik, kimlik ve erişim Aracı ' dir.

- Visual Studio STS şablonları kaldırılır. WIF ile geliştirdiğiniz kimlik çözümlerini test etmek için kimlik ve erişim aracı üzerinden kullanılabilir yerel STS kullanabilirsiniz. Yerel STS yapılandırma sunduğu talepleri özelleştirmek için değiştirilebilir.

- Tek başına Federasyon yardımcı programı'nı (FedUtil), WIF 4.5 içinde kullanılamaz. Yapılandırma dosyalarınızın kimlik yönetimi için bir STS'ye dış değiştirmek için kimlik ve erişim Aracı'nı kullanabilirsiniz.

Kimlik ve erişim aracı hakkında daha fazla bilgi için bkz: [kimlik ve erişim aracı Visual Studio 2012 için](../../../docs/framework/security/identity-and-access-tool-for-vs.md)

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Etkin/pasif (WS-Federation) senaryolar:

- Pasif senaryolarını destekleyen sınıflar taşındı <xref:System.IdentityModel.Services?displayProperty=nameWithType> ad alanı. Bu sınıflar WIF 3.5 içinde bulunduğunuz `Microsoft.IdentityModel.Web` ad alanı.

- Sınıflarda `Microsoft.IdentityModel.Web.Configuration` ad alanı taşındı <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>. Bu sınıfların nesneleri belirli yapılandırma pasif senaryolarda temsil etmektedir.

- `FederatedPassiveSignInControl` Artık desteklenmemektedir; tüm sınıflarda `Microsoft.IdentityModel.Web.Controls` ad alanı WIF 4.5'ten kaldırıldı.

- WS-Federasyon kimlik doğrulama Modülü (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) oturumu kapatma işlevi, WIF 3.5 farklı. WIF 4.5 içinde oturum kapatma işleminin nasıl çalıştığı hakkında daha fazla ayrıntı için bkz. <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> sınıf konusuna.

### <a name="active-wcfws-trust-scenarios"></a>Etkin (WCF/WS-Trust) senaryolar:

- `Microsoft.IdentityModel.Protocols.WSTrust` Ad alanı, WIF 4.5 içinde iki ad alanı içine ağırlıklı olarak bölündü. WS-Trust protokolü için belirli yapıları temsil eden sınıfları artık bulunduğunuz <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>. Bu sınıflar gibi içerir <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>. Hizmet sözleşmeleri, Kanallar, hizmet konakları ve WS-Trust WCF uygulamaları kullanarak söz konusu olan diğer yapıları temsil eden sınıfları taşındı <xref:System.ServiceModel.Security?displayProperty=nameWithType>; Örneğin, <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> arabirimi.

- WIF kullanarak bir WCF uygulaması yapılandırma önemli ölçüde basitleştirilmiştir. Daha önce `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` davranışı uzantısı olarak eklenmiş gerekiyordu ve bu işlevselliği belirterek hizmet davranışı WIF Sürgülü için kullanılan bir `<federatedServiceHostConfiguration>` öğesi. WIF 4.5, WCF ile daha sıkı bir şekilde tümleştirilmiştir. Belirterek bir WCF Hizmeti WIF etkinleştirme artık `useIdentityConfiguration` özniteliği `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` öğesi aşağıdaki XML'de olduğu gibi:

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- WIF 4.5 hizmet üzerinde hizmet konağı bir etkin (WCF) hizmeti tarafından kullanılan sertifikanın belirtilmesi gerekir. Yapılandırmada üzerinden bunu yapabilirsiniz `<system.serviceModel>` / `<behaviors>` / `<serviceBehaviors>` / `<serviceCredentials>` / `<serviceCertificate>` önceki örnekte gösterilen şekilde öğesi. WIF 3.5 ile hizmet sertifikası belirtilebilir `<serviceCertificate>` WIF alt öğesi `<service>` öğesi. Bu işlev, WIF 4.5 içinde yok; belirtin `<serviceCertificate>` öğesi altında `<serviceCredentials>` öğe yerine.

- WIF 3.5 WCF artık Sürgülü için kullanılan sınıflar mevcut. Bu, aşağıdaki sınıfları içerir `Microsoft.IdentityModel.Tokens` ad alanı: `FederatedSecurityTokenManager`, `FederatedServiceCredentials`, ve `IdentityModelServiceAuthorizationManager`, hem de `Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` sınıfı.

## <a name="enabling-wif-35-in-windows-8"></a>WIF 3.5 Windows 8'de etkinleştirme

WIF 4.5, .NET 4.5 parçası olduğundan, Windows 8 ve Windows Server 2012 çalıştıran bilgisayarlarda otomatik olarak etkinleştirilir ve WIF 4.5 kullanılarak oluşturulan uygulamalar varsayılan olarak Windows 8 veya Windows Server 2012 altında çalışacaktır. Ancak, Windows 8 veya Windows Server 2012 çalıştıran bir bilgisayarda WIF 3.5 kullanılarak oluşturulan uygulamalar çalıştırmanız gerekebilir. Bu durumda, hedef bilgisayarda WIF 3.5 etkinleştirmeniz gerekir. Windows 8 çalıştıran bir bilgisayarda, Dağıtım Görüntüsü Bakımı ve Yönetimi (DISM) aracını kullanarak bunu yapabilirsiniz. Windows Server 2012 çalıştıran bir bilgisayarda, DISM aracını kullanabilirsiniz veya Windows PowerShell kullanabilirsiniz `Add-WindowsFeature` cmdlet'i. Komut satırında veya uygun komutları her iki durumda da çağrılabilir Windows PowerShell ortamında.

Aşağıdaki komutlar komut satırından veya gelen DISM aracının nasıl kullanılacağını göstermektedir. Windows PowerShell ortamında. Varsayılan olarak, DISM PowerShell modülü, Windows 8 ve Windows Server 2012'de bulunur ve içeri aktarılması gerekmez. İle Windows PowerShell DISM kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell DISM kullanmak için nasıl](https://go.microsoft.com/fwlink/?LinkId=254419).

WIF 3.5 DISM kullanarak etkinleştirmek için:

```console
dism /online /enable-feature:windows-identity-foundation
```

WIF 3.5 DISM kullanarak devre dışı bırakmak için:

```console
dism /online /disable-feature:windows-identity-foundation
```

Hangi özelliklerin etkin veya DISM kullanarak devre dışı denetlemek için:

```console
dism /online /get-features
```

Alternatif olarak, Windows Server 2012 çalıştıran bilgisayarlarda, WIF 3.5 için Windows PowerShell kullanarak etkinleştirebilirsiniz `Add-WindowsFeature` cmdlet'i. Komut satırından Bunu yapmak için aşağıdaki komutu girebilirsiniz:

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 Windows PowerShell ortamın içinde komut doğrudan girebilirsiniz:

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> Birlikte WIF 3.5 ile WIF 4.5 hem kullanırken sınıflar WIF 3.5 ile WIF 4.5 birçoğu aynı adı paylaştığından, tam nitelikli sınıf adları kullanabilir veya sınıflar WIF 3.5 ile WIF 4.5 arasında ayrım yapmak için ad alanı diğer adlarını kullanma emin olun.

## <a name="see-also"></a>Ayrıca bkz.

- [WIF Yapılandırma Şeması](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/index.md)
- [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](../../../docs/framework/security/namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Windows Identity Foundation 4.5'teki Yenilikler](../../../docs/framework/security/whats-new-in-wif.md)
- [Visual Studio 2012 için Kimlik ve Erişim Aracı](../../../docs/framework/security/identity-and-access-tool-for-vs.md)
