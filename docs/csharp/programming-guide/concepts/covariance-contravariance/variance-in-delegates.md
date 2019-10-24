---
title: Temsilcilerde varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: a65b2fb84e2eae57eecaf5307ca76fbce412d44c
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772048"
---
# <a name="variance-in-delegates-c"></a>Temsilcilerde varyans (C#)
.NET Framework 3,5, içindeki C#tüm Temsilcilerde temsilci türleriyle eşleşen yöntem imzaları için varyans desteği getirmiştir. Bu, yalnızca eşleşen imzalara sahip yöntemlerin değil, aynı zamanda daha fazla türetilmiş tür (Kovaryans) döndüren veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (değişken varyans) döndüren parametreleri kabul eden yöntemlere atayabileceğiniz anlamına gelir. . Bu hem genel hem de genel olmayan temsilcileri içerir.  
  
 Örneğin, iki sınıfı ve iki temsilciyi olan aşağıdaki kodu düşünün: genel ve genel olmayan.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 @No__t_0 veya `SampleGenericDelegate<A, R>` türlerinin temsilcilerini oluşturduğunuzda, aşağıdaki yöntemlerden herhangi birini bu temsilcilere atayabilirsiniz.  
  
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
  
 Daha fazla örnek için bkz. [Temsilcilerde varyans kullanmaC#()](./using-variance-in-delegates.md) ve [Func ve ACTION Genel Temsilciler (C#) için varyans kullanma](./using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametrelerindeki varyans  
 .NET Framework 4 veya sonraki sürümlerde temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz. bu sayede, türler her biri için gerekli olduğu gibi, genel tür parametreleri tarafından belirtilen farklı türlere sahip genel temsilcilerin birbirlerine atanabilmesini sağlar. denetlemesini.  
  
 Örtük dönüştürmeyi etkinleştirmek için, `in` veya `out` anahtar sözcüğünü kullanarak bir temsilcinin genel parametrelerini ortak değişken veya değişken karşıtı olarak açıkça bildirmeniz gerekir.  
  
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
  
 Yöntem imzalarını temsilci türleriyle eşleştirmek için yalnızca varyans desteğini kullanırsanız ve `in` ve `out` anahtar sözcüklerini kullanmıyorsanız, bazen özdeş lambda ifadeleri veya yöntemlerine sahip temsilciler örnekleyebilirsiniz, ancak bir tane atayamazsınız başka bir temsilci.  
  
 Aşağıdaki kod örneğinde, `String` `Object` devramla birlikte `SampleGenericDelegate<String>` açıkça `SampleGenericDelegate<Object>` dönüştürülemiyor. Genel parametre `T` `out` anahtar sözcüğüyle işaretleyerek bu sorunu çözebilirsiniz.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework değişken tür parametrelerine sahip genel Temsilciler  
 .NET Framework 4, çeşitli genel temsilcilerde genel tür parametrelerine yönelik varyans desteği getirmiştir:  
  
- <xref:System> ad alanından temsilciler `Action`, örneğin <xref:System.Action%601> ve <xref:System.Action%602>  
  
- <xref:System> ad alanından temsilciler `Func`, örneğin <xref:System.Func%601> ve <xref:System.Func%602>  
  
- @No__t_0 temsilcisi  
  
- @No__t_0 temsilcisi  
  
- @No__t_0 temsilcisi  
  
 Daha fazla bilgi ve örnek için bkz. [Func ve eylem genel temsilcileri Için varyans kullanmaC#()](./using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel Temsilcilerde değişken tür parametreleri bildirme  
 Genel bir temsilcinin birlikte değişken veya değişken karşıtı genel tür parametreleri varsa, bu, *VARIANT genel temsilcisi*olarak adlandırılır.  
  
 @No__t_0 anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi ortak değişkeni bildirebilirsiniz. Covaryant türü, yöntem bağımsız değişkenlerinin türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, bir covaryant genel temsilcisinin nasıl bildirilemeyeceğini gösterir.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 @No__t_0 anahtar sözcüğünü kullanarak genel bir temsilci içinde genel bir tür parametresi değişken değişkeni bildirebilirsiniz. Değişken karşıtı türü, yöntem dönüş türü olarak değil, yalnızca Yöntem bağımsız değişkenlerinin türü olarak kullanılabilir. Aşağıdaki kod örneği, bir değişken karşıtı genel temsilcinin nasıl bildirilemeyeceğini gösterir.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> içindeki C# `ref`, `in` ve `out` parametreleri değişken olarak işaretlenemez.  
  
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
 Değişken temsilcileri birleştirmemelisiniz. @No__t_0 yöntemi, VARIANT temsilci dönüştürmeyi desteklemez ve temsilcilerin tamamen aynı türde olmasını bekler. Bu, aşağıdaki kod örneğinde gösterildiği gibi <xref:System.Delegate.Combine%2A> yöntemi kullanılarak veya `+` işlecini kullanarak temsilcileri birleştirdiğinizde çalışma zamanı özel durumuna yol açabilir.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve başvuru türleri için genel tür parametrelerinin varyansı  
 Genel tür parametrelerinin varyansı yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant<int>` örtük olarak `DVariant<Object>` veya `DVariant<long>` dönüştürülemez, çünkü tamsayı bir değer türüdür.  
  
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
- [Nasıl yapılır: temsilcileri birleştirme (çok noktaya yayın temsilcileri)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
