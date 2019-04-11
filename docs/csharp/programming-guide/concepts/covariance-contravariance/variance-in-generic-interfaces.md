---
title: Variance in Generic Interfaces (C#)
ms.date: 04/10/2019
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 5874a39a57f85695bedc3d1ffa61adf19fcdbe37
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480787"
---
# <a name="variance-in-generic-interfaces-c"></a>Variance in Generic Interfaces (C#)

.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur. Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar. 

.NET Framework 4 ile başlamanızı, aşağıdaki arabirimlerinden değişken şunlardır:

- <xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)

- <xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)

- <xref:System.Linq.IQueryable%601> (T değişkendir)

- <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)

- <xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)

- <xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)

- <xref:System.IComparable%601> (T karşıtıdır)

.NET Framework 4.5 ile başlayarak, aşağıdaki arabirimlerinden değişken şunlardır:

- <xref:System.Collections.Generic.IReadOnlyList%601> (T karşıtıdır)

- <xref:System.Collections.Generic.IReadOnlyCollection%601> (T karşıtıdır)

Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar. Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`. `IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi. Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz. Bu aşağıdaki kod örneğinde gösterilir.

```csharp
IEnumerable<String> strings = new List<String>();
IEnumerable<Object> objects = strings;
```

Önceki .NET Framework sürümlerinde, bu kod bir derleme hatasına neden olur. C# ve `Option Strict` açıktır, Visual Basic'te. Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.

Kontravaryans, genel arabirimi parametre olarak belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir. Kontravaryans göstermek için oluşturduğunuz varsayılır bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı. `BaseComparer` Sınıfının Implements `IEqualityComparer<BaseClass>` arabirimi. Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi, artık değişken karşıtı, kullanabileceğiniz `BaseComparer` devralan sınıfların örneklerini karşılaştırmak için `BaseClass` sınıfı. Bu aşağıdaki kod örneğinde gösterilir.

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

Daha fazla örnek için bkz. [(C#) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).

Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir. Değer türleri varyansı desteklemez. Örneğin, `IEnumerable<int>` için örtük olarak dönüştürülemez `IEnumerable<object>`, tamsayı değer türü tarafından temsil edilir.

```csharp
IEnumerable<int> integers = new List<int>();
// The following statement generates a compiler error,
// because int is a value type.
// IEnumerable<Object> objects = integers;
```

Değişken arabirimleri uygulayan sınıflar yine de sabit olduğunu unutmamak önemlidir. Örneğin, ancak <xref:System.Collections.Generic.List%601> birlikte değişken arabirimi uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemez `List<Object>` için `List<String>`. Bu aşağıdaki kod örneğinde gösterilmiştir.

```csharp
// The following line generates a compiler error
// because classes are invariant.
// List<Object> list = new List<String>();

// You can use the interface object instead.
IEnumerable<Object> listObjects = new List<String>();
```

## <a name="see-also"></a>Ayrıca bkz.

- [Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)
- [Değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)
- [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
