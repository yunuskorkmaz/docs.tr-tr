---
title: Genel Arabirimlerde Varyans (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 71225814a11074f52e4937dec88ca5e27114d6c7
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179056"
---
# <a name="variance-in-generic-interfaces-c"></a>Genel Arabirimlerde Varyans (C#)

.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir. Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün. 

.NET Framework 4 ' te başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IEnumerable%601> (T değişkenle birlikte)

- <xref:System.Collections.Generic.IEnumerator%601> (T değişkenle birlikte)

- <xref:System.Linq.IQueryable%601> (T değişkenle birlikte)

- <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` değişkenle birlikte)

- <xref:System.Collections.Generic.IComparer%601> (T değişken karşıtı)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T değişken karşıtı)

- <xref:System.IComparable%601> (T değişken karşıtı)

.NET Framework 4,5 ' den başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IReadOnlyList%601> (T değişkenle birlikte)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T değişkenle birlikte)

Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar. Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`. @No__t-0 arabirimi `IEnumerable<Object>` arabirimini almıyor. Ancak `String` türü `Object` türünü devralınır ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

.NET Framework önceki sürümlerinde, bu kod, ' de `Option Strict` varsa, C# Visual Basic içinde derleme hatasına neden olur. Ancak artık, <xref:System.Collections.Generic.IEnumerable%601> arabirimi birlikte değişken olduğu için, önceki örnekte gösterildiği gibi `objects` yerine `strings` kullanabilirsiniz.

Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar. Değişken varyansı göstermek için, `BaseClass` sınıfının örneklerini karşılaştırmak üzere bir `BaseComparer` sınıfı oluşturduğunuzu varsayalım. `BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular. @No__t-0 arabirimi artık değişken karşıtı olduğundan, `BaseClass` sınıfını devraldığı sınıfların örneklerini karşılaştırmak için `BaseComparer` kullanabilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

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

Daha fazla örnek için bkz. [Genel Koleksiyonlar Için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md).

Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, `IEnumerable<int>` örtük olarak `IEnumerable<object>` ' e dönüştürülemez, çünkü tamsayılar bir değer türü ile temsil edilir.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir. Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini <xref:System.Collections.Generic.IEnumerable%601> ' i uygularsa, `List<String>` ' yi `List<Object>` ' e örtülü olarak dönüştüremezsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [Değişken genel arabirimler (C#) oluşturma](./creating-variant-generic-interfaces.md)
- [Genel arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde varyans (C#)](./variance-in-delegates.md)
