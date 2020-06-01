---
title: Genel Arabirimlerde Varyans (C#)
ms.date: 06/06/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: ea5d3d35bc9ee438263707efd16829b6217a1968
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241337"
---
# <a name="variance-in-generic-interfaces-c"></a>Genel Arabirimlerde Varyans (C#)

.NET Framework 4, mevcut birçok genel arabirim için varyans desteği getirmiştir. Varyans desteği, bu arabirimleri uygulayan sınıfların örtük dönüştürülmesini mümkün.

.NET Framework 4 ' te başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IEnumerable%601>(T değişkenle birlikte)

- <xref:System.Collections.Generic.IEnumerator%601>(T değişkenle birlikte)

- <xref:System.Linq.IQueryable%601>(T değişkenle birlikte)

- <xref:System.Linq.IGrouping%602>( `TKey` ve `TElement` değişkenle birlikte)

- <xref:System.Collections.Generic.IComparer%601>(T değişken karşıtı)

- <xref:System.Collections.Generic.IEqualityComparer%601>(T değişken karşıtı)

- <xref:System.IComparable%601>(T değişken karşıtı)

.NET Framework 4,5 ' den başlayarak, aşağıdaki arabirimler değişkendir:

- <xref:System.Collections.Generic.IReadOnlyList%601>(T değişkenle birlikte)

- <xref:System.Collections.Generic.IReadOnlyCollection%601>(T değişkenle birlikte)

Kovaryans, bir metodun, arabirimin genel tür parametresiyle tanımlananla daha türetilmiş bir dönüş türüne sahip olmasını sağlar. Kovaryans özelliğini göstermek için şu genel arabirimleri göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>` . `IEnumerable<String>`Arabirim, `IEnumerable<Object>` arabirimini almıyor. Ancak, `String` tür devralınır `Object` ve bazı durumlarda bu arabirimlerin nesnelerini birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

.NET Framework önceki sürümlerinde, bu kod C# ' de derleme hatasına ve açık ise Visual Basic ' a neden olur `Option Strict` . Ancak, bu, `strings` `objects` Önceki örnekte gösterildiği gibi yerine kullanabilirsiniz, çünkü <xref:System.Collections.Generic.IEnumerable%601> arabirim değişkenle birlikte değişkendir.

Değişken Varyans, bir metodun, arabirimin genel parametresiyle belirtilenden daha az türetilmiş bağımsız değişken türlerine sahip olmasını sağlar. Değişken varyansı göstermek için, `BaseComparer` sınıfının örneklerini karşılaştırmak üzere bir sınıf oluşturduğunuzu varsayalım `BaseClass` . `BaseComparer` sınıfı, `IEqualityComparer<BaseClass>` arabirimini uygular. Arabirim artık değişken karşıtı olduğundan <xref:System.Collections.Generic.IEqualityComparer%601> , `BaseComparer` sınıfı miras alan sınıfların örneklerini karşılaştırmak için kullanabilirsiniz `BaseClass` . Bu, aşağıdaki kod örneğinde gösterilmiştir.

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

Genel Arabirimlerde Varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, `IEnumerable<int>` `IEnumerable<object>` tamsayılar bir değer türü tarafından temsil edildiği için örtük olarak öğesine dönüştürülemez.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Ayrıca, VARIANT arabirimlerini uygulayan sınıfların hala sabit olduğunu unutmamak önemlidir. Örneğin, <xref:System.Collections.Generic.List%601> covaryant arabirimini uygular <xref:System.Collections.Generic.IEnumerable%601> , ancak öğesini örtülü olarak dönüştüremezsiniz `List<String>` `List<Object>` . Bu, aşağıdaki kod örneğinde gösterilmiştir.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel Koleksiyonlar için Arabirimlerde Varyans kullanma (C#)](./using-variance-in-interfaces-for-generic-collections.md)
- [VARIANT genel arabirimleri oluşturma (C#)](./creating-variant-generic-interfaces.md)
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde varyans (C#)](./variance-in-delegates.md)
