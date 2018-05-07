---
title: Genel arabirimler (C#) varyans
ms.date: 07/20/2015
ms.assetid: 4828a8f9-48c0-4128-9749-7fcd6bf19a06
ms.openlocfilehash: fdcfd13a645ffc9b596beed65b74f8e593c642f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="variance-in-generic-interfaces-c"></a>Genel arabirimler (C#) varyans
.NET framework 4 birkaç mevcut genel arabirimler sapma desteği sunmuştur. Bu arabirimleri uygulayan sınıflar örtük dönüştürme sapma desteği sağlar. Aşağıdaki arabirimleri şimdi değişken şunlardır:  
  
-   <xref:System.Collections.Generic.IEnumerable%601> (T değişkendir)  
  
-   <xref:System.Collections.Generic.IEnumerator%601> (T değişkendir)  
  
-   <xref:System.Linq.IQueryable%601> (T değişkendir)  
  
-   <xref:System.Linq.IGrouping%602> (`TKey` ve `TElement` eşdeğişken olan)  
  
-   <xref:System.Collections.Generic.IComparer%601> (T karşıtıdır)  
  
-   <xref:System.Collections.Generic.IEqualityComparer%601> (T karşıtıdır)  
  
-   <xref:System.IComparable%601> (T karşıtıdır)  
  
 Kovaryans arabirimi genel tür parametresi tarafından tanımlanan daha fazla türetilmiş bir dönüş türüne sahip bir yöntem izin verir. Kovaryans özelliği göstermek için bu genel arabirimler göz önünde bulundurun: `IEnumerable<Object>` ve `IEnumerable<String>`. `IEnumerable<String>` Arabirimi devralmaz `IEnumerable<Object>` arabirimi. Ancak, `String` türü devral `Object` türü ve bazı durumlarda bu arabirimleri nesnelerin birbirlerine atamak isteyebilirsiniz. Bu, aşağıdaki kod örneğinde gösterilir.  
  
```csharp  
IEnumerable<String> strings = new List<String>();  
IEnumerable<Object> objects = strings;  
```  
  
 .NET Framework önceki sürümlerinde, bu kod derleme hatası C# ile neden `Option Strict On`. Ancak artık kullanabilirsiniz `strings` yerine `objects`, çünkü önceki örnekte gösterildiği gibi <xref:System.Collections.Generic.IEnumerable%601> arabirimidir eşdeğişken.  
  
 Değişken karşıtı arabirimi genel parametresi tarafından belirtilenden daha az türetilmiş bağımsız değişken türleri için bir yöntem izin verir. Değişken karşıtı göstermek için oluşturduğunuzu varsayalım bir `BaseComparer` örneklerini karşılaştırmak için sınıf `BaseClass` sınıfı. `BaseComparer` Uygulayan sınıf `IEqualityComparer<BaseClass>` arabirimi. Çünkü <xref:System.Collections.Generic.IEqualityComparer%601> arabirimi şimdi karşıtı, kullanabileceğiniz `BaseComparer` devral sınıfların örneklerini Karşılaştırılacak `BaseClass` sınıfı. Bu, aşağıdaki kod örneğinde gösterilir.  
  
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
  
 Daha fazla örnek için bkz: [(C#) genel koleksiyonlar için arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md).  
  
 Genel arabirimlerde varyans yalnızca başvuru türleri için desteklenir. Türlerin varyans desteklemez. Örneğin, `IEnumerable<int>` örtük olarak dönüştürülemiyor `IEnumerable<object>`, tamsayı bir değer türü ile temsil edilir.  
  
```csharp  
IEnumerable<int> integers = new List<int>();  
// The following statement generates a compiler errror,  
// because int is a value type.  
// IEnumerable<Object> objects = integers;  
```  
  
 Değişken arabirimler uygulayan sınıflar hala değişmez olduğunu unutmamak önemlidir. Örneğin, ancak <xref:System.Collections.Generic.List%601> eşdeğişken arabirimini uygulayan <xref:System.Collections.Generic.IEnumerable%601>, örtük olarak dönüştürülemiyor `List<Object>` için `List<String>`. Bu aşağıdaki kod örneğinde gösterilmiştir.  
  
```csharp  
// The following line generates a compiler error  
// because classes are invariant.  
// List<Object> list = new List<String>();  
  
// You can use the interface object instead.  
IEnumerable<Object> listObjects = new List<String>();  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel koleksiyonlar için (C#) arabirimlerde varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-interfaces-for-generic-collections.md)  
 [Değişken genel arabirimler oluşturma (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/creating-variant-generic-interfaces.md)  
 [Genel Arabirimler](../../../../standard/generics/interfaces.md)  
 [Temsilcilerde varyans (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-delegates.md)
