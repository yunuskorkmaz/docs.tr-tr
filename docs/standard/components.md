---
title: .NET mimari bileşenleri
description: .NET Standardı, .NET uygulamaları, .NET çalışma saatleri ve takımlama gibi .NET mimari bileşenlerini açıklar.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: eadcf05069edfa32a52c5e73045b4cebd1a9a6ac
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "79400479"
---
# <a name="net-architectural-components"></a>.NET mimari bileşenleri

.NET uygulaması için geliştirilmiştir ve *.NET'in*bir veya daha fazla uygulamasında çalışır.  .NET'in uygulamaları .NET Framework, .NET Core ve Mono'yu içerir. .NET'in tüm uygulamalarında ortak olan ve .NET Standardı olarak adlandırılan bir API belirtimi vardır. Bu makalede, bu kavramların her biri için kısa bir giriş verir.

## <a name="net-standard"></a>.NET Standard

.NET Standardı, Bir .NET uygulamasının Taban Sınıf Kitaplığı tarafından uygulanan bir API kümesidir. Daha resmi olarak, kodunuzu derlediğiniz tek tip sözleşmeler kümesini oluşturan .NET API'lerinin belirtimidir. Bu sözleşmeler her .NET uygulamasında uygulanır. Bu, farklı .NET uygulamaları arasında taşınabilirlik sağlayarak kodunuzu her yerde etkin bir şekilde çalıştırarak etkinleştirin.

.NET Standardı aynı zamanda bir [hedef çerçevesidir.](glossary.md#target-framework) Kodunuz .NET Standard'ın bir sürümünü hedefliyorsa, .NET Standardının bu sürümünü destekleyen herhangi bir .NET uygulamasında çalıştırılabilir.

.NET Standardı ve nasıl hedeflenecek hakkında daha fazla bilgi edinmek için [.NET Standart](net-standard.md) konusuna bakın.

## <a name="net-implementations"></a>.NET uygulamaları

.NET'in her uygulaması aşağıdaki bileşenleri içerir:

- Bir veya daha fazla çalışma saatleri. Örnekler: .NET Framework için CLR, .NET Core için CoreCLR ve CoreRT.
- .NET Standardını uygulayan ve ek API'ler uygulayabilen bir sınıf kitaplığı. Örnekler: .NET Framework Base Sınıf Kitaplığı, .NET Çekirdek Taban Sınıf Kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: [ASP.NET,](https://www.asp.net/) [Windows Formları](../framework/winforms/windows-forms-overview.md)ve Windows Presentation Foundation [(WPF)](../framework/wpf/index.md) .NET Framework ve .NET Core'a dahildir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

Microsoft'un etkin olarak geliştirdiği ve koruduğu dört birincil .NET uygulaması vardır: .NET Core, .NET Framework, Mono ve UWP.

### <a name="net-core"></a>.NET Core

.NET Core, .NET'in bir platform ötesi uygulamasıdır ve sunucu ve bulut iş yüklerini ölçekte işlemek üzere tasarlanmıştır. Windows, macOS ve Linux'ta çalışır. .NET Standardını uygular, böylece .NET Standardını hedefleyen kod .NET Core'da çalıştırılabilir. [ASP.NET Core,](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core) [Windows Forms](../framework/winforms/windows-forms-overview.md)ve [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) tüm .NET Core üzerinde çalışır.

.NET Core hakkında daha fazla bilgi edinmek [için sunucu uygulamaları için .NET Core](choosing-core-framework-server.md)ve .NET Framework arasında [.NET Core](../core/index.md) ve Seçim Kılavuzu'na bakın.

### <a name="net-framework"></a>.NET Framework

The.NET Framework, 2002 yılından beri var olan orijinal .NET uygulamasıdır. Varolan .NET geliştiricilerin her zaman kullandığı .NET Framework ile aynıdır. Sürüm4.5 ve daha sonra .NET Standardını uygulayın, böylece .NET Standardını hedefleyen kod .NET Framework'ün bu sürümlerinde çalıştırılabilir. Windows Forms ve WPF ile Windows masaüstü geliştirme için API'ler gibi Windows'a özgü ek API'ler içerir. .NET Framework, Windows masaüstü uygulamaları oluşturmak için optimize edilebiyi optimize edin.

.NET Framework hakkında daha fazla bilgi edinmek için [.NET Framework Guide'a](../framework/index.md)bakın.

### <a name="mono"></a>Mono

Mono, küçük bir çalışma süresi gerektiğinde esas olarak kullanılan bir .NET uygulamasıdır. Android, macOS, iOS, tvOS ve watchOS'taki Xamarin uygulamalarına güç veren ve öncelikle küçük bir ayak izine odaklanan çalışma zamanıdır. Mono ayrıca Unity motoru kullanılarak üretilen oyunlara da güç katıyor.

Şu anda yayınlanan tüm .NET Standard sürümlerini destekler.

Tarihsel olarak, Mono .NET Framework'ün daha büyük API'sini uyguladı ve Unix'teki en popüler yeteneklerden bazılarını taklit etti. Bazen Unix'teki bu özelliklere dayanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanında derleyici ile kullanılır, ancak aynı zamanda iOS gibi platformlarda kullanılan tam bir statik derleyici (ileri-zaman derleme) özellikleri.

Mono hakkında daha fazla bilgi edinmek için [Mono belgelerine](https://www.mono-project.com/docs/)bakın.

### <a name="universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP)

UWP, Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows uygulamaları ve yazılımları oluşturmak için kullanılan .NET'in bir uygulamasıdır. Cd'ler, tabletler, phablet'ler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı türde aygıtları birletmek üzere tasarlanmıştır. UWP, merkezi bir uygulama deposu, yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API'si gibi birçok hizmet sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript ile yazılabilir. C# ve Visual Basic kullanırken .NET API'leri .NET Core tarafından sağlanır.

UWP hakkında daha fazla bilgi edinmek [için Evrensel Windows Platformu'na Giriş'e](/windows/uwp/get-started/universal-application-platform-guide)bakın.

## <a name="net-runtimes"></a>.NET çalışma saatleri

Çalışma zamanı, yönetilen bir programın yürütme ortamıdır. İşletim sistemi çalışma zamanı ortamının bir parçasıdır, ancak .NET çalışma zamanının bir parçası değildir. Aşağıda .NET çalışma saatlerine ait bazı örnekler verilmiştir:

- .NET Framework için Ortak Dil Çalışma Süresi (CLR)
- .NET Core için Çekirdek Ortak Dil Çalışma Süresi (CoreCLR)
- .NET Evrensel Windows Platformu için Native
- Xamarin.iOS, Xamarin.Android, Xamarin.Mac ve Mono masaüstü çerçevesi için Mono çalışma süresi

## <a name="net-tooling-and-common-infrastructure"></a>.NET takım lama ve ortak altyapı

.NET'in her uygulamasıyla çalışan kapsamlı bir araç ve altyapı bileşeni kümesine erişebilirsiniz. Bunlar şunlardır, ancak aşağıdakiler ile sınırlı değildir:

- .NET dilleri ve derleyicileri
- .NET proje sistemi *(.csproj*, *.vbproj*ve *.fsproj* dosyalarına göre)
- [MSBuild](/visualstudio/msbuild/msbuild), proje oluşturmak için kullanılan yapı motoru
- [NuGet](/nuget/), Microsoft'un .NET için paket yöneticisi
- [CAKE](https://cakebuild.net/) ve [FAKE](https://fake.build/) gibi açık kaynak yapı orkestrasyon araçları

## <a name="applicable-standards"></a>Geçerli standartlar

C# Language ve Common Language Infrastructure (CLI) spesifikasyonları [Ecma International®](https://www.ecma-international.org/)aracılığıyla standartlaştırılmıştır. Bu standartların ilk baskıları Aralık 2001'de Ecma tarafından yayınlanmıştır.

Program dilleri Teknik Komitesi[(TC49)](https://www.ecma-international.org/memento/tc49.htm)bünyesindeki TC49-TG2 (C#) ve TC49-TG3 (CLI) görev grupları tarafından standartlarda yapılan sonraki revizyonlar, Ecma Genel Kurulu ve daha sonra ISO/IEC JTC 1 tarafından ISO Fast-Track süreci ile kabul edilmiştir.

### <a name="latest-standards"></a>En son standartlar

Aşağıdaki resmi Ecma belgeleri [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) ve [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) [(TR-84)](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)için mevcuttur:

- **C# Dil Standardı (sürüm 5.0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Ortak Dil Altyapısı**: Bu [pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) formu ve [zip](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) şeklinde mevcuttur.
- **Bölüm IV XML Dosyasından Elde Edilen Bilgiler**: Bu [pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) ve [zip](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) formatlarında mevcuttur.

Resmi ISO/IEC belgeleri, ISO/IEC [Genel Kullanıma Sunulan Standartlar](https://standards.iso.org/ittf/PubliclyAvailableStandards/) sayfasından edinilebilir. Bu bağlantılar doğrudan bu sayfadan:

- **Bilgi teknolojisi - Programlama dilleri - C#**: [ISO/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Bilgi teknolojisi — Ortak Dil Altyapısı (CLI) Bölümleri I - VI**: [ISO/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Bilgi teknolojisi — Ortak Dil Altyapısı (CLI) — Bölüm IV XML Dosyadan Elde Edilen Bilgilere Ilişkin Teknik Rapor**: [ISO/IEC TR 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma](choosing-core-framework-server.md)
- [.NET Standard](net-standard.md)
- [.NET Core Kılavuzu](../core/index.md)
- [.NET Çerçeve Rehberi](../framework/index.md)
- [C# Rehberi](../csharp/index.yml)
- [F# Rehberi](../fsharp/index.yml)
- [Visual Basic Kılavuzu](../visual-basic/index.yml)
