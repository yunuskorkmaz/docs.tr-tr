---
title: .NET Standard’daki Yenilikler
description: Bu makalede, .NET Standard her yeni sürümünde bulunan yeni özellikler ve geliştirmeler özetlenmektedir.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: ebf656c4a5499fff54cb5a70a93c4e8cc9c82d0a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73101766"
---
# <a name="whats-new-in-the-net-standard"></a>.NET Standard’daki Yenilikler

.NET Standard, standart sürümü olan .NET uygulamalarında kullanılabilir olması gereken, sürümlenmiş bir API kümesini tanımlayan bir biçimsel belirtimdir. .NET Standard, kitaplık geliştiricileri 'ne yöneliktir. .NET Standard sürümünü hedefleyen bir kitaplık, standart sürümünü destekleyen tüm .NET Framework, .NET Core veya Xamarin uygulamalarında kullanılabilir.

.NET Standard en son sürümü 2,0 ' dir. .NET Core 2,0 SDK 'sının yanı sıra .NET Core iş yükünün yüklü olduğu Visual Studio 2017 sürüm 15,3 ile de birlikte bulunur.

## <a name="supported-net-implementations"></a>Desteklenen .NET uygulamaları

.NET Standard 2,0 aşağıdaki .NET uygulamaları tarafından desteklenir:

- .NET Core 2,0 veya üzeri
- .NET Framework 4.6.1 veya üzeri
- Mono 5,4 veya üzeri
- Xamarin. iOS 10,14 veya üzeri
- Xamarin. Mac 3,8 veya üzeri
- Xamarin. Android 8,0 veya üzeri
- Evrensel Windows Platformu 10.0.16299 veya üzeri

## <a name="whats-new-in-the-net-standard-20"></a>.NET Standard 2,0 ' deki yenilikler

.NET Standard 2,0 aşağıdaki yeni özellikleri içerir:

### <a name="a-vastly-expanded-set-of-apis"></a>Büyük ölçüde genişletilmiş bir API kümesi

Sürüm 1,6 ' den .NET Standard, API 'lerin karşılaştırarak küçük bir alt kümesini içerir. Dışlananlar arasında, .NET Framework veya Xamarin içinde yaygın olarak kullanılan birçok API. Bu, geliştiricilerin birden çok .NET uygulamasını hedefleyen uygulamalar ve kitaplıklar geliştirdiklerinde tanıdık API 'Ler için uygun değişiklikleri bulmasını gerektirdiğinden geliştirmeyi karmaşıklaştırır. 2,0 .NET Standard, Standard 'ın önceki sürümü olan .NET Standard 1,6 ' de bulunandan daha fazla 20.000 ' den fazla API ekleyerek bu sınırlamaya yöneliktir. 2,0 .NET Standard eklenen API 'lerin bir listesi için, bkz. [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).

.NET Standard 2,0 ' de <xref:System> ad alanına yapılan eklemelerin bazıları şunlardır:

- <xref:System.AppDomain> sınıfı için destek.
- <xref:System.Array> sınıfında ek üyelerden diziler ile çalışmaya yönelik daha iyi destek.
- <xref:System.Attribute> sınıfında ek üyelerin öznitelikleriyle çalışma için daha iyi destek.
- <xref:System.DateTime> değerler için daha iyi takvim desteği ve ek biçimlendirme seçenekleri.
- Ek <xref:System.Decimal> yuvarlama işlevselliği.
- <xref:System.Environment> sınıfında ek işlevsellik.
- <xref:System.GC> sınıfı aracılığıyla çöp toplayıcı üzerinde Gelişmiş denetim.
- <xref:System.String> sınıfında dize karşılaştırma, numaralandırma ve normalleştirme için geliştirilmiş destek.
- <xref:System.TimeZoneInfo.AdjustmentRule> ve <xref:System.TimeZoneInfo.TransitionTime> sınıflarında gün ışığından yararlanma ayarlamaları ve geçiş süreleri için destek.
- <xref:System.Type> sınıfında önemli ölçüde gelişmiş işlevsellik.
- <xref:System.Runtime.Serialization.SerializationInfo> ve <xref:System.Runtime.Serialization.StreamingContext> parametrelere sahip bir özel durum Oluşturucusu ekleyerek özel durum nesnelerinin serisini kaldırma için daha iyi destek.

### <a name="support-for-net-framework-libraries"></a>.NET Framework kitaplıkları için destek

Kitaplıkların büyük bölümü .NET Standard yerine .NET Framework hedefleyin. Ancak, bu kitaplıklardaki çağrıların çoğu .NET Standard 2,0 ' ye dahil olan API 'lere sahiptir. 2,0 .NET Standard başlayarak, bir [Uyumluluk dolgusu](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification)kullanarak bir .NET Standard kitaplığından .NET Framework kitaplıklarına erişebilirsiniz. Bu uyumluluk katmanı geliştiriciler için saydamdır; .NET Framework kitaplıklarından yararlanmak için herhangi bir şey yapmanız gerekmez.

Tek gereksinim, .NET Framework sınıf kitaplığı tarafından çağrılan API 'Lerin .NET Standard 2,0 ' ye dahil edilmesini sağlamalıdır.

### <a name="support-for-visual-basic"></a>Visual Basic için destek

Artık Visual Basic .NET Standard kitaplıklarını geliştirebilirsiniz. .NET Core iş yükü yüklüyken Visual Studio 2017 sürüm 15,3 veya üstünü kullanan Visual Basic geliştiriciler için, Visual Studio artık bir .NET Standard sınıf kitaplığı şablonu içerir. Diğer geliştirme araçları ve ortamları kullanan Visual Basic geliştiriciler için, bir .NET Standard kitaplığı projesi oluşturmak üzere [DotNet New](../../core/tools/dotnet-new.md) komutunu kullanabilirsiniz. Daha fazla bilgi için bkz. [.NET Standard kitaplıkları Için araç desteği](#tooling-support-for-net-standard-libraries).

### <a name="tooling-support-for-net-standard-libraries"></a>.NET Standard kitaplıkları için araç desteği

.NET Core 2,0 ve .NET Standard 2,0 sürümü ile hem Visual Studio 2017 hem de [.NET Core komut satırı arabirimi (CLI)](../../core/tools/index.md) , .NET Standard kitaplıkları oluşturmak için araç desteğini içerir.

Visual Studio 'Yu **.NET Core platformlar arası geliştirme** iş yüküyle birlikte yüklerseniz, aşağıdaki şekilde gösterildiği gibi bir proje şablonu kullanarak bir .NET Standard 2,0 kitaplık projesi oluşturabilirsiniz:

<!-- markdownlint-disable MD025 -->

# <a name="ctabcsharp"></a>[C#](#tab/csharp)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-cs.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[Visual Basic](#tab/vb)

![Yeni .NET Standard kitaplığı projesi Ekle](./media/std-project-vb.png)

.NET Core CLI kullanıyorsanız, aşağıdaki [DotNet yeni](../../core/tools/dotnet-new.md) komut, .NET Standard 2,0 ' i hedefleyen bir sınıf kitaplığı projesi oluşturur:

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a>Ayrıca bkz.

- [.NET Standard](../net-standard.md)
- [.NET Standard tanıtımı](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
