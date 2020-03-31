---
title: .NET Standardı'ndaki yenilikler
description: Bu makalede, .NET Standard'ın her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmiştir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 28d6a3546e08bbc3a7d4a26f08ba9cc5e16a901b
ms.sourcegitcommit: 2ff49dcf9ddf107d139b4055534681052febad62
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/31/2020
ms.locfileid: "80438197"
---
# <a name="whats-new-in-net-standard"></a>.NET Standardı'ndaki yenilikler

.NET Standart, standardın bu sürümüne uygun .NET uygulamalarında bulunması gereken sürümlü BIR API kümesini tanımlayan resmi bir belirtimdir. .NET Standard kütüphane geliştiricileri hedeflenir. .NET Standart sürümünü hedefleyen bir kitaplık, standardın bu sürümünü destekleyen herhangi bir .NET Framework, .NET Core veya Xamarin uygulamasında kullanılabilir.

.NET Standardı,.NET Core SDK'nın yanı sıra .NET Core iş yükünü seçtiğinizde Visual Studio ile birlikte verilir.

## <a name="supported-net-implementations"></a>Desteklenen .NET uygulamaları

.NET Standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:

- .NET Core 2.0 veya sonrası
- .NET Framework 4.6.1 veya sonrası
- Mono 5.4 veya sonrası
- Xamarin.iOS 10.14 veya sonrası
- Xamarin.Mac 3.8 veya sonrası
- Xamarin.Android 8.0 veya sonrası
- Evrensel Windows Platformu 10.0.16299 veya sonrası

## <a name="whats-new-in-net-standard-20"></a>.NET Standart 2.0'daki yenilikler

.NET Standart 2.0 aşağıdaki yeni özellikleri içerir:

### <a name="a-vastly-expanded-set-of-apis"></a>Büyük ölçüde genişletilmiş BIR API seti

.NET Standard, sürüm 1.6 aracılığıyla, nispeten küçük bir API alt kümesini içeriyordu. Bu hariç arasında yaygın .NET Framework veya Xamarin kullanılan birçok API'ler vardı. Geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirirken tanıdık API'ler için uygun yedekler bulmalarını gerektirdiğinden, bu durum geliştirmeyi karmaşıklaştırır. .NET Standart 2.0, standardın önceki sürümü olan .NET Standart 1.6'da bulunandan 20.000'den fazla API ekleyerek bu sınırlamayı giderir. .NET Standart 2.0'a eklenen API'lerin listesi [için](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md)bkz.

.NET Standart 2.0'daki <xref:System> ad alanına yapılan eklemelerden bazıları şunlardır:

- Sınıf için <xref:System.AppDomain> destek.
- <xref:System.Array> Sınıftaki ek üyelerden gelen dizilerle çalışmak için daha iyi destek.
- <xref:System.Attribute> Sınıftaki ek üyelerin öznitelikleriyle çalışmak için daha iyi destek.
- Daha iyi takvim desteği ve <xref:System.DateTime> değerler için ek biçimlendirme seçenekleri.
- Ek <xref:System.Decimal> yuvarlama işlevi.
- Sınıfta ek <xref:System.Environment> işlevsellik.
- <xref:System.GC> Sınıf boyunca çöp toplayıcısı üzerinde geliştirilmiş kontrol.
- <xref:System.String> Sınıfta dize karşılaştırması, numaralandırma ve normalleştirme için geliştirilmiş destek.
- Gün ışığından yararlanma ayarlamaları ve <xref:System.TimeZoneInfo.AdjustmentRule> <xref:System.TimeZoneInfo.TransitionTime> sınıflarda geçiş süreleri için destek.
- <xref:System.Type> Sınıfta önemli ölçüde geliştirilmiş işlevsellik.
- Özel durum oluşturucusu <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreler ekleyerek özel durum nesnelerinin deserialization için daha iyi destek.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için destek

Kütüphanelerin ezici çoğunluğu .NET Standardı yerine .NET Framework'ü hedeflemektedir. Ancak, bu kitaplıklarda yapılan çağrıların çoğu .NET Standart 2.0'da yer alan API'lere yapılır. .NET Standard 2.0 ile başlayarak ,.NET Framework kitaplıklarına bir .NET Standart kitaplığından [uyumluluk şim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak erişebilirsiniz. Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için hiçbir şey yapmanıza gerek yoktur.

Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API'lerin .NET Standart 2.0'a dahil edilmesidir.

### <a name="support-for-visual-basic"></a>Visual Basic desteği

Artık Visual Basic'te .NET Standart kitaplıkları geliştirebilirsiniz. Visual Studio 2019 ve Visual Studio 2017 sürüm 15.3 veya daha sonra yüklü .NET Core iş yükü ile bir .NET Standart Sınıf Kitaplığı şablonu içerir. Diğer geliştirme araçlarını ve ortamlarını kullanan Visual Basic geliştiricileri için bir .NET Standart Kitaplığı projesi oluşturmak için [dotnet yeni](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz. Daha fazla bilgi [için .NET Standart kitaplıkları için Araçlama desteğine](#tooling-support-for-net-standard-libraries)bakın.

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standart kitaplıkları için araç desteği

.NET Core 2.0 ve .NET Standard 2.0'ın piyasaya sürülmesiyle, visual studio 2017 ve [.NET Core CLI,.NET](../../core/tools/index.md) Standart kitaplıklarını oluşturmak için araç desteği içerir.

Visual Studio'yu **.NET Core platformlar arası geliştirme** iş yüküyle yüklerseniz, aşağıdaki şekilde belirtildiği gibi, bir proje şablonu kullanarak bir .NET Standart 2.0 kitaplık projesi oluşturabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-cs.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Yeni .NET Standart kitaplık projesi ekle](./media/std-project-vb.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [dotnet yeni](../../core/tools/dotnet-new.md) komutu .NET Standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standard](../net-standard.md)
- [.NET Standardı Tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
