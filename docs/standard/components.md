---
title: .NET mimari bileşenleri
description: .NET Standard, .NET uygulamaları, .NET çalışma zamanları ve araç araçları gibi .NET mimari bileşenlerini açıklar.
author: cartermp
ms.date: 10/05/2020
ms.openlocfilehash: c5f174034ce0cd0e1cf0b799c7b3f4bff99447a2
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100423141"
---
# <a name="net-architectural-components"></a>.NET mimari bileşenleri

.NET uygulaması, bir veya daha fazla *.net* uygulamasında geliştirilir ve çalışır. .NET uygulamaları .NET Framework, .NET 5 (ve .NET Core) ve mono 'yı içerir. .NET Standard adlı çok sayıda .NET uygulaması için ortak bir API belirtimi vardır. Bu makalede, bu kavramların her birine kısa bir giriş sunulmaktadır.

## <a name="net-standard"></a>.NET Standard

.NET Standard, bir .NET uygulamasının temel sınıf kitaplığı tarafından uygulanan bir API kümesidir. Daha basit bir deyişle, kodunuzu derleyebileceğiniz tek bir sözleşme kümesini oluşturan .NET API 'lerinin bir belirtimidir. Bu sözleşmeler birden çok .NET uygulamasında uygulanır.

.NET Standard, [hedef çerçevedir](glossary.md#target-framework). Kodunuz bir .NET Standard sürümünü hedefliyorsa, bu .NET Standard sürümünü destekleyen tüm .NET uygulamalarında çalıştırılabilir.

.NET Standard, farklı .NET uygulamalarında taşınabilirliği sağlamak için oluşturulmuştur, ancak artık .NET 5 birden çok platformda ve iş yükleri arasında kod paylaşmanın daha iyi bir yolunu sunmaktadır. Daha fazla bilgi için bkz. [.NET 5 ve .NET Standard](net-standard.md#net-5-and-net-standard).

## <a name="net-implementations"></a>.NET uygulamaları

Her bir .NET uygulamasını aşağıdaki bileşenleri içerir:

- Bir veya daha fazla çalışma zamanı. Örnekler: .NET Framework CLR, .NET 5 CLR.
- Bir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET 5 temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: [ASP.net](https://www.asp.net/), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)ve [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) .NET Framework ve .NET 5 ' te bulunur.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

Microsoft 'un desteklediği dört .NET uygulaması vardır:

- .NET 5 (ve .NET Core) ve sonraki sürümler
- .NET Framework
- Mono
- UWP

.NET 5 artık, devam eden geliştirmede odak olan birincil uygulama. .NET 5, Windows Masaüstü uygulamaları ve platformlar arası konsol uygulamaları, bulut hizmetleri ve Web siteleri gibi birden çok platformu ve birçok iş yükünü destekleyen tek bir kod tabanı üzerine kurulmuştur.

### <a name="net-5"></a>.NET 5

.NET 5, sunucu ve bulut iş yüklerini ölçekli olarak işleyecek şekilde tasarlanan, .NET 'in platformlar arası bir uygulamasıdır. Masaüstü uygulamaları dahil diğer iş yüklerini da destekler. Windows, macOS ve Linux üzerinde çalışır. .NET Standard uyguladığı için, .NET Standard hedeflenen kod .NET 5 ' te çalıştırılabilir. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](/dotnet/desktop/winforms/windows-forms-overview)ve [Windows Presentation Foundation (WPF)](/dotnet/desktop/wpf/) hepsi .NET 5 ' te çalışır.

Daha fazla bilgi için aşağıdaki kaynaklara bakın:

- [.NET tanıtımı](../core/introduction.md)
- [Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma](choosing-core-framework-server.md)
- [.NET 5 ve .NET Standard](net-standard.md#net-5-and-net-standard)

### <a name="net-framework"></a>.NET Framework

.NET Framework, 2002 tarihinden itibaren var olan özgün .NET uygulamasıdır. 4,5 sürümleri ve daha sonraki sürümler .NET Standard, bu nedenle .NET Standard hedefleyen kod .NET Framework bu sürümlerinde çalıştırılabilir. Windows Forms ve WPF ile Windows masaüstü geliştirme için API 'Ler gibi Windows 'a özgü ek API 'Leri içerir. .NET Framework, Windows Masaüstü uygulamaları oluşturmak için en iyi duruma getirilmiştir.

Daha fazla bilgi için [.NET Framework kılavuzuna](../framework/index.yml)bakın.

### <a name="mono"></a>Mono

Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan bir .NET uygulamasıdır. Android, macOS, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir parmak izine odaklanılmıştır. Mono Ayrıca Unity altyapısı kullanılarak oluşturulan oyunları güçlendirir.

Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.

Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler. Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanında bir derleyici ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir statik derleyici (güncel derleme) da sunar.

Daha fazla bilgi için [mono belgelerine](https://www.mono-project.com/docs/)bakın.

### <a name="universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP)

UWP, Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılımları oluşturmak için kullanılan bir .NET uygulamasıdır. Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır. UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir.

Daha fazla bilgi için bkz. [Evrensel Windows platformu giriş](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>.NET çalışma zamanları

Çalışma zamanı, yönetilen bir programın yürütme ortamıdır. İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir. .NET çalışma zamanlarının bazı örnekleri aşağıda verilmiştir:

- .NET Framework için ortak dil çalışma zamanı (CLR)
- .NET 5 için ortak dil çalışma zamanı (CLR)
- Evrensel Windows Platformu için .NET Native
- Xamarin. iOS, Xamarin. Android, Xamarin. Mac ve mono masaüstü çerçevesi için mono çalışma zamanı

## <a name="net-tooling-and-common-infrastructure"></a>.NET araçları ve ortak altyapı

.NET ' in her uygulamasıyla çalışan kapsamlı bir araç ve altyapı bileşeni kümesine erişirsiniz. Bu araçlar ve bileşenler şunlardır:

- .NET dilleri ve derleyicileri
- .NET proje sistemi ( *. csproj*, *. vbproj* ve *. fsproj* dosyaları temel alınarak)
- [MSBuild](/visualstudio/msbuild/msbuild), proje derlemek için kullanılan derleme altyapısı
- [NuGet](/nuget/), Microsoft 'un .NET için Paket Yöneticisi
- [Pasta](https://cakebuild.net/) ve [sahte](https://fake.build/) gibi açık kaynaklı derleme düzenleme araçları

Daha fazla bilgi için bkz. [Araçlar ve üretkenlik](../core/introduction.md#tools-and-productivity).

## <a name="applicable-standards"></a>Uygun standartlar

C# dili ve ortak dil altyapısı (CLı) belirtimleri [Ecma International &reg; ](https://www.ecma-international.org/)aracılığıyla standartlaştırılmıştır. Bu standartların ilk sürümleri, Aralık 2001 ' de ECMA tarafından yayımlanmıştır.

Standartlardaki sonraki düzeltmeler, programlama dilleri Technical komite ([TC49](https://www.ecma-international.org/memento/tc49.htm)) içinde TC49-tg2 (C#) ve TC49-TG3 (CLI) görev grupları tarafından geliştirilmiştir ve ECMA genel derlemesi tarafından ve ardından ISO/ıEC JTC 1 tarafından ISO Fast-Track işlemi aracılığıyla benimsenmiştir.

### <a name="latest-standards"></a>En son standartlar

Aşağıdaki resmi ECMA belgeleri [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) ve [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([tr-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) için kullanılabilir:

- **C# dil standardı (sürüm 5,0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Ortak dil altyapısı**: [ECMA-335.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf).
- **IV XML dosyasından türetilmiş bilgiler**: [ECMA-084.pdf](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) biçimi.

Resmi ISO/ıEC belgeleri ISO/ıEC [genel kullanıma açık standartlar](https://standards.iso.org/ittf/PubliclyAvailableStandards/) sayfasından kullanılabilir. Bu bağlantılar bu sayfadan doğrudan yapılır:

- **Bilgi teknolojisi-programlama dilleri-C#**: [ıso/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Bilgi teknolojisi — mı Istediğim ortak dil altyapısı (CLI) bölümleri**: [ıso/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Bilgi teknolojisi — ortak dil altyapısı (CLI) — Bölüm IV XML dosyasından türetilen bilgiler hakkında teknik rapor**: [ISO/IEC tr 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Ayrıca bkz.

- [.NET tanıtımı](../core/introduction.md)
- [.NET Standard giriş](net-standard.md)
- [Sunucu uygulamaları için .NET 5 ve .NET Framework arasında seçim yapma](choosing-core-framework-server.md)
- [.NET Framework Kılavuzu](../framework/index.yml)
- [C# Kılavuzu](../csharp/index.yml)
- [F# Kılavuzu](../fsharp/index.yml)
- [Visual Basic Kılavuzu](../visual-basic/index.yml)
