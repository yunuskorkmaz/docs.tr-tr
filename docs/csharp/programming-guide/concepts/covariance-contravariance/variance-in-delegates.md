---
title: Temsilcilerde varyans (C#)
description: .NET Framework ' deki varyans desteğinin, tüm Temsilcilerde temsilci türleriyle Yöntem imzalarını nasıl eşleşeceğini öğrenin.
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: ef57a7fa7feaef98a47822e3f1c9242d0205932d
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/23/2020
ms.locfileid: "87105658"
---
# <a name="variance-in-delegates-c"></a>Temsilcilerde varyans (C#)
.NET Framework 3,5, C# ' deki tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için fark desteğini kullanıma sunmuştur. Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş tür (değişken varyans) içeren parametreleri kabul eden yöntemler için atama yaptığınız anlamına gelir. Bu hem genel hem de genel olmayan temsilcileri içerir.  
  
 Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 `SampleDelegate`Veya türlerinin temsilcilerini oluşturduğunuzda `SampleGenericDelegate<A, R>` , aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.  
  
```csharp  
// Matching signature.  
public static First ASecondRFirst(Second second)  
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
  
 Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi gösterir.  
  
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
  
 Daha fazla örnek için bkz. [Temsilciler Içinde varyans kullanma (c#)](./using-variance-in-delegates.md) ve [Func ve ACTION genel temsilcileri için varyans kullanma (c#)](./using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametrelerindeki varyans  
 .NET Framework 4 veya sonraki sürümlerde temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz; böylece türler, genel tür parametreleri tarafından belirtilen farklı türlere sahip olan genel temsilcilerin birbirini fark eden her bir öğeden devralınabileceği her birine atanabilir.  
  
 Örtük dönüştürmeyi etkinleştirmek için, `in` veya anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini birlikte değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir `out` .  
  
 Aşağıdaki kod örneği, birlikte değişken genel tür parametresine sahip olan bir temsilciyi nasıl oluşturabileceğiniz gösterilmektedir.  
  
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
  
 Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen aynı lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir temsilciyi başka bir temsilciye atayamazsınız.  
  
 Aşağıdaki kod örneğinde, `SampleGenericDelegate<String>` açıkça öğesine dönüştürülemez `SampleGenericDelegate<Object>` , ancak `String` devralır `Object` . Genel parametreyi anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz `T` `out` .  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-net"></a>.NET 'te değişken tür parametrelerine sahip genel Temsilciler

.NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:  
  
- `Action`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Action%601> ve<xref:System.Action%602>  
  
- `Func`ad alanından temsilciler, <xref:System> Örneğin <xref:System.Func%601> ve<xref:System.Func%602>  
  
- <xref:System.Predicate%601>Temsilci  
  
- <xref:System.Comparison%601>Temsilci  
  
- <xref:System.Converter%602>Temsilci  
  
 Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel Temsilcilerde değişken tür parametreleri bildirme  
 Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi*olarak adlandırılır.  
  
 Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz `out` . Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz `in` . Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir. Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> `ref`, `in` ve `out` C# içindeki parametreler değişken olarak işaretlenemez.  
  
 Aynı temsilci, ancak farklı tür parametreleri için hem varyansı hem de kovaryansı desteklemek de mümkündür. Bu, aşağıdaki örnekte gösterilir.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>VARIANT genel temsilcileri örnekleme ve çağırma  
 Sabit temsilcileri örneklediğinizde ve çağırdığınızda değişken temsilcileri örnek oluşturabilir ve çağırabilirsiniz. Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından oluşturulur.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilcileri birleştirme  

Değişken temsilcileri birleştirmeyin. <xref:System.Delegate.Combine%2A>Yöntem, değişken temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler. Bu, <xref:System.Delegate.Combine%2A> `+` Aşağıdaki kod örneğinde gösterildiği gibi, veya işlecini kullanarak temsilcileri birleştirdiğinizde bir çalışma zamanı özel durumuna yol açabilir.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve başvuru türleri için genel tür parametrelerinin varyansı  
 Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant<int>` `DVariant<Object>` tamsayı bir değer türü olduğundan, örtülü olarak veya `DVariant<long>` türüne dönüştürülemez.  
  
 Aşağıdaki örnek, genel tür parametrelerinin farkının değer türleri için desteklenmediğini gösterir.  
  
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

- [Genel Türler](../../../../standard/generics/index.md)
- [Func ve eylem genel temsilcileri için varyans kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
- [Temsilcileri birleştirme (çok noktaya yayın temsilcileri)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
