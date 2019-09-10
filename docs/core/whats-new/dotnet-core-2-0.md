---
title: ​.NET Core 2.0’deki yenilikler
description: .NET Core 'da bulunan yeni özellikler hakkında bilgi edinin.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: c208f565bebedc06e244de1f6554129f21c77b8c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70849939"
---
# <a name="whats-new-in-net-core-20"></a>​.NET Core 2.0’deki yenilikler

.NET Core 2,0, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:

- [Araçları](#tooling)
- [Dil desteği](#language-support)
- [Platform geliştirmeleri](#platform-improvements)
- [API değişiklikleri](#api-changes-and-library-support)
- [Visual Studio tümleştirmesi](#visual-studio-integration)
- [Belge geliştirmeleri](#documentation-improvements)

## <a name="tooling"></a>Araçlar

### <a name="dotnet-restore-runs-implicitly"></a>dotnet restore örtük olarak çalıştırılır

.NET Core 'un önceki sürümlerinde, [DotNet New](../tools/dotnet-new.md) komutuyla yeni bir proje oluşturduktan sonra ve projenize yeni bir bağımlılık eklediğiniz her seferinde bağımlılıkları indirmek için [DotNet restore](../tools/dotnet-restore.md) komutunu çalıştırmanız gerekiyordu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

`dotnet restore` `--no-restore` Ayrıca ,`new`anahtarı, ,,`run`, ve komutlarınageçirerekotomatikçağrısını`test` devre dışı bırakabilirsiniz. `build` `publish` `pack`

### <a name="retargeting-to-net-core-20"></a>.NET Core 2,0 için yeniden hedefleme

.NET Core 2,0 SDK 'Sı yüklüyse, .NET Core 1. x 'i hedefleyen projeler .NET Core 2,0 ' e yeniden hedeflenebilir.

.NET Core 2,0 ' ye yeniden hedeflemesini sağlamak için, 1. x ile 2,0 arasında `<TargetFramework>` (veya proje dosyanızda `<TargetFrameworks>` birden fazla hedef varsa, öğe) değerini değiştirerek proje dosyanızı düzenleyin:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Ayrıca, .NET Standard kitaplıklarını aynı şekilde .NET Standard 2,0 olarak yeniden hedefleyebilirsiniz:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Projenizi .NET Core 2,0 ' e geçirme hakkında daha fazla bilgi için, bkz [. asp.NET Core 1. x ' den ASP.NET Core 2,0 ' ye](/aspnet/core/migration/1x-to-2x/index)geçme.

## <a name="language-support"></a>Dil desteği

Ve C# F#' nin desteklenmesinin yanı sıra, .net Core 2,0 de Visual Basic destekler.

### <a name="visual-basic"></a>Visual Basic

Sürüm 2,0 ile, .NET Core artık Visual Basic 2017 ' yi desteklemektedir. Visual Basic, aşağıdaki proje türlerini oluşturmak için kullanabilirsiniz:

- .NET Core konsol uygulamaları
- .NET Core sınıf kitaplıkları
- .NET Standard sınıf kitaplıkları
- .NET Core birim testi projeleri
- .NET Core xUnit test projeleri

Örneğin, bir Visual Basic "Merhaba Dünya" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:

1. Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizin yapın.

1. Komutunu `dotnet new console -lang vb`girin.

   Bu komut, *program. vb*adlı Visual Basic `.vbproj` kaynak kodu dosyası ile birlikte bir dosya uzantısına sahip bir proje dosyası oluşturur. Bu dosya, "Merhaba Dünya!" dizesinin yazılacağı kaynak kodunu içerir Konsol penceresine.

1. Komutunu `dotnet run`girin. [.NET Core CLI](../tools/index.md) , uygulamayı otomatik olarak derler ve yürütür ve "Merhaba Dünya!" iletisini görüntüler. Konsol penceresinde.

### <a name="support-for-c-71"></a>7,1 için C# destek

.NET Core 2,0, C# aşağıdakiler de dahil olmak üzere çeşitli yeni özellikler ekleyen 7,1 ' i destekler:

- Uygulama giriş noktası [](../../csharp/language-reference/keywords/async.md) yöntemi,asyncanahtarsözcüğüyle`Main` işaretlenebilir.
- Çıkarsanan demet adları.
- Varsayılan ifadeler.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Platform geliştirmeleri

.NET Core 2,0, .NET Core 'u yüklemeyi ve desteklenen işletim sistemlerinde kullanmayı kolaylaştıran birçok özellik içerir.

### <a name="net-core-for-linux-is-a-single-implementation"></a>Linux için .NET Core tek bir uygulama

.NET Core 2,0, birden çok Linux dağıtımı üzerinde çalışabilen tek bir Linux uygulamasını sunmaktadır. .NET Core 1. x, dağıtıma özgü bir Linux uygulamasını indirmeniz gerekir.

Ayrıca, Linux 'u tek bir işletim sistemi olarak hedefleyen uygulamalar da geliştirebilirsiniz. .NET Core 1. x, her bir Linux dağıtımını ayrı olarak hedeflediğiniz için gereklidir.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Apple şifreleme kitaplıkları için destek

MacOS üzerinde .NET Core 1. x, OpenSSL araç setinin şifreleme kitaplığını gerektirdi. .NET Core 2,0, Apple şifreleme kitaplıklarını kullanır ve OpenSSL gerektirmez, bu nedenle artık yüklemeniz gerekmez.

## <a name="api-changes-and-library-support"></a>API değişiklikleri ve kitaplık desteği

### <a name="support-for-net-standard-20"></a>.NET Standard 2,0 desteği

.NET Standard, Standard 'ın bu sürümüyle uyumlu .NET uygulamalarında kullanılabilmesi gereken sürümlenmiş bir API kümesini tanımlar. .NET Standard, kitaplık geliştiricileri 'ne yöneliktir. Her bir .NET uygulamasındaki .NET Standard bir sürümünü hedefleyen bir kitaplık için kullanılabilen işlevselliği garanti etmek için kullanılır. .NET Core 1. x .NET Standard sürüm 1,6 ' ü destekler; .NET Core 2,0, en son sürümü .NET Standard 2,0. Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md).

.NET Standard 2,0, .NET Standard 1,6 ' de kullanılabilir olandan daha fazla 20.000 API 'ye sahiptir. Bu genişletilmiş yüzey alanının büyük bölümü, .NET Framework ve Xamarin için ortak olan API 'Leri .NET Standard ' ye ekleme sonucu oluşur.

.NET Standard 2,0 sınıf kitaplıkları ayrıca .NET Standard 2,0 ' de bulunan API 'Leri çağırmak kaydıyla .NET Framework sınıf kitaplıklarına başvurabilir. .NET Framework kitaplıklarının yeniden derlenmesi gerekli değildir.

Son sürümü bu yana .NET Standard eklenen API 'lerin bir listesi için, .NET Standard 1,6, bkz [. .NET Standard 2,0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Genişletilmiş yüzey alanı

.NET Core 2,0 ' de mevcut olan API 'lerin toplam sayısı, .NET Core 1,1 ile karşılaştırıldığında iki katına çıkar.

[Windows Uyumluluk paketi](../porting/windows-compat-pack.md) .NET Framework 'den taşıma işlemi de çok daha kolay hale geldi.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için destek

.NET Core Code var olan NuGet paketleri de dahil olmak üzere mevcut .NET Framework kitaplıklarına başvurabilir. Kitaplıkların .NET Standard bulunan API 'Leri kullanması gerektiğini unutmayın.

## <a name="visual-studio-integration"></a>Visual Studio tümleştirmesi

Visual Studio 2017 sürüm 15,3 ve bazı durumlarda Mac için Visual Studio .NET Core geliştiricileri için çeşitli önemli geliştirmeler sunar.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>.NET Core uygulamalarını ve .NET Standard kitaplıklarını yeniden hedefleme

.NET Core 2,0 SDK 'Sı yüklüyse, .NET Core 1. x projelerini .NET Core 2,0 ve .NET Standard 1. x kitaplıklarını .NET Standard 2,0 olarak yeniden hedefleyebilirsiniz.

Projenizi Visual Studio 'da yeniden hedeflemek için projenin Özellikler iletişim kutusunun **uygulama** sekmesini açın ve **hedef Framework** değerini **.net Core 2,0** veya **2,0 .NET Standard**olarak değiştirirsiniz. Ayrıca, projeye sağ tıklayıp **. csproj dosyasını Düzenle \*** seçeneğini belirleyerek de değiştirebilirsiniz. Daha fazla bilgi için bu konunun önceki kısımlarında yer alan [Araçlar bölümüne bakın](#tooling) .

### <a name="live-unit-testing-support-for-net-core"></a>.NET Core için Live Unit Testing

Kodunuzu her değiştirdiğinizde Live Unit Testing otomatik olarak etkilenen birim testlerini arka planda çalıştırır ve Visual Studio ortamında sonuçları ve kod kapsamını canlı olarak görüntüler. .NET Core 2,0 artık Live Unit Testing desteklemektedir. Daha önce Live Unit Testing yalnızca .NET Framework uygulamalar için kullanılabilir.

Daha fazla bilgi için bkz. [Visual Studio 2017 ile Live Unit Testing](/visualstudio/test/live-unit-testing) ve [Live Unit Testing SSS](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Birden çok hedef çerçeve için daha iyi destek

Birden çok hedef çerçeve için bir proje oluşturuyorsanız, artık üst düzey menüden hedef platformu seçebilirsiniz. Aşağıdaki şekilde, SCD1 adlı bir proje 64-bit MacOS X 10,11 (`osx.10.11-x64`) ve 64-bit Windows 10/Windows Server 2016 (`win10-x64`) hedefliyor. Bu durumda bir hata ayıklama yapısı çalıştırmak için proje düğmesini seçmeden önce hedef Framework 'ü seçebilirsiniz.

![Proje oluşturulurken hedef çerçeve seçimini gösteren ekran görüntüsü.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>.NET Core SDK 'Ları için yan yana destek

Artık .NET Core SDK Visual Studio 'dan bağımsız olarak yükleyebilirsiniz. Bu, Visual Studio 'nun tek bir sürümünün .NET Core 'un farklı sürümlerini hedefleyen projeler oluşturmasına olanak tanır. Daha önce, Visual Studio ve .NET Core SDK sıkı bir şekilde bağlanmış. Visual Studio 'nun belirli bir sürümüne eşlik eden belirli bir SDK sürümü.

## <a name="documentation-improvements"></a>Belge geliştirmeleri

### <a name="net-application-architecture"></a>.NET uygulama mimarisi

[.NET uygulama mimarisi](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) , oluşturmak için .net kullanırken rehberlik, en iyi uygulamalar ve örnek uygulamalar sağlayan bir dizi e-kitap için erişmenizi sağlar:

- [Mikro hizmetler ve Docker Kapsayıcıları](../../architecture/microservices/index.md)
- [ASP.NET ile Web uygulamaları](../../architecture/modern-web-apps-azure/index.md)
- [Xamarin ile mobil uygulamalar](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Azure ile buluta dağıtılan uygulamalar](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core 2,0 ' deki yenilikler](/aspnet/core/aspnetcore-2.0)
