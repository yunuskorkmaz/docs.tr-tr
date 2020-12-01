---
title: .NET 5’teki yenilikler
description: .NET Core 'un bir sonraki gelişiminde bir çoklu platform ve açık kaynaklı bir geliştirme platformu olan .NET 5 hakkında bilgi edinin.
ms.date: 11/30/2020
ms.topic: overview
ms.author: dapine
author: IEvangelist
ms.openlocfilehash: d0b8533dd63dd7d24f49e11093770b52d7daea89
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437868"
---
# <a name="whats-new-in-net-5"></a>.NET 5’teki yenilikler

.NET 5,0, .NET Core 'un sonraki önemli sürümüdür 3,1. Aşağıdaki iki nedenden dolayı .NET Core 4,0 yerine bu yeni sürüm .NET 5,0 ' i adlandırdık:

- .NET Framework 4. x ile karışıklık oluşmasını önlemek için 4. x sürüm numaralarını atladık.
- Bu, .NET 'in ana uygulamasının ileriye dönük olarak olduğunu vurgulamak için adından "Core" olarak bırakıyoruz. .NET 5,0, .NET Core veya .NET Framework 'dan daha fazla sayıda uygulamayı ve daha fazla platformu destekler.

ASP.NET Core 5,0, .NET 5,0 tabanlıdır ancak "Core" adını ASP.NET MVC 5 ile karıştırmamak için korur. Benzer şekilde, Entity Framework Core 5,0 Entity Framework 5 ve 6 ' a karışmasını önlemek için "Core" adını korur.

.NET 5,0, .NET Core 3,1 ile karşılaştırıldığında aşağıdaki geliştirmeleri ve yeni özellikleri içerir:

- [C# güncelleştirmeleri](#c-updates)
- [F # güncelleştirme](#f-updates)
- [Visual Basic güncelleştirmeleri](#visual-basic-updates)
- [ Yeni özelliklerdeSystem.Text.Js](#systemtextjson-new-features)
- [Tek dosya uygulamaları](deploying/single-file.md)
- [Uygulama kırpması](https://devblogs.microsoft.com/dotnet/app-trimming-in-net-5)
- Windows ARM64 ve ARM64 iç bilgileri
- Döküm hata ayıklaması için araç desteği
- Çalışma zamanı kitaplıkları %80, [null yapılabilir başvuru türleri](../csharp/nullable-references.md) için açıklama eklenmiş
- Performans iyileştirmeleri:
  - [Çöp toplama (GC)](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#gc)
  - [System.Text.Json](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5/#json)
  - [System.Text.RegularExpressions](https://devblogs.microsoft.com/dotnet/regex-performance-improvements-in-net-5)
  - [Zaman uyumsuz ValueTask havuzu](https://devblogs.microsoft.com/dotnet/async-valuetask-pooling-in-net-5)
  - [Kapsayıcı boyutu iyileştirmeleri](https://github.com/dotnet/dotnet-docker/issues/1814#issuecomment-625294750)
  - [Birçok daha fazla alan](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)

## <a name="net-50-doesnt-replace-net-framework"></a>.NET 5,0 .NET Framework değiştirmez

.NET 5,0, .NET ' ün ve .NET Framework 4. x ' in ana uygulamasının hala desteklenmesidir.

Aşağıdaki teknolojilerin .NET Framework .NET 5,0 ' e bağlantı noktası yoktur, ancak .NET 5,0 ' de alternatifler vardır:

| Teknoloji            | Önerilen alternatif                                                                         |
|-----------------------|-------------------------------------------------------------------------------------------------|
| Web Forms             | ASP.NET Core [Blazor](/aspnet/core/blazor) veya [Razor Pages](/aspnet/core/tutorials/razor-pages) |
| Windows Workflow (WF) | [Açık kaynaklı CoreWF](https://github.com/UiPath-Open/corewf)                                     |

### <a name="windows-communication-foundation"></a>Windows Communication Foundation

[Windows Communication Foundation (WCF)](../framework/wcf/index.md) özgün uygulanması yalnızca Windows 'da desteklenmektedir. Ancak, .NET Foundation 'da kullanılabilir bir istemci bağlantı noktası vardır. Bu, tamamen [açık kaynak](https://github.com/dotnet/wcf), platformlar arası ve Microsoft tarafından desteklenmektedir. Temel NuGet paketleri aşağıda listelenmiştir:

- [System. ServiceModel. dupleks](https://www.nuget.org/packages/System.ServiceModel.Duplex)
- [System. ServiceModel. FEDERATION](https://www.nuget.org/packages/System.ServiceModel.Federation)
- [System. ServiceModel. http](https://www.nuget.org/packages/System.ServiceModel.Http)
- [System. ServiceModel. NetTcp](https://www.nuget.org/packages/System.ServiceModel.NetTcp)
- [System. ServiceModel. Ilkel öğeler](https://www.nuget.org/packages/System.ServiceModel.Primitives)
- [System. ServiceModel. Security](https://www.nuget.org/packages/System.ServiceModel.Security)

Topluluk, belirtilen istemci kitaplıklarını tamamlayan sunucu bileşenlerini korur. GitHub deposu [Corewcf](https://github.com/CoreWCF/CoreWCF)'de bulunabilir. Sunucu bileşenleri Microsoft tarafından _resmi olarak desteklenmez._ WCF 'ye alternatif olarak, [GRPC](/aspnet/core/grpc)'yi düşünün.

## <a name="net-50-doesnt-replace-net-standard"></a>.NET 5,0 .NET Standard değiştirmez

Yeni uygulama geliştirme, `net5.0` sınıf kitaplıkları da dahil olmak üzere tüm proje türleri için hedef çerçeve bilinen adını (tfd) belirtebilir. .NET 5 iş yükleri arasında kod paylaşımı, tüm ihtiyacınız olan tfd ' de basitleştirilmiştir `net5.0` .

.NET 5,0 uygulamaları ve kitaplıkları için, `net5.0` hedef Framework bilinen adı (TFM), `netcoreapp` ve tfms 'yi birleştirir ve değiştirir `netstandard` . Ancak, .NET Framework, .NET Core ve .NET 5 iş yükleri arasında kod paylaşmayı planlıyorsanız, `netstandard2.0` TFI olarak belirterek bunu yapabilirsiniz. Daha fazla bilgi için bkz. [.NET Standard](../standard/net-standard.md).

## <a name="c-updates"></a>C# güncelleştirmeleri

.NET 5 uygulamaları yazan geliştiricilerin en son C# sürümüne ve özelliklerine erişimi olur. .NET 5, dile birçok yeni özellik getiren C# 9 ile eşleştirilmiş. Aşağıda bazı önemli noktalar verilmiştir:

- Kayıtlar: değer tabanlı eşitlik semantiklerine sahip başvuru türleri ve yeni bir ifade tarafından desteklenen yıkıcı olmayan mutasyon `with` .
- İlişkisel desen eşleştirme: desen eşleştirme yeteneklerini, karşılaştırma değerlendirmeleri ve ifadeleri için, mantıksal desenler ve yeni anahtar sözcükler `and` ,, ve dahil olmak üzere ilişkisel Işleçlere genişletir `or` `not` .
- En üst düzey deyimler: C# ' ın benimseme ve öğrenmesinin bir yolu olarak, `Main` aşağıdaki geçerli olduğu sürece yöntem atlanabilir ve uygulama basit olur:

   ```csharp
   System.Console.Write("Hello world!");
   ```

- İşlev işaretçileri: aşağıdaki ara dil (IL) OpCodes 'ı kullanıma sunan dil yapıları: `ldftn` ve `calli` .

Kullanılabilir C# 9 özellikleri hakkında daha fazla bilgi için bkz. [C# 9 ' daki](../csharp/whats-new/csharp-9.md)yenilikler.

### <a name="source-generators"></a>Kaynak oluşturucuları

Kaynak oluşturucuları, vurgulanan yeni C# özelliklerinin yanı sıra geliştirici projelerine kendi şeklini yapıyor. Kaynak oluşturucuları, derleme sırasında çalışan kodun, programınızı İnceleme ve kodunuzun geri kalanı ile birlikte derlenen ek dosyalar üretmesine olanak tanır.

Kaynak oluşturucuları hakkında daha fazla bilgi için bkz. [C# kaynak](https://devblogs.microsoft.com/dotnet/introducing-c-source-generators) oluşturucuları ve [c# kaynak Oluşturucu örnekleri](https://devblogs.microsoft.com/dotnet/new-c-source-generator-samples)tanıtımı.

## <a name="f-updates"></a>F # güncelleştirme

F # .NET fonksiyonel programlama dilidir ve .NET 5 ile geliştiricilerin F # 5 ' e erişimi vardır. F # 5 ' in birkaç yeni özelliği aşağıda verilmiştir:

### <a name="interpolated-strings"></a>Ara değerli dizeler

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

## <a name="visual-basic-updates"></a>Visual Basic güncelleştirmeleri

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

## <a name="systemtextjson-new-features"></a>Yeni özelliklerde System.Text.Js

Ve [ üzerindeSystem.Text.Js](../standard/serialization/system-text-json-overview.md)için yeni özellikler mevcuttur:

- [Başvuruları koru ve döngüsel başvuruları işle](../standard/serialization/system-text-json-preserve-references.md)
- [HttpClient ve HttpContent genişletme yöntemleri](../standard/serialization/system-text-json-how-to.md#httpclient-and-httpcontent-extension-methods)
- [Tırnak işaretleri halinde izin ver veya yaz](../standard/serialization/system-text-json-invalid-json.md#allow-or-write-numbers-in-quotes)
- [Sabit türleri ve C# 9 kayıtlarını destekleme](../standard/serialization/system-text-json-immutability.md)
- [Ortak olmayan özellik erişimcileri desteği](../standard/serialization/system-text-json-immutability.md)
- [Destek alanları](../standard/serialization/system-text-json-how-to.md#include-fields)
- [Özelliği koşullu olarak Yoksay](../standard/serialization/system-text-json-ignore-properties.md)
- [Dize olmayan anahtar sözlüklerini destekleme](../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md#dictionary-with-non-string-key)
- [Özel dönüştürücülerin null işlemesine izin ver](../standard/serialization/system-text-json-converters-how-to.md#handle-null-values)
- [JsonSerializerOptions 'ı Kopyala](../standard/serialization/system-text-json-configure-options.md#copy-jsonserializeroptions)
- [Web varsayılanları ile JsonSerializerOptions oluşturma](../standard/serialization/system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions)

## <a name="see-also"></a>Ayrıca bkz.

- [Bir .NET ile yolculuğa](https://channel9.msdn.com/Events/Build/2020/BOD106)
- [.NET 5 ' teki performans iyileştirmeleri](https://devblogs.microsoft.com/dotnet/performance-improvements-in-net-5)
- [.NET SDK'yı indirin](https://dotnet.microsoft.com/download)
