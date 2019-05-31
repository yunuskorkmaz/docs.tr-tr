---
title: New işleci - C# başvurusu
ms.custom: seodec18
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 409a5307eaacd2eac865e2882cc7228521260dbe
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66421879"
---
# <a name="new-operator-c-reference"></a>New işleci (C# Başvurusu)

Nesneleri oluşturmak ve oluşturucuları çağırmak için kullanılır. Örneğin:

```csharp
Class1 obj  = new Class1();
```

Ayrıca, anonim türlerin örneklerini oluşturmak için kullanılır:

```csharp
var query = from cust in customers
            select new { Name = cust.Name, Address = cust.PrimaryAddress };
```

`new` İşleci değer türleri için parametresiz oluşturucu çağırmak için de kullanılır. Örneğin:

```csharp
int i = new int();
```

Önceki deyim içinde `i` değerine ayarlanır `0`, türü için varsayılan değer olan `int`. Deyimi aşağıdaki aynı etkiye sahiptir:

```csharp
int i = 0;
```

Varsayılan değerlerin tam listesi için bkz. [varsayılan değerler tablosu](default-values-table.md).

Parametresiz bir oluşturucu için bildirmek için bir hata olduğunu unutmayın bir [yapı](struct.md) her değer türü örtük olarak genel parametresiz oluşturucusu olmadığından. Parametreli oluşturucular ilk değerleri ayarlamak için bir yapı türü bildirmek mümkündür, ancak bu yalnızca varsayılan dışındaki değerler gerekiyorsa gereklidir.

Hem yapılar gibi değer türü nesneler ve sınıflar gibi başvuru türü nesneleri otomatik olarak edilir, ancak içeren bağlamları kaldırıldığında, bu başvuru türü nesneler çöp tarafından yok ise değer türü nesneler yok edilir Toplayıcı bunları son başvuruysa kaldırıldıktan sonra belirtilmeyen bir zaman. Dosya tanıtıcıları veya ağ bağlantıları gibi kaynakları içeren türleri için içerdikleri kaynakları hemen serbest emin olmak için belirleyici temizleme kullanmayı tercih edilir. Daha fazla bilgi için [using deyimi](using-statement.md).

`new` İşleci aşırı yüklenemez.

Varsa `new` işleci başarısız bellek ayırmaya, özel durum oluşturduğunda <xref:System.OutOfMemoryException>.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, bir `struct` nesnesi ve bir sınıf nesnesi oluşturulur ve kullanılarak başlatılan `new` işleci ve ardından değerler atanır. Varsayılan ve atanan değerleri görüntülenir.

[!code-csharp[csrefKeywordsOperator#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#7)]

Varsayılan değer bir dize örneği bildiriminde `null`. Bu nedenle, bu görüntülenmez.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [new](new.md)
- [Anonim Tipler](../../programming-guide/classes-and-structs/anonymous-types.md)
