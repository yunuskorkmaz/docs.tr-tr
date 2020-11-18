---
title: Null yapılabilir başvuru türleri-C# başvurusu
description: C# null yapılabilir başvuru türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 04/06/2020
ms.openlocfilehash: d961af9ba3b4776e6b4ec3eeea5392fb0d0394ce
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94822431"
---
# <a name="nullable-reference-types-c-reference"></a>Null yapılabilir başvuru türleri (C# Başvurusu)

> [!NOTE]
> Bu makalede null yapılabilir başvuru türleri ele alınmaktadır. [Null olabilir değer türleri](nullable-value-types.md)de bildirebilirsiniz.

Null yapılabilir başvuru türleri, *null yapılabilen bir içeriğe* sahip olan kodda C# 8,0 ile başlayarak kullanılabilir. Null yapılabilir başvuru türleri, null statik analiz uyarıları ve [null-forverme işleci](../operators/null-forgiving.md) isteğe bağlı dil özellikleridir. Tümü varsayılan olarak kapalıdır. *Null yapılabilir bağlam* , derleme ayarları kullanılarak proje düzeyinde veya pragmalar kullanılarak kodda denetlenir.

 Null yapılabilir bir bağlamda:

- Başvuru türünün bir değişkeni `T` null olmayan bir değerle başlatılmalıdır ve hiçbir şekilde bir değer atanmayabilir `null` .
- Başvuru türündeki bir değişken `T?` `null` , veya atanmış `null` olarak başlatılabilir, ancak `null` başvurulmadan önce gözden alınması gerekir.
- Türünde bir değişken, `m` `T?` içinde olduğu gibi null-forverme işlecini uyguladığınızda null olmayan olarak değerlendirilir `m!` .

Null yapılamayan bir başvuru türü `T` ve null yapılabilen bir başvuru türü arasındaki farklılıklar, `T?` derleyicinin önceki kuralların yorumu tarafından zorlanır. Türünde bir değişken `T` ve türünde bir değişken `T?` aynı .NET türü tarafından temsil edilir. Aşağıdaki örnek, null olamayan bir dize ve null yapılabilen bir dize bildirir ve null olmayan bir dizeye değer atamak için null-forverme işlecini kullanır:

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetCoreSyntax":::

Değişkenler `notNull` ve `nullable` her ikisi de türü tarafından temsil edilir <xref:System.String> . Null değer atanamaz ve null atanabilir türler aynı türde depolandığından, null yapılabilir bir başvuru türü kullanılmasına izin verilmez. Genel olarak, null yapılabilir bir başvuru türü, temel sınıf veya uygulanan arabirim olarak kullanılamaz. Herhangi bir nesne oluşturma veya tür testi ifadesinde null yapılabilen bir başvuru türü kullanılamaz. Null yapılabilir bir başvuru türü üye erişim ifadesinin türü olamaz. Aşağıdaki örneklerde bu yapılar gösterilmektedir:

```csharp
public MyClass : System.Object? // not allowed
{
}

var nullEmpty = System.String?.Empty; // Not allowed
var maybeObject = new object?(); // Not allowed
try
{
    if (thing is string? nullableString) // not allowed
        Console.WriteLine(nullableString);
} catch (Exception? e) // Not Allowed
{
    Console.WriteLine("error");
}
```

## <a name="nullable-references-and-static-analysis"></a>Null yapılabilir başvurular ve statik analiz

Önceki bölümdeki örneklerde, null yapılabilir başvuru türlerinin doğası gösterilmektedir. Null yapılabilir başvuru türleri yeni sınıf türleri değil, var olan başvuru türlerinde ek açıklamalar değildir. Derleyici, kodunuzda olası null başvuru hatalarını bulmanıza yardımcı olması için bu ek açıklamaları kullanır. Null yapılamayan bir başvuru türü ve null yapılabilir bir başvuru türü arasında çalışma zamanı farkı yoktur. Derleyici, null olamayan başvuru türleri için hiçbir çalışma zamanı denetimi eklemez. Avantajlar, derleme zamanı analizinde bulunur. Derleyici, kodunuzdaki olası null hataları bulmanıza ve düzeltmenize yardımcı olan uyarılar oluşturur. Amacınızı bildirirsiniz ve kodunuz bu amacı ihlal ettiğinde derleyici sizi uyarır.

Null yapılabilir etkin bir bağlamda derleyici, herhangi bir başvuru türünün değişkenlerinde statik analiz gerçekleştirir, hem null yapılabilir hem de null değer atanamaz. Derleyici, her başvuru değişkeninin null durumunu *null* ya da *belki null* olarak izler. Null yapılamayan bir başvurunun varsayılan durumu *null değil*. Null yapılabilen bir başvurunun varsayılan durumu *null olabilir*.

Null durumu *null* olmadığından, null olamayan başvuru türleri başvuru için her zaman güvenli olmalıdır. Bu kuralı zorlamak için, null olamayan bir başvuru türü null olmayan bir değere başlatılmamışsa, derleyici uyarıları yayınlar. Yerel değişkenlerin, bildirildiği yere atanması gerekir. Her oluşturucunun, gövdesinde, adlandırılmış bir oluşturucuda veya bir alan başlatıcısı kullanarak her alanı ataması gerekir. Durum, durumu *null* olan bir başvuruya null atanamaz bir başvuru atanmışsa, derleyici uyarıları yayınlar. Ancak, null olamayan bir başvuru *null* olmadığından, bu değişkenlere başvuruluyorsa hiçbir uyarı verilmemektedir.

Null yapılabilir başvuru türleri başlatılabilir veya atanabilir `null` . Bu nedenle, Statik Analize başvurulmadan önce bir değişkenin *null* olduğunu belirlemesi gerekir. Null yapılabilir bir başvurunun null olduğu belirlenirse, *null* olamayan bir başvuru değişkenine atanamaz. Aşağıdaki sınıf bu uyarıların örneklerini gösterir:

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetClassWithNullable":::

Aşağıdaki kod parçacığında, bu sınıfı kullanırken derleyicinin uyarı yayar konumu gösterilmektedir:

:::code language="csharp" source="snippets/shared/NullableReferenceTypes.cs" id="SnippetLocalWarnings":::

Yukarıdaki örneklerde, başvuru değişkenlerinin null durumunu belirlemede derleyicinin statik analizi gösterilmektedir. Derleyici, analizini bilgilendirmek için null denetimleri ve atamaları için dil kuralları uygular.  Derleyici, yöntemlerin veya özelliklerin semantiği hakkında varsayımlar yapamaz. Null denetimleri gerçekleştiren Yöntemler çağırırsanız, derleyici bu yöntemlerin bir değişkenin null durumunu etkilediğini bilmez. Derleyiciye bağımsız değişkenlerin semantiğini ve dönüş değerlerini bildirmek için, API 'lerinize ekleyebileceğiniz birçok öznitelik vardır. Bu öznitelikler, .NET Core kitaplıklarında birçok ortak API 'ye uygulandı. Örneğin, <xref:System.String.IsNullOrEmpty%2A> güncelleştirilmiş ve derleyici bu yöntemi null denetim olarak doğru şekilde yorumlar. Null durum statik analizine uygulanan öznitelikler hakkında daha fazla bilgi için, null [yapılabilir öznitelikler](../attributes/nullable-analysis.md)sayfasındaki makaleye bakın.

## <a name="setting-the-nullable-context"></a>Null yapılabilir bağlam ayarlanıyor

Null yapılabilir bağlamı denetlemek için iki yol vardır. Proje düzeyinde `<Nullable>enable</Nullable>` Proje ayarını ekleyebilirsiniz. Tek bir C# kaynak dosyasında, `#nullable enable` null yapılabilir bağlamı etkinleştirmek için pragma ekleyebilirsiniz. [Null yapılabilir bir strateji ayarlama](../../nullable-migration-strategies.md)hakkında makaleye bakın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [C# dil belirtimi](~/_csharplang/spec/introduction.md)için aşağıdaki teklifler:

- [Boş değer atanabilir başvuru türleri](~/_csharplang/proposals/csharp-8.0/nullable-reference-types.md)
- [Taslak Nullable başvuru türleri belirtimi](~/_csharplang/proposals/csharp-9.0/nullable-reference-types-specification.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [Boş değer atanabilen değer türleri](nullable-value-types.md)
