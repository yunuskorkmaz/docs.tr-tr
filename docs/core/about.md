---
title: .NET Core hakkında
description: .NET Core hakkında bilgi edinin.
ms.date: 09/17/2019
ms.openlocfilehash: a1127a39d67b6c24994a2957298c62d87703950d
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416740"
---
# <a name="about-net-core"></a>.NET Core hakkında

.NET Core aşağıdaki özelliklere sahiptir:

- **Platformlar arası:** Windows, macOS ve Linux [işletim sistemlerinde](https://github.com/dotnet/core/blob/master/os-lifecycle-policy.md)çalışır.
- **Mimarilerde tutarlı:** Kodunuzu x64, x86 ve ARM dahil olmak üzere birden çok mimaride aynı davranışla çalıştırır.
- **Komut satırı araçları:**  , Yerel geliştirme ve sürekli tümleştirme senaryolarında kullanılabilecek kullanımı kolay komut satırı araçları içerir.
- **Esnek dağıtım:** Uygulamanıza dahil edilebilir veya yan yana (Kullanıcı genelindeki veya sistem genelindeki Yüklemeler) yüklenebilir. [Docker kapsayıcılarıyla](docker/introduction.md)birlikte kullanılabilir.
- **Uyumlu:** .NET Core, [.NET Standard](../standard/net-standard.md)aracılığıyla .NET Framework, Xamarin ve Mono ile uyumludur.
- **Açık Kaynak:** .NET Core platformu, MıT ve Apache 2 lisansları kullanılarak açık kaynaktır. .NET Core, bir [.net Foundation](https://dotnetfoundation.org/) projem.
- **Microsoft tarafından desteklenen:** .NET Core, [.NET Core desteği](https://dotnet.microsoft.com/platform/support/policy)başına Microsoft tarafından desteklenir.

## <a name="languages"></a>Diller

C#, Visual Basic ve F# dilleri .NET Core için uygulama ve kitaplıklar yazmak üzere kullanılabilir. Bu diller, en sevdiğiniz metin düzenleyicisinde veya tümleşik geliştirme ortamında (IDE) birlikte kullanılabilir:

- [Visual Studio](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)
- [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp)
- Alt lime metni
- V
 
Bu tümleştirme, kapsamında, [Omnisharp](https://www.omnisharp.net/) ve [ıonıde](http://ionide.io) projelerinin katkıda bulunanlar tarafından sağlanır.

## <a name="apis"></a>API'ler

.NET Core pek çok senaryo için API 'Leri kullanıma sunar.

- [Bool](../csharp/language-reference/keywords/bool.md) ve [int](../csharp/language-reference/builtin-types/integral-numeric-types.md)gibi temel türler.
- <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> ve <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType>gibi koleksiyonlar.
- <xref:System.Net.Http.HttpClient?displayProperty=nameWithType>ve <xref:System.IO.FileStream?displayProperty=nameWithType>gibi yardımcı program türleri.
- <xref:System.Data.DataSet?displayProperty=nameWithType>ve [Dbset](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore/)gibi veri türleri.
- <xref:System.Numerics.Vector?displayProperty=nameWithType> ve işlem [hatları](https://devblogs.microsoft.com/dotnet/system-io-pipelines-high-performance-io-in-net/)gibi yüksek performanslı türler.

.NET Core, [.NET Standard](../standard/net-standard.md) belirtimini uygulayarak .NET Framework ve mono API 'leri ile uyumluluk sağlar.

## <a name="frameworks"></a>Çerçeveler

.NET Core 'un üzerine birden çok çerçeve oluşturulmuştur:

- [ASP.NET Core](/aspnet/core/)
- [Windows 10 Evrensel Windows Platformu (UWP)](https://developer.microsoft.com/windows)
- [Tizen](https://developer.tizen.org/development/training/.net-application)

## <a name="composition"></a>Birleştirme

.NET Core aşağıdaki bölümlerden oluşur:

- Bir tür sistemi, derleme yükleme, çöp toplayıcı, yerel birlikte çalışma ve diğer temel hizmetler sağlayan [.NET Core çalışma zamanı](https://github.com/dotnet/coreclr). [.NET Core Framework kitaplıkları](https://github.com/dotnet/corefx) temel veri türleri, uygulama bileşim türleri ve temel yardımcı programları sağlar.
- Web uygulamaları, IoT uygulamaları ve mobil arka uçlar gibi modern bulut tabanlı Internet 'e bağlı uygulamalar oluşturmaya yönelik bir çerçeve sağlayan [ASP.NET çalışma zamanı](https://github.com/aspnet/home).
- .NET Core geliştirici deneyimini etkinleştiren [.NET Core CLI araçları](https://github.com/dotnet/cli) ve dil derleyicileri ( [F#](https://github.com/microsoft/visualfsharp)[Roslyn](https://github.com/dotnet/roslyn) ve).
- .NET Core Uygulamaları ve CLı araçları 'nı başlatmak için kullanılan [DotNet aracı](https://github.com/dotnet/core-setup). Çalışma zamanını seçer ve çalışma zamanını barındırır, bir derleme yükleme ilkesi sağlar ve uygulamaları ve araçları başlatır.

Bu bileşenler aşağıdaki yollarla dağıtılır:

- [.NET Core çalışma zamanı](https://dotnet.microsoft.com/download) --.NET Core çalışma zamanı ve çerçeve kitaplıklarını içerir.
- [ASP.NET Core çalışma zamanı](https://dotnet.microsoft.com/download) --ASP.NET Core ve .NET Core çalışma zamanı ve çerçeve kitaplıklarını içerir.
- [.NET Core SDK](https://dotnet.microsoft.com/download) --.net CLI araçlarını, ASP.NET Core çalışma zamanını ve .NET Core çalışma zamanını ve çerçevesini içerir.

### <a name="open-source"></a>Açık kaynak

[.NET Core](https://github.com/dotnet/core) açık kaynaktır ([MIT Lisansı](https://github.com/dotnet/core/blob/master/LICENSE.TXT)) ve Microsoft tarafından 2014 ' de [.net Foundation](https://dotnetfoundation.org) 'a katkıda bulunulamıştı. Artık en etkin .NET Foundation projelerinden biridir. Kişisel, akademik veya ticari amaçlar dahil olmak üzere bireyler ve şirketler tarafından kullanılabilir. Birden çok şirket uygulamalar, Araçlar, yeni platformlar ve barındırma hizmetleri kapsamında .NET Core kullanır. Bu şirketlerin bazıları GitHub 'daki .NET Core 'a önemli katkılar ve [.net Foundation teknik BT grubu](https://dotnetfoundation.org/blog/tsg-welcome)'nun bir parçası olarak ürün yönüne kılavuzluk sağlar.

### <a name="designed-for-adaptability"></a>Uyarlamalı uyumluluk için tasarlandı

.NET Core, diğer .NET ürünleriyle karşılaştırıldığında çok benzer ancak benzersiz bir ürün olarak oluşturulmuştur. Yeni platformlar ve iş yükleri için geniş uyum sağlayacak şekilde tasarlandı ve kullanılabilir birden fazla işletim sistemi ve CPU bağlantı noktasına sahiptir (ve çok daha fazla olabilir).

Ürün çeşitli parçalara ayrılmıştır ve çeşitli parçaların farklı zamanlarda yeni platformlara uyarlanılmasına olanak sağlar. Çalışma zamanına ve platforma özgü temel kitaplıkların birim olarak bir birim olarak bir arada olması gerekir. Platformdan bağımsız kitaplıklar, oluşturma tarafından tüm platformlarda olduğu gibi çalışır. Her bir algoritma veya API 'nin tam olarak veya yerinde bu şekilde uygulanması için, C# platforma özgü uygulamaları azaltmaya yönelik bir proje sapması vardır.

Çok sayıda işletim sistemini desteklemek için insanlar .NET Core 'un nasıl uygulandığını sorar. Bunlar genellikle ayrı uygulamalar olup olmadığını veya [Koşullu derlemenin](https://en.wikipedia.org/wiki/Conditional_compilation) kullanıldığını sorar. Koşullu derlemeye yönelik güçlü bir sapmanın her ikisi de vardır.

Aşağıdaki grafikte [Corefx](https://github.com/dotnet/corefx) 'in büyük çoğunluğunun tüm platformlarda paylaşılan platformdan bağımsız kod olduğunu görebilirsiniz. Platformdan bağımsız kod, tüm platformlarda kullanılan tek bir taşınabilir derleme olarak uygulanabilir.

![CoreFX: platform başına kod satırları](../images/corefx-platforms-loc.png)

Windows ve UNIX uygulamaları boyutuyla benzerdir. CoreFX, [Microsoft. Win32. Registry](https://github.com/dotnet/corefx/tree/master/src/Microsoft.Win32.Registry) gibi bazı Windows özelliklerini uyguladığından ve henüz yalnızca birçok UNIX kavramı uygulamadıklarından, Windows daha büyük bir uygulamaya sahiptir. Ayrıca, Linux ve macOS uygulamalarının çoğunluğunun UNIX uygulamasında paylaşıldığını ve Linux ve macOS 'a özgü uygulamaların kabaca boyutunun kabaca benzer olduğunu görürsünüz.

.NET Core 'da platforma özgü ve platformdan bağımsız kitaplıkların bir karışımı vardır. Bir örneği birkaç örnekte görebilirsiniz:

- [CoreCLR](https://github.com/dotnet/coreclr) platforma özgüdür. Bellek Yöneticisi ve iş parçacığı zamanlayıcısı gibi işletim sistemi alt sistemleri üzerinde oluşturulur.
- [System.IO](https://github.com/dotnet/corefx/tree/master/src/System.IO) ve [System. Security. Cryptography. algoritmaları](https://github.com/dotnet/corefx/tree/master/src/System.Security.Cryptography.Algorithms) , depolama ve şifreleme API 'lerinin her bir işletim sisteminde farklı olduğu verili platforma özgüdür.
- [System. Collections](https://github.com/dotnet/corefx/tree/master/src/System.Collections) ve [System. LINQ](https://github.com/dotnet/corefx/tree/master/src/System.Linq) , veri yapılarını oluşturup üzerinde işledikleri için platformdan bağımsız bir seçenektir.

## <a name="comparisons-to-other-net-implementations"></a>Diğer .NET uygulamalarıyla karşılaştırmalar

.NET Core 'un boyutunu ve şeklini mevcut .NET uygulamalarıyla karşılaştırarak anlamak büyük olasılıkla daha kolay.

### <a name="comparison-with-net-framework"></a>.NET Framework ile karşılaştırma

.NET öncelikle 2000 ' de Microsoft tarafından duyuruldu ve sonra buradan türetilmiştir. .NET Framework, Microsoft tarafından üretilen, neredeyse iki yıllık dönem boyunca oluşturulan birincil .NET uygulamasıdır.

.NET Core ve .NET Framework arasındaki önemli farklılıklar:

- **App-modeller** --. NET Core, tüm .NET Framework uygulama modellerini desteklemez. Özellikle, ASP.NET Web Forms ve ASP.NET MVC 'yi desteklemez, ancak ASP.NET Core MVC 'yi destekler. .NET Core 3,0 ile başlayarak, .NET Core da WPF ve yalnızca Windows 'da Windows Forms destekler.
- Ağ çekirdeği--. **API 'leri** , farklı bir düzenleme temel sınıf kitaplığının büyük bir alt .NET Framework kümesini içerir (derleme adları farklıdır; türler üzerinde gösterilen üyeler, önemli durumlarda farklılık gösterir). Bazı durumlarda bu farklılıklar, bağlantı noktası kaynağında .NET Core 'a değişiklik yapılmasını gerektirir. Daha fazla bilgi için bkz. [.net taşınabilirlik Çözümleyicisi](../standard/analyzers/portability-analyzer.md). .NET Core, [.NET Standard](../standard/net-standard.md) API belirtimini uygular.
- **Alt sistemler** --. NET Core, daha basit bir uygulama ve programlama modelinin hedefi ile .NET Framework alt sistemlerin bir alt kümesini uygular. Örneğin, yansıma desteklenirken kod erişim güvenliği (CAS) desteklenmez.
- **Platformlar** --.NET Core Ayrıca MacOS ve Linux 'u destekleirken, .NET Framework Windows ve Windows Server 'ı destekler.
- **Açık** kaynak--. NET Core açık kaynak olduğundan [.NET Framework bir salt okuma alt kümesi](https://github.com/microsoft/referencesource) açık kaynak olur.

.NET Core benzersizdir ve .NET Framework ve diğer .NET uygulamalarında önemli farklılıklar olmakla çalışırken, kaynak veya ikili paylaşım tekniklerini kullanarak bu uygulamalar arasında kod paylaşımı kolaydır.

.NET Core yan yana yüklemeyi desteklediğinden ve çalışma zamanı .NET Framework tamamen bağımsız olduğundan, herhangi bir sorun olmadan .NET Framework yüklenmiş makinelere yüklenebilir.

### <a name="comparison-with-mono"></a>Mono ile karşılaştırma

[Mono](https://www.mono-project.com/) , .net 'in özgün platformlar arası uygulamasıdır. .NET Framework için [Açık kaynaklı](https://github.com/mono/mono) alternatif olarak başlatılır ve IOS ve Android cihazlar popüler hale geldiğinden mobil cihazları hedeflemeye geçirilir. .NET Framework topluluk kopyası olarak düşünülebilir. Mono proje ekibi, Microsoft tarafından uyumlu bir uygulama sağlamak üzere yayımlanan açık [.net standartlarına](https://github.com/dotnet/coreclr/blob/master/Documentation/project-docs/dotnet-standards.md) (özellikle ECMA 335) güvendi.

.NET Core ve mono arasındaki önemli farklılıklar:

- **Uygulama-modeller** --Mono, .NET Framework App-modeller (örneğin, Windows Forms) ve daha fazla mobil geliştirme (örneğin, [Xamarin. IOS](https://www.xamarin.com/platform)) için Xamarin ürünüyle bir alt kümesini destekler. .NET Core, Xamarin 'i desteklemez.
- **API 'ler** --mono, aynı derleme adlarını ve düzenleme kullanarak .NET Framework API 'lerinin [büyük bir alt kümesini](http://docs.go-mono.com/?link=root%3a%2fclasslib) destekler.
- **Platformlar** --mono birçok platformu ve CPU 'yu destekler.
- **Açık kaynak** --Mono ve .NET Core her IKISI de MIT lisansı kullanır ve .net Foundation projeleri.
- **Odak** --mono son yıllardaki birincil odak, mobil platformlardır ve .NET Core bulut ve masaüstü iş yüklerine odaklanılmıştır.

## <a name="the-future"></a>Gelecek

.NET 5 ' in, .NET Core 'un bir sonraki sürümü olacağı ve platformun bir listesini temsil ettiği duyurulmuştur. Proje, .net 'i birkaç önemli şekilde geliştirmek için amaçlar:

- Her yerde kullanılabilen ve Tekdüzen çalışma zamanı davranışları ve geliştirici deneyimleri içeren tek bir .NET çalışma zamanı ve çerçevesi üretin.
- .NET Core, .NET Framework, Xamarin ve mono 'nin en iyi özelliklerini alarak .NET yeteneklerini genişletin.
- Bu ürünü, geliştiricilerin (Microsoft ve topluluk) üzerinde çalışabileceği ve birlikte ve tüm senaryoları geliştiren tek bir kod tabanında oluşturun.

.NET 5 için nelerin planlanmakta olduğu hakkında daha fazla ayrıntı için bkz. [.NET 5 tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-5/).
