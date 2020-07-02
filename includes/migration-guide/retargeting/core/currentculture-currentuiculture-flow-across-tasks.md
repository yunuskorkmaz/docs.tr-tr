---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614667"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a>Görevler arasında CurrentCulture ve CurrentUICulture Flow

#### <a name="details"></a>Ayrıntılar

.NET Framework 4,6 ' den başlayarak, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> <xref:System.Threading.ExecutionContext?displayProperty=fullName> zaman uyumsuz işlemler arasında akan iş parçacığında saklanır. Bu, veya üzerindeki değişikliklerin <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> , daha sonra zaman uyumsuz olarak çalıştırılan görevlerde yansıtıldığı anlamına gelir. Bu, önceki .NET Framework sürümlerinin davranışından (yani <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> , <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> tüm zaman uyumsuz görevlerde) farklıdır.

#### <a name="suggestion"></a>Öneri

Bu değişiklikten etkilenen uygulamalar, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> bir zaman uyumsuz görevde istenen veya ilk işlem olarak açıkça ayarlanarak soruna geçici bir çözüm verebilir. Alternatif olarak, eski davranış (akan değil <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) aşağıdaki uyumluluk anahtarı ayarlanarak kabul edilebilir:

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

Bu sorun WPF tarafından .NET Framework 4.6.2 içinde düzeltildi. Ayrıca, .NET Framework 4,6 ' de 4.6.1 ile [KB 3139549](https://support.microsoft.com/kb/3139549)arasında düzeltilmiştir. .NET Framework 4,6 veya sonraki bir sürümü hedefleyen uygulamalar, otomatik olarak WPF uygulamalarında doğru davranış alır- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) dağıtıcı işlemleri genelinde korunacaktır.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | İkincil       |
| Sürüm | 4.6         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
