---
title: Variance in Generic Interfaces (C#)
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: 11d0c8665412bb513cb68d58203a454b7c97e052
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009329"
---
# <a name="variance-in-generic-interfaces-c"></a>Variance in Generic Interfaces (C#)
.NET framework 4, çeşitli genel arabirimlerin mevcut sapma desteği sunmuştur. Bu arabirimleri uygulayan sınıfların örtük dönüştürme varyansı desteği sağlar. Aşağıdaki arabirimlerinden şimdi değişken şunlardır:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)  
  
-   <xref:System.Linq.IQueryable%601> (T değişkendir)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` birlikte değişken olduğu)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)  
  
-   <xref:System.IComparable%601> (T karşıtıdır)  
  
 Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem sağlar. Kovaryans özelliği açıklamak için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`. `IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi. Ancak, `String` türü devralma `Object` türü ve bazı durumlarda bu arabirimler nesnelerin birbirleriyle atamak isteyebilirsiniz. Bu aşağıdaki kod örneğinde gösterilir.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 Önceki .NET Framework sürümlerinde bu kodu C# ile bir derleme hatasına neden olur. `Option Strict On`. Ancak artık kullanabilirsiniz `strings` yerine `objects`için önceki örnekte gösterilen şekilde <xref:System.Collections.Generic.IEnumerable%601> arabirimidir birlikte değişken.  
  
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
// The following statement generates a compiler errror,  
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
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
- [Değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
- [Genel Arabirimler](../../../../standard/generics/interfaces.md)  
- [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
