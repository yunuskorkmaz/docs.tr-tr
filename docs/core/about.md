---
title: .NET Core hakkında
description: .NET Core hakkında bilgi edinin.
author: richlander
ms.date: 08/01/2018
ms.openlocfilehash: d81c6ad15c12d7bb1e866aef3bd1e799d5b62cde
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67421879"
---
# <a name="about-net-core"></a>.NET Core hakkında

.NET core, aşağıdaki özelliklere sahiptir:

- **Platformlar arası:** Windows, macOS ve Linux'ta çalışan [işletim sistemleri](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md).
- **Consistent mimariler arasında:** Kodunuz ile aynı davranışı x64, x86 ve ARM gibi birden fazla mimari üzerinde çalışır.
- **Komut satırı araçları:**  Yerel geliştirme için ve sürekli tümleştirme senaryolarında kullanılabilecek kolay kullanımlı komut satırı araçlarını içerir.
- **Esnek dağıtım:** Uygulamanıza dahil edilebilir ya da yan yana (geniş kullanıcı veya sistem genelinde yüklemeleri) yüklü. Kullanılabilir [Docker kapsayıcıları](docker/index.md).
- **Uyumlu:** .NET Core, .NET Framework, Xamarin ve Mono, uyumlu aracılığıyla [.NET Standard](../standard/net-standard.md).
- **Açık kaynak:** MIT'den ve Apache 2 lisanslarını kullanarak, açık kaynak .NET Core platformudur. .NET Core bir [.NET Foundation](https://dotnetfoundation.org/) proje.
- **Microsoft tarafından desteklenen:** .NET Core, her Microsoft tarafından desteklenir [.NET Core desteği](https://www.microsoft.com/net/core/support/).

## <a name="languages"></a>Diller

C#, Visual Basic ve F# diller için .NET Core uygulamaları ve kitaplıkları yazma için kullanılabilir. Bu dil olan ya da dahil olmak üzere Ide'lerle ve sık kullandığınız metin düzenleyicisi tümleştirilebilir [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp), Sublime Text ve Vim. Bu tümleştirme, kısmen iyi istemeyenler sağlandığı [OmniSharp](https://www.omnisharp.net/) ve [Ionide](http://ionide.io) projeleri.

## <a name="apis"></a>API'ler

.NET core, birkaçını izleyin birçok senaryo için API'leri kullanıma sunar:

- Temel türler, gibi [bool](../csharp/language-reference/keywords/bool.md) ve [int](../csharp/language-reference/builtin-types/integral-numeric-types.md).
- Koleksiyonları gibi <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>.
- Gibi yardımcı programı türleri <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>, ve <xref:System.IO.FileStream?displayProperty=nameWithType>.
- Veri türleri, aşağıdaki gibi <xref:System.Data.DataSet?displayProperty=nameWithType>, ve [olan DB](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/).
- Gibi yüksek performanslı türleri <xref:System.Numerics.Vector?displayProperty=nameWithType> ve [işlem hatları](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/).

.NET core uygulayarak .NET Framework ve Mono API'leri ile uyumluluk sağlar [.NET Standard](../standard/net-standard.md) belirtimi.

## <a name="frameworks"></a>Çerçeveler

Birden çok çerçeveyi .NET Core üzerine yerleştirilmiştir:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Evrensel Windows Platformu (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Oluşturma

.NET core, aşağıdaki bölümlerden oluşur:

- [.NET Core çalışma zamanı](https://github.com/dotnet/coreclr), bir tür sistemi, derleme yüklenirken, çöp toplayıcı, yerel birlikte çalışabilirliği ve diğer temel hizmetleri sağlar. [.NET core framework kitaplıkları](https://github.com/dotnet/corefx) ilkel veri türleri, uygulama oluşturma türleri ve temel yardımcı programları sağlar.
- [ASP.NET çalışma zamanı](https://github.com/aspnet/home), bağlı uygulamalar, web uygulamaları, IOT uygulamaları ve mobil arka uçları gibi internet tabanlı modern bulut oluşturmak için bir çerçeve sağlar.
- [.NET Core CLI Araçları](https://github.com/dotnet/cli) ve dil derleyicileri ([Roslyn](https://github.com/dotnet/roslyn) ve [ F# ](https://github.com/microsoft/visualfsharp)) .NET Core Geliştirici deneyimini etkinleştirin.
- [Dotnet araç](https://github.com/dotnet/core-setup), .NET Core uygulamaları ve CLI Araçları'nı başlatmak için kullanılır. Çalışma zamanının seçtiği çalışma zamanını barındıran, derleme yüklenirken ilke sağlar ve uygulamaları ve Araçları'nı başlatır.

Bu bileşenler, aşağıdaki yollarla dağıtılır:

- [.NET core çalışma zamanı](https://www.microsoft.com/net/download/dotnet-core/2.1) --.NET Core çalışma zamanı ve framework kitaplıkları içerir.
- [ASP.NET Core çalışma zamanı](https://www.microsoft.com/net/download/dotnet-core/2.1) --ASP.NET Core ve .NET Core çalışma zamanı ve framework kitaplıkları içerir.
- [.NET core SDK'sı](https://www.microsoft.com/net/download/dotnet-core/2.1) --.NET CLI araçları, ASP.NET Core çalışma zamanı ve .NET Core çalışma zamanı ve framework içerir.

### <a name="open-source"></a>Açık kaynak

[.NET core](https://github.com/dotnet/core) açık kaynak ([MIT lisansı](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) ve için katkıda [.NET Foundation](https://dotnetfoundation.org) 2014'te Microsoft tarafından. Şimdi en etkin .NET Foundation projeleri biridir. Bu ücretsiz bireyler ve kişisel, akademik veya ticari amaçlar için de dahil olmak üzere, şirketler tarafından önemsenmeksizin devralınabilir. Birden çok şirket .NET Core uygulamaları, araçları, yeni platformlar ve barındırma hizmetlerini bir parçası olarak kullanın. Bazı bu kurumlara işleri açısından önemli katkılar, GitHub üzerinde .NET Core yapmak ve bir parçası olarak ürün yönü rehberlik sağlar [.NET Foundation teknik Yönetimi grubu](https://dotnetfoundation.org/blog/tsg-welcome).

### <a name="designed-for-adaptability"></a>Uyumluluk için tasarlanmış

.NET core, .NET ürünlerin göre çok benzer ancak benzersiz bir ürün olarak oluşturuldu. Yeni platformlar ve iş yükleri için geniş kapsamlı uyumluluk etkinleştirmek için tasarlanmıştır. Bu, çeşitli işletim sistemi ve CPU bağlantı noktaları kullanılabilir olan ve çok daha fazlası için unity'nin.

Ürün yeni platformlar için farklı zamanlarda uyarlanabilen çeşitli kısımlarını etkinleştirilmesi birkaç parçalara ayrılır. Çalışma zamanı ve temel platforma özgü kitaplıklar için bir birim olarak unity'nin gerekir. Platformdan kitaplıkları olarak çalışmalıdır-yapı tarafından tüm platformlarda olan. Geliştirici verimliliği artırmak için bir algoritma veya API uygulanabilir olduğunda platform nötr C# kodu belgelemeyi tam olarak veya bölümü bu şekilde, platforma özel uyarlama miktarını azaltarak için bir proje sapması yoktur.

Kişiler, genellikle birden çok işletim sistemini desteklemek için .NET Core nasıl uygulandığını isteyin. Genellikle ayrı uygulamaları ise veya sorun [koşullu derleme](https://en.wikipedia.org/wiki/Conditional_compilation) kullanılır. Bu güçlü bir sapma koşullu derleme doğrultusunda ile hem de olur.

Gördüğünüz aşağıdaki grafik, büyük çoğunluğu [Corefx'te](https://github.com/dotnet/corefx) tüm platformlar arasında paylaşılan platformdan bağımsız kodudur. Platformdan bağımsız kod, tüm platformlarda kullanılan tek bir taşınabilir derleme olarak uygulanabilir.

![Corefx'te: Platform başına kod satırları](../images/corefx-platforms-loc.png)

Windows ve UNIX benzer boyutta uygulamalarıdır. Windows olan daha büyük bir uygulama Corefx'te bazı yalnızca Windows özellikleri gibi uyguladığından [Microsoft.Win32.Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) ancak henüz pek çok kavramı yalnızca UNIX uygulamaz. Ayrıca, Linux ve macOS uygulamalarının çoğu paylaşılır, UNIX uygulama arasında Linux ve macOS özel uygulamaları boyutu kabaca benzer olsa da görürsünüz.

Platforma özgü ve platform nötr kitaplıkları .NET core'da bir karışımını vardır. Desen birkaç örnek görebilirsiniz:

- [CoreCLR](https://github.com/dotnet/coreclr) platforma özgüdür. İş parçacığı Zamanlayıcısı'nı ve bellek yöneticisi gibi işletim sistemi alt sistemler üzerinde oluşturur.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) ve [System.Security.Cryptography.Algorithms](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) depolama ve şifreleme API'leri her işletim sisteminde farklı olduğuna platforma özgü olan.
- [System.Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) ve [System.Linq](https://github.com/dotnet/corefx/tree/master/src/System.Linq) platformdan bağımsız, oluşturma ve veri yapıları üzerinde çalışması düşünüldüğünde demektir.

## <a name="comparisons-to-other-net-implementations"></a>Diğer .NET uygulamalarına karşılaştırmaları

Belki de boyutu ve şekli .NET Core için var olan .NET uygulamalarını karşılaştırarak anlamak kolaydır.

### <a name="comparison-with-net-framework"></a>.NET Framework ile karşılaştırma

.NET ilk 2000'de Microsoft tarafından duyurulan ve ardından buradan gelişim göstermiştir. .NET Framework, neredeyse iki on dönemi boyunca Microsoft tarafından üretilen birincil .NET uygulaması kaldırıldı.

.NET Core ve .NET Framework arasındaki temel farklar:

- **Uygulama modelleri** --.NET Core, tüm .NET Framework uygulaması-modelleri desteklemez. Özellikle, ASP.NET Web Forms ve ASP.NET MVC desteklemez, ancak ASP.NET Core MVC destekler. Bunu Duyuruldu, [.NET Core 3, WPF ve Windows Forms destekleyeceği](https://devblogs.microsoft.com/dotnet/net-core-3-and-support-for-windows-desktop-applications/).
- **API'leri** --.NET Core içeren farklı bir hesaba katarak ile büyük bir alt kümesini .NET Framework temel sınıf kitaplığı (derleme adları farklı; üyeler türleri üzerinde kullanıma sunulan farklı anahtar durumda). Bu farklılıklar, bazı durumlarda .NET Core için bağlantı noktası kaynak değişiklikler gerektirir (bkz [dotnet/microsoft-apiport](https://github.com/microsoft/dotnet-apiport)). .NET core uygulayan [.NET Standard](../standard/net-standard.md) API belirtimi.
- **Alt sistemler** --.NET Core, .NET Framework'teki amacı, bir basit uygulama ve programlama modeli ile bir alt kümesini uygular. Yansıma desteklense de, kod erişim güvenliği (CAS), desteklenmiyor.
- **Platformları** --.NET Framework, Windows ve Windows Server .NET Core macOS ve Linux desteklese de destekler.
- **Açık kaynak** --.NET Core, açık kaynak, ancak bir [salt okunur alt .NET Framework'ün](https://github.com/microsoft/referencesource) açık kaynaklıdır.

.NET Core benzersizdir ve .NET Framework ve diğer .NET uygulamaları için önemli farkları vardır, ancak kaynak veya ikili paylaşma teknikleri kullanarak, bu uygulamalar arasında kod paylaşma basittir.

.NET Core yan yana yüklemeyi destekler ve onun çalışma zamanı .NET Framework'ü tamamen bağımsız olduğundan, bu makinelerde .NET Framework'ün yüklü herhangi bir sorun olmadan yüklenebilir.

### <a name="comparison-with-mono"></a>Mono ile karşılaştırma

[Mono](https://www.mono-project.com/) özgün çapraz platform ve [açık kaynak](https://github.com/mono/mono) .NET uygulaması, 2004'te ilk aktarma. Bu, bir .NET Framework'ün topluluk kopya olarak düşünülebilir. Mono projesi team Aç yararlandı [.NET standartları](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (ECMA 335 özellikle) uyumlu bir uygulama sunmak amacıyla Microsoft tarafından yayımlanan.

.NET Core ve Mono arasındaki temel farklar:

- **Uygulama modelleri** --Mono, .NET Framework uygulama-modelleri (örneğin, Windows Forms) ve bazı ek vm'lere kümesini destekler (örneğin, [Xamarin.iOS](https://www.xamarin.com/platform)) Xamarin ürün aracılığıyla. .NET core, bunlar desteklemiyor.
- **API'leri** --Mono destekleyen bir [büyük alt](http://docs.go-mono.com/?link=root%3a%2fclasslib) .NET Framework kullanarak aynı derleme adları ve hesaba katacak şekilde API'leri.
- **Platformları** --Mono birçok platformları ve CPU destekler.
- **Açık kaynak** --Mono ve .NET Core hem MIT lisansı kullanın ve .NET Foundation projeleri.
- **Odak** --Bulut ve Masaüstü iş yükleri üzerinde .NET Core odaklıyken mobil platformlar, Son yıllarda Mono birincil odağı olan.
