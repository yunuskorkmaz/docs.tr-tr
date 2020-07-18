---
title: Dizin oluşturucular kullanma-C# Programlama Kılavuzu
ms.date: 07/15/2020
helpviewer_keywords:
- indexers [C#], about indexers
ms.assetid: df70e1a2-3ce3-4aba-ad80-4b2f3538699f
ms.openlocfilehash: e742e4dd5ea92ec3baf37c915e024e713022b7b6
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86416233"
---
# <a name="using-indexers-c-programming-guide"></a>Dizin oluşturucular kullanma (C# Programlama Kılavuzu)

Dizin oluşturucular, istemci uygulamaların dizi olarak erişebileceği bir [sınıf](../../language-reference/keywords/class.md), [Yapı](../../language-reference/builtin-types/struct.md)veya [arabirim](../../language-reference/keywords/interface.md) oluşturmanıza imkan tanıyan sözdizimsel bir kolaylığıdır. Derleyici bir `Item` Özellik (veya varsa alternatif olarak adlandırılmış bir özellik) oluşturur <xref:System.Runtime.CompilerServices.IndexerNameAttribute> ve uygun erişimci yöntemleri olur. Dizin oluşturucular en sık, birincil amacı bir iç koleksiyonu veya diziyi kapsüllemek olan türlerde uygulanır. Örneğin, `TempRecord` 24 saatlik bir dönemde 10 farklı zamanda kaydedildiği gibi Fahrenhayt 'teki sıcaklığı temsil eden bir sınıfınız olduğunu varsayalım. Sınıfı, `temps` `float[]` sıcaklık değerlerini depolamak için türünde bir dizi içerir. Bu sınıfta bir Dizin Oluşturucu uygulayarak istemciler, gibi bir örnekteki sıcakya farklı şekilde erişebilir `TempRecord` `float temp = tempRecord[4]` `float temp = tempRecord.temps[4]` . Dizin Oluşturucu gösterimi yalnızca istemci uygulamaları için söz dizimini basitleştirir; Ayrıca, diğer geliştiricilerin anlayabilmesi için sınıfı ve amacını daha sezgisel hale getirir.

Bir sınıf veya yapı biriminde bir Dizin Oluşturucu bildirmek için aşağıdaki örnekte gösterildiği gibi [this](../../language-reference/keywords/this.md) anahtar sözcüğünü kullanın:

```csharp
// Indexer declaration
public int this[int index]
{
    // get and set accessors
}
```

> [!IMPORTANT]
> Bir dizin oluşturucunun bildirilmesi, otomatik olarak nesne üzerinde adlı bir özellik oluşturur `Item` . `Item`Özelliğe, örnek [üye erişim ifadesinden](../../language-reference/operators/member-access-operators.md#member-access-expression-)doğrudan erişilemez. Ayrıca, kendi `Item` özelliklerinizi bir dizin oluşturucuya sahip bir nesneye eklerseniz, bir [CS0102 derleyici hatası](../../misc/cs0102.md)alırsınız. Bu hatayı önlemek için, <xref:System.Runtime.CompilerServices.IndexerNameAttribute> Dizin oluşturucuyu aşağıda açıklandığı gibi yeniden adlandır ' ı kullanın.

## <a name="remarks"></a>Açıklamalar

Bir dizin oluşturucunun türü ve parametrelerinin türü en az dizin oluşturucunun kendisi olarak erişilebilir olmalıdır. Erişilebilirlik düzeyleri hakkında daha fazla bilgi için bkz. [erişim değiştiricileri](../../language-reference/keywords/access-modifiers.md).

Arabirim ile Dizin oluşturucular kullanma hakkında daha fazla bilgi için bkz. [arabirim dizin oluşturucular](./indexers-in-interfaces.md).

Bir dizin oluşturucunun imzası, biçimsel parametrelerinin sayısı ve türlerinden oluşur. Dizin Oluşturucu türü veya biçimsel parametrelerin adlarını içermez. Aynı sınıfta birden fazla Dizin Oluşturucu bildirirseniz, bunların farklı imzaları olmalıdır.

Dizin Oluşturucu değeri bir değişken olarak sınıflandırılmıyor; Bu nedenle, Dizin Oluşturucu değeri bir [ref](../../language-reference/keywords/ref.md) veya [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi olarak geçirilemez.

Dizin oluşturucuyu diğer dillerin kullanabileceği bir adla sağlamak için, <xref:System.Runtime.CompilerServices.IndexerNameAttribute?displayProperty=nameWithType> Aşağıdaki örnekte gösterildiği gibi kullanın:

```csharp
// Indexer declaration
[System.Runtime.CompilerServices.IndexerName("TheItem")]
public int this[int index]
{
    // get and set accessors
}
```

Dizin `TheItem` Oluşturucu adı özniteliği tarafından geçersiz kılındığından, bu dizin oluşturucunun adı olacaktır. Varsayılan olarak, dizin oluşturucu adı `Item` .

## <a name="example-1"></a>Örnek 1

Aşağıdaki örnek, bir özel dizi alanının, `temps` ve bir dizin oluşturucunun nasıl bildirilemeyeceğini gösterir. Dizin Oluşturucu örneğe doğrudan erişim sağlar `tempRecord[i]` . Dizin oluşturucuyu kullanmanın alternatifi, diziyi [ortak](../../language-reference/keywords/public.md) bir üye olarak bildirmeli ve üyelerine doğrudan erişim sağlar `tempRecord.temps[i]` .

:::code language="csharp" source="snippets/Temperatures/TempRecord.cs":::

Bir dizin oluşturucunun erişim değerlendirildiği zaman, örneğin bir `Console.Write` ifadede, [Get](../../language-reference/keywords/get.md) erişimcisinin çağrıldığına dikkat edin. Bu nedenle, `get` bir erişimci yoksa, bir derleme zamanı hatası oluşur.

:::code language="csharp" source="snippets/Temperatures/Program.cs":::

## <a name="indexing-using-other-values"></a>Diğer değerleri kullanarak dizin oluşturma

C#, dizin oluşturucu parametre türünü tamsayı olarak sınırlamaz. Örneğin, bir Dizin Oluşturucu ile dize kullanmak yararlı olabilir. Bu tür bir Dizin Oluşturucu koleksiyondaki dizeyi arayarak ve uygun değeri döndürerek uygulanabilir. Erişimciler aşırı yüklenmiş olabilir, dize ve tamsayı sürümleri birlikte kullanılabilir.

## <a name="example-2"></a>Örnek 2

Aşağıdaki örnek, haftanın günlerini depolayan bir sınıf bildirir. `get`Erişimci bir dize, bir günün adı alır ve karşılık gelen tamsayıyı döndürür. Örneğin, "Pazar" 0, "Pazartesi" 1 döndürür ve bu şekilde devam eder.

:::code language="csharp" source="snippets/StringIndexers/DayCollection.cs":::

### <a name="consuming-example-2"></a>Tüketim örneği 2

:::code language="csharp" source="snippets/StringIndexers/Program.cs":::

## <a name="example-3"></a>Örnek 3

Aşağıdaki örnek, sabit listesini kullanarak haftanın günlerini depolayan bir sınıf bildirir <xref:System.DayOfWeek?displayProperty=fullName> . `get`Erişimci bir `DayOfWeek` günün değerini alır ve karşılık gelen tamsayıyı döndürür. Örneğin, `DayOfWeek.Sunday` 0 döndürür, `DayOfWeek.Monday` 1 döndürür ve bu şekilde devam eder.

:::code language="csharp" source="snippets/DayOfWeekIndexers/DayOfWeekCollection.cs":::

### <a name="consuming-example-3"></a>Örnek 3

:::code language="csharp" source="snippets/DayOfWeekIndexers/Program.cs":::

## <a name="robust-programming"></a>Güçlü programlama

Dizin oluşturucularının güvenliğinin ve güvenilirliğinin iyileşmesi için kullanabileceğiniz iki ana yol vardır:

- İstemci kodunun geçersiz bir dizin değeri geçirme olasılığını işlemek için bir tür hata işleme stratejisi eklediğinizden emin olun. Bu konunun önceki kısımlarında yer alan ilk örnekte, TempRecord sınıfı, istemci kodun dizin oluşturucuya geçirmeden önce girişi doğrulamasını sağlayan bir length özelliği sağlar. Hata işleme kodunu dizin oluşturucunun içine de yerleştirebilirsiniz. Bir Dizin Oluşturucu erişimcisinde oluşturduğunuz tüm özel durumları kullanıcılara belgelediğinizden emin olun.

- [Get](../../language-reference/keywords/get.md) ve [set](../../language-reference/keywords/set.md) erişimcilerinin erişilebilirliğini makul olacak şekilde kısıtlayıcı olarak belirleyin. Bu, `set` özellikle erişimcinin açısından önemlidir. Daha fazla bilgi için bkz. [erişimci erişilebilirliğini kısıtlama](../classes-and-structs/restricting-accessor-accessibility.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
