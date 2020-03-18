---
title: Temsilcilerde Varyans (C#)
ms.date: 07/20/2015
ms.assetid: 19de89d2-8224-4406-8964-2965b732b890
ms.openlocfilehash: fd1b4824dc3d8f12347e01b804a6e39fe2e086c8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169720"
---
# <a name="variance-in-delegates-c"></a>Temsilcilerde Varyans (C#)
.NET Framework 3.5, C#'daki tüm temsilcilerdeki temsilci türleri ile eşleşen yöntem imzaları için varyans desteği getirmiştir. Bu, yalnızca eşleşen imzalara sahip yöntemlere değil, aynı zamanda daha fazla türemiş türleri (tutarlılık) döndüren veya temsilci türütarafından belirtilenden daha az türemiş türe (kontravariance) olan parametreleri kabul eden yöntemleri de temsilciatamak anlamına gelir . Bu, hem genel hem de genel olmayan temsilcileri içerir.  
  
 Örneğin, iki sınıfı ve iki temsilcisi olan aşağıdaki kodu göz önünde bulundurun: genel ve genel olmayan.  
  
```csharp  
public class First { }  
public class Second : First { }  
public delegate First SampleDelegate(Second a);  
public delegate R SampleGenericDelegate<A, R>(A a);  
```  
  
 `SampleDelegate` Veya `SampleGenericDelegate<A, R>` türlerden temsilciler oluşturduğunuzda, bu temsilcilere aşağıdaki yöntemlerden birini atayabilirsiniz.  
  
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
  
 Aşağıdaki kod örneği, yöntem imzası ve temsilci türü arasındaki örtük dönüştürmeyi göstermektedir.  
  
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
  
 Daha fazla örnek için bkz: [Varyans Kullanarak Temsilciler (C#)](./using-variance-in-delegates.md) ve [Func ve Eylem Genel Delegeler (C# için Varyans kullanma).](./using-variance-for-func-and-action-generic-delegates.md)  
  
## <a name="variance-in-generic-type-parameters"></a>Genel Tip Parametrelerinde Varyans  
 .NET Framework 4 veya sonraki durumlarda, genel tür parametreleri tarafından belirlenen farklı türlere sahip genel temsilcilerin birbirlerinden gerektiği gibi devralınması durumunda, genel tür parametreleri tarafından belirtilen genel temsilcilertarafından atanabilmesi için, temsilciler arasında örtük dönüştürmeyi etkinleştirebilirsiniz Varyans.  
  
 Örtük dönüştürmeyi etkinleştirmek için, genel parametreleri bir temsilcideki genel `in` parametreleri veya `out` anahtar sözcüğü kullanarak ortak değişken veya karşıt değişken olarak açıkça beyan etmelisiniz.  
  
 Aşağıdaki kod örneği, ortak değişken genel tür parametresi olan bir temsilciyi nasıl oluşturabileceğinizi gösterir.  
  
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
  
 Yöntem imzalarını temsilci türleri ile eşleştirmek için yalnızca varyans `in` `out` desteği kullanırsanız ve anahtar kelimeleri kullanmazsanız, bazen aynı lambda ifadeleri veya yöntemleriyle temsilcileri anında atayabileceğinizi, ancak bir temsilciyi diğerine atayamayacağınızı görebilirsiniz.  
  
 Aşağıdaki kod `SampleGenericDelegate<String>` örneğinde, devralınmasına rağmen `SampleGenericDelegate<Object>` `String` açıkça `Object`"ne ş"ye dönüştürülemez. Genel parametreyi `T` `out` anahtar kelimeyle işaretleyerek bu sorunu çözebilirsiniz.  
  
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
  
### <a name="generic-delegates-that-have-variant-type-parameters-in-the-net-framework"></a>.NET Çerçevesinde Varyant Türü Parametreleri Olan Genel Temsilciler  
 .NET Framework 4, varolan birkaç genel temsilcide genel tür parametreleri için varyans desteği getirmiştir:  
  
- `Action`<xref:System> ad alanından delegeler, örneğin <xref:System.Action%601> ve<xref:System.Action%602>  
  
- `Func`<xref:System> ad alanından delegeler, örneğin <xref:System.Func%601> ve<xref:System.Func%602>  
  
- Temsilci <xref:System.Predicate%601>  
  
- Temsilci <xref:System.Comparison%601>  
  
- Temsilci <xref:System.Converter%602>  
  
 Daha fazla bilgi ve örnekler [için Func ve Action Generic Delegates (C#) için Varyans Kullanma'ya](./using-variance-for-func-and-action-generic-delegates.md)bakın.  
  
### <a name="declaring-variant-type-parameters-in-generic-delegates"></a>Genel Temsilcilerde Varyant Türü Parametrelerinin Açıklanması  
 Genel bir temsilcinin ortak veya zıt genel tür parametreleri varsa, bu *türvaryant genel temsilci*olarak adlandırılabilir.  
  
 Genel bir temsilcide anahtar sözcüğü kullanarak genel bir `out` tür parametre eşdeğişkenini bildirebilirsiniz. Ortak varyant türü, yöntem bağımsız değişkenleri türü olarak değil, yalnızca bir yöntem dönüş türü olarak kullanılabilir. Aşağıdaki kod örneği, bir ortak genel temsilcinin nasıl bildirilen gösteriş olduğunu gösterir.  
  
```csharp  
public delegate R DCovariant<out R>();  
```  
  
 `in` Anahtar sözcüğü kullanarak genel bir temsilcide genel tür parametre karşıtlığı bildirebilirsiniz. Karşıt tür, yöntem dönüş türü olarak değil, yalnızca yöntem bağımsız değişkenleri türü olarak kullanılabilir. Aşağıdaki kod örneği, karşıt genel temsilcinin nasıl bildirilen şekli gösterir.  
  
```csharp  
public delegate void DContravariant<in A>(A a);  
```  
  
> [!IMPORTANT]
> `ref`, `in`, `out` ve C# parametreleri varyant olarak işaretlenemez.  
  
 Aynı temsilcide hem varyans hem de covariance desteklemek de mümkündür, ancak farklı tür parametreleri için. Bu, aşağıdaki örnekte gösterilir.  
  
```csharp  
public delegate R DVariant<in A, out R>(A a);  
```  
  
### <a name="instantiating-and-invoking-variant-generic-delegates"></a>Varyant Genel Temsilcileri Anında Ve Çağıran  
 Değişmez delegeleri anında anlayıp çağırabilirsiniz. Aşağıdaki örnekte, temsilci bir lambda ifadesi ile anında.  
  
```csharp  
DVariant<String, String> dvariant = (String str) => str + " ";  
dvariant("test");  
```  
  
### <a name="combining-variant-generic-delegates"></a>Varyant Genel Temsilcileri Birleştirme  
 Varyant temsilcilerini birleştirmemelisiniz. Yöntem <xref:System.Delegate.Combine%2A> varyant temsilci dönüşümdesteklemez ve delegelertam olarak aynı türde olmasını bekliyor. Bu, aşağıdaki kod örneğinde gösterildiği gibi, <xref:System.Delegate.Combine%2A> yöntemi kullanarak veya `+` işleci kullanarak temsilcileri birleştirdiğinizde çalışma zamanı özel bir durum neden olabilir.  
  
```csharp  
Action<object> actObj = x => Console.WriteLine("object: {0}", x);  
Action<string> actStr = x => Console.WriteLine("string: {0}", x);  
// All of the following statements throw exceptions at run time.  
// Action<string> actCombine = actStr + actObj;  
// actStr += actObj;  
// Delegate.Combine(actStr, actObj);  
```  
  
## <a name="variance-in-generic-type-parameters-for-value-and-reference-types"></a>Değer ve Referans Türleri için Genel Tip Parametrelerde Varyans  
 Genel tür parametreleri için varyans yalnızca başvuru türleri için desteklenir. Örneğin, `DVariant<int>` tamsayı bir değer türü `DVariant<Object>` olduğundan, örtülü olarak dönüştürülemez veya `DVariant<long>`,  
  
 Aşağıdaki örnek, genel tür parametrelerindeki varyansın değer türleri için desteklenmediğini göstermektedir.  
  
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
- [Func ve Action Generic Delegeler için Varyans Kullanma (C#)](./using-variance-for-func-and-action-generic-delegates.md)
- [Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)](../../delegates/how-to-combine-delegates-multicast-delegates.md)
