---
description: ReadOnly anahtar sözcüğü-C# başvurusu
title: ReadOnly anahtar sözcüğü-C# başvurusu
ms.date: 04/14/2020
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: b1bab5af18216fcef2162179493dbbb59e3470cf
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137181"
---
# <a name="readonly-c-reference"></a>readonly (C# Başvurusu)

`readonly`Anahtar sözcüğü dört bağlamda kullanılabilecek bir değiştiricisidir:

- Bir [alan bildiriminde](#readonly-field-example), `readonly` alana atamanın yalnızca bildirimin bir parçası olarak veya aynı sınıftaki bir oluşturucuda gerçekleşebileceğini gösterir. Salt okunur bir alan, alan bildirimi ve Oluşturucu içinde birden çok kez atanabilir ve yeniden atanabilir.
  
  `readonly`Oluşturucu çıktıktan sonra bir alan atanamaz. Bu kural, değer türleri ve başvuru türleri için farklı etkilere sahiptir:
  
  - Değer türleri doğrudan verilerini içerdiğinden, bir değer türü olan bir alan  `readonly` sabittir.
  - Başvuru türleri, verilerine yönelik bir başvuru içerdiğinden, başvuru türü olan bir alan `readonly` her zaman aynı nesneye başvurmalıdır. Bu nesne sabit değildir. `readonly`Değiştirici, alanın farklı bir başvuru türü örneğiyle değiştirilmesini önler. Ancak, değiştirici alanın örnek verilerinin salt okunurdur alanı aracılığıyla değiştirilmesini engellemez.

  > [!WARNING]
  > Değişebilir bir başvuru türü olan bir dışarıdan görünür salt okunurdur alanı içeren dışarıdan görünen bir tür, bir güvenlik açığı olabilir ve uyarı [CA2104](/visualstudio/code-quality/ca2104) : "salt okuma kesilebilir başvuru türleri bildiremiyor" olarak tetiklenebilir.

- Bir `readonly struct` tür tanımında, `readonly` yapı türünün sabit olduğunu gösterir. Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` struct](../builtin-types/struct.md#readonly-struct) bölümüne bakın.
- Yapı türü içindeki bir örnek üye bildiriminde, bir `readonly` örnek üyesinin yapının durumunu değiştirmediğini belirtir. Daha fazla bilgi için [yapı türleri](../builtin-types/struct.md) makalesinin [ `readonly` örnek Üyeler](../builtin-types/struct.md#readonly-instance-members) bölümüne bakın.
- Bir [ `ref readonly` Yöntem](#ref-readonly-return-example)döndürüldüğünde, `readonly` değiştirici yöntemin bir başvuru döndürdüğünü ve bu başvuruya yazma izni verilmediğini gösterir.

`readonly struct`Ve `ref readonly` bağlamları C# 7,2 ' ye eklenmiştir. `readonly` C# 8,0 ' de yapı üyeleri eklendi

## <a name="readonly-field-example"></a>ReadOnly alan örneği

Bu örnekte, alan değeri, `year` `ChangeYear` sınıf oluşturucusunda bir değer atanmış olsa da, yönteminde değiştirilemez:

[!code-csharp[Readonly Field example](snippets/ReadonlyKeywordExamples.cs#ReadonlyField)]

Bir `readonly` alana yalnızca aşağıdaki bağlamlarda bir değer atayabilirsiniz:

- Bildirimde bir değişken başlatıldığında, örneğin:

  ```csharp
  public readonly int y = 5;
  ```

- Örnek alan bildirimini içeren sınıfın örnek oluşturucusunda.
- Statik alan bildirimini içeren sınıfın statik oluşturucusunda.

Bu Oluşturucu bağlamları aynı zamanda bir `readonly` alanı [Out](out-parameter-modifier.md) veya [ref](ref.md) parametresi olarak geçirmek için geçerli olduğu tek bağlamlardır.

> [!NOTE]
> `readonly`Anahtar sözcüğü [const](const.md) anahtar sözcüğünden farklıdır. Bir `const` alan yalnızca alanın bildiriminde başlatılabilir. Alan `readonly` bildiriminde ve herhangi bir oluşturucuda bir alana birden çok kez atanabilir. Bu nedenle, `readonly` alan, kullanılan oluşturucuya bağlı olarak farklı değerlere sahip olabilir. Ayrıca, bir `const` alan bir derleme zamanı sabiti olsa da, `readonly` Bu alan aşağıdaki örnekte olduğu gibi çalışma zamanı sabitleri için kullanılabilir:
>
> ```csharp
> public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;
> ```

[!code-csharp[Initialize readonly Field example](snippets/ReadonlyKeywordExamples.cs#InitReadonlyField)]

Yukarıdaki örnekte, aşağıdaki örnekte olduğu gibi bir ifade kullanıyorsanız:

```csharp
p2.y = 66;        // Error
```

Derleyici hata iletisini alırsınız:

**Salt okunur bir alana atama yapılamaz (Oluşturucu veya değişken başlatıcı içinde olması dışında)**

## <a name="ref-readonly-return-example"></a>Ref ReadOnly dönüş örneği

`readonly`Bir üzerinde değiştirici, `ref return` döndürülen başvurunun değiştirilemeyeceğini gösterir. Aşağıdaki örnek, kaynağına bir başvuru döndürür. `readonly`Çağıranların kaynağı değiştiremeyeceğini belirtmek için değiştiricisini kullanır:

[!code-csharp[readonly return example](snippets/ReadonlyKeywordExamples.cs#ReadonlyReturn)]

Döndürülen türün bir olması gerekmez `readonly struct` . Tarafından döndürülebilecek herhangi bir tür `ref` tarafından döndürülebilecek `ref readonly` .

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

Dil belirtimi tekliflerini de görebilirsiniz:

- [ReadOnly ref ve ReadOnly yapısı](~/_csharplang/proposals/csharp-7.2/readonly-ref.md)
- [ReadOnly struct üyeleri](~/_csharplang/proposals/csharp-8.0/readonly-instance-members.md)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [const](const.md)
- [Alanlar](../../programming-guide/classes-and-structs/fields.md)
