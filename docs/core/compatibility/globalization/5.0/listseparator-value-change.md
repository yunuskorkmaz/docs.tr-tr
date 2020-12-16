---
title: 'Son değişiklik: TextInfo. ListSeparator değer değişikliği'
description: TextInfo. ListSeparator varsayılan değerinin 5,0 ve 5.0.1 sürümleri arasında değiştirildiği .NET 5,0 kırma değişikliği hakkında bilgi edinin.
ms.date: 12/10/2020
ms.openlocfilehash: 720d46c1908bcd70812f575a90f580470dbc7f32
ms.sourcegitcommit: e301979e3049ce412d19b094c60ed95b316a8f8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/16/2020
ms.locfileid: "97596611"
---
# <a name="textinfolistseparator-values-changed"></a>TextInfo. ListSeparator değerleri değişti

<xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType>Farklı kültürler için varsayılan değerler tüm işletim sistemlerinde değişmiştir.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET 5.0.0 'de, [NLS 'den ICU kitaplıklarına geçiş](icu-globalization-api.md)bir parçası olarak, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> farklı kültürler Için varsayılan değerler Windows üzerinde değişmiştir. Unicode (ıCU) için uluslararası bileşenlerden alınan ondalık ayırıcı değerleri, değerler olarak kullanılmıştır <xref:System.Globalization.TextInfo.ListSeparator> . Linux ve macOS 'ta, değerlerde hiçbir değişiklik yoktu <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> ; diğer bir deyişle, ondalık ayırıcı değerlerini kullanmaya devam ederler.

.NET 5.0.1 ve sonraki sürümlerindeki tüm işletim sistemleri için değerleri, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> NLS 'den elde edilecek değerlerle eşdeğerdir. Windows için bu, değerlerin .NET Framework ve .NET Core 1,0-3,1 ' de oldukları değere eşit olduğu anlamına gelir. Linux ve macOS için, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> değerler artık <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> Windows için değerlerle eşleşir.

Aşağıdaki tabloda değerleri için değişiklikler özetlenmektedir <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .

| | .NET Framework<br/>.NET Core 1,0-3,1 | .NET 5.0 | .NET 5.0.1 |
-|-|-|-
| **Windows** | NLS 'den al | ICU 'dan ondalık ayırıcı.<br/>, NLS 'ye geri dönebilir. | NLS ile eşdeğer |
| **Linux ve macOS** | ICU 'den ondalık ayırıcı | ICU 'den ondalık ayırıcı | NLS ile eşdeğer |

## <a name="version-introduced"></a>Sunulan sürüm

5.0.1

## <a name="reason-for-change"></a>Değişiklik nedeni

Geliştiriciler, <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> virgülle ayrılmış değer (CSV) dosyalarını ayrıştırırken özelliği kullandıklarını ve yeni değerlerin bu ayrıştırma ile ilgili olduğunu bildirdi <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> .

## <a name="recommended-action"></a>Önerilen eylem

Kodunuz önceki ondalık ayırıcı değerlerini kullanıyorsa, istenen <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=nameWithType> değerleri gönderebilirsiniz.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Globalization.TextInfo.ListSeparator?displayProperty=fullName>

<!--

#### Category

- Globalization

### Affected APIs

- `P:System.Globalization.TextInfo.ListSeparator`

-->
