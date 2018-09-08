---
title: .NET Core 2.0 yenilikleri
description: "' De .NET Core bulunan yeni özellikler hakkında bilgi edinin."
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 02aac2dab2b892927c0c98fae30bb287a6e24ad6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44191059"
---
# <a name="whats-new-in-net-core-20"></a>.NET Core 2.0 yenilikleri

.NET core 2.0, aşağıdaki alanlarda geliştirmeler ve yeni özellikler içerir:

- [Araç kullanımı](#tooling)
- [Dil desteği](#language-support)
- [Platform geliştirmeleri](#platform-improvements)
- [API değişiklikleri](#api-changes-and-library-support)
- [Visual Studio tümleştirmesi](#visual-studio-integration)
- [Belgeleri geliştirmeleri](#documentation-improvements)

## <a name="tooling"></a>Araç kullanımı

### <a name="dotnet-restore-runs-implicitly"></a>DotNet restore örtük olarak çalışır

Çalıştırılacak olan .NET Core önceki sürümlerinde, [dotnet restore](../tools/dotnet-restore.md) bağımlılıkları ile yeni bir proje oluşturduğunuz hemen sonra yüklemek için komut [yeni dotnet](../tools/dotnet-new.md) yanı sıra her komut, Yeni bir bağımlılık projenize eklenir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Ayrıca otomatik çağrılmasını devre dışı bırakabilirsiniz `dotnet restore` geçirerek `--no-restore` geçin `new`, `run`, `build`, `publish`, `pack`, ve `test` komutları.

### <a name="retargeting-to-net-core-20"></a>.NET Core 2.0 yeniden hedefleme

.NET Core 2.0 SDK'sı yüklü değilse, projeler, .NET Core, .NET Core 2.0 için hedeflenmesi 1.x hedefleyin.

.NET Core 2.0 için yeniden hedeflemek için değerini değiştirerek proje dosyanızı düzenlemeniz `<TargetFramework>` öğesi (veya `<TargetFrameworks>` proje dosyanızda birden fazla hedef varsa öğe) 1.x sürümünden 2.0 sürümüne'nden:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Ayrıca, .NET Standard 2.0 .NET standart kitaplıklarına aynı şekilde hedefleyebilirsiniz:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Projeniz .NET Core 2.0 için geçirme hakkında daha fazla bilgi için bkz. [ASP.NET Core geçiş ASP.NET Core 2.0 için 1.x](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Dil desteği

.NET Core 2.0 C# ve F # hizmetinin yanı sıra, Visual Basic de destekler.

### <a name="visual-basic"></a>Visual Basic

Sürüm 2.0 ile .NET Core, Visual Basic 2017 artık desteklemektedir. Visual Basic, aşağıdaki proje türlerini oluşturmak için kullanabilirsiniz:

- .NET core konsol uygulamaları
- .NET core sınıf kitaplıkları
- .NET standart sınıf kitaplıkları
- .NET core birim testi projeleri
- .NET core xUnit test projesi

Örneğin, bir Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:

1. Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve bunu geçerli dizine yapın.

1. Komutu girdikten `dotnet new console -lang vb`.

   Komutu ile bir proje dosyası oluşturur bir `.vbproj` dosya uzantısı, adlı bir Visual Basic kaynak kod dosyası ile birlikte *Program.vb*. Bu dosya "Hello World!" dize yazmak için kaynak kodunu içerir. Konsol penceresinde.

1. Komutu girdikten `dotnet run`. [.NET Core CLI](../tools/index.md) otomatik olarak derler ve "Hello World!" iletisini görüntüler uygulama yürütür Konsol penceresinde.

### <a name="support-for-c-71"></a>C# 7.1 desteği

.NET core 2.0 C# bir dizi gibi yeni özellikler ekleyen 7.1, destekler:

- `Main` Yöntemi, uygulama giriş noktası ile işaretlenebilir [zaman uyumsuz](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü.
- Çıkarsanan demet adları.
- Varsayılan ifade.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Platform geliştirmeleri

.NET core 2.0, .NET Core yükleyin daha kolay hale getirmek özellikleri içerir ve desteklenen işletim sistemleri üzerinde kullanın.

### <a name="net-core-for-linux-is-a-single-implementation"></a>Linux için .NET core tek bir uygulamasıdır

.NET core 2.0 birden çok Linux dağıtımlarında çalışır tek bir Linux uygulaması sunar. .NET core 1.x gerekli dağıtım özel Linux uygulamasını indirin.

Tek bir işletim sistemi olarak Linux'ı hedefleyen uygulamaları da geliştirebilirsiniz. .NET core 1.x gerekli ayrı ayrı her bir Linux dağıtımı hedefleyin.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Apple şifreleme kitaplıkları için desteği

.NET core 1.x macos'ta OpenSSL Toolkit'in şifreleme kitaplığı gerekli. .NET core 2.0 Apple şifreleme kitaplıklarını kullanır ve artık yüklemeniz gerekmez, OpenSSL gerektirmez.

## <a name="api-changes-and-library-support"></a>API değişiklikleri ve kitaplık desteği

### <a name="support-for-net-standard-20"></a>.NET Standard 2.0 desteği

.NET Standard tutulan bir standart'ın bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir API kümesi tanımlar. .NET Standard kitaplığı geliştiricilere yöneliktir. .NET Standard'ı her .NET uygulama sürümünü hedefleyen bir kitaplık için kullanılabilir olan işlevsellik garantisi için amaçlar. .NET core 1.x .NET Standard sürüm 1.6 destekler; .NET Core 2.0, .NET Standard 2.0 en son sürümünü destekler. Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md).

.NET standard 2.0, .NET standart 1.6 içinde kullanılabilir olan çok 20. 000'den daha fazla APIleri içerir. Bu çok ortak Xamarin uygulamasına .NET Standard ve .NET Framework API'ları ekleme yüzey alanını sonuçları genişletildi.

Bunlar, .NET Standard 2.0 sürümünde mevcut olan API'lerini çağırma koşuluyla .NET standard 2.0 sınıf kitaplıkları da .NET Framework sınıf kitaplıkları, başvurabilirsiniz. .NET Framework kitaplıkları, herhangi bir yeniden derleme gereklidir.

Son sürümünden bu yana .NET standart 1.6 için .NET Standard eklenmiş API'lerin bir listesi için bkz: [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Genişletilmiş yüzey alanı

API'ler .NET Core 2.0 kullanılabilir toplam sayısı, birden fazla .NET Core 1.1 karşılaştırıldığında katladı.

İle [Windows Uyumluluk Paketi](../porting/windows-compat-pack.md) .NET Framework'ten taşıma ayrıca haline gelmiştir çok daha kolaydır.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için desteği

.NET core kodu mevcut NuGet paketlerini de dahil olmak üzere var olan .NET Framework kitaplıkları başvurabilirsiniz. .NET Standard sürümünde bulunan API kitaplıklarını kullanması gerektiğini unutmayın.

## <a name="visual-studio-integration"></a>Visual Studio tümleştirmesi

Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio, .NET Core geliştiricileri için önemli geliştirmeleri sunar.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>.NET Core uygulamaları ve .NET standart kitaplıkları yeniden hedefleme

.NET Core 2.0 SDK'sı yüklü değilse, .NET Core 1.x projelerini .NET Standard 2.0 için .NET Core 2.0 ve .NET Standard 1.x kitaplıklara hedefleyebilirsiniz.

Visual Studio projeleri yeniden hedeflemek için açtığınız **uygulama** sekmesi Proje Özellikleri iletişim kutusu ile değiştirin **hedef Framework'ü** değerini **.NET Core 2.0** veya **.NET standard 2.0**. Ayrıca, proje üzerinde sağ tıklatıp seçerek değiştirebilirsiniz **Düzenle \*.csproj dosyasını** seçeneği. Daha fazla bilgi için [Tooling](#tooling) bölümü bu konuda.

### <a name="live-unit-testing-support-for-net-core"></a>.NET Core için Live Unit Testing

Kodunuzu değiştirmeniz her Live Unit Testing otomatik olarak tüm etkilenen birim testlerini arka planda çalıştırır ve sonuçları ve kod kapsamını Canlı Visual Studio ortamında görüntüler. .NET core 2.0, Live Unit Testing artık desteklemektedir. Daha önce Live Unit Testing yalnızca .NET Framework uygulamaları için kullanılabilir.

Daha fazla bilgi için [Visual Studio 2017 ile Live Unit Testing](/visualstudio/test/live-unit-testing) ve [Live Unit Testing SSS](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Birden çok hedef çerçeve için daha iyi destek

Birden çok hedef çerçeve için bir proje oluşturuyorsanız, hedef platformu artık üst düzey menüsünden seçebilirsiniz. Aşağıdaki resimde, bir proje adlı SCD1 hedefleri 64-bit macOS X 10.11 (`osx.10.11-x64`) ve 64-bit Windows 10/Windows Server 2016 (`win10-x64`). Hedef Çerçeve proje düğmesi, bu durumda hata ayıklama derlemesi çalıştırılacak seçmeden önce seçebilirsiniz.

![Hedef Framework'ü bir proje derlenirken seçme](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>.NET Core SDK'ları için yan yana desteği

Artık Visual Studio bağımsız olarak .NET Core SDK'sını yükleyebilirsiniz. Bu, tek bir sürüm farklı sürümlerini hedefleyen .NET Core projeleri derlemek için Visual Studio'nun mümkün kılar. Daha önce Visual Studio ve .NET Core SDK'sını sıkı şekilde bağlı; belirli bir SDK sürümü Visual Studio'nun belirli bir sürümü eşlik.

## <a name="documentation-improvements"></a>Belgeleri geliştirmeleri

### <a name="net-application-architecture"></a>.NET uygulama mimarisi

[.NET uygulama mimarisi](https://www.microsoft.com/net/learn/architecture) rehberlik, e-Kitapları kümesine erişim sağlar, en iyi uygulamalar ve örnek uygulamalar oluşturmak için .NET kullanırken:

- [Mikro hizmetler ve Docker kapsayıcıları](../../standard/microservices-architecture/index.md)
- [ASP.NET ile Web uygulamaları](../../standard/modern-web-apps-azure-architecture/index.md)
- [Xamarin ile mobil uygulamalar](/xamarin/xamarin-forms/enterprise-application-patterns/index.md)
- [Azure ile buluta dağıtılan uygulamalar](/azure/architecture/reference-architectures/index.md)

## <a name="see-also"></a>Ayrıca bkz.

* [ASP.NET Core 2.0 yenilikleri](/aspnet/core/aspnetcore-2.0)
