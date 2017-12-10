---
title: .NET Framework'teki yenilikler
ms.custom: updateeachrelease
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2c8c7f8c4d4c7c882f4f295b13fa4add3a11582f
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="whats-new-in-the-net-framework"></a>.NET Framework'teki yenilikler
<a name="introduction"></a>Bu makalede, anahtar yeni özellikler ve geliştirmeler .NET Framework'ün aşağıdaki sürümlerinde özetlenmektedir:  
 
[.NET framework 4.7.1](#v471)    
[.NET framework 4.7](#v47)   
[.NET framework 4.6.2](#v462)   
[.NET framework 4.6.1](#v461)   
[.NET 2015 ve .NET Framework 4.6](#v46)   
[.NET framework 4.5.2](#v452)   
[.NET framework 4.5.1](#v451)   
[.NET framework 4.5](#core)   

Bu makale, her yeni özellik hakkında kapsamlı bilgi sağlamaz ve değiştirilebilir. .NET Framework hakkında genel bilgi için bkz: [Başlarken](../../../docs/framework/get-started/index.md). Desteklenen platformlar için bkz: [sistem gereksinimleri](~/docs/framework/get-started/system-requirements.md). Yükleme bağlantıları ve yükleme yönergeleri için bkz: [Yükleme Kılavuzu](../../../docs/framework/install/guide-for-developers.md).

> [!NOTE]
> .NET Framework takım platform desteği'ni genişletin ve değişmez koleksiyonlar ve SIMD etkin vektör türleri gibi yeni işlevsellik tanıtmak için NuGet ile bant dışı özellikler de serbest bırakır. Daha fazla bilgi için bkz: [ek sınıf kitaplıkları ve API'leri](../additional-apis/index.md) ve [.NET Framework ve bant dışı sürümler](~/docs/framework/get-started/the-net-framework-and-out-of-band-releases.md). Bkz: bir [NuGet paketlerini tam listesi](https://blogs.msdn.microsoft.com/dotnet/p/nugetpackages/) .NET Framework veya abone olmak [bizim akış](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/).

<a name="v471"></a> 
## <a name="introducing-the-net-framework-471"></a>.NET Framework 4.7.1 Tanıtımı

.NET Framework 4.7.1 birçok yeni düzeltmeler ve birçok yeni özellik çok kararlı bir ürün kalan sırasında ekleyerek .NET Framework 4.6, 4.6.1, 4.6.2 ve 4.7 oluşturur.

### <a name="downloading-and-installing-the-net-framework-471"></a>.NET Framework 4.7.1 yükleyip
 
.NET Framework 4.7.1 aşağıdaki konumlardan yükleyebilirsiniz:

- [.NET framework 4.7.1 Web yükleyicisi](http://go.microsoft.com/fwlink/?LinkId=852095)

- [NET Framework 4.7.1 çevrimdışı yükleyici](http://go.microsoft.com/fwlink/?LinkId=852107)

.NET Framework 4.7.1 Windows 10, Windows 8.1, Windows 7 SP1 ve Windows Server 2008 R2 SP1 ile başlayarak karşılık gelen sunucu platformları yüklenebilir. .NET Framework 4.7.1 web yükleyicisi veya çevrimdışı yükleyici kullanarak yükleyebilirsiniz. Çoğu kullanıcı için önerilen yol, web yükleyicisi kullanmaktır.

.NET Framework 4.7.1 Visual Studio 2012'de veya yükleyerek daha sonra hedef [4.7.1 .NET Framework Geliştirici paketi](http://go.microsoft.com/fwlink/?LinkId=852105). 

### <a name="whats-new-in-the-net-framework-471"></a>.NET Framework 4.7.1 yenilikler

.NET Framework 4.7.1 aşağıdaki alanlarda yeni özellikler içerir:
 
- [Çekirdek](#core471)
- [Ortak dil çalışma zamanı (CLR)](#clr)
- [Ağ oluşturma](#net471)
- [ASP.NET](#asp-net471) 

Ayrıca, .NET Framework 4.7.1 ana odakta yardımcı teknoloji kullanıcılar için uygun bir deneyim sağlamak üzere bir uygulamanın sağlayan iyileştirilmiş Erişilebilirlik ' dir. .NET Framework'teki 4.7.1 erişilebilirlik geliştirmeleri hakkında daha fazla bilgi için bkz: [erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md). 

<a name="core471" />
#### <a name="core"></a>Çekirdek

**.NET standart 2.0 desteği**

[.NET standart](~/docs/standard/net-standard.md) bir dizi standart bu sürümünü destekleyen her .NET uygulama kullanılabilir olmalıdır API tanımlar. .NET Framework 4.7.1 tam olarak .NET standart 2.0 destekler ve ekler [yaklaşık 200 API'leri](https://github.com/dotnet/standard/blob/master/netstandard/src/ApiCompatBaseline.net461.txt) .NET standart 2.0 içinde tanımlanır ve .NET Framework 4.6.1, 4.6.2 ve 4.7'eksik. (Yalnızca ek .NET standart destek dosyalarını da hedef sistemde dağıtıldıysa .NET Framework'ün bu sürümleri .NET standart 2.0 desteklediğini unutmayın.) Daha fazla bilgi için bkz: "BCL – .NET standart 2.0 desteği" [4.7.1 .NET Framework çalışma zamanının ve derleyici özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blog postası.

**Yapılandırma oluşturucular için destek**

Yapılandırma oluşturucular ekleme ve uygulamalar için yapılandırma ayarlarını çalışma zamanında dinamik olarak oluşturmak geliştiriciler izin verin. Özel yapılandırma Oluşturucular, yapılandırma bölümünde var olan verileri değiştirebilir veya tamamen sıfırdan yapılandırma bölümü oluşturmak için kullanılabilir. Yapılandırma oluşturucular olmadan .config dosyaları statik ve ayarlarını bir uygulama başlatılmadan önce biraz zaman tanımlanır.

Özel yapılandırma Oluşturucu oluşturmak için sizin Oluşturucu Özet türetilen <xref:System.Configuration.ConfigurationBuilder> sınıfı ve geçersiz kılma kendi <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> ve <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>. Ayrıca, Oluşturucular .config dosyanızda tanımlayın. Daha fazla bilgi için "Yapılandırma oluşturucular" bölümüne bakın [.NET Framework 4.7.1 ASP.NET ve yapılandırma özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blog postası. 

**Çalışma zamanı özelliği algılama**

<xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=fullName> Sınıfı bir mekanizma sağlar önceden tanımlanmış bir özellik belirli bir .NET uygulama derleme zamanında ya da çalışma zamanında desteklenip desteklenmediğini belirlemek için. Derleme zamanında bir derleyici belirtilen alan özellik desteklenip desteklenmediğini belirlemek için mevcut olup olmadığını kontrol edebilirsiniz; Öyleyse, bu özellik yararlanan kod yayma. Çalışma zamanında uygulama çağırabilirsiniz <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> çalışma zamanında kod yayma önce yöntemi. Daha fazla bilgi için bkz: [çalışma zamanı tarafından desteklenen özellikler açıklamak için yardımcı yöntemi ekleyin](https://github.com/dotnet/corefx/issues/17116).

**Tuple türlerin seri hale getirilebilir**

4.7.1, .NET Framework ile başlayan <xref:System.ValueTuple?displayProperty=fullName> ve onun ilişkili genel türleri olarak işaretlenmiş [Serializable](xref:System.SerializableAttribute), ikili seri hale getirme izin verir. Bu geçirme tanımlama grubu türleri gibi olmalısınız <xref:System.Tuple%603> ve <xref:System.Tuple%604>, değer tanımlama grubu türlerine daha kolay. Daha fazla bilgi için "Derleyici--ValueTuple olduğundan seri hale getirilebilir" bölümüne bakın [4.7.1 .NET Framework çalışma zamanının ve derleyici özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blog postası.

**Salt okunur başvurular için destek**

.NET Framework 4.7.1 ekler <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=fullName>. Bu öznitelik dil derleyicileri tarafından salt okunur ref dönüş türleri veya parametreleri sahip üyeler işaretlemek için kullanılır. Daha fazla bilgi için bkz: "Derleyici--desteği için ReadOnlyReferences" [4.7.1 .NET Framework çalışma zamanının ve derleyici özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features) blog postası. Ref dönüş değerleri hakkında daha fazla bilgi için bkz: [Ref Yereller (C# Kılavuzu) dönüş değerleri ve ref](~/docs/csharp/programming-guide/classes-and-structs/ref-returns.md) ve [Ref dönüş değerleri (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).

<a name="clr" />
#### <a name="common-language-runtime-clr"></a>Ortak dil çalışma zamanı (CLR)

**Çöp toplama performans iyileştirmeleri**

Çöp toplama (GC) .NET Framework 4.7.1 yapılan değişiklikler özellikle büyük nesne yığın (LOH) ayırmaları için genel performansı iyileştirir. .NET Framework 4.7.1'da, arka plan GC (BGC) SOH yerleştirmez ortaya çıkması LOH ayırmaları sağlayan küçük nesne yığın (SOH) ve LOH ayırmalarının ayrı kilitleri kullanılır. Sonuç olarak, çok sayıda LOH ayırmaları uygulamalar ayırma kilit çakışması ve iyileştirilmiş performans azalmasına görmeniz gerekir. Daha fazla bilgi için "Çalışma zamanı--GC performans iyileştirmeleri" bölümüne bakın [4.7.1 .NET Framework çalışma zamanının ve derleyici özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/28/net-framework-4-7-1-runtime-and-compiler-features/) blog postası. 

**Taşınabilir pdb desteği**

.NET Framework 4.7.1 sürümünden başlayarak, taşınabilir pdb destekler. Standart PDB dosyaları yalnızca Windows, taşınabilir açıkken PDB dosyaları oluşturulur ve tüm platformlarda okuyun. Çoğu durumda, dosya biçimi belirli bir .NET uygulama üzerinde çalışan bir uygulama için saydamdır. Bir özel bir derlemeyi çalışma zamanında dinamik olarak gösterdiği bir uygulamadır; Bu durumda, taşınabilir PDB yayma olanağı performans iyileştirmesi sunar ve uygulamanın bellek alanını azaltır. 

Çalışma zamanında taşınabilir pdb geçerli .NET uygulaması üzerinde "PortablePdb" dizesi geçirerek desteklenen olup olmadığını belirlemek <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported(System.String)?displayProperty=nameWithType> derleme yayma önce yöntemi.  
 
<a name="net471"/>
#### <a name="networking"></a>Ağ Oluşturma

**Message.HashAlgorithm SHA-2 desteği**

.NET Framework 4.7 ve önceki sürümlerde, <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> desteklenen özellik değerleri <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> ve <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> yalnızca. 4.7.1, .NET Framework ile başlayan <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, ve <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> de desteklenir. Bu değer gerçekte kullanılıp kullanılmadığını MSMQ üzerinde beri bağlıdır <xref:System.Messaging.Message> örneğinin kendisi hiçbir karma yapar ancak yalnızca değerleri için MSMQ geçirir. Daha fazla bilgi için "Message.HashAlgorithm SHA-2 desteği" bölümüne bakın [.NET Framework 4.7.1 ASP.NET ve yapılandırma özelliklerini](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features/) blog postası.

<a name="asp-net471" />
#### <a name="aspnet"></a>ASP.NET

**ASP.NET uygulamalarında yürütme adımları**

ASP.NET 23 olayları içerdiği önceden tanımlanmış bir ardışık düzende isteklerini işler. ASP.NET her olay işleyicisi yürütme adım olarak yürütür. .NET Framework 4.7 kadar ASP.NET sürümlerinde, yerel ve yönetilen iş parçacıkları arasında geçiş yapma nedeniyle yürütme bağlamı ASP.NET geçirilemez. Bunun yerine, ASP.NET seçmeli olarak yalnızca akar <xref:System.Web.HttpContext>. 4.7.1, .NET Framework ile başlayan <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> yöntemi modülleri ortam verileri geri yüklemek de sağlar. Bu özellik, uygulama yürütme akışı hakkında dikkat izlemeyi, profil oluşturma, tanılama veya işlemler, örneğin, ile ilgilenen kitaplıkları adresindeki yöneliktir. Daha fazla bilgi için bkz: "ASP.NET yürütme adım özelliği" [.NET Framework 4.7.1 ASP.NET ve yapılandırma özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blog postası. 

**ASP.NET ayrıştırma HttpCookie**

.NET Framework 4.7.1 yeni bir yöntem içerir <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, oluşturmak için standartlaştırılmış bir yol sağlayan bir <xref:System.Web.HttpCookie> nesne bir dizeden ve doğru bir şekilde sona erme tarihi ve yol gibi tanımlama bilgisi değerler atayın. Daha fazla bilgi için bkz: "ASP.NET ayrıştırma HttpCookie" [.NET Framework 4.7.1 ASP.NET ve yapılandırma özellikleri](https://blogs.msdn.microsoft.com/dotnet/2017/09/13/net-framework-4-7-1-asp-net-and-configuration-features) blog postası. 

**ASP.NET formları kimlik doğrulama kimlik bilgileri için SHA-2 karma seçenekleri**

.NET Framework 4.7 ve önceki sürümleri, ASP.NET kullanıcı kimlik bilgileriyle karma parolalar MD5 veya SHA1 kullanarak yapılandırma dosyalarını depolamak geliştiricilere izin. ASP.NET .NET Framework 4.7.1 ile başlayarak, SHA256, SHA384 ve SHA512 gibi yeni güvenli SHA-2 karma seçenekleri de destekler. SHA1 varsayılan olarak kalır ve varsayılan olmayan karma algoritma web yapılandırma dosyasında tanımlanabilir. Örneğin:

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47"></a> 
### <a name="whats-new-in-the-net-framework-47"></a>.NET Framework 4.7 yenilikler

.NET Framework 4.7 aşağıdaki alanlarda yeni özellikler içerir:

- [Çekirdek](#Core47)
- [Ağ oluşturma](#net47)
- [ASP.NET](#ASP-NET47)
- [Windows Communication Foundation (WCF)](#wcf47)
- [Windows Forms](#wf47)
- [Windows Presentation Foundation (WPF)](#WPF47)

Yeni API'lerin listesi için .NET Framework 4.7 eklenen için bkz: [.NET Framework 4.7 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) github'da. Özellik geliştirmeleri ve .NET Framework 4.7 hata düzeltmeleri listesi için bkz: [.NET Framework 4.7 değişiklikleri listesi](http://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) github'da.  Ek bilgi için bkz: [.NET Framework 4.7 Duyurusu](https://blogs.msdn.microsoft.com/dotnet/2017/04/05/announcing-the-net-framework-4-7/) .NET Web günlüğündeki.

<a name="Core47" />
#### <a name="core"></a>Çekirdek

.NET Framework 4.7 tarafından serileştirme artırır <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:

**Gelişmiş işlevselliği Eliptik Eğri Şifrelemesi (ECC)***

.NET Framework 4.7 içinde `ImportParameters(ECParameters)` yöntemleri için eklendi <xref:System.Security.Cryptography.ECDsa> ve <xref:System.Security.Cryptography.ECDiffieHellman> sınıfları önceden oluşturulmuş bir anahtar temsil etmek bir nesne için izin vermek için. Bir `ExportParameters(Boolean)` yöntemi, açık eğri parametreleri kullanarak anahtarı dışa aktarmak için de eklenmiştir.

.NET Framework 4.7 ayrıca ek Eğriler (Brainpool eğri paketine dahil) için destek ekler ve önceden tanımlanmış tanımları kolaylığı, oluşturulması yeni aracılığıyla için eklenmiş <xref:System.Security.Cryptography.ECDsa.Create%2A> ve <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> Fabrika yöntemleri.

Gördüğünüz bir [.NET Framework 4.7 şifreleme geliştirmeleri örneği](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) github'da.

**Denetim karakterleri DataContractJsonSerializer göre daha iyi desteği**

.NET Framework 4.7 içinde <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> denetim karakterleri ECMAScript 6 standart in conformity with serileştirir. Bu davranış, .NET Framework 4.7 hedefleyen uygulamalar için varsayılan olarak etkindir ve katılımı özellik .NET Framework 4.7 altında çalışan ancak .NET Framework'ün önceki bir sürümü hedeflemesini uygulamalar için. Daha fazla bilgi için bkz: [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../../../docs/framework/migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

<a name="net47" />
#### <a name="networking"></a>Ağ Oluşturma

.NET Framework 4.7 aşağıdaki ağ ile ilişkili özelliği ekler:

**TLS protokolleri için varsayılan işletim sistemi desteği***

Tarafından kullanılan TLS yığın <xref:System.Net.Security.SslStream?displayProperty=nameWithType> ve yukarı yığın bileşenleri HTTP, FTP ve SMTP gibi işletim sistemi tarafından desteklenen varsayılan TLS protokolleri kullanmak üzere geliştiricilerin sağlar. Geliştiriciler hiçbir uzun sabit kodlu bir TLS sürümü gerekir.

<a name="ASP-NET47" />
#### <a name="aspnet"></a>ASP.NET

.NET Framework 4.7 ASP.NET aşağıdaki yeni özellikleri içerir:

**Nesne önbelleği genişletilebilirliği**

ASP.NET, .NET Framework 4.7 ile başlayarak, yeni bir bellekteki nesne önbelleğe alma ve bellek izlemesi için varsayılan ASP.NET uygulamaları değiştirmek geliştiricilere sağlayan API kümesi ekler. ASP.NET uygulaması yeterli değilse, geliştiriciler artık aşağıdaki üç bileşeni hiçbirini değiştirebilirsiniz:

- **Nesne önbelleği deposu**. Yeni bir önbellek sağlayıcıları yapılandırması bölümü kullanarak, geliştiricilerin bir ASP.NET uygulaması için bir nesne önbelleği yeni uygulamalarında yeni kullanarak ekleyebilirsiniz **ICacheStoreProvider** arabirimi.
 
- **Bellek izlemesi**. Varsayılan bellek İzleyicisi'nde ASP.NET uygulamaları işlemi için yapılandırılan özel bayt sınırına yakın çalıştırırken veya makine üzerinde kullanılabilir toplam fiziksel RAM'in düşük olduğunda bildirir. Bu sınırlar yaklaştığında bildirim tetiklenir. Bazı uygulamalar için bildirimler için yararlı tepki izin vermek için yapılandırılmış sınırları için çok yakın gönderildi. Geliştiriciler artık varsayılan kullanarak değiştirmek için kendi bellek izleyiciler yazma <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> özelliği.

- **Bellek sınırı tepki**. Varsayılan olarak, ASP.NET nesne önbelleği kırpma ve düzenli aralıklarla çağırmayı dener <xref:System.GC.Collect%2A?displayProperty=nameWithType> özel bayt işlem sınırı olduğunda yakın. Bazı uygulamalar, çağrıları sıklığını için <xref:System.GC.Collect%2A?displayProperty=nameWithType> veya kırpılır önbellek miktarı yetersiz. Geliştiriciler, şimdi değiştirmek veya varsayılan davranışı abone olarak ek **IObserver** uygulamaları uygulamanın bellek İzleyicisi.

<a name="wcf47" />
#### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)

Windows Communication Foundation (WFC), aşağıdaki özellikler ve değişiklikleri ekler:

**TLS 1.1 veya TLS 1.2 varsayılan ileti güvenlik ayarlarını yapılandırma yeteneği**

.NET Framework 4.7 ile başlayarak, WCF, TLS 1.1 veya TLS 1.2 SSL 3.0 ve TLS 1.0 ek olarak varsayılan ileti güvenlik protokolü olarak yapılandırmanıza olanak sağlar. Bu katılımı bir ayardır; etkinleştirmek için uygulama yapılandırma dosyasına aşağıdaki giriş eklemeniz gerekir:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" /> 
</runtime>
```

**Geliştirilmiş güvenilirliğini WCF uygulamaları ve WCF seri hale getirme**

WCF, böylece performansı ve güvenilirliği seri hale getirme seçeneklerinin geliştirme yarış durumları ortadan kod değişiklikleri sayısını içerir. Bu güncelleştirmeler şunlardır:

- Zaman uyumsuz ve zaman uyumlu kod çağrılarında karıştırma için daha iyi destek **SocketConnection.BeginRead** ve **SocketConnection.Read**.
- Bağlantı durduruluyor zaman güvenilirlik geliştirilmiş **SharedConnectionListener** ve **DuplexChannelBinder**.
- Çağrılırken seri hale getirme işlemlerinin güvenilirliğini geliştirilmiş <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> yöntemi.
- Bir garson çağırarak kaldırırken güvenilirlik geliştirilmiş **ChannelSynchronizer.RemoveWaiter** yöntemi.

<a name="wf47" />
#### <a name="windows-forms"></a>Windows Forms

.NET Framework 4.7 Windows Forms yüksek DPI monitör artırır.

**Yüksek DPI desteği**

Bu hedef .NET Framework 4.7 .NET Framework uygulamaları ile başlayan özellikler yüksek DPI ve dinamik DPI Windows Forms uygulamaları için desteği. Yüksek DPI desteği düzen ve formlar ve denetimler yüksek DPI monitörde görünümünü geliştirir. Dinamik DPI düzenini ve formlar görünümünü değiştirir ve kullanıcı DPI veya görüntü ölçek faktörü çalışan bir uygulama, değiştiğinde denetler.

Yüksek DPI desteğinin tanımlayarak yapılandırma katılımı özelliği olan bir [ \<System.Windows.Forms.ConfigurationSection >](../configure-apps/file-schema/winforms/index.md) uygulama yapılandırma dosyanızı bölümünde. Windows Forms uygulamanıza yüksek DPI ve dinamik DPI desteği ekleme hakkında daha fazla bilgi için bkz: [yüksek DPI destekleyen Windows Forms'ta](../winforms/high-dpi-support-in-windows-forms.md).

<a name="WPF47"></a> 
#### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)

.NET Framework 4.7 WPF aşağıdaki geliştirmeleri içerir:

**Windows WM_POINTER iletileri dayalı bir touch/kalem yığını desteği**

Şimdi dayalı bir touch/kalem yığını kullanma seçeneğiniz [WM_POINTER iletileri](https://msdn.microsoft.com/library/windows/desktop/hh454903.aspx) yerine Windows mürekkep Hizmetleri Platform'nı (WISP). Bu bir katılımı .NET Framework'teki özelliğidir. Daha fazla bilgi için bkz: [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md).

**WPF API'leri yazdırma için yeni uygulama**

WPF API'leri yazdırma <xref:System.Printing.PrintQueue?displayProperty=nameWithType> çağrı Windows sınıfı [yazdırma belge paket API](https://msdn.microsoft.com/library/windows/desktop/hh448418(v=vs.85).aspx) kullanım dışı yerine [XPS yazdırma API](https://msdn.microsoft.com/library/windows/desktop/ff686814(v=vs.85).aspx). Bu değişiklik uygulama uyumluluğu etkisini için bkz: [.NET Framework 4.7 yeniden hedefleme değişiklikleri](../migration-guide/retargeting-changes-in-the-net-framework-4-7.md). 

<a name="v462"></a> 
## <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 yenilikler

[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Aşağıdaki alanlarda yeni özellikler içerir:

- [ASP.NET](#ASPNET462)

- [Karakter kategorileri](#Strings)

- [Şifreleme](#Crypto462)

- [SqlClient](#SQLClient)

- [Windows Communication Foundation](#WCF)

- [Windows Presentation Foundation (WPF)](#WPF462)

- [Windows Workflow Foundation (WF)](#WF462)

- [ClickOnce](#ClickOnce)

- [Windows Forms ve WPF uygulamaları UWP uygulamaları için dönüştürme](#UWPConvert)

- [Hata ayıklama iyileştirmeleri](#Debug462)

.NET Framework 4.6.2 yeni API'lerin listesi eklenen için bkz: [.NET Framework 4.6.2 API değişiklikleri](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) github'da. Özellik geliştirmeleri ve hata düzeltmeleri .NET Framework 4.6.2 listesi için bkz: [.NET Framework 4.6.2 değişiklikler listesi](http://go.microsoft.com/fwlink/?LinkId=708778) github'da.  Ek bilgi için bkz: [tanışın .NET Framework 4.6.2](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/) .NET Web günlüğündeki.

<a name="ASPNET462"></a> 
### <a name="aspnet"></a>ASP.NET
 İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET aşağıdaki geliştirmeleri içerir:

 **Geliştirilmiş veri ek açıklaması doğrulayıcıları yerelleştirilmiş hata iletileri için destek** veri ek açıklaması doğrulayıcıları sınıf özelliği için bir veya daha fazla öznitelik ekleyerek doğrulama gerçekleştirmek etkinleştirin. Özniteliğin <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> öğesi doğrulama başarısız olursa hata iletisinin metni tanımlar. İle başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], ASP.NET hata iletileri yerelleştirme yapmayı kolaylaştırır. Hata iletileri, yerelleştirilmiş:

1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> Doğrulama özniteliğinde sağlanır.

2.  Kaynak dosyası App_LocalResources klasöründe depolanır.

3.  Formun yerelleştirilmiş kaynaklar dosya adına sahip `DataAnnotation.Localization.{` *adı*`}.resx`, burada *adı* bir kültür adı biçiminde *languageCode* `-` *ülke/regionCode* veya *languageCode*.

4.  Anahtar adı kaynağın atanan dizedir <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> özniteliği, değerini ise yerelleştirilmiş hata iletisi.

 Örneğin, aşağıdaki veri ek açıklaması özniteliği için geçersiz bir derecelendirme varsayılan kültürün hata iletisini tanımlar.

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

 Daha sonra DataAnnotation.Localization.fr.resx hata ileti dizesi olan anahtarıdır ve yerelleştirilmiş hata iletisi, değeri olan bir kaynak dosyası oluşturabilirsiniz. Dosya içinde bulunması gereken `App.LocalResources` klasör. Örneğin, anahtarını ve değerini yerelleştirilmiş Fransızca (fr) dil hata iletisi şudur:

| Ad                                 | Değer                                     |
| ------------------------------------ | ----------------------------------------- |
| Derecelendirme, 1 ile 10 arasında olmalıdır. | Seçeneğinden être oluşturan diğer 1 la Not et 10. |

 Bu dosya daha sonra yapabilirsiniz

 Ayrıca, veri ek açıklaması yerelleştirme genişletilebilir. Geliştiriciler Tak kendi dize yerelleştiriciye sağlayıcısında uygulayarak <xref:System.Web.Globalization.IStringLocalizerProvider> yerelleştirme dize yere dışında bir kaynak dosyasında depolamak için arabirim.

 **Oturum durumu depolama sağlayıcıları ile zaman uyumsuz Destek** ASP.NET şimdi böylece zaman uyumsuz ölçeklenebilirlik avantajlarını almak ASP.NET uygulamalarını izin vererek, oturum durumu depolama sağlayıcıları ile kullanılacak görev döndürme yöntemleri sağlar. Desteklediği için oturum durumu ile zaman uyumsuz işlemleri sağlayıcıları depolamak, ASP.NET içeren yeni bir arabirimi <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, devralan <xref:System.Web.IHttpModule> ve geliştiricilerin kendi oturum durumu modülü ve zaman uyumsuz oturum depolama sağlayıcıları uygulamak olanak tanır. Arabirim şu şekilde tanımlanır:

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

 Ayrıca, <xref:System.Web.SessionState.SessionStateUtility> sınıfı, iki yeni yöntemleri içerir <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> ve <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, zaman uyumsuz işlemleri desteklemek için kullanılabilir.

 **Çıkış önbelleği sağlayıcıları için zaman uyumsuz Destek** başlayarak [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], görev döndürme-yöntemleri zaman uyumsuz ölçeklenebilirlik avantajlarını sağlayacak çıkış önbelleği sağlayıcıları ile kullanılabilir.  Bu yöntemleri uygulayan sağlayıcılar bir web sunucusu üzerinde iş parçacığı engellemelerini azaltmak ve ASP.NET hizmeti ölçeklenebilirliği artırmak.

 Zaman uyumsuz çıkış önbelleği sağlayıcıları desteklemek için aşağıdaki API'ler eklenmiştir:

- <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> Devraldığı sınıfı <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> ve zaman uyumsuz bir çıkış önbelleği sağlayıcısı için uygulanacak geliştiricilerin olanak tanır.

- <xref:System.Web.Caching.OutputCacheUtility> Sınıfı çıkış önbelleğini yapılandırma için yardımcı yöntemleri sağlar.

- 18 yeni yöntemleri <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> sınıfı. Bunlar <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, ve <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> ve <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> ve <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.

- 2 yeni yöntemleri <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> sınıfı: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> ve <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.

- İçinde <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> sınıfı, <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> yöntemi.

- İçinde <xref:System.Web.Caching.CacheDependency>, <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> yöntemi.

<a name="Strings"></a> 
### <a name="character-categories"></a>Karakter kategorileri
 İçindeki karakterleri [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] göre sınıflandırılır [Unicode standart, sürüm 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/). İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], karakter sınıflandırılmış 6.3 Unicode karakter kategorisine göre.

 Unicode 8.0 için destek sınırlıdır karakterleriyle sınıflandırmasını <xref:System.Globalization.CharUnicodeInfo> sınıfı ve türleri ve yöntemleri, kullanan üzerinde. Bunlar <xref:System.Globalization.StringInfo> sınıfı, aşırı yüklenmiş <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> yöntemi ve [karakter sınıfları](../../../docs/standard/base-types/character-classes-in-regular-expressions.md) .NET Framework normal ifade altyapısı tarafından tanınmıyor.  Karakter ve dize karşılaştırma ve sıralama bu değişiklikten etkilenmez ve temel işletim sisteminde veya Windows 7 sistemlerinde, .NET Framework tarafından sağlanan karakter verileri yararlanmaya devam eder.

 Unicode 6.0 karakter kategorilerden Unicode 7.0 değişiklikler için bkz: [Unicode standart, sürüm 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) Unicode Konsorsiyumu Web sitesindeki. Değişiklikler için Unicode 7.0 Unicode 8.0 için bkz: [Unicode standart, sürüm 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) Unicode Konsorsiyumu Web sitesindeki.

<a name="Crypto462"></a> 
### <a name="cryptography"></a>Şifreleme
 **Destek X509 için FIPS 186 3 DSA içeren sertifikalar** [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] DSA (dijital imza algoritması) X509, anahtarları FIPS 186 2 1024 bit sınırı aşan sertifikalar için destek ekler.

 Daha büyük anahtar boyutları FIPS 186-3 ' ü destekleyen yanı sıra [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] (SHA256, SHA384 ve SHA512) karma algoritması SHA-2 ailesini imzalarla bilgi işlem sağlar. FIPS 186 3 desteği sağlanır yeni tarafından <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> sınıfı.

 Yakın zamanda yapılan değişiklikler mantığıyla <xref:System.Security.Cryptography.RSA> .NET Framework 4.6 sınıfında ve <xref:System.Security.Cryptography.ECDsa> .NET Framework 4.6.1, sınıfında <xref:System.Security.Cryptography.DSA> soyut taban sınıf içinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] bunu kullanmak arayanlara izin vermek için ek yöntemleri vardır atama olmadan işlevselliği. Çağırabilirsiniz <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> aşağıdaki örnekte gösterildiği gibi verileri imzalamak için genişletme yöntemi.

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb 
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

 Çağırabilirsiniz <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> genişletme yöntemi aşağıdaki örnekte gösterildiği gibi imzalı verileri doğrulayın.

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

 **Artan daha anlaşılır olması için ECDiffieHellman anahtar türetme yordamları girişleri** .NET Framework 3.5 ile üç farklı anahtar türetme işlevi (KDF) yordamları Ellipic Eğri Diffie-Hellman anahtar anlaşması için destek eklenmiştir. Yordamlar ve yordamları kendileri girişleri özellikleri yapılandırılmışsa <xref:System.Security.Cryptography.ECDiffieHellmanCng> nesnesi. Ancak her yordam her giriş özelliği okuma olduğundan, Karışıklığı önlemek için geçmiş üzerinde geliştiricinin geniş oda vardı.

 Bu adres için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], aşağıdaki üç yöntemi için eklenene <xref:System.Security.Cryptography.ECDiffieHellman> temel sınıfı daha net bir şekilde bu KDF yordamları ve bunların girişleri göstermek için:

|ECDiffieHellman yöntemi|Açıklama|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formül kullanılarak anahtar malzemesi türetilen<br /><br /> KARMA (secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> KARMA (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> Burada *x* hesaplanan EC Diffie-Hellman algoritması sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|Formül kullanılarak anahtar malzemesi türetilen<br /><br /> HMAC (hmacKey, secretPrepend &#124; &#124; *x* &#124; &#124; secretAppend)<br /><br /> HMAC (hmacKey, secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> Burada *x* hesaplanan EC Diffie-Hellman algoritması sonucudur.|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|TLS sözde rastgele işlevi (PRF) türetme algoritmasını kullanarak anahtar malzemesi türer.|

 **Kalıcı anahtarı simetrik şifreleme için destek** Windows şifreleme kitaplığı (CNG) kalıcı simetrik anahtarları depolamak için destek eklenmiştir ve donanım depolanan simetrik anahtarları kullanma ve [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] mades yapmak, geliştiriciler için mümkün Bu özelliği kullanın.  Anahtar adları ve anahtar sağlayıcıları kavramı uygulamaya özel olduğundan, bu özelliği kullanmak için tercih edilen Fabrika yaklaşım yerine somut uygulama türleri Oluşturucusu kullanılarak gerektirir (arama gibi `Aes.Create`).

 Kalıcı anahtarı simetrik şifreleme desteği için AES var (<xref:System.Security.Cryptography.AesCng>) ve 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algoritmaları. Örneğin:

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb 
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

 **SHA-2 karma desteği SignedXml** [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] için destek ekler <xref:System.Security.Cryptography.Xml.SignedXml> Özet algoritmaları RSA SHA256, RSA SHA384 ve SHA512 RSA PKCS #1 imza yöntemleri ve SHA256, SHA384 ve SHA512 başvurusu için sınıf.

 URI sabitleri tüm üzerinde gösterilen <xref:System.Security.Cryptography.Xml.SignedXml>:

|SignedXml alan|Sabit|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|

 Özel bir kayıtlı tüm programları <xref:System.Security.Cryptography.SignatureDescription> işleyicisi içine <xref:System.Security.Cryptography.CryptoConfig> Bu algoritmalar geçmişte oldu, ancak şimdi olduğundan platform varsayılan olarak, çalışmaya devam edecek desteği eklemek için <xref:System.Security.Cryptography.CryptoConfig> kayıt artık değil gerekli.

<a name="SQLClient"></a> 
### <a name="sqlclient"></a>SqlClient
 SQL Server için .NET framework veri sağlayıcısı (<xref:System.Data.SqlClient?displayProperty=nameWithType>) yer alan aşağıdaki yeni özellikler içerir [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:

 **Bağlantı havuzu ve Azure SQL veritabanları zaman aşımlarını** zaman bağlantı havuzu etkinleştirilmişse ve bir zaman aşımı veya diğer oturum açma hatası oluşur, bir özel durum önbelleğe alınır ve sonraki bağlantı girişimleri için sonraki 5 üzerinde önbelleğe alınan özel durum oluşur saniyede 1 dakika.  Daha fazla ayrıntı için bkz: [SQL Server bağlantı havuzu (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md).

 Bu davranış, genellikle hızlı bir şekilde kurtarılmasını geçici hataları ile bağlantı girişimleri başarısız olabilir beri Azure SQL veritabanları için bağlanırken arzu değil. Daha iyi bağlantı yeniden deneme deneyimi, Azure SQL veritabanı bağlantıları başarısız olduğunda davranışı kaldırılır bağlantı havuzu engelleme süresini iyileştirin.

 Yeni eklenen `PoolBlockingPeriod` anahtar sözcüğü uygulamanız için en uygun engelleme süresi seçmenize olanak sağlar. Değerler şunlardır:

 `Auto`Bir Azure SQL veritabanına bağlanan bir uygulama için süresi engelleme bağlantı havuzu devre dışı bırakılır ve başka bir SQL Server örneğine bağlanan bir uygulama için süresi engelleme bağlantı havuzu etkindir. Varsayılan değer budur. Sunucu uç nokta adı aşağıdakilerden herhangi birini ile sona ererse, Azure SQL veritabanları değerlendirilir:

- . database.windows.net

- . database.chinacloudapi.cn

- . database.usgovcloudapi.net

- . database.cloudapi.de

 `AlwaysBlock`Bağlantı havuzu engelleme süresi her zaman etkindir.

 `NeverBlock`Bağlantı havuzu engelleme süresi her zaman devre dışı bırakılır.

 **Her zaman şifreli geliştirmelerine** SQLClient her zaman şifreli için iki geliştirmeleri sunar:

- Şifrelenmiş veritabanı sütunlarını parametreleştirilmiş sorguları performansını artırmak için sorgu parametreleri için şifreleme meta verileri artık önbelleğe alınır. İle <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> özelliğini `true` (varsayılan değer olan), aynı sorgu birden çok kez çağrılırsa, istemci parametre meta verilerini sunucudan yalnızca bir kez alır.

- Sütun şifreleme anahtarı girişleri anahtar önbelleğinde şimdi kullanılarak ayarlanan bir yapılandırılabilir zaman aralığından sonra çıkarılacak <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> özelliği.

<a name="WCF"></a> 
### <a name="windows-communication-foundation"></a>Windows Communication Foundation
 İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Communication Foundation aşağıdaki alanlarda geliştirilmiştir:

 **CNG kullanarak depolanan sertifikalar için WCF Aktarım güvenlik desteği** WCF taşıma güvenliği Windows şifreleme Kitaplığı'nı (CNG) kullanarak depolanan sertifikalar destekler. İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bu destek üs en fazla 32 bit uzunlukta bir ortak anahtar sertifikaları kullanarak sınırlıdır. Bir uygulama hedefleri zaman [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bu özellik varsayılan olarak açıktır.

 Hedef uygulamalar için [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ve önceki ancak üzerinde çalışan [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bu özellik, aşağıdaki satırı ekleyerek etkinleştirilebilir [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config veya web.config Bölümü dosya.

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

Bu ayrıca programlı olarak aşağıdaki gibi kod ile yapılabilir:

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

 **DataContractJsonSerializer sınıfı tarafından birden çok gün ışığından yararlanma saati ayarlama kuralları için daha iyi destek** müşterileri belirlemek için bir uygulama yapılandırma ayarı kullanabilir olup olmadığını <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> sınıfı destekleyen birden çok ayarlama tek bir saat dilimi için kuralları. Bu bir katılımı özelliğidir. Etkinleştirmek için app.config dosyasına aşağıdaki ayarı ekleyin:

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

Bu özellik etkinleştirildiğinde, bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne kullanır <xref:System.TimeZoneInfo> yerine tür <xref:System.TimeZone> tarih ve saat verilerini seri durumdan çıkarılacak türü. <xref:System.TimeZoneInfo>birden çok ayarlama kuralları, geçmiş saat dilimi verilerle çalışmak mümkün destekler;   <xref:System.TimeZone> desteklemez.

Daha fazla bilgi için <xref:System.TimeZoneInfo> yapısı ve saat dilimi düzeltmeleri, bkz: [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).

**Bir UTC koruma desteği zaman seri hale getirme ve seri XMLSerializer sınıfıyla** normalde, ne zaman <xref:System.Xml.Serialization.XmlSerializer> sınıfı bir UTC serileştirmek için kullanılır <xref:System.DateTime> değerini korur serileştirilmiş saat dizesi oluşturur Tarih ve saat ancak zaman yerel olduğunu varsayar.  Örneğin, aşağıdaki kodu çağırarak UTC tarihi ve saati örneği varsa:

```csharp
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);
```

```vb
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)
```

Sonuç serileştirilmiş zaman dizedir "03:00:00.0000000-08:00" sekiz saat geride UTC sistemi.  Ve seri değerlerini her zaman yerel tarih ve saat değerleri seri.

 Bir uygulama yapılandırma ayarı belirlemek için kullanabileceğiniz olup olmadığını <xref:System.Xml.Serialization.XmlSerializer> serileştirilirken UTC saat dilimi bilgilerini ve seri durumdan korur <xref:System.DateTime> değerler:

```xml 
<runtime>
     <AppContextSwitchOverrides 
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />
</runtime>
```

Bu özellik etkinleştirildiğinde, bir <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nesne kullanır <xref:System.TimeZoneInfo> yerine tür <xref:System.TimeZone> tarih ve saat verilerini seri durumdan çıkarılacak türü. <xref:System.TimeZoneInfo>birden çok ayarlama kuralları, geçmiş saat dilimi verilerle çalışmak mümkün destekler;   <xref:System.TimeZone> desteklemez.

Daha fazla bilgi için <xref:System.TimeZoneInfo> yapısı ve saat dilimi düzeltmeleri, bkz: [saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md).

 **NetNamedPipeBinding en iyi eşleşmeyi** WCF her zaman bağlandıkları istediklerinde bir en iyi karşılayan URI üzerinde dinleme hizmeti emin olmak için istemci uygulamaları ayarlanabilen yeni bir uygulama ayarı vardır. Ayarlamak bu uygulama ayarı ile `false` (varsayılan) kullanan istemciler için olası <xref:System.ServiceModel.NetNamedPipeBinding> istenen URI'yi bir dizenin bir URI üzerinde dinleme bir hizmete bağlanmak için.

 Örneğin, bir istemci bir hizmet adresinde dinlemede için bağlanmaya `net.pipe://localhost/Service1`, ancak bu makinede yönetici ayrıcalığıyla çalıştıran farklı bir hizmet adresinde dinlemede `net.pipe://localhost`. Ayarlamak bu uygulama ayarı ile `false`, istemci yanlış hizmete bağlanma girişiminde. Uygulama ayarı ayarını sonra `true`, istemci her zaman en iyi hizmet eşleşen bağlanır.

> [!NOTE]
>  Kullanan istemciler <xref:System.ServiceModel.NetNamedPipeBinding> Hizmetleri (varsa) yerine tam uç noktası adresi hizmetin taban adresine göre bulur. Bu her zaman çalışır hizmet ayarı emin olmak için benzersiz bir taban adresi kullanmanız gerekir.

 Bu değişikliği etkinleştirmek için aşağıdaki uygulama ayarı, istemci uygulamanızın App.config veya Web.config dosyasına ekleyin:

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

 **SSL 3.0 varsayılan protokolü değil** NetTcp taşıma güvenliği ve sertifika bir kimlik bilgisi türü ile kullanırken, SSL 3.0 artık güvenli bağlantı anlaşması için kullanılan bir varsayılan protokolüdür. Çoğu durumda olması gerekir etkisi olan mevcut uygulamalar için TLS 1.0 için NetTcp protokol listesinde yer aldığından. Tüm mevcut istemcilerin kullanarak bir bağlantı anlaşması gerekir en az TLS 1.0. Ssl3 gerekiyorsa, aşağıdaki yapılandırma mekanizmalardan biri üzerinde anlaşılan protokolleri listesine eklemek için kullanın.

- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> Özelliği

- <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> Özelliği

- [ \<Aktarım >](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) bölümünü [ \<netTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) bölümü

- [ \<SslStreamSecurity >](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) bölümünü [ \<customBinding >](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) bölümü

<a name="WPF462"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Presentation Foundation aşağıdaki alanlarda geliştirilmiştir:

 **Grup sıralama** kullanan bir uygulama bir <xref:System.Windows.Data.CollectionView> verileri gruplandırmak için nesne artık açıkça bildirebilirsiniz grupları sıralama nasıl yapılır. Açık adresleri sıralama uygulama dinamik olarak ekler veya grupları kaldırır veya gruplandırma söz konusu öğeyi özelliklerinin değeri değiştiğinde sezgisel olmayan sıralama sorun oluşur. Bu ayrıca Grup oluşturma işleminin karşılaştırmaları gruplandırma özelliklerinin tam koleksiyonu sıralama dışında gruplarının sıralamanın taşıyarak performansı artırabilir.

 Grup sıralama, desteklemek için yeni <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> ve <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> özellikleri açıklar tarafından üretilen Grup koleksiyonu sıralama <xref:System.ComponentModel.GroupDescription> nesnesi. Bu şekilde aynı adlı paraleldir <xref:System.Windows.Data.ListCollectionView> özellikleri, veri öğeleri sıralama açıklar.

 İki yeni statik özelliklerini <xref:System.Windows.Data.PropertyGroupDescription> sınıfı, <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> ve <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, en yaygın örnekleri için kullanılabilir.

 Örneğin, yaşı, aşağıdaki XAML grupları verilerle yaş grupları artan sırada sıralamak ve her yaş grup içindeki öğeleri son ada göre gruplandırın.

```xaml
<GroupDescriptions>
     <PropertyGroupDescription 
         PropertyName="Age" 
         CustomSort= 
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

 **Yazılım klavye desteği** yumuşak klavye desteği otomatik olarak çağırma ve dokunma metinsel giriş alabilir bir denetim tarafından alındığında girdikten sonra Windows 10'daki yeni yazılım klavye durdurulduğundan WPF uygulamalarında izleme odağı sağlar.

 .NET Framework önceki sürümlerde, WPF kalem/touch hareketi desteğini devre dışı bırakmadan izleme odağa WPF uygulamaları ni kaldıramaz.  Sonuç olarak, WPF uygulamalar arasında tam WPF dokunma desteği seçin veya bu üzerinde Windows fare yükseltme kullanan gerekir.

 **İzleyici başına DPI** WPF uygulamaları, WPF içinde yüksek DPI ve karma DPI ortamlar son artışı desteklemek için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] İzleyici başına farkındalık sağlar. Bkz: [örnekleri ve Geliştirici Kılavuzu](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) İzleyici başına DPI farkında olmasını WPF uygulamanızı etkinleştirme hakkında daha fazla bilgi için GitHub üzerinde.

 .NET Framework önceki sürümlerinde, WPF sistem DPI kullanan uygulamalardır. Diğer bir deyişle, uygulamanın kullanıcı Arabirimi OS uygulama işlenen İzleyici DPI bağlı olarak uygun şekilde ölçeklendirilir. ,

 Altında çalışan uygulamalar için [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], bir yapılandırma deyimine ekleyerek WPF uygulamalarında İzleyici başına DPI değişiklikleri devre dışı bırakabilirsiniz [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) uygulama yapılandırmanızı bölümünü dosyasında, aşağıdaki gibi:

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 İçinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], Windows Workflow Foundation aşağıdaki alanında geliştirilmiştir:

 **C# ifadeleri ve Re-hosted WF Tasarımcısı'nda IntelliSense desteği** başlayarak [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], WF hem bir Visual Studio Tasarımcısı'nda ve kod iş akışlarında C# ifadeleri destekler. Re-hosted iş akışı Tasarımcısı Visual Studio'da (örneğin, WPF) dışında bir uygulamada olması iş akışı Tasarımcısı izin veren WF anahtar özelliğidir.  Windows Workflow Foundation C# ifadeleri ve IntelliSense Re-hosted iş akışı Tasarımcısı'nda destekleme özelliği sağlar. Daha fazla bilgi için bkz: [Windows Workflow Foundation blog](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409).

 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`.NET Framework'den önceki sürümlerinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], WF Tasarımcısı IntelliSense olduğunda kopuk bir müşteri bir Visual Studio iş akışı projesinde yeniden oluşturur. Proje oluşturma işlemi başarılı olur, iş akışı türlerini designer'ı bulunamadı ve eksik iş akışı türü için IntelliSense gelen uyarılar görüntülenir **hata listesi** penceresi. [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Bu sorunu giderir ve IntelliSense kullanılabilir hale getirir.

 **Şimdi iş akışı izleme ile iş akışı V1 uygulamaları çalıştırmak FIPS modunda** FIPS uyumluluk modu etkin olan makineleri şimdi başarıyla çalıştırabilirsiniz sürüm 1 stili uygulama bir iş akışı iş akışı ile izleme. Bu senaryoyu etkinleştirmek için app.config dosyasına aşağıdaki değişiklik yapmanız gerekir:

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

 Bu senaryo etkin değilse uygulama çalıştıran bir özel durum iletisi oluşturmak devam eder "Bu uygulama Windows parçası olmayan Platform FIPS şifreleme algoritmaları doğrulandı."

 **Dinamik güncelleştirme ile Visual Studio iş akışı Tasarımcısı kullanarak iş akışı geliştirmeleri** iş akışı Tasarımcısı, akış çizelgesi etkinlik Tasarımcısı ve diğer iş akışı etkinlik tasarımcıları şimdi başarıyla yüklemek ve kaydedilmiş iş akışları görüntülemek çağırdıktan sonra <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> yöntemi. Önce .NET Framework sürümlerinde [!INCLUDE[net_v462](../../../includes/net-v462-md.md)], çağrıldıktan sonra kaydedilmiş bir iş akışı için Visual Studio'da XAML dosyası yüklenirken <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> aşağıdaki sorunlar oluşabilir:

- İş akışı XAML dosyasını doğru tasarımcının yükleyemeyeceği (zaman <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> satırın sonunda olup).

- Akış Çizelgesi etkinlik Tasarımcısı veya diğer iş akışı etkinlik tasarımcıları tüm nesnelerin varsayılan konumlarına ekli özellik değerlerini aksine görüntüleyebilir.

<a name="ClickOnce"></a> 
### <a name="clickonce"></a>ClickOnce
 ClickOnce zaten desteklediği 1.0 protokolü ek olarak, TLS 1.1 ve TLS 1.2 desteklemek için güncelleştirildi. ClickOnce otomatik olarak hangi protokolünün gerekli olduğunu algılar; TLS 1.1 ve 1.2 desteğini etkinleştirmek için ClickOnce uygulamasında hiçbir ek adımlar gereklidir.

<a name="UWPConvert"></a> 
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows Forms ve WPF uygulamaları UWP uygulamaları için dönüştürme
 Windows şimdi WPF ve Windows Forms uygulamaları, Evrensel Windows Platformu (UWP) için de dahil olmak üzere mevcut Windows Masaüstü uygulamaları getirmek için özellikleri sunar. Bu teknoloji, mevcut kodunuzu temel UWP, böylece uygulamanız tüm Windows 10 cihazlarına getiren kademeli olarak geçiş olanak tanıyarak köprü olarak davranır.

 Dönüştürülen Masaüstü uygulamaları UWP API'leri Canlı kutucukları ve bildirimler gibi özellikleri etkinleştirmek için erişilebilir hale getirir UWP uygulamaları, uygulama kimliğini benzer bir uygulama kimliğini elde edilir. Uygulama önceden olduğu gibi davranacak şekilde devam eder ve bir tam güven uygulama olarak çalışır. Uygulama dönüştürüldükten sonra bir uygulama kapsayıcı işlemini uyarlanabilir bir kullanıcı arabirimi eklemek için var olan tam güven işlemi eklenebilir. Tüm işlevlere uygulama kapsayıcı işleme taşındığında, tam güven işlemi kaldırıldı ve yeni UWP uygulaması tüm Windows 10 cihazlar için kullanılabilir hale getirilebilir.

<a name="Debug462"></a> 
### <a name="debugging-improvements"></a>Hata ayıklama iyileştirmeleri
 *Hata ayıklama API'si yönetilmeyen* içinde geliştirilmiş [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] ek analizler yapmak için bir <xref:System.NullReferenceException> böylece hangi değişkenidir kaynak kodu tek bir satıra belirlemek mümkün durum `null`.   Bu senaryoyu desteklemek için aşağıdaki API'leri yönetilmeyen hata ayıklama API'si eklenmiştir.

- [ICorDebugCode4](../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md), ve [ICorDebugVariableHomeEnum](../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) yönetilen değişkenlerin yerel ev kullanıma arabirimleri. Bu, bazı kod akış analizi yapmak hata ayıklayıcıları sağlar, bir <xref:System.NullReferenceException> oluşur ve olduğu yerel bir konuma karşılık gelen yönetilen değişkeni belirlemek için geriye doğru çalışması için `null`.

- [ICorDebugType2::GetTypeID](../../../docs/framework/unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) yöntemi için Icordebugtype için bir eşleme sağlar [cor_typeıd](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), elde etmek hata ayıklayıcı sağlayan bir [cor_typeıd](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) örneği olmadan Icordebugtype. Varolan API'leri [cor_typeıd](../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) türü sınıfı düzenini belirlemek için kullanılabilir.

<a name="v461"></a> 
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 yenilikler
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] Aşağıdaki alanlarda yeni özellikler içerir:

- [Şifreleme](#Crypto)

- [ADO.NET](#ADO.NET461)

- [Windows Presentation Foundation (WPF)](#WPF461)

- [Windows Workflow Foundation](#WWF461)

- [Profil Oluşturma](#Profile461)

- [NGen](#NGEN461)

 Daha fazla bilgi için [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], aşağıdaki konulara bakın:

- [Değişiklikleri .NET Framework 4.6.1 listesi](http://go.microsoft.com/fwlink/?LinkId=622964)

- [4.6.1 uygulama uyumluluğu](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)

- [.NET Framework API fark](http://go.microsoft.com/fwlink/?LinkId=622989) (github'da ile)

<a name="Crypto"></a> 
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>Şifreleme: X509 desteği içeren ECDSA sertifikaları
 .NET Framework 4.6 X509 RSACng desteği eklendi sertifikalar. [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] ECDSA (Eliptik Eğri Dijital imza algoritması) X509 için destek ekler sertifikalar.

 ECDSA daha iyi performans sunar ve RSA, Aktarım Katmanı Güvenliği (TLS) performans ve ölçeklenebilirlik olduğu ilgili bir sorun mükemmel bir seçim sağlayarak daha daha güvenli bir şifreleme algoritması. .NET Framework uygulamasını var olan Windows işlev çağrılarını sarmalar.

 Aşağıdaki kod örneği X 509 sertifika dahil ECDSA için yeni destek kullanarak bir bayt akış için bir imzayı üretmek için ne kadar kolay olduğunu gösterir [!INCLUDE[net_v461](../../../includes/net-v461-md.md)].

 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

 Bu .NET Framework 4.6 bir imzayı üretmek için gereken kod için işaretlenen Karşıtlık sağlar.

 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a> 
### <a name="adonet"></a>ADO.NET
 Aşağıdakiler için ADO.NET eklenmiştir:

 Her zaman şifreli donanım desteği anahtarları ADO.NET şimdi her zaman şifreli sütun ana anahtarları donanım güvenlik modülleri (HSM'ler) yerel olarak depolamak korunan destekler. Bu destek sayesinde, müşterilere özel sütun ana anahtar depolama sağlayıcıları yazmak zorunda ve uygulamalarda kaydetme olmadan HSM'ler içinde depolanan asimetrik anahtarlar yararlanabilirsiniz.

 Müşteriler HSM satıcısı tarafından sağlanan CSP sağlayıcı veya CNG Anahtar depolama sağlayıcıları sütun ana bir HSM'de depolanan anahtarlar ile korunan her zaman şifreli verilere erişebilmesi için uygulama sunucuları veya istemci bilgisayarlara yüklemeniz gerekir.

 Artırmak <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> şimdi bağlantı davranış AlwaysOn SqlClient için bir AlwaysOn Kullanılabilirlik Grubu (ağ) için otomatik olarak daha hızlı bağlantı sağlar. Saydam uygulamanız farklı bir alt ağdaki bir AlwaysOn Kullanılabilirlik Grubu (ağ) bağlanma ve hızlı bir şekilde geçerli etkin sunucunun bulur ve sunucunun bir bağlantı sağlar olup olmadığını algılar. Bu sürümden önce bir uygulama eklemek için bağlantı dizesini ayarlamak gerekiyordu `"MultisubnetFailover=true"` bir AlwaysOn Kullanılabilirlik grubuna bağlanan belirtmek için. Bağlantı anahtar sözcüğü ayarını olmadan `true`, bir uygulama için bir AlwaysOn Kullanılabilirlik grubu bağlanırken bir zaman aşımı karşılaşabilirsiniz. Bu sürümle birlikte, bir uygulama olmadığından *değil* ayarlamak gereken <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> için `true` artık. Always On kullanılabilirlik grupları için SqlClient desteği hakkında daha fazla bilgi için bkz: [SqlClient yüksek kullanılabilirlik, olağanüstü durum kurtarma desteği](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).

<a name="WPF461"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 Windows Presentation Foundation bir dizi yenilikleri ve değişiklikleri içerir.

 Geliştirilmiş performans dokunma olaylarını tetikleme gecikme giderilen [!INCLUDE[net_v461](../../../includes/net-v461-md.md)]. Ayrıca, yazarak bir <xref:System.Windows.Controls.RichTextBox> denetimi sırasında hızlı giriş artık işleme iş parçacığını bağlar.

 WPF'de yazım denetleyicisi Windows 8.1 güncelleştirilmiş denetimi geliştirmeleri yazım ve sonraki sürümler için işletim sistemi kullanmak için ek dilleri yazım denetimi destekler.  Windows 8.1 ' den önceki Windows sürümleri üzerinde işlevsellikte değişiklik yoktur.

 Dil için .NET Framework'ün önceki sürümlerinde olduğu gibi bir <xref:System.Windows.Controls.TextBox> denetlemek ya <xref:System.Windows.Controls.RichTextBox> blok bilgi aşağıdaki sırayla arayarak algılandı:

- `xml:lang`, mevcut değilse.

- Geçerli giriş dili.

- Geçerli iş parçacığı kültür.

 WPF dil desteği hakkında ek bilgi için bkz: [WPF blog gönderisi .NET Framework 4.6.1 özellikleri konusunda](http://go.microsoft.com/fwlink/?LinkID=691819).

 Kullanıcı başına özel sözlükte için ek destek [!INCLUDE[net_v461](../../../includes/net-v461-md.md)], WPF genel kayıtlı özel sözlükler tanır. Bu özellik, bunları denetim başına kaydolabilmek ek olarak kullanılabilir.

 WPF önceki sürümlerde, hariç tutulan sözcükler ve Otomatik Düzeltme listeleri özel sözlük tanıyamadı. Bunlar Windows 8.1 ve Windows 10 altına yerleştirilmiş dosyaları kullanımıyla desteklenir `%AppData%\Microsoft\Spelling\<language tag>` dizin.  Bu dosyalar aşağıdaki kurallar geçerli olur:

- Dosya Uzantıları (için eklenen sözcükleri) .dic, .exc (için hariç tutulan sözcükler) ya da .acl (için düzeltme) olması gerekir.

- Dosyaları bayt sırası işareti (BOM) ile başlayan UTF-16 LE düz metin olmalıdır.

- Her satır bir sözcük (Word'ün eklenen ve dışlanan listelerinde) oluşmalıdır veya sözcükleri düzeltme çiftiyle dikey bir çubukla ayrılan ("&#124;") (otomatik düzeltme word listesinde).

- Bu dosyalar salt okunur olarak kabul edilir ve sistem tarafından değiştirilemez.

> [!NOTE]
>  Bu yeni dosya biçimleri WPF yazım API'nin denetimi tarafından doğrudan desteklenmeyen ve uygulamalarda WPF ile sağlanan özel sözlük .lex dosyalarını kullanmaya devam etmeniz gerekir.

 Bir dizi vardır örnekleri [WPF örnekleri](https://msdn.microsoft.com/library/ms771633.aspx) konusuna bakın. Birden fazla 200 (kendi kullanıma dayalı) en popüler örnekleri içine taşınamaz bir [açık kaynak GitHub deposunu](https://github.com/Microsoft/WPF-Samples). Bir çekme isteği veya açılış bize göndererek örneklerimizi geliştirmemize yardımcı olun bir [GitHub sorunu](https://github.com/Microsoft/WPF-Samples/issues).

 DirectX uzantıları WPF içeren bir [NuGet paketi](http://go.microsoft.com/fwlink/?LinkID=691342) yeni uygulamaları sağlayan <xref:System.Windows.Interop.D3DImage> kolaylaştıran, DX10 ve Dx11 ile birlikte çalışmak içerik. Kod bu paket açıldıktan için kaynaklıdır ve kullanılabilir [github'da](https://github.com/Microsoft/WPFDXInterop).

<a name="WWF461"></a> 
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: işlemleri
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> Yöntemi şimdi MSDTC dışında bir Dağıtılmış İşlem Yöneticisi işlem yükseltmek için kullanabilirsiniz. Yeni bir GUID hareket promoter tanıtıcısı belirterek bunu <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yükleme. Bu işlem başarılı olursa işlem özellikleri üzerine yerleştirilen sınırlamalar vardır. MSDTC olmayan işlem promoter kayıtlı sonra aşağıdaki yöntemlerden throw bir <xref:System.Transactions.TransactionPromotionException> çünkü bu yöntemleri MSDTC yükseltmesine gerektirir:

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

 MSDTC olmayan işlem promoter kayıtlı sonra gelecekte dayanıklı kayıtlar için tanımlayan protokolleri kullanılarak kullanılmalıdır. <xref:System.Guid> Hareket promoter kullanarak elde edilebilir <xref:System.Transactions.Transaction.PromoterType%2A> özelliği. Ne zaman işlem yükseltir, işlem promoter sağlayan bir <xref:System.Byte> yükseltilen belirteci temsil eden bir dizi. Bir uygulama olan olmayan-yükseltilmiş MSDTC işlem için yükseltilmiş belirteci edinebilirsiniz <xref:System.Transactions.Transaction.GetPromotedToken%2A> yöntemi.

 Yeni kullanıcılar <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> aşırı yükleme, yükseltme işleminin başarıyla tamamlanması için sırayla belirli çağrı sırası izlemelidir. Bu kurallar yöntemin belgelerinde belgelenmiştir.

<a name="Profile461"></a> 
### <a name="profiling"></a>Profil Oluşturma
 Yönetilmeyen profil oluşturma API Gelişmiş aşağıdaki olmuştur:

 Pdb içinde erişmek için daha iyi destek [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) ASP.Net 5'nde, arabirim derlenmiş bellek içi Roslyn tarafından olmasını derlemeler için çok daha yaygın durumundadır. Profil Araçları yapmadan geliştiriciler için bu diskte geçmişte sıralanmış pdb artık mevcut olabileceğini anlamına gelir. Profil Oluşturucu Araçlar pdb kod geri kod kapsamı veya satır satır Performans Analizi gibi görevleri için kaynak satırları eşlemek için çoğunlukla kullanır. [ICorProfilerInfo7](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md) arabirimi şimdi iki yeni yöntemleri içerir [ICorProfilerInfo7::GetInMemorySymbolsLength](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) ve [ICorProfilerInfo7::ReadInMemorySymbols](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) , yeni API'leri kullanarak bu profil oluşturucu Araçlar, bellek içi PDB verilere erişimi sağlamak için bir profil oluşturucu bir bellek içi PDB bir bayt dizisi olarak içeriğini edinebilir ve ardından işlemesi veya diske seri.

 Daha iyi izleme ICorProfiler arabirimi kullanıyorsanız profil oluşturucular `ICorProfiler` API'nin ReJit işlevlerini dinamik araçları için artık bazı meta verileri değiştirin. Daha önce gibi araçlar IL herhangi bir zamanda izleme, ancak meta verileri yalnızca modülü yükleme zamanında değiştirilmiş. IL meta verileri başvurduğundan, bu yapılabilir araçları türlerini sınırlı. Biz bu sınırları bazıları ekleyerek kaldırılmış [ICorProfilerInfo7::ApplyMetaData](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) modülü, özellikle yeni ekleyerek yüklendikten sonra bir alt kümesini meta verileri düzenlemeleri desteklemek için yöntemi `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, ve `UserString` kaydeder. Bu değişiklik, daha geniş bir temel-çalışma sırasında araçları mümkün kılar.

<a name="NGEN461"></a> 
### <a name="native-image-generator-ngen-pdbs"></a>Yerel Görüntü Oluşturucu (NGEN) PDB'leri
 Bir program bir makinede profil müşterilere makineler arası olay izleme sağlar ve profil oluşturma verileri .NET Framework, kullanıcı önceki sürümlerinde B. makine kullanarak kaynak satırı eşleme ile göz tüm modüller ve yerel görüntüler profili kopyalayın Analiz makine, kaynak yerel eşlemesi oluşturmak için IL PDB içeren makineye. İyi dosyaları phone uygulamaları için görece küçük, gibi olduğunda bu işlem çalışabilir olsa da, dosyaları masaüstü sistemlerine çok büyük ve kopyalamak için önemli zaman gerektirir.

 Ngen pdb ile NGen IL PDB bağımlılığını olmadan IL yerel eşleme içeren bir PDB oluşturabilirsiniz. Makineler arası olay izleme Senaryomuzda gereken tek şey yerel görüntü makine A makine b tarafından oluşturulan PDB kopyalayın ve kullanmak için [hata ayıklama arabirimi erişim API'leri](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) IL PDB'ın kaynak IL eşleme ve yerel okumak için PDB'ın IL yerel eşleme görüntü. Her iki eşlemeleri birleştiren bir kaynak yerel eşleme sağlar. Yerel görüntü PDB tüm modülleri ve yerel görüntüler çok daha küçük olduğundan makine A'dan makine B'ye kopyalama işlemi daha hızlıdır.

<a name="v46"></a> 
## <a name="whats-new-in-net-2015"></a>.NET 2015'te yenilikler nelerdir?
 .NET 2015 tanıtır [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] ve .NET Core. Bazı yeni özellikler için her ikisini de uygulamak ve diğer özellikleri özgü [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] veya [!INCLUDE[net_core](../../../includes/net-core-md.md)].

- **ASP.NET 5**

     .NET 2015 modern bulut tabanlı uygulamalar oluşturmak için yalın bir .NET uygulaması ASP.NET 5'i içerir. ASP.NET 5 modüler olduğu uygulamanızda gerekli özellikler içerebilir. IIS üzerinde barındırılan veya özel bir işlem olarak kendi kendini barındıran ve aynı sunucuda farklı sürümlerini .NET Framework uygulamaları çalıştırabilirsiniz. Bulut dağıtım için tasarlanan yeni bir ortam yapılandırma sistemi içerir.

     MVC, Web API ve Web sayfaları MVC 6 adlı tek bir çerçeve birleştirilmiş. Visual Studio 2015'te yeni araçları aracılığıyla ASP.NET 5 uygulamalar oluşturun. Mevcut uygulamalarınızı yeni .NET Framework üzerinde çalışır; Ancak, MVC 6 veya SignalR 3 kullanan bir uygulama oluşturmak için proje sistemi Visual Studio 2015'te kullanmanız gerekir.

     Bilgi için bkz: [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238).

- **ASP.NET güncelleştirmeleri**

    - **Görev tabanlı zaman uyumsuz yanıt düzenleniyor için API**

         ASP.NET şimdi zaman uyumsuz yanıt Temizleme için basit bir görev tabanlı API sağlar <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, dilinizi 's kullanarak zaman uyumsuz olarak kopyalanması yanıtlar sağlayan `async/await` destekler.

    - `Model binding supports task-returning methods`

         İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ASP.NET Web formları sayfaları ve kullanıcı denetimleri CRUD tabanlı veri işlemler için genişletilebilir, kod odaklı bir yaklaşım etkin Model bağlama özelliği eklendi. Model bağlama sistem artık destekliyor <xref:System.Threading.Tasks.Task>-model bağlama yöntemleri döndürüyor. Bu özellik Web Forms geliştiricilerin ORMs Entity Framework dahil olmak üzere, daha yeni sürümlerini kullanırken veri bağlama sistem kolaylığı zaman uyumsuz ölçeklenebilirlik avantajlarını elde olanak tanır.

         Zaman uyumsuz model bağlama tarafından denetlenir `aspnet:EnableAsyncModelBinding` yapılandırma ayarı.

        ```xml
        <appSettings>
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
        </appSettings>
        ```

         Uygulamalarını hedef [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], onu varsayılan olarak `true`. Çalışan uygulamaları üzerinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] .NET Framework'ün önceki bir sürümünü hedeflemek için bu `false` varsayılan olarak. Yapılandırma ayarı ayarlayarak etkinleştirilebilir `true`.

    - **HTTP/2 Destek (Windows 10)**

         [HTTP/2](http://www.wikipedia.org/wiki/HTTP/2) sağlayan çok daha iyi bağlantı kullanımı (daha az arasındaki gidiş dönüş istemci ve sunucu), HTTP protokolünü yeni bir sürümünü daha düşük gecikme süresi web sayfası için kullanıcıları yüklenirken sonuçlanır.  Tek bir deneyim bir parçası olarak istenen birden çok yapıları için protokol iyileştirme yaptığından web sayfaları (aksine, Hizmetler) HTTP/2, en fazla yararlanır. .NET Framework 4.6 ASP.NET için HTTP/2 desteği eklendi. Ağ işlevlerini birden çok katmanına bulunduğundan, yeni özellikler Windows, IIS ve ASP.NET HTTP/2 etkinleştirmek için gerekli. HTTP/2 ASP.NET ile kullanmak için Windows 10 çalıştırıyor olmalıdır.

         HTTP/2 da desteklenir ve Windows 10 Evrensel Windows Platformu (UWP) kullanan uygulamalar varsayılan değer olarak <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.

         Kullanmak için bir yol sağlamak için [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE) özellik ASP.NET uygulamalarında iki aşırı yüklemeleri, yeni bir yöntemle <xref:System.Web.HttpResponse.PushPromise%28System.String%29> ve <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, eklendi <xref:System.Web.HttpResponse> sınıfı.

        > [!NOTE]
        >  ASP.NET 5 HTTP/2 desteklerken, anında PROMISE özellik olmayan bir henüz eklenmiştir desteği.

         Tarayıcı ile web sunucusu (IIS Windows üzerinde) tüm çalışma yapın. Kullanıcılarınız için tüm ağır kaldırma yapmak zorunda değilsiniz.

         Çoğu [ana tarayıcıları desteklemesi HTTP/2](http://www.wikipedia.org/wiki/HTTP/2), sunucunuz destekliyorsa, kullanıcılarınızın HTTP/2 Destek'ten faydalanırsınız olasıdır.

    - **Belirteç bağlama protokolü desteği**

         Microsoft ve Google işbirliği adlı kimlik doğrulama için yeni bir yaklaşım üzerinde [belirteci bağlama Protokolü](https://github.com/TokenBinding/Internet-Drafts). , Kimlik doğrulama belirteçleri (önbelleğindeki, tarayıcı) kullanılabilir çalınması ve parolanızı ya da ayrıcalıklı herhangi bir bilgi gerek kalmadan suçlular aksi güvenli kaynaklarına (örn, banka hesabı) erişmek için kullandığı olduğunu dayanır. Bu sorunu azaltmak için yeni Protokolü amaçlar.

         Belirteç bağlama protokolü Windows 10'da bir tarayıcı özelliği olarak uygulanacaktır. Böylece kimlik doğrulama belirteçleri yasal olarak doğrulandığı ASP.NET uygulamaları Protokolü katılın. İstemci ve sunucu uygulamaları iletişim kuralı tarafından belirtilen uçtan uca koruma oluşturun.

    - **Rastgele dize karma algoritmaları**

         .NET Framework 4.5 sunulan bir [rastgele dize karma algoritması](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md). Ancak, bunu ASP.NET tarafından nedeniyle bazı ASP.NET desteklenmiyordu özellikleri bağımlı olduğu bir kararlı karma kod. İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], rastgele dize karma algoritmaları artık desteklenmektedir. Bu özelliği etkinleştirmek için kullanın `aspnet:UseRandomizedStringHashAlgorithm` yapılandırma ayarı.

        ```xml
        <appSettings>
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
        </appSettings>
        ```

- **ADO.NET**

     ADO .NET şimdi her zaman şifreli özelliği SQL Server 2016 Community Technology Preview 2 (CTP2) kullanılabilir destekler. Her zaman şifreli ile SQL Server şifrelenmiş veriler üzerinde işlemler yapabilir ve Müşteri'nin güvenilen ortamı içindeki ve sunucuda uygulamayla en iyi tüm şifreleme anahtarı bulunur. Her zaman şifreli DBAs düz metin veri erişimi olmayan şekilde müşteri verilerin güvenliğini sağlar. Şifreleme ve şifre çözme veri olur saydam sürücü düzeyinde, mevcut uygulamalarına yapılacak değişiklikler en aza indirir. Ayrıntılar için bkz [(veritabanı altyapısı)'her zaman şifreli](/sql/relational-databases/security/encryption/always-encrypted-database-engine) ve [(istemci geliştirme)'her zaman şifreli](/sql/relational-databases/security/encryption/always-encrypted-client-development).

- **yönetilen kod için 64-bit JIT derleyicisi**

     .NET Framework 4.6 64-bit JIT Derleyici (ilk olarak kod adı RyuJIT) yeni bir sürümünü içerir. Yeni 64 bit derleyici eski 64-bit JIT Derleyici önemli ölçüde performans artışı sağlar. Yeni 64 bit Derleyici, .NET Framework 4.6 üstünde çalıştıran 64 bit işlemleri için etkinleştirilir. Uygulamanızı bir 64-bit işlem olarak 64-bit derlenmiş ise veya AnyCPU çalışır ve bir 64-bit işletim sisteminde çalışır. Dikkatli olarak saydam yeni derleyici geçiş yapmak için gerçekleştirilecek olsa da, davranış değişiklikleri mümkündür. Yeni JIT Derleyici kullanırken doğrudan karşılaştığı sorunları hakkında duymak isteriz. Lütfen aracılığıyla Bize Ulaşın [Microsoft Connect](http://connect.microsoft.com/) yeni 64-bit JIT Derleyici ilgili bir sorunla karşılaşırsanız.

     Yeni 64-bit JIT Derleyici ayrıca SIMD etkin türleri ile birlikte, donanım SIMD hızlandırma özellikler içerir <xref:System.Numerics> iyi performans iyileştirmeleri sağlayabilen ad alanı.

- **Derleme yükleyicisi geliştirmeleri**

     Karşılık gelen bir NGEN görüntü yüklendikten sonra derleme yükleyicisi şimdi daha verimli bir şekilde kaldırma IL derlemeleri tarafından bellek kullanır. Bu değişiklik (örneğin, Visual Studio) büyük 32-bit uygulamalar için özellikle yararlıdır ve ayrıca fiziksel bellekten tasarruf sanal bellek azaltır.

- **Taban sınıf kitaplığı değişiklikleri**

     Yeni API'lerin geçici eklenmiş [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] önemli senaryoları etkinleştirmek için. Bunlar aşağıdaki değişiklikler ve eklemeler şunlardır:

    - **IReadOnlyCollection\<T > uygulamaları**

         Ek koleksiyonları uygulamak <xref:System.Collections.Generic.IReadOnlyCollection%601> gibi <xref:System.Collections.Generic.Queue%601> ve <xref:System.Collections.Generic.Stack%601>.

    - **CultureInfo.CurrentCulture ve CultureInfo.CurrentUICulture**

         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> Ve <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> özellikleri artık okuma-yazma yerine salt okunur. Yeni bir atarsanız <xref:System.Globalization.CultureInfo> bu özellikler tarafından tanımlanan geçerli iş parçacığı kültür nesnesine `Thread.CurrentThread.CurrentCulture` özelliği ve geçerli kullanıcı Arabirimi iş parçacığı tarafından tanımlanan kültür `Thread.CurrentThread.CurrentUICulture` özelliklerini de değiştirebilirsiniz.

    - **Çöp toplama (GC) geliştirmeleri**

         <xref:System.GC> Sınıfı şimdi içerir <xref:System.GC.TryStartNoGCRegion%2A> ve <xref:System.GC.EndNoGCRegion%2A> çöp toplama kritik yol yürütülmesi sırasında izin vermeyecek şekilde izin yöntemleri.

         Yeni bir aşırı yüklemesini <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi vermediğini, denetimine küçük nesne yığın ve büyük nesne yığın gözden geçirilmiştir ve sıkıştırılmış veya yalnızca gözden geçirilmiştir.

    - **SIMD etkin türleri**

         <xref:System.Numerics> Ad alanı artık çeşitli içerir SIMD etkin türleri gibi <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, ve <xref:System.Numerics.Vector4>.

         Yeni 64-bit JIT Derleyici donanım SIMD ivmesini da içerdiği için özellikle önemli performans geliştirmeleri SIMD etkin türleri yeni 64-bit JIT derleyicisi ile kullanırken yoktur.

    - **Şifreleme güncelleştirmeleri**

         <xref:System.Security.Cryptography?displayProperty=nameWithType> API güncelleştiriliyor desteklemek için [Windows CNG şifreleme API'leri](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx). .NET Framework'ün önceki sürümlere dayanıyordu tamamen açık bir [Windows şifreleme API'leri önceki sürümünü](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx) için temel olarak <xref:System.Security.Cryptography?displayProperty=nameWithType> uygulaması. Bunu desteklediğinden CNG API desteklemek için istekleri bizde [modern şifreleme algoritmalarını](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support), belirli uygulamaları kategorileri için önemli olan.

         .NET Framework 4.6 Windows CNG şifreleme API'leri desteklemek için aşağıdaki yeni geliştirmeleri içerir:

        - Bir dizi X509 için genişletme yöntemleri sertifikalar, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` ve `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, CAPI tabanlı mümkün olduğunda bir uygulama yerine CNG tabanlı bir uygulama döndürür. (Bazı akıllı kartlar, vb. hala CAPI gerektirir ve geri dönüş API'leri tanıtıcı).

        - <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> RSA algoritması CNG uyarlamasını sağlayan sınıf.

        - RSA API geliştirmeler böylece ortak Eylemler atama artık gerek yoktur. Örneğin, verileri kullanarak şifreleme bir <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> nesnesi .NET Framework'ün önceki sürümlerinde aşağıdaki gibi kod gerektirir.

             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

             Yeni şifreleme API'leri .NET Framework 4.6 kullanan kodu cast önlemek için şu şekilde yazılabilir.

             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

    - **Tarihler ve saatler için veya UNIX zamandan dönüştürmek için destek**

         Aşağıdaki yeni yöntemler eklenmiştir <xref:System.DateTimeOffset> UNIX zaman kaynağı veya tarih ve saat değerlerini dönüştürme desteklemek için yapısı:

        - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

        - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - **Uyumluluk anahtarları**

         Yeni <xref:System.AppContext> sınıf kitaplığı yazıcılar, kullanıcılar için yeni işlevsellik Tekdüzen çevirin mekanizmaya sağlayan yeni bir uyumluluk özellik ekler. Gevşek bağlanmış bir sözleşme vazgeçme isteği iletişim kurmak için bileşenler arasındaki oluşturur. Var olan işlevselliği için bir değişiklik yapıldığında bu genellikle önemli bir özelliktir. Buna karşılık, zaten var. bir örtük katılımı yeni işlevsellik için.

         İle <xref:System.AppContext>, kitaplıkları tanımlayın ve onlara bağımlı kod çalışırken sunmaya uyumluluk anahtarları kitaplığı davranışını etkilemek için bu anahtarları ayarlayabilirsiniz. Varsayılan olarak, kitaplıkları, yeni işlevsellik sağlar ve bunlar yalnızca alter (diğer bir deyişle, önceki işlevselliği sağladıkları) anahtarı ayarlanırsa.

         Bir uygulama (veya bir kitaplık) bir anahtar değeri bildirebilirsiniz (her zaman olduğu bir <xref:System.Boolean> değeri) bağımlı kitaplığı tanımlayan. Anahtarı her zaman örtülü olarak başvuruluyor `false`. Anahtar ayarını `true` sağlar. Anahtar açıkça ayarını `false` yeni davranış sağlar.

        ```csharp
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
        ```

         Bir tüketici anahtarı değeri belirtmiş ve sonra uygun şekilde onun üzerinde işlem kitaplığının denetlemeniz gerekir.

        ```csharp
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow)) 
        {
           // This is the case where the switch value was not set by the application. 
           // The library can choose to get the value of shouldThrow by other means. 
           // If no overrides nor default values are specified, the value should be 'false'. 
           // A false value implies the latest behavior.
        }

           // The library can use the value of shouldThrow to throw exceptions or not.
           if (shouldThrow) 
           {
              // old code
           }
           else {
              // new code
           }
        }
        ```

         Bir kitaplık tarafından kullanıma sunulan resmi bir sözleşme olduğundan anahtarları için tutarlı bir biçim kullanmak faydalıdır. Aşağıdaki iki belirgin biçimler geçerlidir.

        - *Anahtar*. *ad alanı*. *backendswitch*

        - *Anahtar*. *Kitaplık*. *backendswitch*

    - **Görev tabanlı zaman uyumsuz desen (TAP) değişiklikleri**

         Hedef uygulamalar için [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], <xref:System.Threading.Tasks.Task> ve <xref:System.Threading.Tasks.Task%601> kültür ve UI kültürü çağıran iş parçacığı nesneleri devralır. .NET Framework'ün önceki sürümlerini hedefleyen ya da belirli bir .NET Framework sürümünü oluşturmayın uygulamalarınızın davranışını etkilenmez. Daha fazla bilgi için "Kültür ve görev tabanlı zaman uyumsuz işlemler" bölümüne bakın <xref:System.Globalization.CultureInfo> sınıfı konu.

         <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> Sınıfı gibi belirli bir zaman uyumsuz denetim akışı için yerel olan ortam verilerini temsil eden olanak tanır bir `async` yöntemi. İş parçacıkları arasında veri kalıcı hale getirmek için kullanılabilir. Ortam veri olduğundan ya da değiştiğinde bildirilir bir geri çağırma yöntemi de tanımlayabilirsiniz <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> özelliği açıkça değiştirilirse, veya iş parçacığının içeriği geçiş karşılaştığından.

         Üç kullanışlı yöntemler <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, ve <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, belirli bir durumdaki tamamlanan görevler döndürmek için görev tabanlı zaman uyumsuz desen (TAP) eklenmiştir.

         <xref:System.IO.Pipes.NamedPipeClientStream> Sınıfı şimdi kendi yeni ile zaman uyumsuz iletişim destekler <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>. yöntem.

    - **EventSource şimdi olay günlüğüne yazma destekler**

         Artık kullanabilirsiniz <xref:System.Diagnostics.Tracing.EventSource> günlüğüne yönetimsel veya işletimsel messages sınıfı olay günlüğüne ek olarak makinede oluşturulan ETW oturumlarına için. Geçmişte, bu işlev için Microsoft.Diagnostics.Tracing.EventSource NuGet paketi kullanmanız gerekiyordu. Bu işlev artık yerleşik-.NET Framework 4.6.

         NuGet paketi ve .NET Framework 4.6 aşağıdaki özelliklerle güncelleştirilmiştir:

        - **Dinamik olayları**

             "Anında" olay yöntemleri oluşturmadan tanımlanan olaylar sağlar.

        - **Zengin yüklerde**

             İlkel türler, yükü olarak geçirilecek yanı sıra özel öznitelikli sınıfları ve diziler sağlar

        - **İzleme etkinliği**

             Tüm etkin etkinlikleri temsil eden bir Kimliğe sahip aralarında etiketi olayları başlatma ve durdurma olaylarına neden olur.

         Bu destek özellikleri için aşırı yüklenmiş <xref:System.Diagnostics.Tracing.EventSource.Write%2A> yöntemi eklenmiştir <xref:System.Diagnostics.Tracing.EventSource> sınıfı.

- **Windows Presentation Foundation (WPF)**

    - **HDPI geliştirmeleri**

         WPF HDPI desteği içinde daha iyi şimdi [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Kenarlıklar denetimleriyle kırpmayı örneklerini azaltmak için yuvarlama Düzen değişiklikler yapıldı. Varsayılan olarak, bu özellik yalnızca etkin, <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4.6 ayarlanır.  Framework'ün önceki sürümlerini hedefleyen ancak üzerinde çalışan uygulamalar [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] yeni davranış aşağıdaki satırı ekleyerek kabul [ \<çalışma zamanı >](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config dosyasının:

        ```xml
        <AppContextSwitchOverrides
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
        />
        ```

         WPF windows farklı DPI ayarlarıyla (çoklu DPI kurulum) birden çok monitör payından şimdi blacked çıkış bölgeler tamamen işlenir. Aşağıdaki satırı ekleyerek bu davranışı iptal seçebilirsiniz `<appSettings>` app.config dosyasının bu yeni davranışı devre dışı bırakmak için:

        ```xml
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>
        ```

         DPI ayarına göre doğru imleci yüklemeyi otomatik olarak eklendi desteği <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.

    - **Dokunma daha iyi?**

         Müşteri raporları [Bağlan](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) beklenmeyen davranışlara ele içinde üretir touch [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]. Windows mağazası uygulamaları ve WPF uygulamaları çift dokunun eşiği artık Windows 8.1 ve üzeri aynıdır.

    - **Saydam alt pencere desteği**

         WPF'de [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] saydam alt windows Windows 8.1 ve üstünü destekler. Bu, en üst düzey windows dikdörtgen olmayan ve saydam alt öğe pencerelerini oluşturmanıza olanak sağlar. Bu özellik ayarlayarak etkinleştirebilirsiniz <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> özelliğine `true`.

- **Windows Communication Foundation (WCF)**

    - **SSL desteği**

         WCF artık SSL sürüm TLS 1.1 ve TLS 1.2, SSL 3.0 ve TLS 1.0, ek olarak NetTcp taşıma güvenliği ve istemci kimlik doğrulaması ile kullanırken destekler. Artık, hangi protokolü kullanın ya da eski daha az güvenli protokolleri devre dışı bırakmak için seçmek mümkündür. Bu ayarı tarafından yapılabilir <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> özelliği ya da aşağıdaki yapılandırma dosyasına ekleyerek.

        ```xml
        <netTcpBinding>
           <binding>
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >
                 <transport clientCredentialType="None|Windows|Certificate"
                            protectionLevel="None|Sign|EncryptAndSign"
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                    </transport>
              </security>
           </binding>
        </netTcpBinding>
        ```

    - **Farklı HTTP bağlantılarını kullanarak ileti gönderme**

         WCF artık belirli iletileri farklı temel HTTP bağlantılarını kullanarak gönderildiğinden emin olmak kullanıcılara izin verir. Bunu yapmak için iki yol vardır:

        - **Bir bağlantı grup adı ön eki kullanma**

             Kullanıcılar bir önek elde gibi WCF bağlantısı grup adı için kullanacağı bir dize belirtebilirsiniz. Farklı öneklerle iki ileti farklı temel HTTP bağlantılarını kullanılarak gönderilir. İleti için bir anahtar/değer çifti ekleyerek öneki ayarlayın <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> özelliği. "HttpTransportConnectionGroupNamePrefix"; anahtarıdır istediğiniz önek değerdir.

        - **Farklı bir kanal fabrikaları kullanma**

             Kullanıcılar, farklı bir kanal üreteçleri tarafından oluşturulan kanalları kullanılarak gönderilen iletileri farklı temel HTTP bağlantılarını kullanmanızı sağlar bir özelliğini de etkinleştirebilirsiniz. Bu özelliği etkinleştirmek için kullanıcıların aşağıdaki ayarlamalısınız `appSetting` için `true`:

            ```xml
            <appSettings>
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
            </appSettings>
            ```

- **Windows Workflow Foundation (WWF)**

     Şimdi, istek zaman aşımına uğramadan bekleyen bir "Protokolü olmayan" yer işareti olduğunda bir iş akışı hizmeti için bir düzen dışı operation isteğini tutacak saniye sayısını belirtebilirsiniz. "Protokolü olmayan" yer işareti bekleyen alma etkinliklerle ilgili olmayan bir yer işareti ' dir. Bazı etkinlikler Protokolü olmayan yer işareti varolduğunu belirgin olmayabilir, uygulama içinde Protokolü olmayan yer işaretleri oluşturun. Bunlar, durumu ve çekme içerir. Bu nedenle Durum makinesi ile uygulanan bir iş akışı hizmeti varsa veya çekme etkinliğini içeren, büyük olasılıkla olacak Protokolü olmayan yer işaretleri gerekir. Aşağıdakine benzer bir satır ekleyerek aralığı belirtin `appSettings` app.config dosyasının:

    ```xml
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
    ```

     Varsayılan değer 60 saniyedir. Varsa `value` ayarlanmış 0 olarak düzen dışı istekler hemen metinle şuna benzer bir hata ile reddedilir:

    ```
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees. 
    ```

     Bu sipariş işlem iletisi alırsanız, aldığınız iletinin ve hiçbir Protokolü olmayan yer işaretleri vardır.

     Varsa değerini `FilterResumeTimeoutInSeconds` sıfır olmayan bir öğedir Protokolü olmayan yer işaretleri vardır ve zaman aşımı aralığı sona, işlem zaman aşımı iletisi vererek başarısız olur.

- **İşlemler**

     Bir özel duruma neden oldu işlem türetildiği için Dağıtılmış işlem tanımlayıcısı artık ekleyebilirsiniz <xref:System.Transactions.TransactionException> oluşturulmasına. Aşağıdaki anahtarı ekleyerek bunu `appSettings` app.config dosyasının:

    ```xml
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/> 
    ```

     Varsayılan değer `false` şeklindedir.

- **Ağ oluşturma**

    - **Yuva yeniden kullanma**

         Windows 10 giden TCP bağlantıları için yerel bağlantı noktaları yeniden kullanarak makine kaynakları daha iyi kullanımı sağlayan yeni bir ağ yüksek ölçeklenebilirlik algoritmasını içerir. .NET Framework 4.6, yeni davranışı yararlanmak .NET uygulamaları etkinleştirme yeni algoritmasını destekler. Önceki Windows sürümlerinde, bir hizmet ölçeklenebilirliğini bağlantı noktası Tükenme olduğunda yük altında neden olarak kısıtlayacaktır bir yapay eşzamanlı bağlantı sınırı (genellikle 16,384, dinamik bağlantı noktası aralığının varsayılan boyut), vardı.

         İçinde [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], etkili bir şekilde eşzamanlı bağlantı 64 K sınırını kaldırır Bağlantı noktası yeniden etkinleştirmek için iki yeni API'ler eklenmiştir:

        - <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> Numaralandırma değeri.

        - <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> Özelliği.

         Varsayılan olarak, <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliği `false` sürece `HWRPortReuseOnSocketBind` değeri `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` kayıt defteri anahtarını 0x1 olarak ayarlayın. HTTP bağlantılarında yerel bağlantı noktası yeniden etkinleştirmek için ayarlanmış <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> özelliğine `true`. Bu tüm giden TCP yuva bağlantılarından neden <xref:System.Net.Http.HttpClient> ve <xref:System.Net.HttpWebRequest> yeni bir Windows 10 yuva seçeneği kullanmak için [SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx), yerel bağlantı noktası yeniden kullanılmasını sağlar.

         Yalnızca yuva uygulama yazan geliştiriciler belirtebilirsiniz <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> seçeneği yöntem gibi çağırırken <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> giden yuva yerel bağlantı noktaları bağlama sırasında yeniden böylece.

    - **Uluslararası etki alanı adları ve zayıf kod desteği**

         Yeni bir özellik <xref:System.Uri.IdnHost%2A>, eklendi <xref:System.Uri> uluslararası etki alanı adları ve PunyCode daha iyi desteklemek için sınıf.

- **Windows Forms denetimleri yeniden boyutlandırma.**

     Bu özellik, Genişletilmiş [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] içerecek şekilde <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> ve <xref:System.Windows.Forms.ToolStripSplitButton> türleri ve tarafından belirtilen dikdörtgen <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> özelliği çizim sırasında kullanılan bir <xref:System.Drawing.Design.UITypeEditor> .

     Bu bir katılımı özelliğidir. Etkinleştirmek için ayarlanmış `EnableWindowsFormsHighDpiAutoResizing` öğesine `true` uygulama yapılandırması (app.config) dosyasında:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Kod sayfası kodlaması için destek**

      [!INCLUDE[net_core](../../../includes/net-core-md.md)] primarily supports the Unicode encodings and by default provides limited support for code page encodings. You can add support for code page encodings available in the .NET Framework but unsupported in [!INCLUDE[net_core](../../../includes/net-core-md.md)] by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method. For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.

- **.NET Native**

     Windows uygulamaları için Windows 10 hedefleyen [!INCLUDE[net_core](../../../includes/net-core-md.md)] ve C# dilinde yazılmıştır veya Visual Basic yararlanabilir uygulamaları IL yerine yerel koda derlenen yeni bir teknoloji. Hızlı Başlangıç ve yürütme sürelerinin tarafından temsil edilen uygulamaları oluşturdukları. Daha fazla bilgi için bkz: [.NET yerel ile derleme uygulamaları](../../../docs/framework/net-native/index.md). Anlamına gelir, kodunuz için .NET nasıl JIT derleme hem NGEN farklıdır ve hangi, inceleyen yerel genel bakış için bkz: [.NET yerel ve derleme](../../../docs/framework/net-native/net-native-and-compilation.md).

     Visual Studio 2015 ile derlerken uygulamalarınızı varsayılan olarak yerel koda derlenen. Daha fazla bilgi için bkz: [.NET yerel ile çalışmaya başlama](../../../docs/framework/net-native/getting-started-with-net-native.md).

     Hata ayıklama .NET yerel uygulamalarını desteklemek için bir dizi yeni arabirimleri ve numaralandırmalar yönetilmeyen hata ayıklama API'si eklenmiştir. Daha fazla bilgi için bkz: [hata ayıklama (yönetilmeyen API Başvurusu)](../../../docs/framework/unmanaged-api/debugging/index.md) konu.

- **Açık kaynak .NET Framework paketleri**

      [!INCLUDE[net_core](../../../includes/net-core-md.md)] packages such as the immutable collections, [SIMD APIs](http://go.microsoft.com/fwlink/?LinkID=518639), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open source packages on [GitHub](https://github.com/). To access the code, see [NetFx on GitHub](http://go.microsoft.com/fwlink/?LinkID=518634). For more information and how to contribute to these packages, see [.NET Core and Open-Source](../../../docs/framework/get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](http://go.microsoft.com/fwlink/?LinkID=518635).

 [Başa dön](#introduction)

<a name="v452"></a> 
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 yenilikler

- **ASP.NET uygulamaları için yeni API'ler.** Yeni <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> yöntemleri inceleyin ve yanıt istemci uygulamasına Temizlenen gibi yanıt üst bilgileri ve durum kodunu değiştirmenizi sağlar. Bu yöntemleri yerine kullanmayı <xref:System.Web.HttpApplication.PreSendRequestHeaders> ve <xref:System.Web.HttpApplication.PreSendRequestContent> olayları; daha etkili ve güvenilir.

     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> Yöntemi küçük arka plan iş öğeleri zamanlamanıza olanak sağlar. ASP.NET bu öğeler izler ve tüm arka plan iş öğeleri tamamlanana kadar aniden çalışan işlemi sonlandırılıyor gelen IIS engeller. Bu yöntem, bir ASP.NET yönetilen uygulama etki alanı dışında çağrılamaz.

     Yeni <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> ve <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> özellikleri yanıt üstbilgileri yazılan olup olmadığını gösteren bir Boole değerleri döndürür. Bu özellikleri emin olmak için API'leri gibi çağıran kullanabileceğiniz <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (üstbilgileri yazılmış, özel durumlar oluşturma) başarılı olur.

- **Windows Forms denetimleri yeniden boyutlandırma.** Bu özellik genişletilmiştir. Sistem DPI ayarı şimdi bileşenleri aşağıdaki ek denetimleri (örneğin, birleşik giriş kutularında açılan ok) yeniden boyutlandırmak için de kullanabilirsiniz:

     <xref:System.Windows.Forms.ComboBox>    <xref:System.Windows.Forms.ToolStripComboBox>    <xref:System.Windows.Forms.ToolStripMenuItem>    <xref:System.Windows.Forms.Cursor>    <xref:System.Windows.Forms.DataGridView>    <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

     Bu bir katılımı özelliğidir. Etkinleştirmek için ayarlanmış `EnableWindowsFormsHighDpiAutoResizing` öğesine `true` uygulama yapılandırması (app.config) dosyasında:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

- **Yeni iş akışı özelliği.** Kullanan bir kaynak yöneticisi <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> yöntemi (ve bu nedenle uygulama <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi) yeni kullanabilirsiniz <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> yöntemi aşağıdaki istemek için:

    - Microsoft Dağıtılmış İşlem Düzenleyicisi (MSDTC) işlem harekete yükseltin.

    - Değiştir <xref:System.Transactions.IPromotableSinglePhaseNotification> ile bir <xref:System.Transactions.ISinglePhaseNotification>, tek aşamalı yürütme destekleyen sağlam bir kaydı olduğu.

     Bu aynı uygulama etki alanı içinde yapılabilir ve yükseltme gerçekleştirmek için MSDTC ile etkileşim için herhangi bir ek yönetilmeyen kod gerektirmez. Yalnızca bir bekleyen çağrısından olduğunda yeni yöntemi çağrılabilir <xref:System.Transactions?displayProperty=nameWithType> için <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote` yükseltilebilir kaydı tarafından uygulanan yöntemi.

- **Profil oluşturma geliştirmeleri.** Aşağıdaki yeni yönetilmeyen profil oluşturma API daha sağlam profil sağlar:

     [Cor_prf_assembly_reference_ınfo yapısı](../../../docs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md) [cor_prf_hıgh_monıtor numaralandırması](../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) [GetAssemblyReferences yöntemi](../../../docs/framework/unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md) [GetEventMask2 yöntemi](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) [SetEventMask2 yöntemi](../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) [AddAssemblyReference yöntemi](../../../docs/framework/unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

     Önceki `ICorProfiler` uygulamaları desteklenen bağımlı derlemelerin yavaş yükleniyor. Yeni profil oluşturma API uygulama tamamen hazırlandıktan sonra hemen yüklenen yerine yüklenebilir olması için Profil Oluşturucu tarafından eklenen bağımlı derlemeleri gerektirir. Bu değişiklik var olan kullanıcıları etkilemez `ICorProfiler` API'leri.

- **Hata ayıklama iyileştirmeleri.** Aşağıdaki yeni yönetilmeyen hata ayıklama API'ler bir profil oluşturucu ile daha iyi tümleştirme sağlar. Profil Oluşturucu yanı sıra yerel değişkenleri ve kod tarafından eklenen erişim meta verileri derleyici ReJIT istekleri tarafından üretilen artık olduğunda hata ayıklama dökümü.

     [SetWriteableMetadataUpdateMode yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md) [EnumerateLocalVariablesEx yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md) [GetLocalVariableEx yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md) [GetCodeEx yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md) [Getactiverejitrequestılcode yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md) [Getınstrumentedılmap yöntemi](../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- **Değişiklik izleme olay.** .NET Framework 4.5.2 büyük yüzey alanı için işlem dışı, izleme için Windows olay ETW tabanlı Etkinlik izleme sağlar. Bu, tek tek isteklerin ve iş parçacıkları arası etkinlikleri maliyetlerini doğru bir şekilde izlemenize basit araçları sağlamak Gelişmiş Güç Yönetimi (APM) satıcıları sağlar.  Yalnızca ETW denetleyicileri bunları etkinleştirdiğinizde bu olaylar oluşturulur; Bu nedenle, değişiklikleri önceden yazılmış ETW kodu veya devre dışı ETW ile çalışan bir kod etkilemez.

- **Bir işlem yükseltme ve sağlam bir liste dönüştürme**

     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType>Yeni bir API, .NET Framework 4.5.2 ve 4.6 eklenir:

    ```csharp
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                              IPromotableSinglePhaseNotification promotableNotification,
                                              ISinglePhaseNotification enlistmentNotification,
                                              EnlistmentOptions enlistmentOptions)
    ```

     Yöntemi tarafından daha önce oluşturulmuş bir kaydı tarafından kullanılabilir <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> yanıt olarak <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> yöntemi. Bunu ister `System.Transactions` MSDTC işleminde harekete yükseltmek için ve "yükseltilebilir kaydı için sağlam bir kaydı dönüştürmek için". Bu yöntem başarıyla tamamlandıktan sonra <xref:System.Transactions.IPromotableSinglePhaseNotification> arabirimi artık başvurulur tarafından `System.Transactions`, ve gelecekteki tüm bildirimler sağlanan ulaşır <xref:System.Transactions.ISinglePhaseNotification> arabirimi. Söz konusu kaydı, işlem günlüğü ve kurtarma destekleyen bir dayanıklı kaydı davranmalıdır. Başvurmak <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> Ayrıntılar için. Ayrıca, kaydı desteklemelidir <xref:System.Transactions.ISinglePhaseNotification>.  Bu yöntem için *yalnızca* işlenirken çağrılabilir bir <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> çağırın. Bu durumda, değilse bir <xref:System.Transactions.TransactionException> özel durumu oluşur.

 [Başa dön](#introduction)

<a name="v451"></a> 
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 yenilikler
 **Nisan 2014 güncelleştirmeleri**:

- [Visual Studio 2013 güncelleştirme 2](http://go.microsoft.com/fwlink/p/?LinkId=393658) bu senaryoları desteklemek için taşınabilir sınıf kitaplığı şablonları için güncelleştirmeleri içerir:

    - Windows çalışma zamanı API'leri, Windows 8.1, Windows Phone 8.1 ve Windows Phone Silverlight 8.1 hedefleyen taşınabilir kitaplıkları kullanabilirsiniz.

    - Windows 8.1 veya Windows Phone 8.1 hedeflediğinizde, taşınabilir kitaplıklara XAML (Windows.UI.XAML türleri için) ekleyebilirsiniz. Aşağıdaki XAML şablonları desteklenir: boş bir sayfa, kaynak sözlüğü, şablonlu denetim ve kullanıcı denetimi.

    - Hedef Windows 8.1 ve Windows Phone 8.1 mağazası uygulamaları kullanmak için bir taşınabilir Windows çalışma zamanı bileşeni (.winmd dosyası) oluşturabilirsiniz.

    - Taşınabilir sınıf kitaplığı gibi bir Windows mağazası veya Windows Phone mağazası sınıf kitaplığı yeniden hedefleyin.

     Bu değişiklikler hakkında daha fazla bilgi için bkz: [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

- Şimdi .NET Framework belgelerine içeriği [!INCLUDE[net_native](../../../includes/net-native-md.md)], oluşturma ve Windows uygulamalarını dağıtmak için bir ön derleme teknoloji olduğu. [!INCLUDE[net_native](../../../includes/net-native-md.md)]uygulamalarınızı Ara dile (IL) yerine, doğrudan yerel kod için daha iyi performans için derler. Ayrıntılar için bkz [.NET yerel ile derleme uygulamaları](../../../docs/framework/net-native/index.md).

- [.NET Framework başvuru kaynağı](http://referencesource.microsoft.com/) yeni gözatma deneyimini ve gelişmiş işlevsellik sağlar. .NET Framework kaynak kodu çevrimiçi gözatabilirsiniz [başvurusunu karşıdan](http://referencesource.microsoft.com/download.html) çevrimdışı izleme ve hata ayıklama sırasında (düzeltme eklerini ve güncelleştirmeleri dahil) kaynakları ilerleyebilirsiniz. Daha fazla bilgi için blog girişine bakın [.NET başvuru kaynağı için yeni bir görünüm](https://blogs.msdn.microsoft.com/dotnet/2014/02/24/a-new-look-for-net-reference-source/).

 Çekirdek yeni özellikler ve .NET Framework 4.5.1'deki geliştirmeler şunları içerir:

- Otomatik bağlama yönlendirmesini derlemeler için. İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], hedefleyen bir uygulamayı derlediğinizde [!INCLUDE[net_v451](../../../includes/net-v451-md.md)], bağlama yeniden yönlendirmeleri eklenebilir uygulama yapılandırma dosyasına uygulamanız veya bileşenlerinin aynı bütünleştirilmiş kodda birden fazla sürümünü başvurursanız. Bu özellik .NET Framework'ün daha eski sürümlerini hedefleyen projeler için de etkinleştirebilirsiniz. Daha fazla bilgi için bkz: [nasıl yapılır: etkinleştirme ve devre dışı bırakmak, bağlama otomatik yeniden yönlendirme](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).

- Sunucu ve bulut uygulamalarının performansını geliştiricilere yardımcı olmak için tanılama bilgilerini toplamak için yeteneği. Daha fazla bilgi için bkz: <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> ve <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> yöntemleri <xref:System.Diagnostics.Tracing.EventSource> sınıfı.

- Açıkça (LOH) büyük nesne yığın çöp toplama sırasında compact yeteneği. Daha fazla bilgi için bkz: <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> özelliği.

- .NET Framework sonra ek performans iyileştirmeleri ASP.NET uygulama askıya alma, çok çekirdekli JIT geliştirmeleri ve daha hızlı bir uygulama başlatma gibi güncelleştirin. Ayrıntılar için bkz [.NET Framework 4.5.1 duyuru](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/) ve [ASP.NET uygulama askıya](https://blogs.msdn.microsoft.com/dotnet/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog postası.

 Windows Forms geliştirmeler:

- Windows Forms denetimleri yeniden boyutlandırma. Uygulamanız için uygulama yapılandırma dosyasına (app.config) bir giriş oturum kullanmama tarafından denetimleri (örneğin, bir özellik kılavuzunda görünmesini simgeleri) bileşenlerinin yeniden boyutlandırmak için sistem DPI ayarı kullanabilirsiniz. Bu özellik şu anda aşağıdaki Windows Forms denetimlerinde desteklenir:

     <xref:System.Windows.Forms.PropertyGrid>    <xref:System.Windows.Forms.TreeView>Bazı yönlerini <xref:System.Windows.Forms.DataGridView> (bkz [4.5.2'deki yeni özellikler](#v452) desteklenen ek denetimler için)

     Bu özelliği etkinleştirmek için yeni bir ekleme \<appSettings > ayarlama ve yapılandırma dosyası (app.config) öğesine `EnableWindowsFormsHighDpiAutoResizing` öğesine `true`:

    ```xml
    <appSettings>
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
    </appSettings>
    ```

 .NET Framework uygulamalarında hata ayıklama sırasında geliştirmeleri [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] içerir:

- Visual Studio Hata Ayıklayıcısı'ndaki dönüş değerleri. Yönetilen bir uygulamada hata ayıklama zaman, [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], türleri ve yöntemleri için değerleri otomatik değişkenler penceresi görüntüler döndürür. Bu bilgiler, masaüstü, Windows mağazası ve Windows Phone uygulamaları için kullanılabilir. Daha fazla bilgi için bkz: [inceleyin dönüş değerleri yöntem çağrılarının](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx) MSDN Kitaplığı'nda.

- Düzenle ve devam et 64-bit uygulamalar için. [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]yönetilen uygulamaların Masaüstü, Windows mağazası ve Windows Phone için 64-bit Düzenle ve devam et özelliğini destekler. 32 bit ve 64-bit uygulamaları için mevcut kısıtlamaları yürürlükte kalır (son Kısım bkz [desteklenen kod değişiklikleri (C#)](/visualstudio/debugger/supported-code-changes-csharp) makale).

- Zaman uyumsuz algılayan hata ayıklama. Zaman uyumsuz uygulamalarda hata ayıklama kolaylaştırmak için [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]çağrı yığını zaman uyumsuz programlama desteği derleyicileri tarafından sağlanan altyapı kodu gizler ve aynı zamanda mantıksal izleyebilirsiniz şekilde mantıksal üst çerçeveler zincirde yürütme daha program açıkça. Görevleri penceresini Paralel Görevler penceresi değiştirir ve için belirli bir kesme noktası ile ilgili görevleri görüntüler ve ayrıca şu anda etkin ya da uygulama zamanlanmış diğer görevleri görüntüler. Bu özellik "zaman uyumsuz algılayan hata ayıklama" bölümündeki hakkında bilgi edinebilirsiniz [.NET Framework 4.5.1 duyuru](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/).

- Windows çalışma zamanı bileşenleri için daha iyi özel durum desteği. İçinde [!INCLUDE[win81](../../../includes/win81-md.md)], Windows mağazası uygulamaları çıkan özel durumları korumak bile dil sınırlarında özel duruma neden oldu hata hakkındaki bilgi. "Windows mağazası uygulaması geliştirme" bölümünü'deki bu özellik hakkında bilgi edinebilirsiniz [.NET Framework 4.5.1 duyuru](https://blogs.msdn.microsoft.com/dotnet/2013/06/26/announcing-the-net-framework-4-5-1-preview/). 

 İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], kullanabileceğiniz [yönetilen profil temelli iyileştirme Aracı (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md) en iyi duruma getirme [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] masaüstü uygulamalarının yanı sıra uygulamaları.

 ASP.NET 4.5.1 yeni özellikler için bkz: [ASP.NET 4.5.1 ve Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET sitesinde.

 [Başa dön](#introduction)

<a name="core"></a> 
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4. 5 ' yenilikler nelerdir?

### <a name="core-new-features-and-improvements"></a>Çekirdek yeni özellikleri ve geliştirmeleri

- Reduce sistemi yeteneği algılama ve dağıtım sırasında .NET Framework 4 uygulamaları kapatarak yeniden başlatır. Bkz: [sistem yeniden başlatmalarını azaltma .NET Framework 4.5 yüklemeleri sırasında](../../../docs/framework/deployment/reducing-system-restarts.md).

- 64 bit platformlarda 2 gigabayt (GB) büyük diziler için destek. Bu özellik, uygulama yapılandırma dosyasında etkinleştirilebilir. Bkz: [ \<gcAllowVeryLargeObjects > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), nesne boyutu ve dizi büyüklüğü diğer kısıtlamalar da listelerinin.

- Daha iyi performans sunucuları için arka plan çöp toplama yoluyla. Sunucu çöp toplama kullandığınızda [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], arka plan çöp toplama otomatik olarak etkinleştirilir. Arka plan sunucu çöp toplama bölümüne bakın [çöp toplama Temelleri](../../../docs/standard/garbage-collection/fundamentals.md) konu.

- İsteğe bağlı olarak uygulama performansını artırmak için çok çekirdekli işlemciler kullanılabildiğinden arka plan tam zamanında (JIT) derleme. Bkz: <xref:System.Runtime.ProfileOptimization>.

- Ne kadar normal ifade altyapısı sınırlama yeteneği normal bir ifade zaman aşımına uğramadan önce çözümlemeye çalışır. Bkz: <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> özelliği.

- Uygulama etki alanı için varsayılan kültürü tanımlama yeteneği. Bkz: <xref:System.Globalization.CultureInfo> sınıfı.

- Unicode (UTF-16) kodlama için konsol desteği. Bkz: <xref:System.Console> sınıfı.

- Sürüm oluşturma kültürel dize sıralama ve karşılaştırma veri desteği. Bkz: <xref:System.Globalization.SortVersion> sınıfı.

- Kaynaklar alınırken daha iyi performans. Bkz: [paketleme ve dağıtma kaynakları](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md).

- Sıkıştırılmış bir dosya boyutunu azaltmak için ZIP sıkıştırma geliştirmeleri. Bkz: <xref:System.IO.Compression?displayProperty=nameWithType> ad alanı.

- Aracılığıyla varsayılan yansıma davranışını geçersiz kılmak için bir yansıma bağlamı özelleştirebilme <xref:System.Reflection.Context.CustomReflectionContext> sınıfı.

- Uluslararası yapılan etki alanı adları (IDNA) uygulamaları 2008 sürümü için destek standart olduğunda <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> sınıfı kullanılan [!INCLUDE[win8](../../../includes/win8-md.md)].

- Dize karşılaştırması Unicode 6.0, .NET Framework kullanıldığında gerçekleştiren işletim sistemi, temsilinin [!INCLUDE[win8](../../../includes/win8-md.md)]. Diğer platformlarda çalıştırırken, .NET Framework Unicode uygulayan kendi dize karşılaştırma verileri içeren 5.x. Bkz: <xref:System.String> sınıfı ve Açıklamalar bölümüne <xref:System.Globalization.SortVersion> sınıfı.

- Karma kodlarını dizeleri üzerinde işlem yeteneği bir uygulama etki alanı temelinde. Bkz: [ \<UseRandomizedStringHashAlgorithm > öğesi](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).

- Türü arasında bölme yansıma desteği <xref:System.Type> ve <xref:System.Reflection.TypeInfo> sınıfları. Bkz: [Windows mağazası uygulamaları için .NET Framework'te yansıma](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md).

### <a name="managed-extensibility-framework-mef"></a>Managed Extensibility Framework (MEF)
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Yönetilen Genişletilebilirlik Çerçevesi (MEF) aşağıdaki yeni özellikleri sağlar:

- Genel türler için destek.

- Öznitelikleri yerine adlandırma kurallarına göre parçaları oluşturmanızı sağlayan kurala dayalı programlama modeli.

- Birden çok kapsamı.

- Bir alt kümesini, oluştururken kullanabileceğiniz MEF [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] uygulamalar. Bu alt olarak kullanılabilir bir [indirilebilir paket](http://go.microsoft.com/fwlink/?LinkId=256238) NuGet galerisinden. Paketi yüklemek için projenizi Visual Studio'da açın, seçin **NuGet paketlerini Yönet** gelen **proje** menü ve çevrimiçi arama `Microsoft.Composition` paket.

 Daha fazla bilgi için bkz: [Yönetilen Genişletilebilirlik Çerçevesi (MEF)](../../../docs/framework/mef/index.md).

### <a name="asynchronous-file-operations"></a>Zaman uyumsuz dosya işlemleri
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], yeni zaman uyumsuz özellikler, C# ve Visual Basic dili için eklenmiştir. Bu özellikler, zaman uyumsuz işlemleri gerçekleştirmek için bir görev tabanlı modeli ekleyin. Bu yeni model kullanmak için g/ç sınıfları zaman uyumsuz yöntemleri kullanın. Bkz: [zaman uyumsuz dosya g/ç](../../../docs/standard/io/asynchronous-file-i-o.md).

<a name="tools"></a> 
### <a name="tools"></a>Araçlar
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], kaynak dosya oluşturucu (Resgen.exe) kullanmak için .resw dosya oluşturmanıza olanak sağlar [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] .resources dosyası uygulamalardan katıştırılmış bir .NET Framework derleme. Daha fazla bilgi için bkz: [Resgen.exe (kaynak dosya oluşturucu)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md).

 Yönetilen profil temelli iyileştirme (Mpgo.exe), yerel görüntü derlemeleri iyileştirerek uygulama başlangıç zamanı, bellek kullanımı (çalışma kümesi boyutu) ve verimliliği artırmak sağlar. Komut satırı aracı yerel görüntü uygulama derlemeler için profil verileri oluşturur. Bkz: [Mpgo.exe (yönetilen profil temelli iyileştirme aracı)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md). İle başlayarak [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)], Mpgo.exe en iyi duruma getirmek için kullanabileceğiniz [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] masaüstü uygulamalarının yanı sıra uygulamaları.

<a name="parallel"></a> 
### <a name="parallel-computing"></a>Paralel bilgi işlem
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] Birkaç yeni özellik ve paralel bilgi işlem geliştirmeleri sağlar. Bunlar, Gelişmiş performans, daha yüksek denetim, zaman uyumsuz programlama için geliştirilmiş destek, yeni veri akışı kitaplığı ve paralel hata ayıklama ve performans analizi için gelişmiş destek içerir. Girişine bakın [.NET 4.5 paralellik yenilikler](http://go.microsoft.com/fwlink/?LinkId=235061) paralel programlama .NET blog ile içinde.

<a name="web"></a> 
### <a name="web"></a>Web
 ASP.NET 4.5 ve 4.5.1 Web Forms, WebSocket desteği, zaman uyumsuz işleyicileri, performans geliştirmeleri ve diğer birçok özellik için model bağlama ekleyin. Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [ASP.NET 4.5 ve Visual Studio 2012](http://msdn.microsoft.com/library/ac9bb7f6-f094-4af7-bad0-acf49a5dbc55) MSDN Kitaplığı'nda.

- [ASP.NET 4.5.1 ve Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET sitesinde.

<a name="networking"></a> 
### <a name="networking"></a>Ağ Oluşturma
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] HTTP uygulamaları için yeni bir programlama arabirimi sağlar. Daha fazla bilgi için yeni bkz <xref:System.Net.Http?displayProperty=nameWithType> ve <xref:System.Net.Http.Headers?displayProperty=nameWithType> ad alanları.

 Destek eklenmiştir de kabul etmek ve varolan kullanarak WebSocket bağlantısı ile etkileşmek için yeni bir programlama arabirimi için <xref:System.Net.HttpListener> ve ilgili sınıflar. Daha fazla bilgi için yeni bkz <xref:System.Net.WebSockets> ad alanı ve <xref:System.Net.HttpListener> sınıfı.

 Ayrıca, [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] aşağıdaki ağ geliştirmeleri içerir:

- RFC uyumlu URI desteği. Daha fazla bilgi için bkz: <xref:System.Uri> ve ilgili sınıflar.

- Uluslararası yapılan etki alanı adı (IDN) ayrıştırma desteği. Daha fazla bilgi için bkz: <xref:System.Uri> ve ilgili sınıflar.

- E-posta adresi uluslararası hale getirme (EAI) desteği. Daha fazla bilgi için bkz: <xref:System.Net.Mail> ad alanı.

- Geliştirilmiş IPv6 desteği. Daha fazla bilgi için bkz: <xref:System.Net.NetworkInformation> ad alanı.

- Çift modlu yuva desteği. Daha fazla bilgi için bkz: <xref:System.Net.Sockets.Socket> ve <xref:System.Net.Sockets.TcpListener> sınıfları.

<a name="client"></a> 
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], Windows Presentation Foundation (WPF), değişiklikler ve aşağıdaki alanlarda geliştirmeler içerir:

- Yeni <xref:System.Windows.Controls.Ribbon.Ribbon> hızlı erişim araç çubuğu, uygulama menüsü ve sekmeleri barındıran bir Şerit kullanıcı arabirimini sağlar denetim.

- Yeni <xref:System.ComponentModel.INotifyDataErrorInfo> zaman uyumlu ve zaman uyumsuz veri doğrulamayı destekleyip arabirimi.

- İçin yeni özellikler <xref:System.Windows.Controls.VirtualizingPanel> ve <xref:System.Windows.Threading.Dispatcher> sınıfları.

- Büyük görüntülerken, Gelişmiş performans gruplandırılmış veri ve kullanıcı Arabirimi iş parçacıkları koleksiyonlarında erişerek ayarlar.

- Veri bağlama için statik özellikleri, veri özel bağlama uygulayan türleri <xref:System.Reflection.ICustomTypeProvider> arabirimi ve bağlama ifadesinden veri bağlama bilgileri alma.

- (Dinamik şekillendirme) değerlerini değiştirmek gibi veri yeniden konumlandırma.

- Bir öğe kapsayıcısı için veri bağlamı bağlantısı olup olmadığını denetleme yeteneği.

- Özellik değişiklikleri ve veri kaynağı güncelleştirmelerini arasında geçmesi gereken süreyi ayarlama kabiliyeti.

- Zayıf olay desenleri uygulama için geliştirilmiş destek. Ayrıca, olayları artık biçimlendirme uzantıları kabul edebilir.

<a name="windows_communication_foundation"></a> 
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], yazma ve Windows Communication Foundation (WCF) uygulamaları korumak daha kolay yapmak için aşağıdaki özellikler eklenmiştir:

- Oluşturulan yapılandırma dosyalarında basitleştirme.

- Önce anlaşma geliştirme desteği.

- ASP.NET uyumluluğu modunu daha kolay yapılandırma yeteneği.

- Değişiklikleri varsayılan bunları tahsis etmek zorunda kalacaksınız olasılığını azaltmak için özellik değerlerini taşıma.

- Güncelleştirmeleri <xref:System.Xml.XmlDictionaryReaderQuotas> kotaları XML sözlük okuyucular için el ile yapılandırmanız gerekecektir olasılığını azaltmak için sınıf.

- WCF yapılandırma dosyaları Visual Studio tarafından doğrulanmasını uygulamanızı çalıştırmadan önce yapılandırma hataları algılayabilmesi için derleme işleminin parçası olarak.

- Yeni zaman uyumsuz akış desteği.

- Internet Information Services (IIS) ile HTTPS üzerinden bir uç nokta kullanıma kolaylaştırmak için yeni HTTPS protokolü eşleme.

- Meta verileri tek bir WSDL belgesinde ekleyerek oluşturmak yeteneği `?singleWSDL` hizmet URL'si için.

- Bağlantı noktaları 80 ve 443 numaralı TCP taşıma benzer performans özellikleri ile üzerinden true çift yönlü iletişimi etkinleştirmek için Websockets destekler.

- Hizmetlerini kodda yapılandırma desteği.

- XML Düzenleyicisi araç ipuçları.

- <xref:System.ServiceModel.ChannelFactory>Destek önbelleğe alma.

- İkili kodlama sıkıştırma desteği.

- "Yangın ve unut" kullanan hizmetler yazmak geliştiricilerinin UDP taşıma için destek Mesajlaşma. Bir istemci bir hizmete bir ileti gönderir ve hizmet yanıt bekliyor.

- Birden çok kimlik doğrulama modları tek bir WCF uç noktasında HTTP taşıma ve taşıma güvenliği kullanırken destekleyebilmek için.

- Kullanan WCF hizmetleri için destek Uluslararası yapılan etki alanı adlarını (IDN'ler).

 Daha fazla bilgi için bkz: [Windows Communication Foundation yenilikler](http://go.microsoft.com/fwlink/?LinkId=228173).

<a name="windows_workflow_foundation"></a> 
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)
 İçinde [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], birçok yeni özellik Windows Workflow Foundation (WF) için eklenen dahil olmak üzere:

- Durum 4.0.1 .NET Framework'ün bir parçası olarak ilk kez sunulan makine iş akışları ([.NET Framework 4 Platform Güncelleştirmesi 1](http://go.microsoft.com/fwlink/?LinkID=215092)). Bu, birkaç yeni sınıflar ve Durum makinesi iş akışları oluşturmak geliştiriciler etkin etkinlikler güncelleştirmenin. Bu sınıf ve etkinlikler için güncelleştirildi [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] eklemek için:

    - Kesme noktaları durumlarına ayarlayabilme.

    - Geçişler iş akışı Tasarımcısı'nda kopyalayıp yeteneği.

    - Tasarımcı desteği paylaşılan tetikleyici geçiş oluşturma.

    - Etkinlikler dahil olmak üzere Durum makinesi iş akışlarını oluşturmak için: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, ve <xref:System.Activities.Statements.Transition>.

- Aşağıdaki gibi gelişmiş iş akışı Tasarımcısı özellikleri:

    - Geliştirilmiş Visual Studio iş akışı arama yetenekleri de dahil olmak üzere **Hızlı Bul'u** ve **dosyalarda Bul**.

    - İkinci bir alt etkinlik, kapsayıcı bir etkinliğe eklendiğinde, otomatik olarak bir dizi etkinlik oluşturmak ve her iki etkinlikleri sıralı etkinlik eklemek için yeteneği.

    - Destek kaydırma, kaydırma çubukları kullanmadan değiştirilmesi için bir iş akışı görünen dilimini sağlar.

    - Yeni bir **belge anahattı** bir iş akışı bileşenleri bir ağaç stili anahat görünümünde gösterilir ve olanak tanır görünümü seçin bir bileşenin **belge anahattı** görünümü.

    - Etkinlikler için ek açıklamalar ekleme yeteneği.

    - Tanımlama ve iş akışı Tasarımcısı kullanarak etkinlik temsilcileri kullanma olanağı.

    - Otomatik olarak bağlanabilir ve etkinliklerini ve durumunu makine ve akış iş akışlarında geçişler için otomatik ekleme.

- Bir iş akışı XAML dosyasındaki kolayca bulun ve görünüm durumu bilgilerini düzenlemek için tek bir öğede görünüm durumu bilgilerini depolama.

- Kalıcı gelen alt etkinlikler önlemek için NoPersistScope kapsayıcı bir etkinliğe.

- C# ifadeler için destek:

    - Visual Basic kullanan iş akışı projeleri Visual Basic ifadeleri kullanır ve C# iş akışı projeleri için C# ifadeleri kullanır.

    - Visual Studio 2010'da oluşturulan ve Visual Basic ifadeleri olan C# iş akışı projeleri için C# ifadeleri kullanan C# iş akışı projeleri ile uyumlu değildir.

- Sürüm oluşturma geliştirmeleri:

    - Yeni <xref:System.Activities.WorkflowIdentity> kalıcı iş akışı örneği ve iş akışı tanımı arasında bir eşleme sağlayan sınıf.

    - Yan yana yürütme dahil olmak üzere aynı ana bilgisayar, birden çok iş akışı sürümlerinde <xref:System.ServiceModel.Activities.WorkflowServiceHost>.

    - Dinamik güncelleştirme kalıcı iş akışı örneği tanımını değiştirme olanağı.

- Sözleşme ilk iş akışı hizmeti geliştirme var olan bir hizmet sözleşmesini eşleşecek şekilde etkinlikler otomatik olarak oluşturmak için destek sağlar.

 Daha fazla bilgi için bkz: [Windows Workflow Foundation yenilikler](http://go.microsoft.com/fwlink/?LinkId=228176).

<a name="tailored"></a> 
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]Uygulamalar belirli form faktörleri için tasarlanmıştır ve Windows işletim sisteminin güç yararlanın. Bir alt kümesini [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] veya 4.5.1 için yapı kullanılabilir [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] C# veya Visual Basic kullanarak Windows için uygulamalar. Bu alt adlı [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] ve içinde ele alınmıştır bir [genel bakış](http://go.microsoft.com/fwlink/?LinkId=228491) Windows geliştirme Merkezi'ndeki.

<a name="portable"></a> 
### <a name="portable-class-libraries"></a>Taşınabilir sınıf kitaplıkları
 Taşınabilir sınıf kitaplığı projesinde [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (ve sonraki sürümler), yazma ve Yönetilen derlemeler çalışan birden çok .NET Framework platformda yapı sağlar. Taşınabilir sınıf kitaplığı proje kullanarak platformlarını seçin (Windows Phone gibi ve [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]) hedef. Kullanılabilir türler ve projenizdeki üyeleri bu platformları arasında ortak türleri ve üyeleri için otomatik olarak kısıtlanır. Daha fazla bilgi için bkz: [taşınabilir sınıf kitaplığı](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [.NET Framework ve bant dışı yayınlar](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Erişilebilirlik .NET Framework'teki yenilikler](whats-new-in-accessibility.md)   
 [Visual Studio 2017 yenilikler](/visualstudio/ide/whats-new-in-visual-studio)   
 [ASP.NET](/aspnet)   
 [Visual c++'ta yenilikler nelerdir?](/cpp/what-s-new-for-visual-cpp-in-visual-studio) 
