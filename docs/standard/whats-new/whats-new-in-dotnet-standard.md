---
title: .NET Standard'daki yenilikler
description: Bu makalede, yeni özellikler ve geliştirmeler her .NET Standard'ın yeni sürümünde bulunan özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8810508bc61f6fd625b1485f199249a96b2686e6
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43674409"
---
# <a name="whats-new-in-the-net-standard"></a>.NET Standard'daki yenilikler

.NET standard'ın bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir API sürümü tutulan kümesini tanımlayan bir resmi belirtimi standarttır. .NET Standard kitaplığı geliştiricilere yöneliktir. .NET Standard bir sürümü hedefleyen bir kitaplık standart sürümünün desteklediği tüm .NET Framework, .NET Core ve Xamarin uygulaması üzerinde kullanılabilir.

En son .NET Standard 2.0 sürümüdür. .NET Core iş yükü yüklenmiş olan .NET Core 2.0 SDK'sını yanı sıra Visual Studio 2017 sürüm 15.3 ile dahil edilmiştir.

## <a name="supported-net-implementations"></a>Desteklenen .NET uygulamaları

.NET Standard 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:

- .NET core 2.0 veya üzeri
- .NET framework 4.6.1 veya üzeri
- Mono 5.4 veya üzeri
- Xamarin.iOS 10.14 veya üzeri
- Xamarin.Mac 3.8 veya üzeri
- Xamarin.Android 8.0 veya üzeri
- Evrensel Windows platformu 10.0.16299 veya üzeri

## <a name="whats-new-in-the-net-standard-20"></a>.NET Standard 2.0 yenilikler

.NET Standard 2.0 aşağıdaki yeni özellikler içerir:

### <a name="a-vastly-expanded-set-of-apis"></a>Büyük ölçüde genişletilmiş bir API kümesi

Sürüm 1.6 .NET Standard API'leri daha küçük bir kısmı dahil. Arasında olanlar hariç, Xamarin ve .NET Framework içinde yaygın olarak kullanılan birçok API'leri yoktu. Uygulamalar ve birden çok .NET uygulamaları hedefleyen kitaplıklar geliştirirken geliştiriciler için tanıdık API'lerini uygun değiştirmeler öğrenin gerektirdiğinden, geliştirme, daha karmaşık hale getirir. .NET Standard 2.0, .NET standart 1.6, standart'ın önceki sürümünü kullanılabilen çok 20. 000'den daha fazla API ekleyerek bu sınırlama yöneliktir. .NET Standard 2.0 eklenmiş olan API'leri bir listesi için bkz. [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Bazı eklemeler <xref:System> ad alanında .NET Standard 2.0 içerir:

- Destek <xref:System.AppDomain> sınıfı.
- Ek üyeleri dizilerden ile çalışmak için daha iyi destek <xref:System.Array> sınıfı.
- Ek üye öznitelikleri ile çalışmak için daha iyi destek <xref:System.Attribute> sınıfı.
- Daha iyi destek ve ek biçimlendirme seçenekleri için Takvim <xref:System.DateTime> değerleri.
- Ek <xref:System.Decimal> işlevselliği yuvarlama.
- Ek işlevsellik <xref:System.Environment> sınıfı.
- Gelişmiş çöp toplayıcı üzerinde denetim <xref:System.GC> sınıfı.
- Dize karşılaştırması, numaralandırma ve normalleştirme içinde için gelişmiş destek <xref:System.String> sınıfı.
- Destek ayarlamalar ve geçiş süreleri içinde ışığından <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıfları.
- İşlevindeki'önemli ölçüde geliştirilmiş <xref:System.Type> sınıfı.
- Bir özel durum oluşturucuyla ekleyerek nesneleri seri durumdan çıkarma özel durum için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreleri.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için desteği

.NET Framework yerine .NET Standard kitaplıkları büyük çoğunluğu hedefleyin. Ancak, bu kitaplıkları çağrılarında .NET Standard 2.0 içinde bulunan API'lerin çoğu. .NET Standard 2.0 ile başlayarak, .NET Framework kitaplıkları bir .NET Standard Kitaplığı'ndan kullanarak erişebileceğiniz bir [uyumluluk dolgu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-20/README.md#assembly-unification). Bu uyumluluk katmanı, geliştiriciler için saydamdır; .NET Framework kitaplıkları yararlanmak için herhangi bir şey yapmanız gerekmez.

.NET Framework sınıf kitaplığının adlı API'leri .NET Standard 2.0 dahil edilmesi gerektiğini tek gereksinimdir.

### <a name="support-for-visual-basic"></a>Visual Basic için destek

Artık Visual Basic'te .NET standart kitaplıkları da geliştirebilirsiniz. Visual Studio 2017 sürüm 15.3 kullanan Visual Basic geliştiriciler için ya da daha sonra .NET Core iş yükü yüklenmiş olan Visual Studio artık .NET standart sınıf kitaplığı şablonu içerir. Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiricileri için kullanabileceğiniz [yeni dotnet](../../core/tools/dotnet-new.md) komutunu bir .NET Standard kitaplığı projesi oluşturun. Daha fazla bilgi için [.NET standart kitaplıkları için araç desteği](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard kitaplıkları için araç desteği

.NET Core 2.0 ve .NET Standard 2.0, hem Visual Studio 2017 sürümünde ve [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) araç .NET standart kitaplıkları oluşturmak için desteği içerir.

Visual Studio'ya yüklerseniz **.NET Core çoklu platform geliştirme** iş yükü, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2.0 kitaplık projesi oluşturabilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi ekleme](./media/std-project-cs.png)

.NET Core CLI, aşağıdaki kullanıyorsanız [yeni dotnet](../../core/tools/dotnet-new.md) komut .NET Standard 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Yeni .NET Standard kitaplığı projesi ekleme](./media/std-project-vb.png)

.NET Core CLI, aşağıdaki kullanıyorsanız [yeni dotnet](../../core/tools/dotnet-new.md) komut .NET Standard 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Ayrıca bkz.

[.NET Standard](../net-standard.md)  
[.NET Standard ile tanışın](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
