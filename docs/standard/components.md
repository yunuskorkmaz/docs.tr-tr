---
title: ".NET Mimari Bileşenleri"
description: ".NET Mimari bileşenleri gibi .NET standart, .NET uygulamaları, .NET çalışma zamanları ve araçları açıklanmaktadır."
author: cartermp
ms.author: mairaw
ms.date: 08/23/2017
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.openlocfilehash: ce3368f4c34a8e4b20a7deb2a6c6e4d163927cd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="net-architectural-components"></a>.NET Mimari Bileşenleri

.NET uygulaması için geliştirilen ve bir veya daha fazla çalışan *.NET uygulamalarında*.  .NET uygulamaları, .NET Framework, .NET Core ve Mono içerir. Tüm .NET standardını çağırdı .NET uygulamaları için ortak API belirtimine yoktur. Bu makalede her Bu kavramlar kısa bir giriş sağlar.

## <a name="net-standard"></a>.NET standart

.NET standart bir .NET uygulaması temel sınıf kitaplığı tarafından uygulanan API kümesidir. Daha resmi olarak karşı kodunuzu derleyin sözleşmeleri Tekdüzen kümesini oluşturan .NET API'lerini belirtimi değil. Bu sözleşmeler, her .NET uygulamasında uygulanır. Bu, etkili bir şekilde kodunuzun her yerde çalışmasına izin vererek farklı .NET uygulamaları arasında taşınabilirlik sağlar.

.NET de standarttır bir [hedef framework](glossary.md#target-framework). Kodunuzu .NET standart bir sürümünü hedefliyorsa, bu sürümü .NET standardını destekleyen tüm .NET uygulaması çalışabilir.

.NET standart hem de hedeflemek üzere nasıl hakkında daha fazla bilgi için bkz: [.NET standart](net-standard.md) konu.

## <a name="net-implementations"></a>.NET uygulamaları

Her .NET uygulaması aşağıdaki bileşenleri içerir:

- Bir veya daha fazla çalışma zamanları. Örnekler: CLR .NET Framework, CoreCLR ve .NET Core CoreRT.
- .NET standart uygular ve ek API'leri uygulayabilir sınıf kitaplığı. Örnekler: .NET Framework temel sınıf kitaplığı, .NET Core temel sınıf kitaplığı.
- İsteğe bağlı olarak, bir veya daha fazla uygulama çerçeveleri. Örnekler: [ASP.NET](https://www.asp.net/), [Windows Forms](../framework/winforms/windows-forms-overview.md), ve [Windows Presentation Foundation (WPF)](../framework/wpf/index.md) .NET Framework dahil edilir.
- İsteğe bağlı olarak, geliştirme araçları. Bazı geliştirme araçları birden çok uygulamalar arasında paylaşılır.

Microsoft etkin olarak geliştirir ve tutar dört birincil .NET uygulamaları vardır: .NET Core, .NET Framework, Mono ve UWP.

### <a name="net-core"></a>.NET Core

.NET core .NET platformlar arası uygulamasıdır ve ölçekte server ve bulut iş yüklerini işlemek üzere tasarlanmıştır. Windows, macOS ve Linux üzerinde çalışır. .NET standardını hedefleyen kod .NET Core üzerinde çalıştırabilmeniz için .NET standart, uygular. ASP.NET Core .NET Core üzerinde çalışır. 

.NET Core hakkında daha fazla bilgi için bkz: [.NET Core Kılavuzu](../core/index.md) ve [sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma](choosing-core-framework-server.md).

### <a name="net-framework"></a>.NET Framework

.NET Framework itibaren 2002 olmamış özgün .NET uygulamasıdır. Var olan .NET geliştiricilerinin her zaman kullanılan .NET Framework değil. Sürüm 4.5 ve sonraki uygulama .NET standart, .NET standardını hedefleyen Bu kod .NET Framework'ün bu sürümlerde çalıştırabilirsiniz. Windows Forms ve WPF ile API'leri için Windows Masaüstü geliştirme gibi ek Windows'a özgü API içerir. .NET Framework Windows Masaüstü uygulamaları oluşturmak için en iyi duruma getirilmiştir.

.NET Framework hakkında daha fazla bilgi için bkz: [.NET Framework Kılavuzu](../framework/index.md).

### <a name="mono"></a>Mono

Mono küçük bir çalışma zamanı gerekli olduğunda, genel olarak kullanılan bir .NET uygulamasıdır. Bu, Android, Mac, iOS, tvOS ve watchOS Xamarin uygulamalarını çalıştırır ve öncelikle küçük bir yer üzerinde odaklanmıştır çalışma zamanı gösterir.

Şu anda yayımlanan .NET standart sürümlerin tümünü destekler.

Geçmişte, Mono büyük API'si .NET Framework'ün uygulanan ve bazı UNIX üzerindeki en popüler özelliklerini benzetilmiş. Bazı durumlarda, bu yetenekleri UNIX Bel .NET uygulamalarını çalıştırmak için kullanılır.

Mono genellikle tam zamanı derleyicisi ile kullanılır, ancak ayrıca iOS gibi platformlarda kullanılan bir tam statik derleyici (biri zamanında tamamlanan derleme) sahiptir.

Mono hakkında daha fazla bilgi için bkz: [Mono belgelerine](http://www.mono-project.com/docs/).

### <a name="universal-windows-platform-uwp"></a>Evrensel Windows Platformu (UWP)

UWP modern, Dokunmatik özellikli Windows uygulamaları ve yazılım nesnelerin interneti için (IOT) oluşturmak için kullanılan .NET uygulamasıdır. Bu farklı türde hedeflemek isteyebilirsiniz cihazları birleştirmek için PC'ler, tabletler, phablets, telefonlar ve bile Xbox dahil olmak üzere tasarlanmıştır. UWP Merkezi uygulama mağazası, Yürütme Ortamı (Appcontaıner) ve Windows API'larını Win32 yerine kullanılacak bir dizi gibi birçok hizmetler sağlar (WinRT). Uygulamalar, C++, C#, VB.NET ve JavaScript yazılabilir. C# ve VB.NET kullanırken, .NET API'lerini .NET Core tarafından sağlanır.

UWP hakkında daha fazla bilgi için bkz: [Evrensel Windows platformu giriş](https://docs.microsoft.com/windows/uwp/get-started/universal-application-platform-guide).

## <a name="net-runtimes"></a>.NET çalışma zamanları

Bir çalışma zamanı yönetilen program Yürütme Ortamı ' dir. İşletim Sisteminin çalışma zamanı ortamı parçası olan ancak .NET çalışma zamanı parçası değil. .NET çalışma zamanları bazı örnekleri şunlardır:
 
 - Ortak dil çalışma zamanı (CLR) .NET Framework için
 - Çekirdek ortak dil çalışma zamanı (CoreCLR) .NET Core için
 - Evrensel Windows platformu için .NET yerel 
 - Xamarin.iOS, Xamarin.Android, Xamarin.Mac ve Mono Masaüstü framework Mono çalışma zamanı

## <a name="net-tooling-and-common-infrastructure"></a>.NET araçları ve ortak altyapısı

Kapsamlı birtakım Araçlar ve .NET her bir uygulama ile iş altyapı bileşenlerini erişebilirsiniz. Bunlar arasında ancak bunlarla sınırlı değildir:

- .NET dilleri ve bunların derleyicileri
- .NET proje sistemini (temel *.csproj*, *.vbproj*, ve *.fsproj* dosyaları)
- [MSBuild](/visualstudio/msbuild/msbuild), projeler derlemek için kullanılan yapı altyapısı
- [NuGet](/nuget/), .NET için Microsoft Paket Yöneticisi
- Açık kaynak yapı düzenleme araçları, gibi [PASTA](http://cakebuild.net/) ve [sahte](https://fake.build/)

## <a name="see-also"></a>Ayrıca bkz.
[Sunucu uygulamaları için .NET Core ve .NET Framework arasında seçim yapma](choosing-core-framework-server.md)   
[.NET standart](net-standard.md)  
[.NET core Kılavuzu](../core/index.md)  
[.NET framework Kılavuzu](../framework/index.md)  
[C# Kılavuzu](../csharp/index.md)  
[F # Kılavuzu](../fsharp/index.md)  
[VB.NET Kılavuzu](../visual-basic/index.md)  

