---
title: Genel Arabirimlerde Varyans (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 2020ea54734724de775192a1a438413a73003d17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169668"
---
# <a name="variance-in-generic-interfaces-c"></a>Genel Arabirimlerde Varyans (C#)

.NET Framework 4, varolan birkaç genel arabirim için varyans desteği sundu. Varyans desteği, bu arabirimleri uygulayan sınıfların örtülü olarak dönüştürülmesini sağlar.

.NET Framework 4 ile başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IEnumerable%601>(T eşdeğişkendir)

- <xref:System.Collections.Generic.IEnumerator%601>(T eşdeğişkendir)

- <xref:System.Linq.IQueryable%601>(T eşdeğişkendir)

- <xref:System.Linq.IGrouping%602>(`TKey` `TElement` ve eşdeğişkendir)

- <xref:System.Collections.Generic.IComparer%601>(T zıt değişkendir)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T zıt değişkendir)

- <xref:System.IComparable%601>(T zıt değişkendir)

.NET Framework 4.5 ile başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T eşdeğişkendir)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T eşdeğişkendir)

Covariance, bir yöntemin arabirimin genel türü parametresi tarafından tanımlanandan daha türetilmiş bir iade türüne sahip olmasını sağlar. Tutarlılık özelliğini göstermek için, bu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`. `IEnumerable<Object>` Arabirim, `IEnumerable<String>` arabirimi devralmaz. Ancak, `String` `Object` tür türü devralmak yok ve bazı durumlarda bu arabirimlerin nesneleri birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

.NET Framework'ün önceki sürümlerinde, bu kod C#'da `Option Strict` ve üzerindeyse Visual Basic'te bir derleme hatasına neden olur. Ancak `strings` `objects`şimdi, <xref:System.Collections.Generic.IEnumerable%601> önceki örnekte gösterildiği gibi, arabirim ortak olduğundan, bunun yerine kullanabilirsiniz.

Kontravariance, arabirimin genel parametresi tarafından belirtilenden daha az türemiş bağımsız değişken türlerine sahip bir yönteme izin verir. Kontraşeyi göstermek için, sınıfın örneklerini `BaseComparer` karşılaştırmak için bir `BaseClass` sınıf oluşturduğunuzu varsayalım. `BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular. <xref:System.Collections.Generic.IEqualityComparer%601> Arabirim artık karşıt olduğundan, `BaseComparer` `BaseClass` sınıfı devralan sınıf örneklerini karşılaştırmak için kullanabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
// Simple hierarchy of classes.
class BaseClass { }
class DerivedClass : BaseClass { }

// Comparer class.
class BaseComparer : IEqualityComparer<BaseClass>
{
    public int GetHashCode(BaseClass baseInstance)
    {
        return baseInstance.GetHashCode();
    }
    public bool Equals(BaseClass x, BaseClass y)
    {
        return x == y;
    }
}
class Program
{
    static void Test()
    {
        IEqualityComparer<BaseClass> baseComparer = new BaseComparer();

        // Implicit conversion of IEqualityComparer<BaseClass> to
        // IEqualityComparer<DerivedClass>.
        IEqualityComparer<DerivedClass> childComparer = baseComparer;
    }
}
```

Daha fazla örnek için bkz: [Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md).

Genel arabirimlerdeki varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, `IEnumerable<int>` tamsayılar bir değer `IEnumerable<object>`türü tarafından temsil edildiğinden, dolaylı olarak dönüştürülemez.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Varyant arabirimleri uygulayan sınıfların hala değişmez olduğunu da unutmamak önemlidir. Örneğin, ortak <xref:System.Collections.Generic.List%601> değişken <xref:System.Collections.Generic.IEnumerable%601>arabirimi uygulasa da, `List<String>` `List<Object>`örtülü olarak . Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Koleksiyonlar için Arabirimlerde Varyans Kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [Varyant Genel Arabirimler Oluşturma (C#)](./creating-variant-generic-interfaces.md)
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde Varyans (C#)](./variance-in-delegates.md)
