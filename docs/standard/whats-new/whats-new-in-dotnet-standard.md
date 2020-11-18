---
title: .NET Standard’daki yenilikler
description: Bu makalede, .NET Standard her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.prod: dotnet-whatsnew
ms.openlocfilehash: 299477a7375381fa7f8064562e2a68e221944a05
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817180"
---
# <a name="whats-new-in-net-standard"></a>.NET Standard’daki yenilikler

.NET Standard, standart sürümü olan .NET uygulamalarında kullanılabilir olması gereken, sürümlenmiş bir API kümesini tanımlayan bir biçimsel belirtimdir. .NET Standard, kitaplık geliştiricileri 'ne yöneliktir. .NET Standard sürümünü hedefleyen bir kitaplık, standart sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulamalarında kullanılabilir.

.NET Standard, .NET Core iş yükünü seçerken .NET Core SDK ve Visual Studio ile birlikte sunulur.

## <a name="supported-net-implementations"></a>Desteklenen .NET uygulamaları

.NET Standard 2,0 aşağıdaki .NET uygulamaları tarafından desteklenir:

- .NET Core 2,0 veya üzeri
- .NET Framework 4.6.1 veya üzeri
- Mono 5,4 veya üzeri
- Xamarin. iOS 10,14 veya üzeri
- Xamarin. Mac 3,8 veya üzeri
- Xamarin. Android 8,0 veya üzeri
- Evrensel Windows Platformu 10.0.16299 veya üzeri

## <a name="whats-new-in-net-standard-20"></a>.NET Standard 2,0 ' deki yenilikler

.NET Standard 2,0 aşağıdaki yeni özellikleri içerir:

### <a name="a-vastly-expanded-set-of-apis"></a>Büyük ölçüde genişletilmiş bir API kümesi

Sürüm 1,6 ' den .NET Standard, API 'lerin bir karşılaştırarak küçük alt kümesini içerir. Dışlanlar arasında yaygın olarak .NET Framework veya Xamarin içinde kullanılan birçok API. Bu, geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirdiklerinde tanıdık API 'Ler için uygun değişiklikleri bulmasını gerektirdiğinden geliştirmeyi karmaşıklaştırır. .NET Standard 2,0, standart bir önceki sürümü olan .NET Standard 1,6 ' de bulunandan daha fazla 20.000 ' den fazla API ekleyerek bu sınırlamaya yöneliktir. 2,0 .NET Standard eklenen API 'lerin bir listesi için, bkz. [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

<xref:System>.NET Standard 2,0 ' deki ad alanına yapılan eklemelerin bazıları şunlardır:

- Sınıfı için destek <xref:System.AppDomain> .
- Sınıfında ek üyelerden diziler ile çalışmaya yönelik daha iyi destek <xref:System.Array> .
- Sınıfında ek üyelerin öznitelikleriyle çalışma için daha iyi destek <xref:System.Attribute> .
- Daha iyi takvim desteği ve değerler için ek biçimlendirme seçenekleri <xref:System.DateTime> .
- Ek <xref:System.Decimal> yuvarlama işlevselliği.
- Sınıfında ek işlevsellik <xref:System.Environment> .
- Sınıfından çöp toplayıcı üzerinde Gelişmiş denetim <xref:System.GC> .
- Sınıfında dize karşılaştırma, numaralandırma ve normalleştirme için geliştirilmiş destek <xref:System.String> .
- Ve sınıflarında gün ışığından yararlanma ayarlamaları ve geçiş süreleri için <xref:System.TimeZoneInfo.AdjustmentRule> Destek <xref:System.TimeZoneInfo.TransitionTime> .
- Sınıfında önemli ölçüde gelişmiş işlevsellik <xref:System.Type> .
- Ve parametrelerine sahip bir özel durum Oluşturucusu ekleyerek özel durum nesnelerinin serisini kaldırma için daha iyi destek <xref:System.Runtime.Serialization.SerializationInfo> <xref:System.Runtime.Serialization.StreamingContext> .

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için destek

Birçok kitaplık .NET Standard yerine .NET Framework hedef. Ancak, bu kitaplıklardaki çağrıların çoğu .NET Standard 2,0 ' ye dahil olan API 'lere sahiptir. .NET Standard 2,0 ' den başlayarak, bir [Uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak bir .NET Standard kitaplığından .NET Framework kitaplıklarına erişebilirsiniz. Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için herhangi bir şey yapmanız gerekmez.

Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API 'Lerin .NET Standard 2,0 ' ye dahil edilmesini sağlamalıdır.

### <a name="support-for-visual-basic"></a>Visual Basic için destek

Artık Visual Basic .NET Standard kitaplıklarını geliştirebilirsiniz. .NET Core iş yükünün yüklü olduğu Visual Studio 2019 ve Visual Studio 2017 sürüm 15,3 veya üzeri bir .NET Standard sınıf kitaplığı şablonu içerir. Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiriciler için, bir .NET Standard kitaplığı projesi oluşturmak üzere [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz. Daha fazla bilgi için bkz. [.NET Standard kitaplıkları Için araç desteği](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard kitaplıkları için araç desteği

.NET Core 2,0 ve .NET Standard 2,0 sürümü ile hem Visual Studio 2017 hem de [.NET Core CLI](../../core/tools/index.md) .NET Standard kitaplıkları oluşturmak için araç desteğini içerir.

Visual Studio 'Yu **.NET Core platformlar arası geliştirme** iş yüküyle birlikte yüklerseniz, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2,0 kitaplık projesi oluşturabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[C#](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-cs.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[Visual Basic](#tab/vb)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-vb.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standard](../net-standard.md)
- [.NET Standard tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
- [.NET SDK'yı indirin](https://dotnet.microsoft.com/download)
