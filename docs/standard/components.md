---
title: .NET mimari bileşenleri
description: .NET Standard, .NET uygulamaları, .NET çalışma zamanları ve araç araçları gibi .NET mimari bileşenlerini açıklar.
author: cartermp
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: 2fc8bcea59cd2ba652b88644677f077d62994ca4
ms.sourcegitcommit: b1f4756120deaecb8b554477bb040620f69a4209
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89414740"
---
# <a name="net-architectural-components"></a>.NET mimari bileşenleri

.NET uygulaması, bir veya daha fazla *.net*uygulamasında geliştirilir ve çalışır.  .NET uygulamaları .NET Framework, .NET Core ve mono 'yı içerir. .NET Standard adı verilen tüm .NET uygulamalarında ortak bir API belirtimi vardır. Bu makalede, bu kavramların her birine kısa bir giriş sunulmaktadır.

## <a name="net-standard"></a>.NET Standard

.NET Standard, bir .NET uygulamasının temel sınıf kitaplığı tarafından uygulanan bir API kümesidir. Daha basit bir deyişle, kodunuzu derleyebileceğiniz tek bir sözleşme kümesini oluşturan .NET API 'lerinin bir belirtimidir. Bu sözleşmeler her bir .NET uygulamasında uygulanır. Bu, farklı .NET uygulamalarında taşınabilirliği sağlayarak kodunuzun her yerde çalışmasına olanak tanır.

.NET Standard Ayrıca bir [hedef çerçevedir](glossary.md#target-framework). Kodunuz bir .NET Standard sürümünü hedefliyorsa, bu .NET Standard sürümünü destekleyen tüm .NET uygulamalarında çalıştırılabilir.

.NET Standard ve nasıl hedeflenecek hakkında daha fazla bilgi edinmek için bkz. [.NET Standard](net-standard.md).

## <a name="net-implementations"></a>.NET uygulamaları

Her bir .NET uygulamasını aşağıdaki bileşenleri içerir:

- Bir veya daha fazla çalışma zamanı. Örnekler: CLR for .NET Framework, CoreCLR ve CoreRT for .NET Core.
- .NET Standard uygulayan ve ek API 'Leri uygulayan bir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçevesi. Örnekler: [ASP.net](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md)ve [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) .NET Framework ve .NET Core 'a dahildir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulama arasında paylaşılır.

Microsoft 'un etkin bir şekilde geliştirdiği ve bakımını yaptığı dört birincil .NET uygulaması vardır: .NET Core, .NET Framework, mono ve UWP.

### <a name="net-core"></a>.NET Core

.NET Core, .NET 'in platformlar arası bir uygulamasıdır ve sunucu ve bulut iş yüklerini ölçekli olarak işleyecek şekilde tasarlanmıştır. Windows, macOS ve Linux üzerinde çalışır. .NET Standard uyguladığı için, .NET Standard hedefleyen kod .NET Core üzerinde çalıştırılabilir. [ASP.NET Core](https://dotnet.microsoft.com/learn/aspnet/what-is-aspnet-core), [Windows Forms](../framework/winforms/windows-forms-overview.md)ve [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) tüm .NET Core üzerinde çalışır.

.NET Core hakkında daha fazla bilgi edinmek için bkz. .NET Core [tanıtımı](../core/introduction.md) ve [sunucu uygulamaları için .net Core ve .NET Framework seçme](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework, 2002 tarihinden itibaren var olan özgün .NET uygulamasıdır. 4,5 sürümleri ve daha sonraki sürümler .NET Standard, bu nedenle .NET Standard hedefleyen kod .NET Framework bu sürümlerinde çalıştırılabilir. Windows Forms ve WPF ile Windows masaüstü geliştirme için API 'Ler gibi Windows 'a özgü ek API 'Leri içerir. .NET Framework, Windows Masaüstü uygulamaları oluşturmak için en iyi duruma getirilmiştir.

.NET Framework hakkında daha fazla bilgi edinmek için [.NET Framework kılavuzuna](../framework/index.yml)bakın.

### <a name="mono"></a>Mono

Mono, genellikle küçük bir çalışma zamanı gerektiğinde kullanılan bir .NET uygulamasıdır. Android, macOS, iOS, tvOS ve watchOS üzerinde Xamarin uygulamalarını güçlendirir ve öncelikle küçük bir parmak izine odaklanılmıştır. Mono Ayrıca Unity altyapısı kullanılarak oluşturulan oyunları güçlendirir.

Şu anda yayımlanmış .NET Standard sürümlerinin tümünü destekler.

Tarihsel olarak, mono .NET Framework daha büyük API 'sini uyguladık ve UNIX üzerinde en popüler yeteneklerin bazılarını öykünüyler. Bu özellik bazen UNIX üzerinde bu özellikleri kullanan .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanında bir derleyici ile kullanılır, ancak iOS gibi platformlarda kullanılan tam bir statik derleyici (güncel derleme) da sunar.

Mono hakkında daha fazla bilgi edinmek için [mono belgelerine](https://www.mono-project.com/docs/)bakın.

### <a name="universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP)

UWP, Nesnelerin İnterneti (IoT) için modern, dokunmatik özellikli Windows Uygulamaları ve yazılımları oluşturmak için kullanılan bir .NET uygulamasıdır. Bilgisayar, tabletler, telefonlar ve hatta Xbox dahil olmak üzere hedeflemek isteyebileceğiniz farklı cihaz türlerini içerecek şekilde tasarlanmıştır. UWP, merkezi bir App Store, bir yürütme ortamı (AppContainer) ve Win32 (WinRT) yerine kullanılacak bir dizi Windows API 'si gibi birçok hizmeti sağlar. Uygulamalar C++, C#, Visual Basic ve JavaScript 'te yazılabilir. C# ve Visual Basic kullanılırken .NET API 'Leri .NET Core tarafından sağlanır.

UWP hakkında daha fazla bilgi edinmek için bkz. [Evrensel Windows platformu giriş](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>.NET çalışma zamanları

Çalışma zamanı, yönetilen bir programın yürütme ortamıdır. İşletim sistemi çalışma zamanı ortamının bir parçasıdır ancak .NET çalışma zamanının bir parçası değildir. .NET çalışma zamanlarının bazı örnekleri aşağıda verilmiştir:

- .NET Framework için ortak dil çalışma zamanı (CLR)
- .NET Core için çekirdek ortak dil çalışma zamanı (CoreCLR)
- Evrensel Windows Platformu için .NET Native
- Xamarin. iOS, Xamarin. Android, Xamarin. Mac ve mono masaüstü çerçevesi için mono çalışma zamanı

## <a name="net-tooling-and-common-infrastructure"></a>.NET araçları ve ortak altyapı

.NET ' in her uygulamasıyla çalışan kapsamlı bir araç ve altyapı bileşeni kümesine erişirsiniz. Bu araçlar ve bileşenler şunlardır:

- .NET dilleri ve derleyicileri
- .NET proje sistemi ( *. csproj*, *. vbproj*ve *. fsproj* dosyaları temel alınarak)
- [MSBuild](/visualstudio/msbuild/msbuild), proje derlemek için kullanılan derleme altyapısı
- [NuGet](/nuget/), Microsoft 'un .NET için Paket Yöneticisi
- [Pasta](https://cakebuild.net/) ve [sahte](https://fake.build/) gibi açık kaynaklı derleme düzenleme araçları

## <a name="applicable-standards"></a>Uygun standartlar

C# dili ve ortak dil altyapısı (CLı) belirtimleri [Ecma International &reg; ](https://www.ecma-international.org/)aracılığıyla standartlaştırılmıştır. Bu standartların ilk sürümleri, Aralık 2001 ' de ECMA tarafından yayımlanmıştır.

Standartlardaki sonraki düzeltmeler, programlama dilleri Technical komite ([TC49](https://www.ecma-international.org/memento/tc49.htm)) içinde TC49-tg2 (C#) ve TC49-TG3 (CLI) görev grupları tarafından geliştirilmiştir ve ECMA genel derlemesi tarafından ve ardından ISO/ıEC JTC 1 tarafından ISO hızlı izleme işlemi aracılığıyla benimsenmiştir.

### <a name="latest-standards"></a>En son standartlar

Aşağıdaki resmi ECMA belgeleri [C#](http://www.ecma-international.org/publications/standards/Ecma-334.htm) ve [CLI](http://www.ecma-international.org/publications/standards/Ecma-335.htm) ([tr-84](http://www.ecma-international.org/publications/techreports/E-TR-084.htm)) için kullanılabilir:

- **C# dil standardı (sürüm 5,0)**: [ECMA-334.pdf](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)
- **Ortak dil altyapısı**: [PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.pdf) form ve [ZIP](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-335.zip) formunda kullanılabilir.
- **IV XML dosyasından türetilmiş bilgiler**: [PDF](https://www.ecma-international.org/publications/files/ECMA-TR/ECMA%20TR-084.pdf) ve [ZIP](https://www.ecma-international.org/publications/files/ECMA-TR/TR-084.zip) biçimlerinde kullanılabilir.

Resmi ISO/ıEC belgeleri ISO/ıEC [genel kullanıma açık standartlar](https://standards.iso.org/ittf/PubliclyAvailableStandards/) sayfasından kullanılabilir. Bu bağlantılar bu sayfadan doğrudan yapılır:

- **Bilgi teknolojisi-programlama dilleri-C#**: [ıso/IEC 23270:2018](https://standards.iso.org/ittf/PubliclyAvailableStandards/c075178_ISO_IEC_23270_2018.zip)
- **Bilgi teknolojisi — mı Istediğim ortak dil altyapısı (CLI) bölümleri**: [ıso/IEC 23271:2012](https://standards.iso.org/ittf/PubliclyAvailableStandards/c058046_ISO_IEC_23271_2012(E).zip)
- **Bilgi teknolojisi — ortak dil altyapısı (CLI) — Bölüm IV XML dosyasından türetilen bilgiler hakkında teknik rapor**: [ISO/IEC tr 23272:2011](https://standards.iso.org/ittf/PubliclyAvailableStandards/c057955_ISO_IEC_TR_23272_2011.zip)

## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma](choosing-core-framework-server.md)
- [.NET Standard giriş](net-standard.md)
- [.NET Core tanıtımı](../core/introduction.md)
- [.NET Framework Kılavuzu](../framework/index.yml)
- [C# Kılavuzu](../csharp/index.yml)
- [F # Kılavuzu](../fsharp/index.yml)
- [Visual Basic Kılavuzu](../visual-basic/index.yml)
