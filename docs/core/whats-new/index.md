---
title: .NET Core 2. 0 ' yenilikler nelerdir?
description: ".NET Core bulunan yeni özellikler hakkında bilgi edinin."
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: e54cabe67558300b5c5fb9552d78397850d4c782
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="whats-new-in-net-core"></a>.NET Core yenilikler nelerdir?

.NET core 2.0 aşağıdaki alanlarda geliştirmeler ve yeni özellikleri içerir:

- [Araçları](#tooling)
- [Dil desteği](#language-support)
- [Platform geliştirmeleri](#platform-improvements)
- [API değişiklikleri](#api-changes-and-library-support)
- [Visual Studio tümleştirmesi](#visual-studio-integration)
- [Belge geliştirmeleri](#documentation-improvements)

## <a name="tooling"></a>Araçları

### <a name="dotnet-restore-runs-implicitly"></a>DotNet geri yükleme örtük olarak çalışır

.NET Core önceki sürümlerini çalıştıran gerekiyordu [dotnet geri yükleme](../tools/dotnet-restore.md) yeni bir proje ile oluşturulan hemen sonra bağımlılıklarını karşıdan yüklemek için komut [dotnet yeni](../tools/dotnet-new.md) yanı sıra her komut, Yeni bir bağımlılık projenize eklenir.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

Ayrıca otomatik çağrılmasını devre dışı bırakabilirsiniz `dotnet restore` geçirerek `--no-restore` geçiş `new`, `run`, `build`, `publish`, `pack`, ve `test` komutları. 

### <a name="retargeting-to-net-core-20"></a>.NET Core 2.0 yeniden hedefleme

.NET Core 2.0 SDK'sı yüklü ise, projeler, .NET Core 1.x .NET Core 2.0 yönlendirilebilir hedefleyin.

.NET Core 2.0 yeniden hedefleyin için değerini değiştirerek proje dosyanızı düzenleyin `<TargetFramework>` öğesi (veya `<TargetFrameworks>` proje dosyanızda birden fazla hedef varsa öğe) 2.0 1.x gelen:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

Ayrıca aynı şekilde .NET standart 2.0 için .NET standart kitaplıkları yeniden hedefleyin da:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Projeniz .NET Core 2.0 geçirme hakkında daha fazla bilgi için bkz: [ASP.NET çekirdek geçirme 1.x ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).

## <a name="language-support"></a>Dil desteği

C# ve F # destekleyen ek olarak, .NET Core 2.0 Visual Basic de destekler.

### <a name="visual-basic"></a>Visual Basic

Sürüm 2.0 .NET Core artık Visual Basic 2017 destekler. Visual Basic aşağıdaki proje türleri oluşturmak için kullanabilirsiniz:

- .NET core konsol uygulamaları
- .NET core sınıf kitaplıkları
- Standart .NET sınıf kitaplıkları
- .NET core birim testi projelerini
- .NET core xUnit test projeleri

Örneğin, bir Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları uygulayın:

1. Bir konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizin yapın.

1. Aşağıdaki komutu girin `dotnet new console -lang vb`.

   Komut bir proje dosyası ile oluşturur bir `.vbproj` adlı bir Visual Basic kaynak kodu dosyasının yanı sıra dosya uzantısı, *Program.vb*. Bu dosyayı "Hello World!" dizesini yazmak için kaynak kodunu içerir Konsol penceresine.

1.  Aşağıdaki komutu girin `dotnet run`. [.NET Core CLI araçlarını](../tools/index.md) otomatik olarak derleyin ve "Hello World!" iletisi görüntüler ve uygulamanın yürütme Konsol penceresinde.

### <a name="support-for-c-71"></a>C# 7.1 desteği

.NET core 2.0 C# gibi yeni özellikler sayısı ekleyen 7.1, destekler:

- `Main` Yöntemi, uygulama giriş noktası işaretlenir ile [zaman uyumsuz](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü.
- Tanımlama grubu adları sonuçlandı.
- Varsayılan ifadeler.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Platform geliştirmeleri

.NET core 2.0, .NET Core yüklemek kolaylaştıran özellikler içerir ve desteklenen işletim sistemleri üzerinde kullanmak için.

### <a name="net-core-for-linux-is-a-single-implementation"></a>.NET core Linux için tek bir uygulamasıdır

.NET core 2.0 birden çok Linux dağıtımları üzerinde çalışan tek bir Linux uygulama sunar. .NET core 1.x gereken bir dağıtım özgü Linux uygulamasını indirin.

Ayrıca, tek bir işletim sistemi olarak Linux hedef uygulamaları geliştirebilirsiniz. .NET core 1.x gerekli her Linux dağıtım ayrı olarak hedefleyin.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Apple şifreleme kitaplıkları için desteği

.NET core üzerinde macOS 1.x OpenSSL Toolkit'in şifreleme kitaplığı gerekli. .NET core 2.0 Apple şifreleme kitaplıklarını kullanır ve böylece yüklemek gerek OpenSSL, gerektirmez.

## <a name="api-changes-and-library-support"></a>API değişiklikleri ve kitaplık desteği

### <a name="support-for-net-standard-20"></a>.NET standart 2.0 desteği

.NET standart bu standart sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir olması gereken API sürümü tutulan kümesini tanımlar. .NET standart kitaplığı geliştiricileri yöneliktir. Her .NET uygulaması .NET standart sürümü hedefleyen bir kitaplık için kullanılabilir olan işlevselliği garanti amaçlar. .NET core 1.x .NET Standard sürüm 1.6 destekler; .NET Core 2.0 .NET standart 2.0 en son sürümünü destekler. Daha fazla bilgi için bkz: [.NET standart](../../standard/net-standard.md).

.NET standart 2.0, .NET standart 1.6 içinde bulunmamaktaydı daha üzerinde 20.000 daha fazla API'leri içerir. Bu çoğunu .NET standart içine Xamarin ve .NET Framework için ortak API'ler ekleme yüzey alanını sonuçları genişletilmiştir.

.NET standart 2.0 mevcut API çağrısı koşuluyla standart 2.0 .NET sınıf kitaplıkları da .NET Framework sınıf kitaplıkları başvuruda bulunabilir. .NET Framework kitaplıkların hiçbir yeniden derlenmek gereklidir.

Son sürümünden bu yana .NET standart 1.6 için .NET standart eklenmiş API'ları listesi için bkz: [.NET standart 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

### <a name="expanded-surface-area"></a>Yüzey alanını genişletilmiş

.NET Core 2.0 kullanılabilen API'lerin toplam sayısı birden fazla .NET Core 1.1 karşılaştırıldığında iki katına.

İle [Windows Uyumluluk Paketi](../porting/windows-compat-pack.md) .NET Framework'bağlantı noktası oluşturma da duruma çok daha kolaydır.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için desteği

.NET core kodu mevcut NuGet paketleri de dahil olmak üzere var olan .NET Framework kitaplıkları başvuruda bulunabilir. Kitaplıkları .NET Standard sürümünde bulunan API'lerini kullanmanız gerektiğini unutmayın.

## <a name="visual-studio-integration"></a>Visual Studio tümleştirmesi

Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio birkaç .NET Core geliştiricilere yönelik önemli geliştirmeler sunar.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>Yeniden hedefleme .NET Core uygulamaları ve .NET standart kitaplıkları

.NET Core 2.0 SDK'yı yüklediyseniz, .NET Core 1.x projeleri .NET standart 2.0 için .NET Core 2.0 ve .NET standart 1.x kitaplıklara yeniden hedefleyin.

Visual Studio, projenizin hedefini için açmanız **uygulama** projenin özellikleri iletişim kutusu ve değişiklik sekmesinde **hedef framework** değeri **.NET Core 2.0** veya **.NET standart 2.0**. Ayrıca, projeye sağ tıklayıp seçerek değiştirebilirsiniz **Düzenle \*.csproj dosya** seçeneği. Daha fazla bilgi için bkz: [Tooling](#tooling) bu konunun önceki kısımlarında.

### <a name="live-unit-testing-support-for-net-core"></a>.NET Core için Live Unit Testing

Kodunuzu değiştirmek her birim testi Canlı otomatik olarak arka planda tüm etkilenen ünite testleri çalıştırır ve sonuçları ve kod kapsamı Visual Studio ortamında canlı görüntüler. .NET core 2.0 artık canlı birim testi destekler. Daha önce Canlı birim testi yalnızca .NET Framework uygulamaları için kullanılabilir.

Daha fazla bilgi için bkz: [Canlı birim testi Visual Studio 2017](/visualstudio/test/live-unit-testing) ve [Canlı birim testi SSS](/visualstudio/test/live-unit-testing-faq).

### <a name="better-support-for-multiple-target-frameworks"></a>Birden çok hedef çerçeve için daha iyi destek

Birden çok hedef çerçeve için bir proje oluşturuyorsanız, üst düzey menüsünden artık hedef platformu seçebilirsiniz. Aşağıdaki şekilde, 64-bit Mac OS X 10.11 sürümünü SCD1 adlı projesi hedefler (`osx.10.11-x64`) ve 64 bit Windows 10/Windows Server 2016 (`win10-x64`). Proje düğmesi, bu durumda bir hata ayıklama derlemesini çalışmasına seçmeden önce hedef Framework'ü seçebilirsiniz.

![Proje derleme hedef Framework'ü seçme](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>.NET Core SDK'ları için yan yana desteği

Visual Studio bağımsız olarak .NET Core SDK şimdi yükleyebilirsiniz. Bu, tek bir .NET Core bu hedef farklı sürümlerini projeler derlemek için Visual Studio sürümü için mümkün kılar. Daha önce Visual Studio ve .NET Core SDK sıkı şekilde bağlı; belirli bir SDK sürümü Visual Studio belirli bir sürümü eşlik.

## <a name="documentation-improvements"></a>Belge geliştirmeleri

### <a name="net-application-architecture"></a>.NET uygulama mimarisi

[.NET uygulama mimarisi](https://www.microsoft.com/net/learn/architecture) en iyi yöntemler ve .NET derleme için kullanırken uygulamaları örnek kılavuzluk, e-kitap kümesine erişim sağlar:

- Mikro ve Docker kapsayıcıları.
- ASP.NET ile Web uygulamaları.
- Xamarin ile mobil uygulamaları.
- Azure ile bulutta dağıtılan uygulamalar.

## <a name="see-also"></a>Ayrıca bkz.
 [ASP.NET Core 2. 0 ' yenilikler nelerdir?](/aspnet/core/aspnetcore-2.0)
