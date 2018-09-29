---
title: .NET Mimari Bileşenleri
description: .NET Mimari bileşenleri gibi .NET standart, .NET uygulamaları, .NET çalışma zamanları ve araçları açıklar.
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.technology: dotnet-standard
ms.openlocfilehash: e131ab48b666f2d22d8bd02e41ed76e415a2597d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47456031"
---
# <a name="net-architectural-components"></a>.NET Mimari Bileşenleri

Bir .NET uygulaması için geliştirilmiştir ve bir veya daha fazla çalışan *.NET uygulamalarını*.  .NET uygulamaları, .NET Framework, .NET Core ve Mono içerir. Tüm .NET Standard çağırdı .NET uygulamaları için ortak bir API belirtim yoktur. Bu makalede, her biri bu kavramlar kısa bir giriş sağlar.

## <a name="net-standard"></a>.NET standard

.NET Standard bir .NET uygulaması temel sınıf kitaplığı tarafından uygulanan bir API kümesidir. Daha eski adıyla, kodunuzu derlemek sözleşmeleri Tekdüzen bir kümesini oluşturan bir .NET API'lerini belirtimini olduğu. Bu sözleşmeler, her bir .NET uygulamasında uygulanır. Bu, etkili bir şekilde kodunuzu her yerde çalışmasına izin vererek farklı .NET uygulamaları arasında taşınabilirlik sağlar.

Ayrıca .NET Standard olduğu bir [hedef Framework'ü](glossary.md#target-framework). Kodunuzu .NET Standard bir sürümü hedefliyorsa, .NET Standard sürümünü destekleyen tüm .NET uygulaması çalıştırabilirsiniz.

.NET Standard ve hedeflemek nasıl hakkında daha fazla bilgi için bkz: [.NET Standard](net-standard.md) konu.

## <a name="net-implementations"></a>.NET uygulamaları

Her .NET uygulaması, aşağıdaki bileşenleri içerir:

- Bir veya daha fazla çalışma zamanları. Örnekler: .NET Framework, CoreCLR ve .NET Core için CoreRT CLR.
- Ek API'ler uygulayabilir ve .NET Standard uygulayan bir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri. Örnekler: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), ve [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) .NET Framework'teki dahil edilir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları, birden çok uygulama arasında paylaşılır.

Microsoft etkin olarak geliştirir ve tutar dört birincil .NET uygulamaları vardır: .NET Core, .NET Framework, Mono ve UWP.

### <a name="net-core"></a>.NET Core

.NET core, bir çoklu platform .NET uygulamasıdır ve uygun ölçekte sunucu ve bulut iş yüklerini işlemek üzere tasarlanmıştır. İşlem, Windows, macOS ve Linux üzerinde çalışır. .NET Standard hedefleyen kod, .NET Core üzerinde çalışabilen bu nedenle .NET standart, uygular. ASP.NET Core, .NET Core üzerinde çalışır. 

.NET Core hakkında daha fazla bilgi için bkz: [.NET Core Kılavuzu](../core/index.md) ve [sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework beri 2002 olmamış özgün .NET uygulamasıdır. Mevcut .NET geliştiricilerinin her zaman kullanılan .NET Framework var. Sürüm 4.5 ve sonraki uygulamanıza .NET standart, .NET Framework sürümlerinin .NET Standard hedefleyen çok kod çalıştırabilirsiniz. Windows Forms ve WPF ile API'leri için Windows Masaüstü geliştirme gibi ek Windows özel API'ler içeriyor. .NET Framework, Windows Masaüstü uygulamaları oluşturmak için en iyi duruma getirilmiştir.

.NET Framework hakkında daha fazla bilgi için bkz: [.NET Framework Kılavuzu](../framework/index.md).

### <a name="mono"></a>Mono

Mono küçük bir çalışma zamanı gerekli olduğunda, esas olarak kullanılan bir .NET uygulamasıdır. Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikli olarak küçük ayak izine üzerinde odaklanmıştır çalışma zamanıdır. Mono ayrıca Unity altyapısı kullanılarak oluşturulan oyunlar çalıştırır.

Tüm şu anda yayımlanan .NET Standard sürümlerini destekler.

Tarihsel olarak, Mono .NET Framework'ün daha büyük API uygulanan ve bazı UNIX üzerinde en popüler özelliklerini benzetilmiş. Bazen UNIX bu özellikleri kullanan .NET uygulamaları çalıştırmak için kullanılır.

Mono genellikle bir tam zamanında derleyici ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan tam statik bir derleyici (, zamanında tamamlanan derleme) sahiptir.

Mono hakkında daha fazla bilgi için bkz: [Mono belgeleri](https://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP)

UWP, Windows uygulamaları ve yazılım modern ve Dokunmatik kullanıma nesnelerin interneti için (IOT) oluşturmak için kullanılan .NET uygulamasıdır. Bunu hedeflemek isteyebilirsiniz cihazlar farklı türde buluşturulan PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır. UWP, merkezi bir mağazaya, Yürütme Ortamı (AppContainer) ve bir dizi yerine Win32 kullanmak için Windows API gibi birçok hizmetleri sunar (WinRT). Uygulamaları, C++, C#, VB.NET ve JavaScript içinde yazılabilir. C# ve vb.NET'TE kullanırken, .NET API'lerini .NET Core tarafından sağlanır.

UWP hakkında daha fazla bilgi için bkz: [Evrensel Windows platformu giriş](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>.NET çalışma zamanları

Bir çalışma zamanı, yönetilen bir program için yürütme ortamıdır. İşletim Sisteminin çalışma zamanı ortamının parçası olan ancak .NET çalışma zamanı bir parçası değil. .NET çalışma zamanları bazı örnekleri aşağıda verilmiştir:

- Ortak dil çalışma zamanı (CLR) için .NET Framework
- Çekirdek ortak dil çalışma zamanı (CoreCLR) .NET Core için
- Evrensel Windows platformu için .NET native 
- Xamarin.iOS ve Xamarin.Android, Xamarin.Mac ve Mono Masaüstü framework için Mono çalışma zamanı

## <a name="net-tooling-and-common-infrastructure"></a>.NET araçları ve ortak altyapı

Kapsamlı bir dizi araç ve her .NET uygulaması ile çalışma altyapı bileşenlerini erişebilirsiniz. Bunlar içerir ancak bunlarla sınırlı değildir:

- .NET dilleri ve bunların derleyicileri
- .NET proje sistemi (temel *.csproj*, *.vbproj*, ve *.fsproj* dosyaları)
- [MSBuild](/visualstudio/msbuild/msbuild), projeleri derlemek için kullanılan yapı altyapısı
- [NuGet](/nuget/), Microsoft'un .NET için Paket Yöneticisi
- Gibi açık kaynak derleme düzenleme araçları [PASTA](https://cakebuild.net/) ve [sahte](https://fake.build/)

## <a name="see-also"></a>Ayrıca bkz.

- [Sunucu uygulamaları için .NET Core ile .NET Framework arasında seçim yapma](choosing-core-framework-server.md)   
- [.NET Standard](net-standard.md)  
- [.NET Core Kılavuzu](../core/index.md)  
- [.NET Framework Kılavuzu](../framework/index.md)  
- [C# Kılavuzu](../csharp/index.md)  
- [F# Kılavuzu](../fsharp/index.md)  
- [VB.NET Kılavuzu](../visual-basic/index.md)  
