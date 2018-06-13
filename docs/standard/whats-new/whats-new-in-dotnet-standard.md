---
title: .NET standart yenilikler nelerdir?
description: Bu makalede, yeni özellikler ve geliştirmeler her yeni sürümünde .NET standart bulunan özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e422e6ff65439d105020a6305b66a8192586a8f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591495"
---
# <a name="whats-new-in-the-net-standard"></a>.NET standart yenilikler nelerdir?

.NET standart sürümü tutulan bir dizi standart bu sürümü ile uyumlu .NET uygulamaları üzerinde kullanılabilir olması gereken API tanımlayan bir resmi belirtimidir. .NET standart kitaplığı geliştiricileri yöneliktir. .NET standart sürümünü hedefleyen bir kitaplık standart bu sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulaması üzerinde kullanılabilir.

En son .NET standart 2.0 sürümüdür. .NET Core iş yükü yüklü .NET Core 2.0 SDK'sı yanı sıra Visual Studio 2017 sürüm 15.3 ile dahil edilir.

## <a name="supported-net-implementations"></a>Desteklenen .NET uygulamaları

.NET standart 2.0 aşağıdaki .NET uygulamaları tarafından desteklenir:

- .NET core 2.0 veya üstü
- .NET framework 4.6.1 veya daha yenisi
- Mono 5.4 veya üstü
- Xamarin.iOS 10.14 veya üzeri
- Xamarin.Mac 3.8 ya da daha yeni
- Xamarin.Android 8.0 veya üzeri
- Evrensel Windows platformu 10.0.16299 veya daha yenisi

## <a name="whats-new-in-the-net-standard-20"></a>.NET standart 2.0 yenilikler nelerdir?

.NET standart 2.0 aşağıdaki yeni özellikleri içerir:

### <a name="a-vastly-expanded-set-of-apis"></a>Fazla genişletilmiş bir API kümesi

Sürüm 1.6 ile .NET standart API'leri daha küçük bir kısmı dahil. Dışlanan bunlar arasında .NET Framework veya Xamarin yaygın olarak kullanılan birçok API'ları bulunuyordu. Uygulamalar ve birden çok .NET uygulamalarında hedefleyen kitaplıklar geliştirirken geliştiriciler bilinen API'leri uygun donanımlarının Bul gerektirdiğinden, geliştirme, daha karmaşık hale getirir. .NET standart 2.0, .NET standart 1.6 içinde standard'ın önceki sürümünü kullanılabilir olan çok fazla 20.000 daha fazla API'leri ekleyerek bu sınırlamaya giderir. .NET standart 2.0 için eklenene API'ları listesi için bkz: [.NET standart 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

Bazı eklemeler <xref:System> ad alanı .NET standart 2.0 içerir:

- Desteği <xref:System.AppDomain> sınıfı.
- Diziler ek üyelerinden ile çalışmak için daha iyi destek <xref:System.Array> sınıfı.
- Ek üyeleri öznitelikleri ile çalışmak için daha iyi destek <xref:System.Attribute> sınıfı.
- Daha iyi Takvim desteği ve ek biçimlendirme seçeneklerini <xref:System.DateTime> değerleri.
- Ek <xref:System.Decimal> işlevselliği yuvarlama.
- Ek işlevsellik <xref:System.Environment> sınıfı.
- Gelişmiş atık toplayıcı üzerinde denetim <xref:System.GC> sınıfı.
- Dize karşılaştırması, numaralandırma ve içinde normalleştirme için gelişmiş destek <xref:System.String> sınıfı.
- Ayarlamaları ve geçiş saat gün ışığından yararlanma desteği <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıfları.
- İşlevindeki'önemli ölçüde geliştirilmiş <xref:System.Type> sınıfı.
- Bir özel durum Oluşturucusu ile ekleyerek nesneleri seri durumdan çıkarma özel durumu için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametreleri.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için desteği

Kitaplıkları zorlamayı çoğunluğu .NET Framework yerine .NET standart hedefleyin. Ancak, bu kitaplıkları çağrılarında .NET standart 2.0 dahil API'lerine çoğu. .NET standart 2.0 ile başlayarak, .NET Framework kitaplıkları .NET standart bir kitaplıktan kullanarak erişebilirsiniz bir [uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification). Bu uyumluluk katmanı geliştiricileri için saydamdır; .NET Framework kitaplıkları yararlanmak için bir şey yapmanız gerekmez.

.NET Framework sınıf kitaplığı tarafından çağırılan API'lerin .NET standart 2.0 dahil edilmesi gerektiğini tek gereksinimdir.

### <a name="support-for-visual-basic"></a>Visual Basic desteği

Visual Basic'te .NET standart kitaplıkları şimdi geliştirebilirsiniz. Visual Studio 2017 sürüm 15.3 kullanarak Visual Basic geliştiricileri için ya da yüklü daha sonra .NET Core iş yükü ile Visual Studio artık bir .NET standart sınıf kitaplığı şablonu içerir. Diğer geliştirme araçları ve ortamlar kullanan Visual Basic geliştiricileri için kullandığınız [dotnet yeni](../../core/tools/dotnet-new.md) .NET standart kitaplığı projesi oluşturmak için komutu. Daha fazla bilgi için bkz: [.NET standart kitaplıkları için araç desteği](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>.NET standart kitaplıkları için araç desteği

.NET Core 2.0 ve .NET standart 2.0, hem Visual Studio 2017'in çıkışıyla ve [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) araç .NET standart kitaplıkları oluşturmak için desteği içerir.

Visual Studio ile yüklerseniz **.NET Core platformlar arası geliştirme** iş yükü, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET standart 2.0 kitaplığı projesi oluşturabilirsiniz:

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-cs.png)

Aşağıdaki .NET Core CLI kullanıyorsanız [dotnet yeni](../../core/tools/dotnet-new.md) komut .NET standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Yeni .NET standart Kitaplığı projesini ekleyin](./media/std-project-vb.png)

Aşağıdaki .NET Core CLI kullanıyorsanız [dotnet yeni](../../core/tools/dotnet-new.md) komut .NET standart 2.0 hedefleyen bir sınıf kitaplığı projesi oluşturur:

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Ayrıca bkz.

[.NET Standard](../net-standard.md)  
[.NET standart giriş](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
