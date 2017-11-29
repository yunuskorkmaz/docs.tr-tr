---
title: Temsilcilerde varyans (C#)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6eacc9f6ac815e01c446f7cdea6026904ad2ba90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="variance-in-delegates-c"></a>Temsilcilerde varyans (C#)
.NET framework 3.5 yöntem imzaları bulunan tüm temsilcileri C# temsilci türleriyle eşleşen farkı desteği sunmuştur. Yalnızca imzalar eşleşen yöntemleri, aynı zamanda daha fazla türetilmiş tür (kovaryans) veya temsilci türü tarafından belirtilenden daha az türetilmiş türler (kontravaryans) sahip parametreleri kabul döndüren yöntemler için atayabilirsiniz Bunun anlamı temsilciler . Bu, hem genel hem de genel olmayan temsilciler içerir.  
  
 Örneğin, iki sınıf ve iki temsilciler aşağıdaki kodu göz önünde bulundurun: Genel ve genel olmayan.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 Temsilciler, oluşturduğunuzda `SampleDelegate` veya `SampleGenericDelegate<A, R>` türleri, aşağıdaki yöntemlerden birini bu temsilcileri atayabilirsiniz.  
  
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
  
 Aşağıdaki kod örneğinde yöntem imzası ve temsilci türü arasında örtük dönüşüm gösterilmektedir.  
  
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
  
 Daha fazla örnek için bkz: [Temsilcilerde varyans (C#) kullanarak](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md) ve [işlev ve eylem genel temsilciler (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
## <a name="variance-in-generic-type-parameters"></a>Genel tür parametreleri varyans  
 Böylece türlerini birbirinden gerektirdiği şekilde devralınırsa, genel tür parametresi tarafından belirtilen farklı türlerine sahip genel temsilciler birbirine atanabilir .NET Framework 4 veya üstü temsilciler arasında örtük dönüştürmeye etkinleştirebilirsiniz sapması.  
  
 Örtük dönüştürme etkinleştirmek için açıkça bir temsilci eşdeğişken olarak genel parametreleri bildirmeniz gerekir veya kullanarak karşıtı `in` veya `out` anahtar sözcüğü.  
  
 Aşağıdaki kod örneğinde eşdeğişken genel tür parametresi var. bir temsilci nasıl oluşturabileceğinizi gösterir.  
  
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
  
 Eşleştirilecek tek farkı destek kullanırsanız, yöntemi imzalarla temsilci türleri'yı ve kullanmayın `in` ve `out` anahtar sözcüklerini bulduğunuz bazen aynı lambda ifadeleri veya yöntemleri ile temsilciler örneğini oluşturabilirsiniz, ancak yapamazsınız bir temsilci diğerine atayın.  
  
 Aşağıdaki kod örneğinde, `SampleGenericDelegate<String>` açıkça dönüştürülemiyor `SampleGenericDelegate<Object>`, ancak `String` devralır `Object`. Genel parametresini işaretleyerek bu sorunu düzeltebilirsiniz `T` ile `out` anahtar sözcüğü.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Framework değişken sahip genel temsilciler tür parametreleri  
 .NET framework 4 birkaç mevcut genel temsilciler genel tür parametreleri sapma desteği sunulur:  
  
-   `Action`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Action%601> ve<xref:System.Action%602>  
  
-   `Func`gelen Temsilciler <xref:System> ad alanı, örneğin, <xref:System.Func%601> ve<xref:System.Func%602>  
  
-   <xref:System.Predicate%601> Temsilci seçme  
  
-   <xref:System.Comparison%601> Temsilci seçme  
  
-   <xref:System.Converter%602> Temsilci seçme  
  
 Daha fazla bilgi ve örnekler için bkz: [işlev ve eylem genel temsilciler (C#) kullanarak varyansını](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel temsilciler değişken türü parametrelerinde bildirme  
 Genel temsilci eşdeğişken varsa veya karşıtı genel tür parametreleri, onu başvurulabilir için farklı bir *değişken Genel temsilci*.  
  
 Genel tür parametresi bir genel temsilci eşdeğişken kullanarak bildirebilirsiniz `out` anahtar sözcüğü. Eşdeğişken türü yöntem bağımsız değişkenleri bir tür değil de, yalnızca bir yöntemin dönüş türü olarak kullanılabilir. Aşağıdaki kod örneğinde eşdeğişken Genel temsilci bildirme gösterilmektedir.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 Kullanarak bir genel tür parametresi karşıtı genel temsilcisi de bildirebilirsiniz `in` anahtar sözcüğü. Karşıtı türü yönteminin dönüş türü olarak değil de yalnızca yöntem bağımsız değişkenleri bir tür olarak kullanılabilir. Aşağıdaki kod örneğinde karşıtı Genel temsilci bildirme gösterilmektedir.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
>  `ref`ve `out` parametreleri C# değişken işaretlenmiş olamaz.  
  
 Aynı temsilci, ancak farklı tür parametreleri için sapması ve Kovaryans desteklemek mümkündür. Bu, aşağıdaki örnekte gösterilir.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Örnek oluşturma ve değişken genel temsilciler çağırma  
 Örneği ve yalnızca örneği ve sabit temsilciler çağırma değişken temsilciler çağırma. Aşağıdaki örnekte, temsilci bir lambda ifadesi tarafından başlatılmış.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Değişken genel temsilciler birleştirme  
 Değişken temsilciler birleştirmelisiniz değil. <xref:System.Delegate.Combine%2A> Yöntemi değişken temsilci dönüşümü desteklemez ve temsilciler tam olarak aynı türünde olmasını bekler. Ya da kullanarak temsilcileri birleştirme olduğunda bu bir çalışma zamanı özel yol açabilir <xref:System.Delegate.Combine%2A> yöntemi kullanarak veya `+` aşağıdaki kod örneğinde gösterildiği gibi işleci.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Genel tür parametreleri varyans değer ve başvuru türleri  
 Genel tür parametreleri için varyansı yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant<int>` örtük olarak dönüştürülemiyor `DVariant<Object>` veya `DVariant<long>`, çünkü tamsayı değer türü.  
  
 Aşağıdaki örnek, bu farkı gösterir genel tür parametreleri değer türleri için desteklenmiyor.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Genel türler](~/docs/standard/generics/index.md)  
 [İşlev ve eylem genel temsilciler (C#) için varyans kullanma](../../../../csharp/programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)  
 [Nasıl yapılır: temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
