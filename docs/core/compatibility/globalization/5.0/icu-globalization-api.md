---
title: "Son değişiklik: genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır"
description: ICU kitaplıklarının NLS yerine Genelleştirme işlevselliği için kullanıldığı .NET 5,0 ' de Genelleştirme bölünmesi değişikliği hakkında bilgi edinin.
ms.date: 05/19/2020
ms.openlocfilehash: efc20e21969ea4a83c9122e40b262e1dc38e6770
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761706"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a>Genelleştirme API 'Leri Windows üzerinde ıCU kitaplıklarını kullanır

.NET 5,0 ve sonraki sürümleri, Windows 10 Mayıs 2019 güncelleştirme veya sonrasında çalışırken Genelleştirme işlevselliği için [Unicode (ıCU)](http://site.icu-project.org/home) kitaplıklarını kullanır.

## <a name="change-description"></a>Açıklamayı Değiştir

.NET Core 1,0-3,1 ve .NET Framework 4 ve üzeri sürümlerde, .NET kitaplıkları Windows üzerinde Genelleştirme işlevselliği için [ulusal dil desteği (NLS)](/windows/win32/intl/national-language-support) API 'lerini kullanır. Örneğin, NLS işlevleri dizeleri karşılaştırmak, kültür bilgilerini almak ve uygun kültür içinde dize büyük harfleri gerçekleştirmek için kullanılır.

.NET 5,0 ' den itibaren, bir uygulama Windows 10 Mayıs 2019 veya sonraki sürümlerde çalışıyorsa, .NET kitaplıkları varsayılan olarak [ICU](http://site.icu-project.org/home) genelleştirme API 'lerini kullanır.

> [!NOTE]
> Windows 10 Mayıs 2019 güncelleştirmesi ve sonraki sürümleri ıCU yerel kitaplığıyla birlikte sevk. .NET çalışma zamanı ıCU 'yi yükleye, bunun yerine NLS kullanır.

## <a name="behavioral-differences"></a>Davranış farkları

Genelleştirme tesislerini kullandığınızı fark etmeseniz bile uygulamanızdaki değişiklikleri görebilirsiniz. Bu bölüm, görebileceğiniz bazı davranış değişikliklerini listeler, ancak diğerleri de vardır.

### <a name="stringindexof"></a>String. IndexOf

<xref:System.String.IndexOf(System.String)?displayProperty=nameWithType>Bir dizedeki yeni satır karakterinin dizinini bulmak için çağıran aşağıdaki kodu göz önünde bulundurun.

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- Önceki .NET sürümlerinde, kod parçacığı yazdırılır `6` .
- .NET 5,0 ve sonraki sürümlerinde, kod parçacığı yazdırılır `-1` .

Kültüre duyarlı arama yerine bir sıralı arama gerçekleştirerek bu kodu onarmak için, <xref:System.String.IndexOf(System.String,System.StringComparison)> aşırı yüklemeyi çağırın ve <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> bağımsız değişken olarak geçirin.

Kod çözümleme kurallarını [CA1307: açıklık ve CA1309 Için StringComparison belirtin](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) : kodunuzda bu çağrı sitelerini bulmak Için [sıralı StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) ' i kullanın.

Daha fazla bilgi için bkz. [.NET 5 + üzerindeki dizeleri karşılaştırırken davranış değişiklikleri](../../../../standard/base-types/string-comparison-net-5-plus.md).

### <a name="currency-symbol"></a>Para birimi simgesi

Para birimi biçim belirticisini kullanarak bir dizeyi biçimlendiren aşağıdaki kodu göz önünde bulundurun `C` . Geçerli iş parçacığının kültürü, ülkeyi değil yalnızca dili içeren bir kültüre ayarlanır.

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- Önceki .NET sürümlerinde, metin değeri `"100,00 €"` .
- .NET 5,0 ve sonraki sürümlerde Windows 19H1 ve sonraki sürümlerinde, metin değeri, `"100,00 ¤"` Euro yerine uluslararası para birimi sembolünü kullanan olur. ICU 'de tasarım, bir para biriminin bir ülke veya bölgenin bir dil değil bir özelliğidir.

## <a name="reason-for-change"></a>Değişiklik nedeni

Bu değişiklik, birleştirme için sunulmuştur. Tüm desteklenen işletim sistemleri genelinde NET ' in Genelleştirme davranışı. Ayrıca, uygulamaların işletim sisteminin yerleşik kitaplıklarına göre değil, kendi Genelleştirme kitaplıklarını paketleyebilme olanağı da sağlar.

## <a name="version-introduced"></a>Sunulan sürüm

.NET 5,0

## <a name="recommended-action"></a>Önerilen eylem

Geliştiricinin bölümünde herhangi bir eylem gerekmez. Ancak, NLS genelleştirme API 'Lerini kullanmaya devam etmek istiyorsanız, bu davranışa dönmek için bir [çalışma zamanı anahtarı](../../../run-time-config/globalization.md#nls) ayarlayabilirsiniz. Kullanılabilir anahtarlar hakkında daha fazla bilgi için bkz. [.NET Genelleştirme ve ıCU](../../../../standard/globalization-localization/globalization-icu.md) makalesi.

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- Ad alanındaki çoğu tür <xref:System.Globalization?displayProperty=fullName>
- <xref:System.Array.Sort%2A?displayProperty=fullName> (dizeler dizisini sıralarken)
- <xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (liste öğeleri dizeler olduğunda)
- <xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)
- <xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (anahtarlar dizeler olduğunda)
- <xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (küme dizeler içerdiğinde)

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
