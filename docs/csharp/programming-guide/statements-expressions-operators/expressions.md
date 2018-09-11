---
title: İfadeler (C# Programlama Kılavuzu)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 3cf084102186d9e13727c36ed14e2ea72ca324f9
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342780"
---
# <a name="expressions-c-programming-guide"></a>İfadeler (C# Programlama Kılavuzu)
Bir *ifade* bir veya daha fazla işlenenler ve tek bir değer, nesne, yöntemi veya ad alanı için değerlendirilen sıfır veya daha fazla işleçleri oluşan bir dizidir. İfadeler, değişmez değer, bir yöntem çağrısı, bir işleci ve işlenenleri, oluşabilir veya *basit adı*. Basit adları bir değişken, tür üyesi, yöntem parametresi, ad alanı veya tür adı olabilir.  
  
 İfadeler sırayla parametreleri ya da ifadeleri basitten çok karmaşık değişebilir sırayla diğer yöntem çağrılarını parametreleri olduğundan, yöntem çağrılarını diğer ifadeler kullanan işleçlerini kullanabilirsiniz. İki örnekleri şunlardır:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>İfade değerleri  
 Çoğunda ifadeler kullanılan bağlamları, örneğin deyimleri ya da yöntem parametreleri ifade bazı değer olarak değerlendirilmesi bekleniyor. X ve y tamsayılardır ifade `x + y` sayısal bir değere değerlendirir. İfade `new MyClass()` yeni bir örneğini bir başvuru olarak değerlendirilen bir `MyClass` nesne. İfade `myClass.ToString()` , yöntemin dönüş türü olduğundan, bir dizeye değerlendirir. Ancak, bir ad alanı adı bir ifade olarak sınıflandırılır ancak bir değer olarak değerlendirilmesi değil ve bu nedenle herhangi bir ifade sonucunu hiçbir zaman olabilir. Bir yöntem parametresi için bir ad alanı adı geçirin veya yeni bir ifadede kullanamaz veya bir değişkene atayın. Geniş bir ifadedeki alt bir ifade olarak yalnızca kullanabilirsiniz. Aynı türleri için geçerlidir (olarak distinct gelen <xref:System.Type?displayProperty=nameWithType> nesneleri), yöntem grubu adları (as distinct from belirli yöntemler) ve olay [ekleme](../../../csharp/language-reference/keywords/add.md) ve [Kaldır](../../../csharp/language-reference/keywords/remove.md) erişimcileri.  
  
 Her değer, ilişkili bir türe sahip. Örneğin, x ve y hem değişken türünün `int`, ifadenin değerini `x + y` olarak yazıldığı `int`. Değeri, farklı türden bir değişkene atanırsa veya x ve y farklı türleri, tür dönüştürme kurallarını uygulanır. Bu tür dönüştürmeler nasıl çalıştığı hakkında daha fazla bilgi için bkz. [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Taşıyor  
 Değer türü en yüksek değerden daha büyük bir değer ise sayısal ifadeler taşıyor neden olabilir. Daha fazla bilgi için [Checked ve Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) ve [Explicit Numeric Conversions Table](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve ilişkiselliği  
 Bir ifadenin değerlendirilme şekilde ilişkilendirilebilirliği ve İşleç önceliği kurallarıyla yönetilir. Daha fazla bilgi için [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Atama ifadeleri ve yöntem çağırma ifadeleri dışında çoğu ifadenin bir deyimde gömülü olması gerekir. Daha fazla bilgi için [deyimleri](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Değişmez değerler ve basit adları  
 İki basit türde ifadeler sabit değerler ve basit adları var. Bir sabit değer adı yok sabit bir değerdir. Örneğin, aşağıdaki kod örneği, hem de `5` ve `"Hello World"` değişmez değerler şunlardır:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Değişmez değerler hakkında daha fazla bilgi için bkz. [türleri](../../../csharp/language-reference/keywords/types.md).  
  
 Yukarıdaki örnekte, her ikisi de `i` ve `s` yerel değişkenler belirlemek basit adlarıdır. Bu değişkenleri ifadede kullanıldığında, değişken adı şu anda değişken bellek konumunda depolanan değeri için değerlendirir. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Çağrı ifadeleri  
 Aşağıdaki kod örneğinde, çağrı `DoWork` çağırma ifadesidir.  
  
```csharp
DoWork();  
```  
  
 Bir yöntem çağırmayla yönteminin adı önceki örnekte olduğu gibi bir ad olarak veya başka bir ifadenin ardından parantez ve herhangi bir yöntem parametre sonucu olarak gerektirir. Daha fazla bilgi için [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md). Temsilci çağrısı parantez içinde bir temsilci ve yöntem parametre adını kullanır. Daha fazla bilgi için [Temsilciler](../../../csharp/programming-guide/delegates/index.md). Yöntem bir değer döndürüyorsa yöntemin dönüş değeri için yöntem çağrıları ve temsilci çağrılarını değerlendirin. Void döndüren yöntemler yerine bir ifade bir değer kullanılamaz.  

## <a name="query-expressions"></a>Sorgu ifadeleri  
 İfadeler için aynı kurallara genel sorgu ifadeleri için de geçerlidir. Daha fazla bilgi için [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Lambda ifadeleri  
 Lambda ifadeleri "adı yok, ancak parametre ve birden fazla giriş satır içi yöntemler" temsil eder. Bağımsız değişkenler yöntemlere geçirmek için bunlar üzerinde LINQ yaygın olarak kullanılır. Lambda ifadeleri, temsilci veya ifade ağaçları kullanılan bağlama bağlı olarak derlenir. Daha fazla bilgi için [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>İfade ağaçları

İfade ağaçları ifadeleri veri yapılarını temsil edilmesini sağlar. Sorgu ifadeleri anlamlı bir SQL veritabanı gibi diğer bazı bağlamında koda çevirmek için bunlar LINQ sağlayıcıları tarafından yaygın olarak kullanılır. Daha fazla bilgi için [ifade ağaçları (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

C# destekler *ifade gövdeli üyeler*, yöntemleri, Oluşturucular, bir Sonlandırıcı, özellikler ve dizin oluşturucular için bir kısa ifade gövdesi tanımı kaynağı sağlar. Daha fazla bilgi için [ifade gövdeli üyeler](expression-bodied-members.md).

## <a name="remarks"></a>Açıklamalar  
 Bir ifade tarafından tanımlanan bir değişken, nesne özellik veya nesne dizinleyici erişimi olduğunda, o öğenin değerini ifade değeri olarak kullanılır. Bir ifade bir değer veya nesne gerekli olduğu #c dilinde herhangi bir ifade, sonuçta gereken türe değerlendirir sürece yerleştirilebilir.  

## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
- [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
- [Türler](../../../csharp/programming-guide/types/index.md)  
- [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
