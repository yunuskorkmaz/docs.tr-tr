---
title: .NET Core hakkında
description: .NET Core hakkında bilgi edinin.
ms.date: 09/17/2019
ms.openlocfilehash: 89740b67b294650f78cf36361548c2fe24ac80cb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79147366"
---
# <a name="about-net-core"></a>.NET Core hakkında

.NET Core aşağıdaki özelliklere sahiptir:

- **Çapraz platform:** Windows, macOS ve Linux [işletim sistemlerinde](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)çalışır.
- **Mimariler arasında tutarlı:** Kodunuzu x64, x86 ve ARM dahil olmak üzere birden çok mimaride aynı davranışla çalıştırır.
- **Komut satırı araçları:**  Yerel geliştirme ve sürekli tümleştirme senaryolarında kullanılabilecek kullanımı kolay komut satırı araçlarını içerir.
- **Esnek dağıtım:** Uygulamanıza veya yan yana yüklenebilir (kullanıcı çapında veya sistem genelinde yüklemeler). [Docker konteynerleri](docker/introduction.md)ile kullanılabilir.
- **Uyumlu:** .NET Core .NET Framework, Xamarin ve Mono ile [.NET Standardı](../standard/net-standard.md)üzerinden uyumludur.
- **Açık kaynak:** .NET Core platformu, MIT ve Apache 2 lisanslarını kullanarak açık kaynak kodludur. .NET Core bir [.NET Vakfı](https://dotnetfoundation.org/) projesidir.
- **Microsoft tarafından desteklenir:** .NET Core Microsoft tarafından desteklenir, başına [.NET Çekirdek Desteği.](https://dotnet.microsoft.com/platform/support/policy)

## <a name="languages"></a>Diller

C#, Visual Basic ve F# dilleri .NET Core için uygulama ve kitaplık yazmak için kullanılabilir. Bu diller, aşağıdakiler dahil olmak üzere en sevdiğiniz metin düzenleyicisinde veya Tümleşik Geliştirme Ortamında (IDE) kullanılabilir:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://code.visualstudio.com/download)
- Yüce Metin
- Vim

Bu entegrasyon, kısmen [OmniSharp](https://www.omnisharp.net/) ve [Ionide](http://ionide.io) projelerinin katkıda bulunanları tarafından sağlanmaktadır.

## <a name="apis"></a>API'ler

.NET Core, birkaçı aşağıdaki birçok senaryo için API'leri ortaya çıkarır:

- İlkel türleri, <xref:System.Boolean?displayProperty=nameWithType> <xref:System.Int32?displayProperty=nameWithType>gibi ve .
- Koleksiyonlar, gibi <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>ve .
- Gibi yardımcı program <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>türleri, ve <xref:System.IO.FileStream?displayProperty=nameWithType>.
- ve <xref:System.Data.DataSet?displayProperty=nameWithType> [DbSet](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)gibi veri türleri.
- Gibi yüksek performanslı <xref:System.Numerics.Vector?displayProperty=nameWithType> türleri, ve [Boru Hatları.](../standard/io/pipelines.md)

.NET [Core,.NET Standart](../standard/net-standard.md) belirtimini uygulayarak .NET Framework ve Mono API'ler ile uyumluluk sağlar.

## <a name="frameworks"></a>Framework’ler

.NET Core'un üzerine birden fazla çerçeve oluşturulmuştur:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Evrensel Windows Platformu (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Birleşim

.NET Core aşağıdaki bölümlerden oluşmaktadır:

- Bir tür sistemi, montaj yükleme, çöp toplayıcı, yerel interop ve diğer temel hizmetleri sağlayan [.NET Core çalışma zamanı.](https://github.com/dotnet/runtime/tree/master/src/coreclr) [.NET Core framework kitaplıkları](https://github.com/dotnet/runtime/tree/master/src/libraries) ilkel veri türleri, uygulama kompozisyonu türleri ve temel yardımcı programlar sağlar.
- Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı internet bağlantılı uygulamalar oluşturmak için bir çerçeve sağlayan [ASP.NET Core çalışma süresi.](https://github.com/dotnet/aspnetcore)
- .NET Core geliştirici deneyimini sağlayan [.NET Core SDK](https://github.com/dotnet/sdk) ve dil derleyicileri[(Roslyn](https://github.com/dotnet/roslyn) ve [F#](https://github.com/microsoft/visualfsharp)).
- .NET Core uygulamalarını ve CLI komutlarını başlatmak için kullanılan [dotnet komutu.](./tools/dotnet.md) Çalışma saatini seçer ve çalışma saatini barındırAn, bir montaj yükleme ilkesi sağlar ve uygulamaları ve araçları başlayır.

Bu bileşenler aşağıdaki şekillerde dağıtılır:

- [.NET Core Runtime](https://dotnet.microsoft.com/download) -- .NET Core çalışma zamanı ve çerçeve kitaplıklarını içerir.
- [ASP.NET Core Runtime](https://dotnet.microsoft.com/download) -- ASP.NET Core ve .NET Core çalışma zamanı ve çerçeve kitaplıklarını içerir.
- [.NET Core SDK](https://dotnet.microsoft.com/download) -- .NET Core CLI, ASP.NET Core çalışma zamanı ve .NET Core çalışma zamanı ve çerçeveyi içerir.

### <a name="open-source"></a>Açık kaynak

[.NET Core](https://github.com/dotnet/core) açık kaynak koda[(MIT lisansı)](https://github.com/dotnet/core/blob/master/LICENSE.TXT)ve Microsoft tarafından 2014 yılında [.NET Vakfı'na](https://dotnetfoundation.org) katkıda bulunulmuş. Şu anda en aktif .NET Foundation projelerinden biri. Kişisel, akademik veya ticari amaçlar için de dahil olmak üzere bireyler ve şirketler tarafından kullanılabilir. Birden çok şirket .NET Core'u uygulamalar, araçlar, yeni platformlar ve barındırma hizmetlerinin bir parçası olarak kullanır. Bu şirketlerden bazıları GitHub'da .NET Core'a önemli katkılarda bulunmakta ve [.NET Foundation Teknik Yönlendirme Grubu'nun](https://dotnetfoundation.org/blog/tsg-welcome)bir parçası olarak ürün yönü hakkında rehberlik etmektedir.

### <a name="designed-for-adaptability"></a>Adaptasyon için tasarlanmıştır

.NET Core, diğer .NET ürünlerine göre benzer ama benzersiz bir ürün olarak üretilmiştir. Yeni platformlara ve iş yüklerine geniş adaptasyon sağlamak üzere tasarlanmıştır ve kullanılabilir birkaç işletim sistemi ve CPU bağlantı noktasına sahiptir (ve çok daha fazlasına taşınabilir).

Ürün çeşitli parçalara bölünerek çeşitli parçaların farklı zamanlarda yeni platformlara adapte edilmesini sağlar. Çalışma zamanı ve platforma özgü temel kitaplıklar bir birim olarak taşınabilir. Platform-agnostik kütüphaneler inşaat, tüm platformlarda olduğu gibi çalışması gerekir. Geliştirici verimliliğini artırmak için platforma özgü uygulamaları azaltmaya yönelik bir proje önyargısı vardır, bir algoritma veya API bu şekilde tam veya kısmen uygulanabilir olduğunda platformdan bağımsız C# kodunu tercih eder.

İnsanlar genellikle .NET Core'un birden çok işletim sistemlerini desteklemek için nasıl uygulandığını sorarlar. Genellikle ayrı uygulamalar olup olmadığını veya [koşullu derleme](https://en.wikipedia.org/wiki/Conditional_compilation) kullanıp kullanılmadıklarını sorarlar. Her ikisi de, koşullu derleme doğru güçlü bir önyargı ile.

Aşağıdaki grafikte [.NET Core kitaplıklarının](https://github.com/dotnet/runtime/tree/master/src/libraries) büyük çoğunluğunun tüm platformlarda paylaşılan platform-nötr kod olduğunu görebilirsiniz. Platform-nötr kod tüm platformlarda kullanılan tek bir taşınabilir montaj olarak uygulanabilir.

![CoreFX: Platform Başına Kod Satırları](../images/corefx-platforms-loc.png)

Windows ve Unix uygulamaları boyutu benzer. .NET Core kitaplıkları [Microsoft.Win32.Registry](https://github.com/dotnet/runtime/tree/master/src/libraries/Microsoft.Win32.Registry) gibi yalnızca Windows'a özel bazı özellikleri uyguladığından, ancak henüz yalnızca Unix'e özel birçok kavram uygulamadığından, Windows'un daha büyük bir uygulaması vardır. Linux ve macOS uygulamalarının çoğunun unix uygulaması nda paylaşılırken, Linux ve macOS'a özgü uygulamaların boyutu kabaca benzer olduğunu da görürsünüz.

.NET Core'da platforma özgü ve platformdan bağımsız kitaplıkların bir karışımı vardır. Deseni birkaç örnekte görebilirsiniz:

- [CoreCLR](https://github.com/dotnet/runtime/tree/master/src/coreclr) platforma özeldir. Bellek yöneticisi ve iş parçacığı zamanlayıcısı gibi işletim sistemi alt sistemlerinin üzerine inşa eder.
- [System.IO](https://github.com/dotnet/runtime/tree/master/src/libraries/System.IO) ve [System.Security.Cryptography.Algorithms](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Security.Cryptography.Algorithms) platforma özgüdür, depolama ve şifreleme API'leri her işletim sisteminde farklıdır.
- [System.Collections](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Collections) ve [System.Linq,](https://github.com/dotnet/runtime/tree/master/src/libraries/System.Linq) veri yapıları oluşturmak ve üzerinde faaliyet göz önüne alındığında, platform-nötr.

## <a name="comparisons-to-other-net-implementations"></a>Diğer .NET uygulamalarıyla karşılaştırmalar

.NET Core'un boyutunu ve şeklini varolan .NET uygulamalarıyla karşılaştırarak anlamak muhtemelen daha kolaydır.

### <a name="comparison-with-net-framework"></a>.NET Framework ile karşılaştırma

.NET ilk olarak Microsoft tarafından 2000 yılında duyuruldu ve daha sonra oradan gelişti. .NET Framework, Microsoft'un yaklaşık 20 yıllık dönemde ürettiği birincil .NET uygulaması olmuştur.

.NET Core ve .NET Framework arasındaki temel farklar:

- **Uygulama modelleri** -- .NET Core tüm .NET Framework uygulama modellerini desteklemiyor. Özellikle, Web Formlar ve ASP.NET MVC ASP.NET desteklemez, ancak ASP.NET Core MVC destekler. .NET Core 3.0 ile başlayan .NET Core, yalnızca Windows'da WPF ve Windows Formlarını da destekler.
- **API'ler** -- .NET Core, farklı bir çarpanetleme içeren .NET Framework Base Class Library'nin büyük bir alt kümesini içerir (derleme adları farklıdır; türlerde açığa çıkarılan üyeler önemli durumlarda farklılık gösterir). Bazı durumlarda, bu farklar bağlantı noktası kaynağında .NET Core'da değişiklik yapılmasını gerektirir. Daha fazla bilgi için [.NET Taşınabilirlik Çözümleyicisi'ne](../standard/analyzers/portability-analyzer.md)bakın. .NET Core [,NET Standart](../standard/net-standard.md) API belirtimini uygular.
- **Alt sistemler** -- .NET Core, daha basit bir uygulama ve programlama modeli amacıyla .NET Framework'de alt sistemlerin bir alt kümesini uygular. Örneğin, Kod Erişim Güvenliği (CAS) desteklenmezken, yansıma desteklenir.
- **Platformlar** -- .NET Framework Windows ve Windows Server'ı desteklerken .NET Core macOS ve Linux'u da destekler.
- **Açık Kaynak** -- .NET Core açık kaynak, [.NET Framework'ün salt okunur alt kümesi](https://github.com/microsoft/referencesource) ise açık kaynakkod.

.NET Core benzersiz olmakla birlikte ve .NET Framework ve diğer .NET uygulamalarında önemli farklılıklar olsa da, kaynak veya ikili paylaşım tekniklerini kullanarak bu uygulamalar arasında kod paylaşımı kolaydır.

.NET Core yan yana yüklemeyi desteklediği nden ve çalışma süresi .NET Framework'den tamamen bağımsız olduğundan, .NET Framework'e sahip makinelere sorunsuz bir şekilde kurulabilir.

### <a name="comparison-with-mono"></a>Mono ile karşılaştırma

[Mono,](https://www.mono-project.com/) .NET'in orijinal çapraz platform uygulamasıdır. .NET Framework'e [açık kaynak](https://github.com/mono/mono) alternatifi olarak başladı ve iOS ve Android cihazlar popüler hale geldikçe mobil cihazları hedeflemeye geçti. .NET Framework'ün bir topluluk klonu olarak düşünülebilir. Mono proje ekibi, uyumlu bir uygulama sağlamak için Microsoft tarafından yayınlanan açık [.NET standartlarına](https://github.com/dotnet/runtime/blob/master/docs/project/dotnet-standards.md) (özellikle ECMA 335) güvendi.

.NET Core ve Mono arasındaki temel farklar:

- **Uygulama modelleri** -- Mono, Xamarin ürünü aracılığıyla .NET Framework uygulama modellerinin (örneğin, Windows Forms) ve mobil geliştirme için bazı ek modellerin (örneğin, [Xamarin.iOS)](https://www.xamarin.com/platform)bir alt kümesini destekler. .NET Core Xamarin'i desteklemiyor.
- **API'ler** -- Mono, aynı derleme adlarını ve faktoringi kullanarak .NET Framework API'lerinin büyük bir [alt kümesini](http://docs.go-mono.com/?link=root%3a%2fclasslib) destekler.
- **Platformlar** -- Mono birçok platformu ve CPU'ları destekler.
- **Açık Kaynak** -- Mono ve .NET Core hem MIT lisansını kullanıyor hem de .NET Foundation projeleri.
- **Odak** -- Mono'nun son yıllarda ki ana odak noktası mobil platformlarken,.NET Core bulut ve masaüstü iş yüklerine odaklanmışdurumda.

## <a name="the-future"></a>Gelecek

.NET 5'in .NET Core'un bir sonraki sürümü olacağı ve platformun birleşmesi olacağı duyuruldu. Proje .NET'i birkaç temel şekilde geliştirmeyi amaçlamaktadır:

- Her yerde kullanılabilen ve tek çalışma zamanı davranışları ve geliştirici deneyimleri olan tek bir .NET çalışma zamanı ve çerçeve üretin.
- .NET Core, .NET Framework, Xamarin ve Mono'yu en iyi şekilde ele alarak .NET'in yeteneklerini genişletin.
- Bu ürünü, geliştiricilerin (Microsoft ve topluluk) birlikte çalışabileceği ve birlikte genişletebileceği ve tüm senaryoları iyileştirebileceği tek bir kod tabanından oluşturun.

.NET 5 için nelerin planlandığı hakkında daha fazla bilgi için [.NET 5 tanıtımına](https://devblogs.microsoft.com/dotnet/introducing-net-5/)bakın.
