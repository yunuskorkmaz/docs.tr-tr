---
title: Temsilcilerde varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: 75b1f94a3fc7a59393d6a114a2b5346dd0534297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54657213"
---
# <a name="variance-in-delegates-c"></a>Temsilcilerde varyans (C#)
.NET framework 3.5, tüm temsilciler C# içindeki temsilci türleriyle yöntem imzalarının eşleştirilmesi için varyans desteği sunmuştur. Yalnızca imzalarının eşleştirilmesi içeren yöntemlerin yanı sıra temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip bir parametre kabul eden ya da daha fazla türetilmiş türler (kovaryans) döndüren yöntemler için atayabileceğiniz anlamına gelir temsilciler . Bu, hem genel hem de genel olmayan temsilcileri içerir.  
  
 Örneğin, iki sınıf ve iki temsilci olduğunda sahip aşağıdaki kodu düşünün: Genel ve genel olmayan.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleGenericDelegate<A, R>` türleri, bu temsilcileri için aşağıdaki yöntemlerden herhangi birini atayabilirsiniz.  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second first)  
{ return new First(); }  
  
// The return type is more derived.  
public static Second ASecondRSecond(Second second)  
{ return new Second(); }  
  
// The argument type is less derived.  
public static First AFirstRFirst(First first)  
{ return new First(); }  
  
// The return type is more derived   
// and the argument type is less derived.  
public static Second AFirstRSecond(First first)  
{ return new Second(); }  
```  
  
 Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasında örtülü dönüştürme gösterilmektedir.  
  
```csharp  
// Assigning a method with a matching signature   
// to a non-generic delegate. No conversion is necessary.  
SampleDelegate dNonGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a non-generic delegate.  
// The implicit conversion is used.  
SampleDelegate dNonGenericConversion = AFirstRSecond;  
  
// Assigning a method with a matching signature to a generic delegate.  
// No conversion is necessary.  
SampleGenericDelegate<Second, First> dGeneric = ASecondRFirst;  
// Assigning a method with a more derived return type   
// and less derived argument type to a generic delegate.  
// The implicit conversion is used.  
SampleGenericDelegate<Second, First> dGenericConversion = AFirstRSecond;  
```  
  
 Daha fazla örnek için bkz. [Temsilcilerde varyans (C#) kullanarak](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametreleri varyans  
 Böylece türlerini birbirinden gerektirdiği devralınırsa, genel tür parametrelerle belirtilen farklı türlere sahip genel temsilciler birbiriyle atanabilir .NET Framework 4 veya üzeri temsilciler arasında örtük dönüştürme etkinleştirebilirsiniz farkı.  
  
 Örtük dönüştürme etkinleştirmek için açıkça genel parametreler birlikte değişken olarak bir temsilci bildirmeniz gerekir veya kullanarak, değişken karşıtı `in` veya `out` anahtar sözcüğü.  
  
 Aşağıdaki kod örneği, bir genel birlikte değişen türde parametresi olan bir temsilci nasıl oluşturabileceğinizi gösterir.  
  
```csharp  
// Type T is declared covariant by using the out keyword.  
public delegate T SampleGenericDelegate <out T>();  
  
public static void Test()  
{  
    SampleGenericDelegate <String> dString = () => " ";  
  
    // You can assign delegates to each other,  
    // because the type T is declared covariant.  
    SampleGenericDelegate <Object> dObject = dString;             
}  
```  
  
 Tek farkı destek eşleştirilecek kullanırsanız birlikte yöntem imzaları temsilci türleri ve kullanmaz `in` ve `out` anahtar bulduğunuz bazen aynı lambda ifadeleri veya yöntemler ile temsilciler örneği oluşturabilir, ancak bunu yapamazsınız bir temsilci diğerine atayın.  
  
 Aşağıdaki kod örneğinde, `SampleGenericDelegate<String>` açıkça dönüştürülemez `SampleGenericDelegate<Object>`, ancak `String` devralan `Object`. Genel parametre olarak işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.  
  
```csharp  
public delegate T SampleGenericDelegate<T>();  
  
public static void Test()  
{  
    SampleGenericDelegate<String> dString = () => " ";  
  
    // You can assign the dObject delegate  
    // to the same lambda expression as dString delegate  
    // because of the variance support for   
    // matching method signatures with delegate types.  
    SampleGenericDelegate<Object> dObject = () => " ";  
  
    // The following statement generates a compiler error  
    // because the generic type T is not marked as covariant.  
    // SampleGenericDelegate <Object> dObject = dString;  
  
}  
```  
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework tür parametreleri varyant sahip genel temsilciler  
 .NET framework 4, varolan birçok genel temsilciler genel tür parametrelerinde varyansı başlanmıştır:  
  
-   `Action` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve <xref:System.Action%602>  
  
-   `Func` gelen temsilci <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve <xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Temsilci seçme  
  
-   <xref:System.Comparison%601> Temsilci seçme  
  
-   <xref:System.Converter%602> Temsilci seçme  
  
 Daha fazla bilgi ve örnekler için bkz. [işlev ve eylem genel temsilcileri (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Değişken türünde parametreler genel temsilciler bildirme  
 Genel temsilci birlikte değişken veya değişken karşıtı genel tür parametreleri, başvurulabilir olarak varsa bir *değişken Genel temsilci*.  
  
 Genel tür parametresi birlikte değişken Genel temsilci kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Birlikte değişken türünde yöntem bağımsız bir tür değil de, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, birlikte değişken genel bir temsilcinin nasıl belirtileceğini gösterir.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Genel tür parametresi değişken karşıtı Genel temsilci kullanarak bildirebilirsiniz `in` anahtar sözcüğü. Değişken karşıtı türü, yöntemin dönüş türü değil de, yalnızca bir tür yöntem bağımsız olarak kullanılabilir. Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl belirtileceğini gösterir.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`, `in`, ve `out` C# parametreleri varyant olarak işaretlenemez.  
  
 Farkı hem Kovaryans aynı temsilci, ancak farklı tür parametreleri için destek de mümkündür. Bu, aşağıdaki örnekte gösterilir.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Örnekleme ve bunları çağırırken değişken genel temsilciler  
 Örneği oluşturun ve yalnızca örneklemek ve sabit temsilciler çağırmak değişken temsilciler çağır. Aşağıdaki örnekte, temsilci bir lambda ifadesiyle başlatılır.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilciler birleştirme  
 Değişken temsilciler birleştirmemelisiniz değil. <xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüştürmeyi desteklemez ve temsilciler tam olarak aynı veri türünde olmasını bekliyor. Temsilcileri kullanarak ya da birleştirdiğinizde bu için bir çalışma zamanı özel durumuna neden olabilir <xref:System.Delegate.Combine%2A> yöntemi kullanarak veya `+` aşağıdaki kod örneğinde gösterildiği gibi işleci.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve başvuru türleri için genel tür parametrelerindeki varyansı  
 Varyans genel tür parametreleri için yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant<int>` için örtük olarak dönüştürülemez `DVariant<Object>` veya `DVariant<long>`tamsayı değer türü olduğundan.  
  
 Aşağıdaki örnek, bu farkı göstermektedir genel tür parametreleri değer türleri için desteklenmiyor.  
  
```csharp  
// The type T is covariant.  
public delegate T DVariant<out T>();  
  
// The type T is invariant.  
public delegate T DInvariant<T>();  
  
public static void Test()  
{  
    int i = 0;  
    DInvariant<int> dInt = () => i;  
    DVariant<int> dVariantInt = () => i;  
  
    // All of the following statements generate a compiler error  
    // because type variance in generic parameters is not supported  
    // for value types, even if generic type parameters are declared variant.  
    // DInvariant<Object> dObject = dInt;  
    // DInvariant<long> dLong = dInt;  
    // DVariant<Object> dVariantObject = dVariantInt;  
    // DVariant<long> dVariantLong = dVariantInt;              
}  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Genel Türler](~/docs/standard/generics/index.md)
- [İşlev ve eylem genel temsilcileri (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)
- [Nasıl yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
