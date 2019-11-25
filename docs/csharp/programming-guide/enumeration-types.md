---
title: Sabit listesi türleri C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 09/10/2017
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
ms.openlocfilehash: 3573959a1e10b475a9867631767de5d10a08b9ea
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73969771"
---
# <a name="enumeration-types-c-programming-guide"></a>Sabit listesi türleriC# (Programlama Kılavuzu)

Bir sabit listesi türü (numaralandırma veya sabit listesi olarak da adlandırılır), bir değişkene atanabilecek adlandırılmış integral sabitleri kümesini tanımlamak için etkili bir yol sağlar. Örneğin, değeri haftanın gününü temsil edecek bir değişken tanımlamanız gerektiğini varsayın. Bu değişkenin her zaman depolayabileceği yedi anlamlı değer vardır. Bu değerleri tanımlamak için, [enum](../language-reference/keywords/enum.md) anahtar sözcüğü kullanılarak bildirilebilecek bir numaralandırma türü kullanabilirsiniz.

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

Varsayılan olarak, numaralandırıcıdaki her öğenin temel alınan türü [int](../language-reference/builtin-types/integral-numeric-types.md)'tir. Önceki örnekte gösterildiği gibi, iki nokta üst üste kullanarak başka bir integral sayısal türü belirtebilirsiniz. Olası türlerin tam listesi için bkz. [enum (C# başvuru)](../language-reference/keywords/enum.md).

Aşağıdaki örnekte gösterildiği gibi temel alınan türe atama yaparak temeldeki sayısal değerleri doğrulayabilirsiniz.

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

Sayısal bir tür yerine bir sabit listesi kullanmanın avantajları aşağıda verilmiştir:

- Değişken için hangi değerlerin geçerli olduğunu açıkça istemci kodu için belirtirsiniz.

- Visual Studio 'da, IntelliSense tanımlı değerleri listeler.

Numaralandırıcı listesindeki öğeler için değer belirtmeyin, değerler otomatik olarak 1 ' den artırılır. Önceki örnekte, `Day.Sunday` 0 değerine sahiptir, `Day.Monday` 1 değeri vardır ve bu şekilde devam eder. Yeni bir `Day` nesnesi oluşturduğunuzda, açıkça bir değer atamadıysanız varsayılan değeri `Day.Sunday` (0) olur. Bir sabit listesi oluşturduğunuzda, en mantıksal varsayılan değeri seçin ve sıfıra bir değer verin. Bu, tüm Numaralandırmaların, oluşturulduklarında açıkça bir değer atamadığı takdirde, bu varsayılan değere sahip olmasına neden olur.

Değişken `meetingDay` `Day`tür ise (açık bir atama olmadan), yalnızca `Day`tarafından tanımlanan değerlerden birini atayabilirsiniz. Toplantı günü değişirse, `meetingDay``Day` yeni bir değer atayabilirsiniz:

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> `meetingDay`için herhangi bir rastgele tamsayı değeri atamak mümkündür. Örneğin, bu kod satırı bir hata oluşturmaz: `meetingDay = (Day) 42`. Ancak, örtük beklentide bir numaralandırma değişkeninin yalnızca enum tarafından tanımlanan değerlerden birini tutacağından bunu yapmanız gerekmez. Sabit listesi türünde bir değişkene rastgele bir değer atamak için, hatalara yönelik yüksek riskli bir hata ortaya çıkaracak.

Bir numaralandırma türünün Numaralandırıcı listesindeki öğelere herhangi bir değer atayabilir ve hesaplanan değerleri de kullanabilirsiniz:

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a>Bit bayrakları olarak numaralandırma türleri

Bir numaralandırma türü örneğini, Numaralandırıcı listesinde tanımlanan değerlerin herhangi bir birleşimini depolamak üzere bir numaralandırma türü örneği sağlayan bit bayraklarını tanımlamak için kullanabilirsiniz. (Tabii ki, bazı birleşimler program kodunuzda anlamlı veya izin verilebilir olmayabilir.)

<xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğini uygulayarak ve değerleri uygun şekilde tanımlayarak, `AND`, `OR`, `NOT` ve `XOR` bit düzeyinde işlemler gerçekleştirilmeleri için bir bit bayrakları numaralandırması oluşturursunuz. Bir bit bayrakları numaralandırmasında, "hiçbir bayrak ayarlanmadı" anlamına gelen değeri sıfır olan adlandırılmış sabiti ekleyin. "Bayrak ayarlanmamışsa" bir değere sıfır değeri vermeyin.

Aşağıdaki örnekte, `Days`adlı `Day` numaralandırmasının başka bir sürümü tanımlanmıştır. `Days` `Flags` özniteliğine sahiptir ve her değere 2 ' nin sonraki daha yüksek gücüne atanır. Bu, değeri `Days.Tuesday | Days.Thursday`olan `Days` bir değişken oluşturmanıza olanak sağlar.

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

Bir numaralandırıcıda bayrak ayarlamak için aşağıdaki örnekte gösterildiği gibi bit düzeyinde `OR` işlecini kullanın:

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

Belirli bir bayrağın ayarlanmış olup olmadığını anlamak için aşağıdaki örnekte gösterildiği gibi bit düzeyinde `AND` işlem kullanın:

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<xref:System.FlagsAttribute?displayProperty=nameWithType> özniteliğiyle numaralandırma türlerini tanımlarken göz önünde bulundurmanız gerekenler hakkında daha fazla bilgi için, bkz. <xref:System.Enum?displayProperty=nameWithType>.

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a>Enum değerlerini bulma ve işlemek için System. Enum yöntemlerini kullanma

Tüm numaralandırmalar <xref:System.Enum?displayProperty=nameWithType> türünün örnekleridir. <xref:System.Enum?displayProperty=nameWithType>yeni sınıflar türetemezsiniz, ancak kendi yöntemlerini kullanarak bir numaralandırma örneğindeki değerleri hakkında bilgi bulabilir ve bunları değiştirebilirsiniz.

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

Daha fazla bilgi için bkz. <xref:System.Enum?displayProperty=nameWithType>.

Ayrıca, bir uzantı yöntemi kullanarak bir numaralandırma için yeni bir yöntem oluşturabilirsiniz. Daha fazla bilgi için bkz. [bir numaralandırma için yeni bir yöntem oluşturma](./classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Enum?displayProperty=nameWithType>
- [C# Programlama Kılavuzu](./index.md)
- [enum](../language-reference/keywords/enum.md)
