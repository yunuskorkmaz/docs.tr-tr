---
title: .NET Core 'un .NET 5 sürümüne evrimi
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 09/02/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: 9318b1afbe22c97f056bd38732306c6a6b60ad00
ms.sourcegitcommit: 43d5aca3fda42bad8843f6c4e72f6bd52daa55f1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2020
ms.locfileid: "89598120"
---
# <a name="the-evolution-of-net-core-to-net-5"></a>.NET Core 'un .NET 5 sürümüne evrimi

Bu makalede, .NET Core 'un sonraki sürümü olan 3,1 ' de bulunan .NET 5 ' te yer alan ayrıntılar ayrıntılı olarak verilmiştir. Sürüm numarası, .NET Framework 4. x ile karışıklık oluşmasını önlemek için 5,0. Ve "çekirdek", .NET ' in ana uygulama olduğu için adından bırakılır. ASP.NET Core, ASP.NET MVC 5 ile karıştırmamak için "Core" adını korur. Ayrıca, Entity Framework Core "çekirdek" adını Entity Framework 5 ve 6 ile karıştırmamak için korur. .NET 5, .NET Core veya .NET Framework daha fazla sayıda uygulamayı ve daha fazlasını destekler.

.NET Core 'un bir bütün olarak .NET ekosistemini etkileyici yollarla geliştirmiştir. GitHub 'da açık kaynaklı bir proje olarak, topluluk katkılarını kutluyor ve zaman içinde gelişerek daha fazla iyileştiriliyor.

.NET Core 'un birkaç birincil özelliği vardır:

> [!div class="checklist"]
>
> - Platformlar arası
> - Açık kaynak
> - Yan yana yükleme
> - Küçük proje dosyaları (SDK stili)
> - Esnek dağıtım

.NET 5 bu özellikleri genişleterek artımlı iyileştirmeler yapar:

- Tek dosya uygulamaları
- Windows ARM64 ve ARM64 iç bilgileri
- Performans iyileştirmeleri:
  - [Çöp toplama (GC)](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [Zaman uyumsuz ValueTask havuzu](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [Birçok daha fazla alan](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- Kapsayıcı boyutu iyileştirmeleri
- [Uygulama kırpması](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- [C# derleyici geliştirmeleri](https://devblogs.microsoft.com/dotnet/automatically-find-latent-bugs-in-your-code-with-net-5)
- Döküm hata ayıklaması için araç desteği
- Platform [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için %80 açıklanmalıdır

### <a name="what-net-5-is-not"></a>.NET 5 ne değildir?

.NET 5 .NET Framework için bir değiştirme değildir. Aşağıdaki teknolojilerin .NET Framework .NET 5 ' e bağlantı noktası yoktur, ancak .NET 5 ' te desteklenen alternatifler bulunmaktadır:

| Teknoloji                             | Öneri                                              |
|----------------------------------------|-------------------------------------------------------------|
| Web Forms                              | [ASP.NET Core Blazor](/aspnet/core/blazor)                  |
| Windows Communication Foundation (WCF) | [gRPC](/aspnet/core/grpc)                                   |
| Windows Workflow (WF)                  | [Açık kaynaklı CoreWF](https://github.com/UiPath-Open/corewf) |

## <a name="net-standard"></a>.NET Standard

Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir. .NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .

`net5.0`Tfd, ve adlarını birleştirir ve `netcoreapp` değiştirir `netstandard` . Bu TFM genellikle, .NET Standard gibi, platformlar arası çalışan teknolojileri dahil eder. Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz. Daha fazla bilgi için bkz. [hedef çerçeveleri belirtme](../standard/frameworks.md#how-to-specify-a-target-framework).

## <a name="language-updates"></a>Dil güncelleştirmeleri

.NET 5 ile .NET programlama dilleri iyileştirilmesine devam etmektedir.

### <a name="c-updates"></a>C# güncelleştirmeleri

.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur. .NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş. Aşağıda bazı önemli noktalar verilmiştir:

- Kayıtlar: değer türleri gibi davranan ve yeni anahtar sözcüğünü dile tanıtan değişmez başvuru türleri `with` .
- İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .
- En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:

   ```csharp
   System.Console.Write("Hello world!");
   ```

- İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .

Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.

#### <a name="source-generators"></a>Kaynak oluşturucuları

Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor. Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.

Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.

### <a name="f-updates"></a>F # güncelleştirme

F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır. F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:

#### <a name="interpolated-strings"></a>Ara değerli dizeler

C# ' de enterpolasyonlu dizeye benzer ve hatta JavaScript, F # temel dize ilişkilendirmeyi destekler.

```fsharp
let name = "David"
let age = 36
let message = $"{name} is {age} years old."
```

Temel dize ilişkilendirmesinin yanı sıra, yazılı ilişkilendirme de vardır. Yazılı ilişkilendirmeden, belirli bir tür biçim belirticisiyle eşleşmelidir.

```fsharp
let name = "David"
let age = 36
let message = $"%s{name} is %d{age} years old."
```

Bu, [`sprintf`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-printfmodule.html#sprintf) türü güvenli girişlere göre bir dizeyi biçimlendiren işleve benzerdir. <!-- For more information, see [What's new in F# 5](fsharp/whats-new/fsharp-50.md). -->

### <a name="visual-basic-updates"></a>Visual Basic güncelleştirmeleri

.NET 5 ' teki Visual Basic için yeni dil özellikleri yoktur. Bununla birlikte, .NET 5 ile Visual Basic desteği şu şekilde genişletilir:

| Açıklama                            | `dotnet new` parametresinin |
|----------------------------------------|------------------------|
| Konsol Uygulaması                    | `console`              |
| Sınıf kitaplığı                          | `classlib`             |
| WPF uygulaması                        | `wpf`                  |
| WPF sınıf kitaplığı                      | `wpflib`               |
| WPF Özel Denetim Kitaplığı             | `wpfcustomcontrollib`  |
| WPF Kullanıcı denetimi kitaplığı               | `wpfusercontrollib`    |
| Windows Forms (WinForms) uygulaması   | `winforms`             |
| Windows Forms (WinForms) sınıf kitaplığı | `winformslib`          |
| Birim testi projesi                      | `mstest`               |
| NUnit 3 test projesi                   | `nunit`                |
| NUnit 3 test öğesi                      | `nunit-test`           |
| xUnit test projesi                     | `xunit`                |

.NET CLı 'dan proje şablonları hakkında daha fazla bilgi için bkz [`dotnet new`](tools/dotnet-new.md) ..

## <a name="net-maui"></a>.NET MAUı

.NET MAUı, giderek daha popüler Xamarin. Forms araç seti 'nin bir evrimi ve [DotNet/MAUI](https://github.com/dotnet/maui)'de GitHub 'da açık kaynaktır. .Net MAUı sayesinde, .NET geliştiricileri için seçim, tüm modern iş yüklerini destekleyen tek bir yığın sağlayan basitleştirilmiştir: Android, iOS, macOS ve Windows. .NET MAUı ile birden çok platformu ve cihazı hedefleyen tek bir proje geliştirici deneyimi edinirsiniz.

> [!IMPORTANT]
> .NET MAUı erken önizlemededir. Örnek kaynak kodu, [Xamarin/NET6-Samples](https://github.com/xamarin/net6-samples)adresinde bulunabilir.

### <a name="model-view-update-pattern"></a>Model-Görünüm-güncelleştirme modeli

Geliştiriciler modern geliştirme düzenlerini sevdiğinde. UI geliştirmeye yönelik akıcı bir yaklaşım, "karaağaç mimarisi" tarafından ilham [Model-View-Update](https://elmprogramming.com/model-view-update-part-1.html) veya MVU deseninin bir sürümüdür. MVU veri ve durum yönetiminin tek yönlü bir akışını ve yalnızca gerekli değişiklikleri uygulayarak Kullanıcı arabirimini hızla güncelleştiren bir kod ilk geliştirme deneyimi yükseltir.

Örnek olarak, MVU modelini kullanarak .NET MAUı 'de yazılmış aşağıdaki sayacı göz önünde bulundurun:

```csharp
readonly State<int> _count = 0;

[Body]
View body() => new StackLayout
{
    new Label("Welcome to .NET MAUI!"),
    new Button(
        () => $"You clicked {_count} times.",
        () => ++ _count.Value)
    )
};
```

Daha fazla bilgi için bkz. [.net MAUI yol haritası](https://github.com/dotnet/maui/wiki/Roadmap)ve [.net MAUI makalesine giriş](https://devblogs.microsoft.com/dotnet/introducing-net-multi-platform-app-ui) .

## <a name="see-also"></a>Ayrıca bkz.

- [Bir .NET ile yolculuğa](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [.NET 5 ' teki performans iyileştirmeleri](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
