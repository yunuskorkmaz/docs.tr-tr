---
title: .NET Core’a genel bakış
description: .NET Core'un özellikleri ve bileşimi hakkında bilgi edinin ve diğer .NET uygulamalarıyla karşılaştırın.
ms.date: 09/17/2019
ms.openlocfilehash: f2f97fe6a5f822266582c443fd916c270cb0cb6a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345198"
---
# <a name="net-core-overview"></a>.NET Core’a genel bakış

.NET Core aşağıdaki özelliklere sahiptir:

- **Çapraz platform:** Windows, macOS ve Linux [işletim sistemlerinde](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)çalışır.
- **Mimariler arasında tutarlı:** Kodunuzu x64, x86 ve ARM dahil olmak üzere birden çok mimaride aynı davranışla çalıştırır.
- **Komut satırı araçları:**  Yerel geliştirme ve sürekli tümleştirme senaryolarında kullanılabilecek kullanımı kolay komut satırı araçlarını içerir.
- **Esnek dağıtım:** Uygulamanıza veya yan yana yüklenebilir (kullanıcı çapında veya sistem genelinde yüklemeler). [Docker konteynerleri](docker/introduction.md)ile kullanılabilir.
- **Uyumlu:** .NET Core .NET Framework, Xamarin ve Mono uygulamaları ile [.NET Standardı](../standard/net-standard.md)üzerinden uyumludur.
- **Açık kaynak:** .NET Core platformu, MIT ve Apache 2 lisanslarını kullanarak açık kaynak kodludur. .NET Core bir [.NET Vakfı](https://dotnetfoundation.org/) projesidir.
- **Microsoft tarafından desteklenir:** .NET Core [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy)

## <a name="languages"></a>Diller

C#, Visual Basic ve F# dilleri .NET Core için uygulama ve kitaplık yazmak için kullanılabilir. Bu diller, aşağıdakiler dahil olmak üzere en sevdiğiniz metin düzenleyicisinde veya Tümleşik Geliştirme Ortamında (IDE) kullanılabilir:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)
- Yüce Metin
- Vim

Editör entegrasyonu, kısmen [OmniSharp](https://www.omnisharp.net/) ve [Ionide](http://ionide.io) projelerinin katkıda bulunanları tarafından sağlanmaktadır.

## <a name="apis"></a>API'ler

Birçok API'ler gibi ortak ihtiyaçlarını karşılamak dahildir:

- İlkel türleri, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>gibi ve .
- Koleksiyonlar, gibi <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>ve .
- Gibi yardımcı program <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>türleri, ve <xref:System.IO.FileStream?displayProperty=nameWithType>.
- ve <xref:System.Data.DataSet?displayProperty=nameWithType> [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)gibi veri türleri.
- Gibi yüksek performanslı <xref:System.Numerics.Vector?displayProperty=nameWithType> türleri, ve [Boru Hatları.](../standard/io/pipelines.md)

.NET [Core,.NET Standart](../standard/net-standard.md) belirtimini uygulayarak .NET Framework ve Mono API'ler ile uyumluluk sağlar.

## <a name="frameworks"></a>Framework’ler

.NET Core'un üzerine birden fazla çerçeve oluşturulmuştur:

- [ASP.NET Core](/aspnet/core/)
- [Evrensel Windows Platformu (UWP)](/windows/uwp/)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Birleşim

.NET Core aşağıdaki bölümlerden oluşmaktadır:

- Bir tür sistemi, montaj yükleme, çöp toplayıcı, yerel interop ve diğer temel hizmetleri sağlayan [.NET Core çalışma zamanı.](https://github.com/dotnet/runtime/tree/master/src/coreclr) [.NET Core framework kitaplıkları](https://github.com/dotnet/runtime/tree/master/src/libraries) ilkel veri türleri, uygulama kompozisyonu türleri ve temel yardımcı programlar sağlar.
- Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi modern, bulut tabanlı, internete bağlı uygulamalar oluşturmak için bir çerçeve sağlayan [ASP.NET Core çalışma süresi.](https://github.com/dotnet/aspnetcore)
- .NET Core geliştirici deneyimini sağlayan [.NET Core SDK](https://github.com/dotnet/sdk) ve dil derleyicileri[(Roslyn](https://github.com/dotnet/roslyn) ve [F#](https://github.com/microsoft/visualfsharp)).
- .NET Core uygulamalarını ve CLI komutlarını başlatmak için kullanılan [dotnet komutu.](./tools/dotnet.md) Çalışma saatini seçer ve barındırıyor, bir montaj yükleme ilkesi sağlar ve uygulamaları ve araçları başlatıyor.

Bu bileşenler aşağıdaki şekillerde dağıtılır:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) -- .NET Core çalışma zamanı ve çerçeve kitaplıklarını içerir.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) -- ASP.NET Core ve .NET Core çalışma süreleri ve çerçeve kitaplıklarını içerir.
- [.NET Core SDK](https://dotnet.microsoft.com/download) -- .NET Core CLI, ASP.NET Core çalışma zamanı ve .NET Core çalışma zamanı ve çerçeveyi içerir.

### <a name="open-source"></a>Açık kaynak

[.NET Core](https://github.com/dotnet/core) açık kaynak kodludur[(MIT lisansı)](https://github.com/dotnet/core/blob/master/LICENSE.TXT)ve 2014 yılında Microsoft tarafından [.NET Foundation'a](https://dotnetfoundation.org) katkıda bulunulmıştır. Şu anda en aktif .NET Foundation projelerinden biri. Kişisel, akademik veya ticari amaçlar için de dahil olmak üzere bireyler ve şirketler tarafından kullanılabilir. Birden çok şirket .NET Core'u uygulamalar, araçlar, yeni platformlar ve barındırma hizmetlerinin bir parçası olarak kullanır. Bu şirketlerden bazıları GitHub'da .NET Core'a önemli katkılarda bulunmakta ve [.NET Foundation Teknik Yönlendirme Grubu'nun](https://dotnetfoundation.org/blog/tsg-welcome)bir parçası olarak ürün yönü hakkında rehberlik etmektedir.

### <a name="designed-for-adaptability"></a>Adaptasyon için tasarlanmıştır

.NET Core, diğer .NET ürünlerine göre benzer ama benzersiz bir ürün olarak üretilmiştir. Yeni platformlara ve iş yüklerine geniş adaptasyon sağlamak üzere tasarlanmıştır ve kullanılabilir birkaç işletim sistemi ve CPU bağlantı noktasına sahiptir (ve çok daha fazlasına taşınabilir).

Ürün çeşitli parçalara bölünerek çeşitli parçaların farklı zamanlarda yeni platformlara adapte edilmesini sağlar. Çalışma zamanı ve platforma özgü temel kitaplıklar bir birim olarak taşınabilir. Platform-agnostik kütüphaneler inşaat, tüm platformlarda olduğu gibi çalışması gerekir. Geliştirici verimliliğini artırmak için platforma özgü uygulamaları azaltmaya yönelik bir proje önyargısı vardır, bir algoritma veya API bu şekilde tam veya kısmen uygulanabilir olduğunda platformdan bağımsız C# kodunu tercih eder.

İnsanlar genellikle .NET Core'un birden çok işletim sistemlerini desteklemek için nasıl uygulandığını sorarlar. Genellikle ayrı uygulamalar olup olmadığını veya [koşullu derleme](https://en.wikipedia.org/wiki/Conditional_compilation) kullanıp kullanılmadıklarını sorarlar. Her ikisi de, koşullu derleme doğru güçlü bir önyargı ile.

Aşağıdaki grafikte [.NET Core kitaplıklarının](https://github.com/dotnet/runtime/tree/master/src/libraries) büyük çoğunluğunun tüm platformlarda paylaşılan platform-nötr koddan derlenmiş olduğunu görebilirsiniz. Platformdan bağımsız kod, tüm platformlarda kullanılan tek bir taşınabilir derleme olarak uygulanabilir.

![CoreFX: Platform Başına Kod Satırları](../images/corefx-platforms-loc.png)

Windows ve Unix uygulamaları boyutu benzer. Windows uygulaması, [Microsoft.Win32.Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry)gibi yalnızca Windows'a özel bazı özellikler içerir, ancak henüz yalnızca Unix'e özel birçok kavram uygulamaz. Linux ve macOS uygulamalarının çoğu Unix uygulamasında paylaşılır. Linux'a özel ve macOS'a özgü uygulamalar boyut olarak benzerdir.

.NET Core'da platforma özgü ve platformdan bağımsız kitaplıkların bir karışımı vardır. Deseni birkaç örnekte görebilirsiniz:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) platforma özeldir. Bellek yöneticisi ve iş parçacığı zamanlayıcısı gibi işletim sistemi alt sistemlerinin üzerine inşa eder.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) ve [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) platforma özgüdür, depolama ve şifreleme API'leri her işletim sisteminde farklıdır.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) ve [System.Linq,](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) veri yapıları oluşturmak ve üzerinde faaliyet göz önüne alındığında, platform-nötr.

## <a name="comparisons-to-other-net-implementations"></a>Diğer .NET uygulamalarıyla karşılaştırmalar

.NET Core'un boyutunu ve şeklini anlamak için, aşağıdaki bölümler bunu varolan .NET uygulamalarıyla karşılaştırın.

### <a name="net-core-vs-net-framework"></a>.NET Core vs. .NET Framework

.NET ilk olarak Microsoft tarafından 2000 yılında duyuruldu ve oradan gelişti. .NET Framework, Yaklaşık yirmi yıllık dönemde Microsoft tarafından üretilen birincil .NET uygulaması olmuştur.

.NET Core ve .NET Framework arasındaki temel farklar şunlardır:

- **Uygulama modelleri** -- .NET Core tüm .NET Framework uygulama modellerini desteklemiyor. Özellikle, Web Formlar ve ASP.NET MVC ASP.NET desteklemez, ancak ASP.NET Core MVC destekler. .NET Core 3.0 ile başlayan .NET Core, yalnızca Windows'da WPF ve Windows Formlarını da destekler.
- **API'ler** -- .NET Core, farklı bir çarpanetleme içeren .NET Framework Base Class Library'nin büyük bir alt kümesini içerir (derleme adları farklıdır; türlerde açığa çıkarılan üyeler önemli durumlarda farklılık gösterir). Bazı durumlarda, bu farklar bağlantı noktası kaynağında .NET Core'da değişiklik yapılmasını gerektirir. Daha fazla bilgi için [.NET Taşınabilirlik Çözümleyicisi'ne](../standard/analyzers/portability-analyzer.md)bakın. .NET Core [,NET Standart](../standard/net-standard.md) API belirtimini uygular.
- **Alt sistemler** -- .NET Core, daha basit bir uygulama ve programlama modeli amacıyla alt sistemlerin bir alt kümesini .NET Framework'de uygular. Örneğin, Kod Erişim Güvenliği (CAS) desteklenmezken, yansıma desteklenir.
- **Platformlar** -- .NET Framework Windows ve Windows Server'ı desteklerken .NET Core da macOS ve Linux'u destekler.
- **Açık kaynak -- .NET** Core açık kaynak, [.NET Framework'ün salt okunur alt kümesi](https://github.com/microsoft/referencesource) ise açık kaynakkod.

.NET Core benzersiz olmakla birlikte ve .NET Framework ve diğer .NET uygulamaları arasında önemli farklılıklar olsa da, kaynak veya ikili paylaşım tekniklerini kullanarak bu uygulamalar arasında kod paylaşmak kolaydır.

.NET Core yan yana yüklemeyi desteklediği nden ve çalışma süresi .NET Framework'den tamamen bağımsız olduğundan, .NET Framework'ü sorunsuz bir şekilde yüklü olan makinelere kurulabilir.

### <a name="net-core-vs-mono"></a>.NET Çekirdek vs Mono

[Mono,](https://www.mono-project.com/) .NET'in orijinal çapraz platform uygulamasıdır. .NET Framework'e [açık kaynak](https://github.com/mono/mono) alternatifi olarak başladı ve iOS ve Android cihazlar popüler hale geldikçe mobil cihazları hedeflemeye geçti. .NET Framework'ün bir topluluk klonu olarak düşünülebilir. Mono proje ekibi, uyumlu bir uygulama sağlamak için Microsoft tarafından yayınlanan açık [.NET standartlarına](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (özellikle ECMA 335) güvendi.

.NET Core ve Mono arasındaki başlıca farklar şunlardır:

- **Uygulama modelleri** -- Mono, Xamarin ürünü aracılığıyla .NET Framework uygulama modellerinin (örneğin, Windows Forms) ve mobil geliştirme için bazı ek modellerin (örneğin, [Xamarin.iOS)](https://www.xamarin.com/platform)bir alt kümesini destekler. .NET Core Xamarin'i desteklemiyor.
- **API'ler** -- Mono, aynı derleme adlarını ve faktoringi kullanarak .NET Framework API'lerinin büyük bir [alt kümesini](http://docs.go-mono.com/?link=root%3a%2fclasslib) destekler.
- **Platformlar** -- Mono birçok platformu ve CPU'ları destekler.
- **Açık Kaynak** -- Mono ve .NET Core hem MIT lisansını kullanıyor hem de .NET Foundation projeleri.
- **Odak** -- Mono'nun son yıllarda ki ana odak noktası mobil platformlarken,.NET Core bulut ve masaüstü iş yüklerine odaklanmışdurumda.

## <a name="support"></a>Destek

.NET Core, Windows, macOS ve Linux'ta [Microsoft tarafından desteklenir.](https://dotnet.microsoft.com/platform/support/policy) Güvenlik ve kalite açısından düzenli olarak güncellenir (her ayın ikinci Salı günü).

Microsoft'un .NET Core ikili dağıtımları, Azure'da Microsoft tarafından tutulan sunucularda oluşturulur ve test edilir ve Microsoft mühendislik ve güvenlik uygulamalarını izler.

Red Hat, Red Hat Enterprise Linux (RHEL) üzerinde [.NET Core'u destekler.](http://redhatloves.net/) Red Hat kaynaktan .NET Core oluşturur ve [Red Hat Yazılım Koleksiyonları'nda](https://developers.redhat.com/products/softwarecollections/overview/)kullanılabilir hale getirir. Red Hat ve Microsoft, .NET Core'un RHEL'de iyi çalışmasını sağlamak için işbirliği içindedir.

[Tizen, Tizen](https://developer.tizen.org/development/training/.net-application) platformlarında .NET Core'u destekler.
