---
title: readonly anahtar kelime - C# Başvuru
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: 03b0aa63eda3e7a9d8745baaa33479fd5e85b01b
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389053"
---
# <a name="readonly-c-reference"></a>readonly (C# Başvurusu)

Anahtar `readonly` kelime, dört bağlamda kullanılabilen bir değiştiricidir:

- Alan [bildiriminde,](#readonly-field-example) `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini belirtir. Yalnızca okunan bir alan, alan bildirimi ve oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.
  
  Bir `readonly` alan, yapıcı çıktıktan sonra atanamaz. Bu kuralın değer türleri ve başvuru türleri için farklı etkileri vardır:
  
  - Değer türleri doğrudan verilerini içerdiğinden, değer `readonly` türü olan bir alan değişmez.
  - Başvuru türleri verilerine bir başvuru içerdiğinden, `readonly` başvuru türü olan bir alanın her zaman aynı nesneye başvurması gerekir. Bu nesne değişmez değil. Değiştirici, `readonly` alanın başvuru türünün farklı bir örneğiyle değiştirilmesini önler. Ancak, değiştirici, alanın örnek verilerinin salt okunur alanı boyunca değiştirilmesini engellemez.

  > [!WARNING]
  > Mutable başvuru türü olan harici olarak görünür salt okunur alan içeren harici olarak görünen bir tür bir güvenlik açığı olabilir ve [ca2104](/visualstudio/code-quality/ca2104) uyarısını tetikleyebilir: "Yalnızca mutable başvuru türlerini okumayı bildirin."

- Bir `readonly struct` tür tanımında, `readonly` yapı türünün değişmez olduğunu gösterir. Daha fazla bilgi [ `readonly` ](../builtin-types/struct.md#readonly-struct) için Yapı [türleri](../builtin-types/struct.md) makalesinin yapı bölümüne bakın.
- Bir yapı türü içindeki bir `readonly` örnek üye bildiriminde, bir örnek üyenin yapının durumunu değiştirmediğini gösterir. Daha fazla bilgi için [Yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` örnek üyeler](../builtin-types/struct.md#readonly-instance-members) bölümüne bakın.
- Yöntem [ `ref readonly` dönüşünde,](#ref-readonly-return-example) `readonly` değiştirici yöntemin bir başvurudöndürür ve bu başvuru için yazı izin verilmez gösterir.

Ve `readonly struct` `ref readonly` bağlamlar C# 7.2'ye eklendi. `readonly`yapı üyeleri C# 8.0'a eklendi

## <a name="readonly-field-example"></a>Readonly alan örneği

Bu örnekte, sınıf oluşturucuya bir değer atanmış `ChangeYear`olsa bile, yöntemde alanın `year` değeri değiştirilemez:

[!code-csharp[Readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyField)]

Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:

- Değişken bildirimde başharfe geçtiğinde, örneğin:

  ```csharp
  public readonly int y = 5;
  ```

- Örnek alan bildirimini içeren sınıfın bir örnek oluşturucu.
- Statik alan bildirimini içeren sınıfın statik oluşturucuda.

Bu oluşturucu bağlamlar, bir `readonly` alanı dış [veya](out-parameter-modifier.md) [ref](ref.md) parametresi olarak geçirmenin geçerli olduğu tek bağlamdır.

> [!NOTE]
> Anahtar `readonly` kelime [const](const.md) anahtar kelime farklıdır. Bir `const` alan yalnızca alanın bildiriminde başlatılabilir. Alan `readonly` bildiriminde ve herhangi bir oluşturucuya birden çok kez atanabilir. Bu `readonly` nedenle, alanların kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, bir `const` alan derleme zamanı sabiti `readonly` olsa da, alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Önceki örnekte, aşağıdaki örnek gibi bir deyim kullanırsanız:

```csharp
p2.y = 66;        // Error
```

derleyici hata iletisini alırsınız:

**Yalnızca okunan bir alan atanamıyor (bir oluşturucu veya değişken baş harfi hariç)**

## <a name="ref-readonly-return-example"></a>Ref readonly dönüş örneği

A'daki `readonly` değiştirici, döndürülen başvurunun değiştirilemediğini `ref return` gösterir. Aşağıdaki örnek, kaynağına bir başvuru döndürür. Arayanların `readonly` kaynağı değiştiremediğini belirtmek için değiştirici kullanır:

[!code-csharp[readonly return example](~/samples/snippets/csharp/keywords/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Döndürülen tür bir `readonly struct`. olması gerekmez Tarafından `ref` döndürülebilen herhangi bir tür `ref readonly`.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Ayrıca dil belirtimi önerilerini de görebilirsiniz:

- [readonly ref ve readonly struct](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [readonly struct üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
- [const](const.md)
- [Alanlar](../../programming-guide/classes-and-structs/fields.md)
