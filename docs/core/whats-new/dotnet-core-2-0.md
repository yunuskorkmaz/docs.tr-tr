---
title: ​.NET Core 2.0’deki yenilikler
description: .NET Core'da bulunan yeni özellikler hakkında bilgi edinin.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398834"
---
# <a name="whats-new-in-net-core-20"></a>​.NET Core 2.0’deki yenilikler

.NET Core 2.0 aşağıdaki alanlarda ki geliştirmeleri ve yeni özellikleri içerir:

- [Araçlar](#tooling)
- [Dil desteği](#language-support)
- [Platform geliştirmeleri](#platform-improvements)
- [API değişiklikleri](#api-changes-and-library-support)
- [Visual Studio ile tümleştirme](#visual-studio-integration)
- [Dokümantasyon geliştirmeleri](#documentation-improvements)

## <a name="tooling"></a>Araçlar

### <a name="dotnet-restore-runs-implicitly"></a>dotnet geri yükleme örtülü çalışır

.NET Core'un önceki sürümlerinde, [dotnet](../tools/dotnet-restore.md) yeni komutuyla yeni bir proje oluşturduktan hemen sonra ve projenize yeni bir bağımlılık eklediğinizde bağımlılıkları indirmek için [dotnet](../tools/dotnet-new.md) geri yükleme komutunu çalıştırmanız gerekiyordu.

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

`--no-restore` Ayrıca, `new`, , `run` `build` `publish` `pack`, , , ve `test` komutları anahtarı `dotnet restore` geçirerek otomatik çağırma devre dışı leyebilirsiniz.

### <a name="retargeting-to-net-core-20"></a>.NET Core 2.0'a yeniden hedefleme

.NET Core 2.0 SDK kuruluysa, .NET Core 1.x'i hedefleyen projeler .NET Core 2.0'a yeniden hedeflenebilir.

.NET Core 2.0'ı yeniden hedeflemek için, öğenin `<TargetFramework>` (veya proje `<TargetFrameworks>` dosyanızda birden fazla hedefiniz varsa öğeyi) 1,x'ten 2.0'a değiştirerek proje dosyanızı düzenleme:

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

.NET Standart kitaplıklarını aynı şekilde .NET Standart 2.0'a da yeniden hedefleyebilirsiniz:

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

Projenizi .NET Core 2.0'a geçirme hakkında daha fazla bilgi ASP.NET [ASP.NET](/aspnet/core/migration/1x-to-2x/index)için bkz.

## <a name="language-support"></a>Dil desteği

C# ve F#'ı desteklemenin yanı sıra .NET Core 2.0 Visual Basic'i de destekler.

### <a name="visual-basic"></a>Visual Basic

.NET Core, sürüm 2.0 ile Visual Basic 2017'yi destekliyor. Aşağıdaki proje türlerini oluşturmak için Visual Basic'i kullanabilirsiniz:

- .NET Core konsol uygulamaları
- .NET Çekirdek sınıf kitaplıkları
- .NET Standart sınıf kitaplıkları
- .NET Çekirdek ünite test projeleri
- .NET Core xUnit test projeleri

Örneğin, Visual Basic "Hello World" uygulaması oluşturmak için komut satırından aşağıdaki adımları yapın:

1. Konsol penceresi açın, projeniz için bir dizin oluşturun ve geçerli dizini yapın.

1. Komutu `dotnet new console -lang vb`girin.

   Komut, *Program.vb*adlı `.vbproj` Visual Basic kaynak kodu dosyasıyla birlikte dosya uzantısı olan bir proje dosyası oluşturur. Bu dosya "Merhaba Dünya!" dizesini yazmak için kaynak kodu içerir. konsol penceresine.

1. Komutu `dotnet run`girin. [.NET Core CLI,](../tools/index.md) "Hello World!" mesajını görüntüleyen uygulamayı otomatik olarak derler ve yürütür. konsol penceresinde.

### <a name="support-for-c-71"></a>C# 7.1 desteği

.NET Core 2.0, c# 7.1'i destekler ve bu özellikler şunlardır:

- Yöntem, `Main` uygulama giriş noktası, [async](../../csharp/language-reference/keywords/async.md) anahtar sözcüğü ile işaretlenebilir.
- Çıkarılan tuple adları.
- Varsayılan ifadeler.

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a>Platform geliştirmeleri

.NET Core 2.0, .NET Core'un yüklenmesini ve desteklenen işletim sistemlerinde kullanılmasını kolaylaştıran bir dizi özellik içerir.

### <a name="net-core-for-linux-is-a-single-implementation"></a>Linux için .NET Core tek bir uygulamadır

.NET Core 2.0, birden fazla Linux dağıtımı nda çalışan tek bir Linux uygulaması sunar. .NET Core 1.x, dağıtıma özel bir Linux uygulamasını indirmenizi zorunlu kattı.

Linux'u tek bir işletim sistemi olarak hedefleyen uygulamalar da geliştirebilirsiniz. .NET Core 1.x, her Linux dağıtımına ayrı ayrı hedeflemeniz gerekir.

### <a name="support-for-the-apple-cryptographic-libraries"></a>Apple şifreleme kitaplıkları için destek

MacOS'ta .NET Core 1.x, OpenSSL araç setinin şifreleme kitaplığını gerekli kattı. .NET Core 2.0, Apple şifreleme kitaplıklarını kullanır ve OpenSSL gerektirmez, bu nedenle artık yüklemeniz gerekmez.

## <a name="api-changes-and-library-support"></a>API değişiklikleri ve kitaplık desteği

### <a name="support-for-net-standard-20"></a>.NET Standard 2.0 desteği

.NET Standardı, standardın bu sürümüne uygun .NET uygulamalarında bulunması gereken sürümlenmiş bir API kümesi tanımlar. .NET Standardı kitaplık geliştiricileri hedeflenebilmektedir. Her .NET uygulamasında .NET Standardının bir sürümünü hedefleyen bir kitaplığın kullanabileceği işlevselliği garanti etmeyi amaçlar. .NET Core 1.x .NET Standart sürüm 1.6 destekler; .NET Core 2.0 en son sürümü destekler, .NET Standart 2.0. Daha fazla bilgi için [.NET Standard](../../standard/net-standard.md)' a bakın.

.NET Standart 2.0, .NET Standart 1.6'da bulunandan 20.000'den fazla API içerir. Bu genişletilmiş yüzey alanının çoğu,.NET Framework ve Xamarin'de ortak olan API'lerin .NET Standardına dahil edilmesinden kaynaklanır.

.NET Standart 2.0 sınıf kitaplıkları, .NET Standart 2.0'da bulunan API'leri aramaları koşuluyla .NET Framework sınıf kitaplıklarına da başvuruyapabilir. .NET Framework kitaplıklarının yeniden derlemesi gerekmez.

Son sürümünden bu yana .NET Standardına eklenen API'lerin listesi için .NET Standart 1.6'ya [bakın.NET Standart 2.0 vs. 1.6.](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)

### <a name="expanded-surface-area"></a>Genişletilmiş yüzey alanı

.NET Core 2.0'da bulunan toplam API sayısı .NET Core 1.1 ile karşılaştırıldığında iki kattan fazla artmıştır.

Ve [.NET](../porting/windows-compat-pack.md) Framework'den windows uyumluluk paketi taşıma ile de çok daha basit hale gelmiştir.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için destek

.NET Core kodu, mevcut NuGet paketleri de dahil olmak üzere varolan .NET Framework kitaplıkları referans olabilir. Kitaplıkların .NET Standardı'nda bulunan API'leri kullanması gerektiğini unutmayın.

## <a name="visual-studio-integration"></a>Visual Studio ile tümleştirme

Visual Studio 2017 sürüm 15.3 ve bazı durumlarda Mac için Visual Studio .NET Core geliştiricileri için önemli geliştirmeler sunar.

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a>.NET Core uygulamalarını ve .NET Standart kitaplıklarını yeniden hedefleme

.NET Core 2.0 SDK yüklüyse, .NET Core 1.x projelerini .NET Core 2.0 ve .NET Standard 1.x kitaplıklarını .NET Standard 2.0'a yeniden hedefleyebilirsiniz.

Visual Studio'da projenizi yeniden hedeflemek için, projenin özellikleri iletişim kutusunun **Uygulama** sekmesini açar ve **Hedef çerçeve** değerini **.NET Core 2.0** veya **.NET Standard 2.0**olarak değiştirirsiniz. Ayrıca, projeye sağ tıklayarak ve **Düzenleme \*.csproj dosya** seçeneğini seçerek değiştirebilirsiniz. Daha fazla bilgi için, bu konunun daha önceki [Araçlama](#tooling) bölümüne bakın.

### <a name="live-unit-testing-support-for-net-core"></a>.NET Core için Live Unit Testing

Kodunuzu her değiştirdiğinizde, Canlı Birim Testi etkilenen birim testlerini arka planda otomatik olarak çalıştırArak sonuçları ve kod kapsamını Visual Studio ortamında canlı olarak görüntüler. .NET Core 2.0 artık Canlı Birim Testini destekliyor. Daha önce, Canlı Birim Testi yalnızca .NET Framework uygulamaları için mevcuttu.

Daha fazla bilgi için [Visual Studio ile Canlı Birim Testi](/visualstudio/test/live-unit-testing) ve Canlı Birim Test [SSS'ye](/visualstudio/test/live-unit-testing-faq)bakın.

### <a name="better-support-for-multiple-target-frameworks"></a>Birden çok hedef çerçeve için daha iyi destek

Birden çok hedef çerçevesi için bir proje oluşturuyorsanız, artık üst düzey menüden hedef platformu seçebilirsiniz. Aşağıdaki şekilde, SCD1 adlı bir proje 64-bit macOS X`osx.10.11-x64`10.11 ( ) ve 64-bit`win10-x64`Windows 10/Windows Server 2016 ( hedefliyor. Bu durumda hata ayıklama oluşturma yı çalıştırmak için proje düğmesini seçmeden önce hedef çerçeveyi seçebilirsiniz.

![Proje inşa ederken hedef çerçeve seçimini gösteren ekran görüntüsü.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a>.NET Core SDK'lar için yan yana destek

Artık .NET Core SDK'yı Visual Studio'dan bağımsız olarak yükleyebilirsiniz. Bu, Visual Studio'nun tek bir sürümünün .NET Core'un farklı sürümlerini hedefleyen projeler oluşturmasını mümkün kılar. Daha önce, Visual Studio ve .NET Core SDK sıkıca birleştirilmiş; SDK'nın belirli bir versiyonu Visual Studio'nun belirli bir sürümüne eşlik etti.

## <a name="documentation-improvements"></a>Dokümantasyon geliştirmeleri

### <a name="net-application-architecture"></a>.NET Uygulama Mimarisi

[.NET Application Architecture,](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) oluşturmak için .NET'i kullanırken rehberlik, en iyi uygulamalar ve örnek uygulamalar sağlayan bir dizi e-kitap'a erişmenizi sağlar:

- [Mikrohizmetler ve Docker konteynerleri](../../architecture/microservices/index.md)
- [ASP.NET ile Web uygulamaları](../../architecture/modern-web-apps-azure/index.md)
- [Xamarin ile mobil uygulamalar](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [Azure ile Bulut'a dağıtılan uygulamalar](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a>Ayrıca bkz.

- [ASP.NET Core 2.0'daki yenilikler](/aspnet/core/aspnetcore-2.0)
