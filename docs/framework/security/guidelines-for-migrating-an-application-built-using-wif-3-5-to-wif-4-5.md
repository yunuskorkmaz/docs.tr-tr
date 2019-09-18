---
title: WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri
ms.date: 03/30/2017
ms.assetid: 7a32fe6e-5f68-4693-9371-19411fa8063c
author: BrucePerlerMS
ms.openlocfilehash: 3ba99a061d060ebe7740fe61846c3684b5c3085d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045481"
---
# <a name="guidelines-for-migrating-an-application-built-using-wif-35-to-wif-45"></a>WIF 3.5 Kullanılarak Derlenmiş bir Uygulamayı WIF 4.5’e Geçirme Yönergeleri

## <a name="applies-to"></a>Uygulanan Öğe

- Microsoft® Windows® Identity Foundation (WıF) 3,5 ve 4,5.

## <a name="overview"></a>Genel Bakış

Windows Identity Foundation (WıF), ilk olarak .NET 3,5 SP1 zaman diliminde yayımlanmıştır. Bu WıF sürümü, WıF 3,5 olarak adlandırılır. Ayrı bir çalışma zamanı ve SDK olarak yayımlanmıştır. Bu, WıF özellikli bir uygulamanın çalıştırıldığı her bilgisayarın WıF çalışma zamanının yüklü olması ve geliştiricilerin, etkin olan Visual Studio şablonlarını ve araçları almak için WıF SDK 'sını indirmesi ve yüklemesi gerekiyordu WıF özellikli uygulamalar geliştirme. .NET 4,5 ile başlayarak WıF, .NET Framework ile tamamen tümleşiktir. Ayrı bir çalışma zamanına artık gerek yoktur ve Visual Studio uzantıları Yöneticisi kullanılarak Visual Studio 2012 ' de WıF araçları yüklenebilirler. Bu WıF sürümü, WıF 4,5 olarak adlandırılır.

WıF 'in .NET ' e tümleştirmesi, WıF API yüzeyinde birkaç değişikliği ortaya çıkarır. WıF 4,5 yeni ad alanları, yapılandırma öğelerinde yapılan bazı değişiklikler ve Visual Studio için yeni araç içerir. Bu konuda, WıF 3,5 kullanılarak oluşturulan uygulamaları WıF 4,5 ' e geçirmenize yardımcı olması için kullanabileceğiniz rehberlik sunulmaktadır. Windows 8 veya Windows Server 2012 çalıştıran bilgisayarlarda WıF 3,5 kullanılarak oluşturulan eski uygulamaları çalıştırmanız gereken senaryolar olabilir. Bu konu ayrıca, bu işletim sistemleri için WıF 3,5 ' i etkinleştirme hakkında rehberlik sağlar.

## <a name="changes-required-for-wif-45"></a>WıF 4,5 için gereken değişiklikler

Bu bölümde bir WıF 3,5 uygulamasını WıF 4,5 ' ye geçirmek için gereken değişiklikler açıklanmaktadır.

### <a name="assembly-and-namespace-changes"></a>Derleme ve ad alanı değişiklikleri

WIF 3,5 ' de, tüm WIF sınıfları `Microsoft.IdentityModel` derlemede yer alır (Microsoft. ıdentitymicrosoft. IdentityModel. dll). WIF 4,5 ' de `mscorlib` , WIF sınıfları şu derlemeler arasında bölünür: (mscorlib. dll), `System.IdentityModel` (System. IdentityModel. dll), `System.IdentityModel.Services` (System. IdentityModel. Services. dll) ve `System.ServiceModel` (System. ServiceModel. dll ).

WIF `Microsoft.IdentityModel` 3,5 sınıflarının hepsi ad alanlarından birinde içerilir; `Microsoft.IdentityModel`örneğin `Microsoft.IdentityModel.Tokens` `Microsoft.IdentityModel.Web`,,, vb. WIF 4,5 ' de WIF sınıfları artık [System. IdentityModel](https://go.microsoft.com/fwlink/?LinkId=272004) ad alanları, <xref:System.Security.Claims?displayProperty=nameWithType> <xref:System.ServiceModel.Security?displayProperty=nameWithType> ad alanı ve ad alanına yayılırlar. Bu yeniden kuruluşa ek olarak, bazı WıF 3,5 sınıfları WıF 4,5 ' de bırakılmıştı.

Aşağıdaki tabloda daha fazla önemli WıF 4,5 ad alanı ve içerdikleri sınıf türleri gösterilmektedir. Ad alanlarının WıF 3,5 ile WıF 4,5 arasında nasıl eşlendiğini ve WıF 4,5 ' de bırakılan ad alanları ve sınıflar hakkında daha ayrıntılı bilgi için bkz. [wıf 3,5 Ile wıf 4,5 arasında ad alanı eşlemesi](namespace-mapping-between-wif-3-5-and-wif-4-5.md).

|WıF 4,5 ad alanı|Açıklama|
|-----------------------|-----------------|
|<xref:System.IdentityModel?displayProperty=nameWithType>|Tanımlama bilgisi dönüştürmeleri, güvenlik belirteci Hizmetleri ve özelleşmiş XML sözlüğü okuyucuları temsil eden sınıflar içerir. Şu WIF 3,5 ad alanlarından sınıfları içerir: `Microsoft.IdentityModel`, `Microsoft.IdentityModel.SecurityTokenService`ve `Microsoft.IdentityModel.Threading`.|
|<xref:System.Security.Claims?displayProperty=nameWithType>|Talepleri, talep tabanlı kimlikleri, talep tabanlı sorumluları ve diğer talebe dayalı kimlik modeli yapılarını temsil eden sınıflar içerir. `Microsoft.IdentityModel.Claims` Ad alanından sınıfları içerir.|
|<xref:System.IdentityModel.Tokens?displayProperty=nameWithType>|Güvenlik belirteçlerini, güvenlik belirteci işleyicilerini ve diğer güvenlik belirteci yapıtlarını temsil eden sınıflar içerir. Şu WIF 3,5 ad alanlarından sınıfları içerir: `Microsoft.IdentityModel.Tokens`, `Microsoft.IdentityModel.Tokens.Saml11`ve `Microsoft.IdentityModel.Tokens.Saml2`.|
|<xref:System.IdentityModel.Services?displayProperty=nameWithType>|Pasif (WS-Federation) senaryolarında kullanılan sınıfları içerir. `Microsoft.IdentityModel.Web` Ad alanından sınıfları içerir.|
|<xref:System.ServiceModel.Security?displayProperty=nameWithType>|WCF sözleşmelerini, kanalları, hizmet ana bilgisayarlarını ve etkin (WS-Trust) senaryolarında kullanılan diğer yapıtları temsil eden sınıflar artık bu ad alanında yer alır. WIF 3,5 ' de, bu sınıflar `Microsoft.IdentityModel.Protocols.WSTrust` ad alanında yer alan.|

> [!IMPORTANT]
> Aşağıdaki `System.IdentityModel` ad alanlarında, WCF talep tabanlı kimlik modelini uygulayan sınıflar bulunur: <xref:System.IdentityModel.Claims?displayProperty=nameWithType>, <xref:System.IdentityModel.Policy?displayProperty=nameWithType>, ve <xref:System.IdentityModel.Selectors?displayProperty=nameWithType>. WCF beyana dayalı kimlik modelinin yerini WIF almıştır. WıF tabanlı çözümler oluştururken bu üç ad alanında sınıfları kullanmamalısınız.

### <a name="changes-due-to-net-integration"></a>.NET tümleştirmesi nedeniyle değişiklikler

WıF artık .NET Framework tümleşiktir. Çoğu .net kimliği ve asıl sınıf artık ve ' <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>den türetilir. WıF 4,5 ' de aşağıdaki değişiklikler oluşur:

- Artık talepler, kimlikler ve sorumlularını temsil eden WIF sınıfları <xref:System.Security.Claims?displayProperty=nameWithType> ad alanında mevcuttur.

    > [!IMPORTANT]
    > Ad <xref:System.IdentityModel.Claims?displayProperty=nameWithType> alanı, WCF talep tabanlı kimlik modelindeki yapıtları temsil eden sınıflar içerir. Bu sınıfların birçoğu WıF sınıflarıyla aynı ada sahiptir; Örneğin, `Claims`. WıF tabanlı çözümler oluştururken bu sınıfları kullanmayın.

- .Net kimliği ve asıl sınıflar artık, talep tabanlı <xref:System.Security.Claims.ClaimsIdentity?displayProperty=nameWithType> kimlikleri <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=nameWithType>ve sorumlularını temsil eden ve ' den doğrudan türetilir. Bu nedenle, WIF 3,5 arabirimleri `IClaimsIdentity` ve `IClaimsPrincipal` artık gerekli değildir ve WIF 4,5 ' de kullanılamaz.

- Ve gibi because.NET Identity ve Principal sınıfları <xref:System.Security.Principal.WindowsIdentity?displayProperty=nameWithType> <xref:System.Security.Principal.WindowsPrincipal?displayProperty=nameWithType> , <xref:System.Security.Claims.ClaimsIdentity> ve <xref:System.Security.Claims.ClaimsPrincipal>' de türetilmiş talepler işlevselliğine sahiptir. Bu nedenle, 3,5 `WindowsClaimsIdentity` ve `WindowsClaimsPrincipal` gibi talebe özgü kimlik ve asıl sınıflar artık gerekli değildir ve WIF 4,5 ' de mevcut değildir.

### <a name="other-changes-to-wif-functionality"></a>WıF Işlevlerine yapılan diğer değişiklikler

.NET ile tümleştirme nedeniyle ad alanı değişikliklerine ve değişikliklere ek olarak, WIF 4,5 ' de WıF işlevselliği için aşağıdaki genel değişiklikler yapılır.

- Belirli SOAP hatalarına özel durumlar eşlemenize olanak tanıyan işlevselliği sağlayan sınıfıkaldırılır.`Microsoft.IdentityModel.ExceptionMapper`

- Özel durum yüzeyi büyük ölçüde azalır.

- Protokol veya WS-* ' n i n Özel sabitler tarafından tanımlanan sınıfların birçoğu kaldırılmıştır; Örneğin, `Microsoft.IdentityModel.WSAddressing10Constants` ws-Addressing 1,0 ile ilgili sabitleri tanımlayan sınıf.

- Windows belirteç hizmeti (c2wts) talepleri ve `Microsoft.IdentityModel.WindowsTokenService` ad alanındaki ilişkili sınıfları kaldırılır.

### <a name="wif-configuration-changes"></a>WıF yapılandırma değişiklikleri

Yapılandırma dosyasındaki değişikliklerin birçoğu WıF 4,5 ' deki ad alanı güncelleştirmelerinden kaynaklanır. Örneğin, bir uygulamaya WS-Federation Authentication Manager eklemek için `<httpModules>` bölümünde aşağıdaki WIF 3,5 girişini göz önünde bulundurun:

```xml
<add name="WSFederationAuthenticationModule" type="Microsoft.IdentityModel.Web.WSFederationAuthenticationModule, Microsoft.IdentityModel, Version=3.5.0.0, Culture=neutral, PublicKeyToken=abcd … 5678" />
```

Bu giriş, yeni ad alanlarını ve derleme sürümünü eklemek için WıF 4,5 ' de güncelleştirilmiştir:

```xml
<add name="WSFederationAuthenticationModule" type="System.IdentityModel.Services.WSFederationAuthenticationModule, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=abcd … 5678"/>
```

Aşağıdaki listede, WıF 4,5 yapılandırma dosyasında yapılan büyük değişiklikler numaralandırılır.

- Artık System. IdentityModel > bölümdür. [ \<](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) `<microsoft.identityModel>`

- Öğesi artık IdentityConfiguration > öğesidir. [ \<](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) `<service>`

- Pasif (WS-Federation) senaryolarında davranışı denetleyen ayarları belirtmek için, [ \<System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)yeni bir bölüm eklenmiştir.

- `<service>` `<system.identityModel.services>` [ FederationConfiguration>öğesiveonunaltöğeleri,WIF\<](../configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 3,5 ' deki öğeden yeni öğeye taşınmıştır.

- WIF 3,5 ' deki `<service>` öğe kapsamında doğrudan hizmet düzeyinde belirtilebileceğiniz birkaç öğe, [ \<SecurityTokenHandlerConfiguration >](../configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) öğesi altında belirtilme sınırlandırılmıştır. (Geriye dönük uyumluluk için WIF 4,5 ' de [ \<IdentityConfiguration >](../configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) öğesi altında yine de belirtilebilir.)

WıF 4,5 yapılandırma öğelerinin tüm listesi için bkz. [WIF yapılandırma şeması](../configure-apps/file-schema/windows-identity-foundation/index.md).

### <a name="visual-studio-tooling-changes"></a>Visual Studio Araçları değişiklikleri

WıF 3,5 SDK 'Sı, WıF özellikli uygulamalarda kimlik yönetimi 'ni bir güvenlik belirteci hizmeti 'ne (STS) aktarmak için kullanabileceğiniz bir tek başına Federasyon yardımcı programı olan FedUtil. exe (FedUtil) önerdi. Bu araç, uygulamanın bir veya daha fazla STSs 'den güvenlik belirteçleri almasını sağlamak için uygulama yapılandırma dosyasına WıF ayarları ekledi ve **STS hizmeti başvurusu Ekle** düğmesi aracılığıyla Visual Studio 'da ortaya çıkmış. FedUtil, WıF 4,5 ile birlikte gelmez. Bunun yerine, WıF 4,5, Visual Studio 2012 için kimlik ve erişim aracı adlı yeni bir Visual Studio uzantısını destekler. böylece, kimlik yönetiminin bir STS 'ye dış kaynak atamak için gereken WıF ayarlarıyla uygulamanızın yapılandırma dosyasını değiştirebilirsiniz. Kimlik ve erişim aracı, WıF özellikli uygulamalarınızı test etmek için kullanabileceğiniz yerel STS adlı bir STS de uygular. Çoğu durumda, bu özellik geliştirme kapsamındaki çözümleri test etmek için WıF 3,5 ' de genellikle gerekli olan özel STSs 'leri oluşturma ihtiyacını obviates. Bu nedenle, STS şablonları artık Visual Studio 2012 ' de desteklenmemektedir; Ancak, STSs geliştirmeyi destekleyen sınıflar WıF 4,5 ' de yine de kullanılabilir.

Kimlik ve erişim aracını Visual Studio 'daki Uzantılar ve güncelleştirmeler yöneticisinden yükleyebilir veya kod galerisindeki aşağıdaki sayfadan indirebilirsiniz: [Kod galerisinde Visual Studio 2012 Için kimlik ve erişim aracı](https://go.microsoft.com/fwlink/?LinkID=245849). Visual Studio araç değişiklikleri aşağıdaki listede özetlenmiştir:

- STS hizmeti başvurusu Ekle işlevi kaldırılır. Değişiklik, kimlik ve erişim aracıdır.

- Visual Studio STS şablonları kaldırılır. WıF ile geliştirdiğiniz kimlik çözümlerini test etmek için kimlik ve erişim aracı aracılığıyla kullanılabilen yerel STS 'yi kullanabilirsiniz. Yerel STS yapılandırması, hizmet verdiği talepleri özelleştirmek için değiştirilebilir.

- Tek başına Federasyon yardımcı programı (FedUtil), WıF 4,5 ' de kullanılamaz. Yapılandırma dosyalarınızı bir STS 'ye dış kimlik yönetimi ile değiştirmek için kimlik ve erişim aracını kullanabilirsiniz.

Kimlik ve erişim aracı hakkında daha fazla bilgi için bkz. [Visual Studio Için kimlik ve erişim aracı 2012](identity-and-access-tool-for-vs.md)

<a name="BKMK_ToolingChanges"></a>

### <a name="passive-ws-federation-scenarios"></a>Pasif (WS-Federation) senaryoları:

- Pasif senaryoları destekleyen sınıflar <xref:System.IdentityModel.Services?displayProperty=nameWithType> ad alanına taşınmıştır. WIF 3,5 ' de bu sınıflar `Microsoft.IdentityModel.Web` ad alanında vardı.

- `Microsoft.IdentityModel.Web.Configuration` Ad alanındaki sınıflar öğesine <xref:System.IdentityModel.Services.Configuration?displayProperty=nameWithType>taşındı. Bu sınıflar, pasif senaryolarda yapılandırmaya özgü nesneleri temsil eder.

- Artık desteklenmiyor; `Microsoft.IdentityModel.Web.Controls` ad alanındaki tüm sınıflar WIF 4,5 ' den kaldırılmıştır. `FederatedPassiveSignInControl`

- WS-Federasyon kimlik doğrulama modülü (<xref:System.IdentityModel.Services.WSFederationAuthenticationModule>) oturum kapatma işlevselliği WIF 3,5 ' den farklıdır. Kaydolma işlevinin WIF 4,5 ' de nasıl çalıştığı hakkında daha fazla bilgi için bkz <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> . sınıf konusu.

### <a name="active-wcfws-trust-scenarios"></a>Etkin (WCF/WS-Trust) senaryolar:

- Ad `Microsoft.IdentityModel.Protocols.WSTrust` alanı, temel olarak WIF 4,5 ' de iki ad alanına bölünür. WS-Trust protokolüne özgü yapıtları temsil eden sınıflar artık ' de <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=nameWithType>bulunur. Buna benzer <xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken>sınıflar dahildir. WCF uygulamalarında <xref:System.ServiceModel.Security?displayProperty=nameWithType>WS-Trust kullanımı ile ilgili hizmet sözleşmelerini, kanalları, hizmet ana bilgisayarlarını ve diğer yapıtları temsil eden sınıflar,. Örneğin <xref:System.ServiceModel.Security.IWSTrust13AsyncContract> , arabirim.

- Bir WCF uygulamasını WıF 'yi kullanacak şekilde yapılandırmak büyük ölçüde basitleştirilmiştir. Daha önce bir davranış uzantısı olarak eklenmesi `<federatedServiceHostConfiguration>` gerekiyorduvebuişlevdahasonrabiröğesibelirtilerekhizmetdavranışındayeralmakiçinkullanılır.`Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` WıF 4,5, WCF ile daha sıkı bir şekilde tümleşiktir. Artık `useIdentityConfiguration` aşağıdaki XML 'de olduğu gibi, `<behaviors>` / `<system.serviceModel>` öğesindeözniteliğini/ belirterek bir WCF hizmetinde WIF 'yi etkinleştirirsiniz: `<serviceBehaviors>` / `<serviceCredentials>`

    ```xml
    <serviceCredentials useIdentityConfiguration="true">
        <!--Certificate added by Identity And Access VS Package.  Subject='CN=localhost', Issuer='CN=localhost'. Make sure you have this certificate installed. The Identity and Access tool does not install this certificate.-->
        <serviceCertificate findValue="CN=localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectDistinguishedName" />
    </serviceCredentials>
    ```

- WıF 4,5 ' de, hizmet ana bilgisayarında etkin bir (WCF) hizmeti tarafından kullanılan hizmet sertifikasının belirtilmesi gerekir. Yapılandırma bölümünde, `<system.serviceModel>` bunu Yukarıdaki örnekte gösterildiği gibi `<serviceBehaviors>` / / öğesi`<serviceCertificate>` aracılığıyla `<behaviors>` / `<serviceCredentials>` yapabilirsiniz. / WIF 3,5 ' de, hizmet sertifikası WIF `<serviceCertificate>` `<service>` öğesinin alt öğesi aracılığıyla belirtilebilir. Bu işlevsellik WıF 4,5 içinde yok; Bunun yerine öğesi `<serviceCredentials>` altında öğesinibelirtin.`<serviceCertificate>`

- WıF 3,5 ' i WCF 'ye bölmek için kullanılan sınıflar artık yok. Bu,, ve `Microsoft.IdentityModel.Tokens` `FederatedServiceCredentials` `FederatedSecurityTokenManager` gibiad`Microsoft.IdentityModel.Configuration.ConfigureServiceHostBehaviorExtensionElement` alanında aşağıdaki sınıfları içerir. `IdentityModelServiceAuthorizationManager`

## <a name="enabling-wif-35-in-windows-8"></a>Windows 8 ' de WıF 3,5 etkinleştiriliyor

WıF 4,5, .NET 4,5 ' nin bir parçası olduğundan, Windows 8 ve Windows Server 2012 çalıştıran bilgisayarlarda otomatik olarak etkinleştirilir ve varsayılan olarak Windows 8 veya Windows Server 2012 altında, 4,5 kullanılarak oluşturulan uygulamalar bu şekilde çalışır. Ancak, Windows 8 veya Windows Server 2012 çalıştıran bir bilgisayarda WıF 3,5 kullanılarak oluşturulan uygulamaları çalıştırmanız gerekebilir. Bu durumda, hedef bilgisayarda WıF 3,5 ' i etkinleştirmeniz gerekir. Windows 8 çalıştıran bir bilgisayarda, Dağıtım Görüntüsü Bakımı ve yönetimi (DıSM) aracını kullanarak bunu yapabilirsiniz. Windows Server 2012 çalıştıran bir bilgisayarda, DISM aracını kullanabilir veya Windows PowerShell `Add-WindowsFeature` cmdlet 'ini kullanabilirsiniz. Her iki durumda da, uygun komutlar komut satırında veya Windows PowerShell ortamının içinden çağrılabilir.

Aşağıdaki komutlarda, komut satırından veya Windows PowerShell ortamının içinden DıSM aracının nasıl kullanılacağı gösterilmektedir. Varsayılan olarak, DıSM PowerShell modülü Windows 8 ve Windows Server 2012 ' ye dahildir ve içeri aktarılması gerekmez. DıSM 'yi Windows PowerShell ile kullanma hakkında daha fazla bilgi için bkz. [Windows PowerShell 'de DISM kullanma](https://go.microsoft.com/fwlink/?LinkId=254419).

DıSM kullanarak WıF 3,5 ' i etkinleştirmek için:

```console
dism /online /enable-feature:windows-identity-foundation
```

DıSM kullanarak WıF 3,5 'yi devre dışı bırakmak için:

```console
dism /online /disable-feature:windows-identity-foundation
```

DıSM kullanarak hangi özelliklerin etkinleştirildiğini veya devre dışı bırakıldığını denetlemek için:

```console
dism /online /get-features
```

Alternatif olarak, Windows Server 2012 çalıştıran bilgisayarlarda, Windows PowerShell `Add-WindowsFeature` cmdlet 'ini kullanarak WIF 3,5 ' yi etkinleştirebilirsiniz. Bunu komut satırından yapmak için aşağıdaki komutu girebilirsiniz:

```console
powershell "add-windowsfeature windows-identity-foundation"
```

 Windows PowerShell ortamının içinden komutu doğrudan girebilirsiniz:

```powershell
Add-WindowsFeature windows-identity-foundation
```

> [!NOTE]
> WıF 3,5 ve WıF 4,5 ' deki sınıfların birçoğu aynı adları paylaşıyorsa, hem WıF 3,5 hem de WıF 4,5 birlikte kullanıldığında, tam sınıf adlarını kullandığınızdan emin olun veya WıF 3,5 ve WıF 4,5 içindeki sınıfları ayırt etmek için ad alanı diğer adlarını kullanın.

## <a name="see-also"></a>Ayrıca bkz.

- [WIF Yapılandırma Şeması](../configure-apps/file-schema/windows-identity-foundation/index.md)
- [WIF 3.5 ile WIF 4.5 Arasında Ad Alanı Eşleme](namespace-mapping-between-wif-3-5-and-wif-4-5.md)
- [Windows Identity Foundation 4.5'teki Yenilikler](whats-new-in-wif.md)
- [Visual Studio 2012 için Kimlik ve Erişim Aracı](identity-and-access-tool-for-vs.md)
