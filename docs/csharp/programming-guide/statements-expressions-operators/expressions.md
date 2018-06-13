---
title: İfadeler (C# Programlama Kılavuzu)
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 830c68e6857e72fe19099753ba57a7e22491af2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339663"
---
# <a name="expressions-c-programming-guide"></a>İfadeler (C# Programlama Kılavuzu)
Bir *ifade* bir veya daha fazla işlenenler ve tek bir değer, nesne, yöntemi veya ad alanı için değerlendirilen sıfır veya daha fazla işleçleri dizisidir. Değişmez değer, bir yöntem çağrısının, bir işleç ve kendi işlenenler ifadeleri oluşabilir veya *basit bir ad*. Basit adları bir değişken, türü üyesinin, yöntem parametresi, ad alanı veya türü adı olabilir.  
  
 İfadeler sırayla parametreleri veya ifadeleri basitten için çok karmaşık değişebilir sırayla diğer yöntem çağrılarını parametreleri olduğundan yöntem çağrılarını olarak diğer ifadeleri kullanma işleçleri kullanabilirsiniz. İki ifadeleri örnekleri aşağıda verilmiştir:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));
   
System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>İfade değerleri  
 Çoğunda ifadeleri kullanılan bağlamları, örneğin deyimleri veya yöntem parametreleri ifade bazı değeri bekleniyor. X ve y tamsayılar, ifade olan `x + y` sayısal değer değerlendirir. İfade `new MyClass()` yeni bir örneğini başvuru değerlendiren bir `MyClass` nesnesi. İfade `myClass.ToString()` yönteminin dönüş türü olduğu için bir dizeye değerlendirir. Ancak, bir ad alanı adı bir ifade olarak sınıflandırılır ancak değerine değerlendirmez ve bu nedenle hiçbir zaman sonucunu herhangi bir ifade olabilir. Yöntem parametresi için bir ad alanı adını geçirmek olamaz veya yeni bir ifadede kullanın veya bir değişkene atayın. Alt ifade daha büyük bir ifadede olarak yalnızca kullanabilirsiniz. Aynı türleri için geçerlidir (olarak distinct gelen <xref:System.Type?displayProperty=nameWithType> nesneler), yöntem grubu adları (as distinct from belirli yöntemler) ve olay [eklemek](../../../csharp/language-reference/keywords/add.md) ve [kaldırmak](../../../csharp/language-reference/keywords/remove.md) erişimciler.  
  
 Her değer bir ilişkili türüne sahip. Örneğin, ise x ve y hem değişkenlerdir türü `int`, ifadenin değerini `x + y` olarak yazıldığından `int`. Farklı türde bir değişkene değer atanmazsa veya x ve y olan farklı tür, tür dönüştürme kuralları uygulanır. Bu tür dönüşümleri nasıl çalıştığı hakkında daha fazla bilgi için bkz: [atama ve tür dönüşümleri](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Taşan  
 Sayısal ifadeler değerinin türü en yüksek değerden daha büyük bir değerdir taşan neden olabilir. Daha fazla bilgi için bkz: [Checked ve Unchecked](../../../csharp/language-reference/keywords/checked-and-unchecked.md) ve [açık sayısal dönüşümler tablosu](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md).  
  
## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve birleşim  
 Bir ifadenin değerlendirilmesi şekilde birleşim ve İşleç önceliği kurallarıyla yönetilir. Daha fazla bilgi için bkz: [işleçleri](../../../csharp/programming-guide/statements-expressions-operators/operators.md).  
  
 Atama deyimleri ve yöntemi çağırma ifadeleri dışında çoğu ifadenin bir deyimde gömülü olması gerekir. Daha fazla bilgi için bkz: [deyimleri](../../../csharp/programming-guide/statements-expressions-operators/statements.md).  
  
## <a name="literals-and-simple-names"></a>Değişmez değerler ve basit adları  
 İki basit ifadeleri değişmez değerleri ve basit adları türleridir. Bir hazır değer adı yok sabit bir değerdir. Örneğin, aşağıdaki kod örneği, her ikisi de `5` ve `"Hello World"` değişmez değerler şunlardır:  
  
 [!code-csharp[csProgGuideStatements#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_1.cs)]  
  
 Değişmez değerler hakkında daha fazla bilgi için bkz: [türleri](../../../csharp/language-reference/keywords/types.md).  
  
 Önceki örnekte, her ikisi de `i` ve `s` yerel değişkenleri tanımlamak basit adlardır. Bu değişkenler bir ifadede kullanıldığında, değişken adı bellek değişkenin konumda saklanan değerle olarak değerlendirilir. Bu aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/expressions_2.cs)]  
## <a name="invocation-expressions"></a>Çağırma ifadeleri  
 Aşağıdaki kod örneğinde, çağrısı `DoWork` çağırma ifade.  
  
```csharp
DoWork();  
```  
  
 Yöntem çağırma yönteminin adı, önceki örnekte olduğu gibi bir ad olarak veya başka bir ifadenin ardından parantez ve herhangi bir yöntem parametre sonucu olarak gerektirir. Daha fazla bilgi için bkz: [yöntemleri](../../../csharp/programming-guide/classes-and-structs/methods.md). Temsilci çağırma parantez içine bir temsilci ve yöntem parametreleri adını kullanır. Daha fazla bilgi için bkz: [Temsilciler](../../../csharp/programming-guide/delegates/index.md). Yöntemi bir değer döndürürse yönteminin dönüş değeri için yöntem çağrılarına ve temsilci çağrılarını değerlendirin. Void döndüren yöntemler, bir ifadede bir değer yerine kullanılamaz.  

## <a name="query-expressions"></a>Sorgu ifadeleri  
 İfadeleri için aynı kuralları genel sorgu ifadeleri için geçerlidir. Daha fazla bilgi için bkz: [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md).  
  
## <a name="lambda-expressions"></a>Lambda ifadeleri  
 Lambda ifadeleri "adı olan, ancak parametreler ve birden çok deyime giriş satır içi yöntemleri" temsil eder. Bağımsız değişkenler yöntemlere geçirmek için bunlar LINQ yaygın olarak kullanılır. Lambda ifadeleri temsilciler veya bunların kullanıldığı bağlam bağlı olarak ifade ağaçları derlenir. Daha fazla bilgi için bkz: [Lambda ifadeleri](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
## <a name="expression-trees"></a>İfade ağaçları  
 İfade ağaçları veri yapılarını gösterilemeyecek kadar ifadeleri etkinleştirin. Sorgu ifadeleri bir SQL veritabanı gibi diğer bazı bağlamında anlamlı koda çevirmek için bunlar LINQ sağlayıcıları tarafından yaygın olarak kullanılır. Daha fazla bilgi için bkz: [ifade ağaçları](http://msdn.microsoft.com/library/fb1d3ed8-d5b0-4211-a71f-dd271529294b).  
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

C# destekler *ifade bodied üyeleri*, yöntemleri, Oluşturucular, sonlandırıcılar, özellikler ve dizin oluşturucular için kısa ifade gövdesi tanım tedarik izin. Daha fazla bilgi için bkz: [ifade bodied üyeleri](expression-bodied-members.md).

## <a name="remarks"></a>Açıklamalar  
 Değişken, nesnenin özellik veya nesne dizin oluşturucu erişimi ifadeden tanımlanır olduğunda, bu öğenin değeri ifade değeri olarak kullanılır. Bir ifade C bir değer veya nesne gerekli olduğu # içinde herhangi bir yere deyimi için gerekli tür sonuçta değerlendirir sürece yerleştirilebilir.  

## <a name="see-also"></a>Ayrıca bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Yöntemler](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [Temsilciler](../../../csharp/programming-guide/delegates/index.md)  
 [İşleçler](../../../csharp/programming-guide/statements-expressions-operators/operators.md)  
 [Türler](../../../csharp/programming-guide/types/index.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
