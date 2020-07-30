---
title: İfadeler-C# Programlama Kılavuzu
description: Çağırma, sorgu, lambda, sabit değerler ve basit adlar gibi C# programlamada ifadeler hakkında bilgi edinin.
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 5bcfdae27c30bd5d845f621ac4b5b20ff37612a0
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381833"
---
# <a name="expressions-c-programming-guide"></a>İfadeler (C# Programlama Kılavuzu)

Bir *ifade* bir veya daha fazla işlenenin dizisi ve tek bir değer, nesne, yöntem veya ad alanı olarak değerlendirilebilen sıfır veya daha fazla [işleçlerdir](../../language-reference/operators/index.md) . İfadeler, bir değişmez değer, bir yöntem çağırma, bir işleç ve işlenenleri ya da *basit bir ad*içerebilir. Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir.  
  
 İfadeler, diğer ifadeleri parametre olarak kullanan işleçler veya parametreleri diğer Yöntem çağrılarını çağıran Yöntem çağrılarını kullanabilir, böylece ifadeler basit ve çok karmaşık olabilir. Aşağıdaki iki ifade örneğidir:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>İfade değerleri

 İfadelerin çoğunda, örneğin deyimlerde veya yöntem parametrelerinde kullanıldığında, ifadenin bazı değerler değerlendirmesi beklenir. X ve y tamsayılardır ise, ifade `x + y` sayısal bir değer olarak değerlendirilir. İfade, bir `new MyClass()` sınıfın yeni bir örneğine başvuru olarak değerlendirilir `MyClass` . İfade, `myClass.ToString()` yöntemin dönüş türü olduğundan bir dize olarak değerlendirilir. Ancak, bir ad alanı adı bir ifade olarak sınıflandırılabilse de, bir değer olarak değerlendirilmez ve bu nedenle hiçbir ifadenin nihai sonucu olmaz. Bir ad alanı adını yöntem parametresine geçiremez veya yeni bir ifadede kullanamaz veya bir değişkene atayabilirsiniz. Daha büyük bir ifadede yalnızca alt ifade olarak kullanabilirsiniz. Aynı şekilde türler (nesnelerden farklı olarak <xref:System.Type?displayProperty=nameWithType> ), Yöntem grubu adları (belirli yöntemlerden farklı olarak) ve olay [ekleme](../../language-reference/keywords/add.md) ve [kaldırma](../../language-reference/keywords/remove.md) erişimcileri için de geçerlidir.  
  
 Her değerin ilişkili bir türü vardır. Örneğin, x ve y öğelerinin her ikisi de türünde `int` değişkensiyse, ifadenin değeri `x + y` de olarak yazılır `int` . Değer farklı türde bir değişkene atanırsa veya x ve y farklı türse, tür dönüştürme kuralları uygulanır. Bu dönüşümlerin nasıl çalıştığı hakkında daha fazla bilgi için bkz. [atama ve tür dönüştürmeleri](../types/casting-and-type-conversions.md).  
  
## <a name="overflows"></a>Taşmalar

 Değer değerin türünün en büyük değerinden daha büyükse sayısal ifadeler taşmaya neden olabilir. Daha fazla bilgi için, bkz. [Checked ve unchecked](../../language-reference/keywords/checked-and-unchecked.md) ve [yerleşik sayısal](../../language-reference/builtin-types/numeric-conversions.md) dönüşümler makalesindeki [Açık sayısal dönüştürmeler](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) bölümü.
  
## <a name="operator-precedence-and-associativity"></a>İşleç önceliği ve ilişkilendirilebilirlik

 Bir ifadenin değerlendirilme şekli, birleşim ve işleç önceliği kurallarına tabidir. Daha fazla bilgi için bkz. [işleçler](../../language-reference/operators/index.md).  
  
 Atama ifadeleri ve yöntem çağırma ifadeleri hariç olmak üzere çoğu ifadenin bir deyime katıştırılması gerekir. Daha fazla bilgi için bkz. [deyimler](./statements.md).  
  
## <a name="literals-and-simple-names"></a>Değişmez değerler ve basit adlar

 İki basit ifade türü değişmez değer ve basit adlardır. Sabit değer, adı olmayan bir sabit değerdir. Örneğin, aşağıdaki kod örneğinde, her ikisi de `5` `"Hello World"` değişmez değerlerdir:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Değişmez değerler hakkında daha fazla bilgi için bkz. [türler](/dotnet/csharp/language-reference/keywords).  
  
 Yukarıdaki örnekte, `i` ve `s` yerel değişkenleri tanımlayan basit adlardır. Bu değişkenler bir ifadede kullanıldığında, değişken adı, şu anda, değişkenin bellekteki konumunda depolanan değeri değerlendirir. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Çağırma ifadeleri

 Aşağıdaki kod örneğinde, çağrısı `DoWork` bir çağırma deyimidir.  
  
```csharp
DoWork();  
```  
  
 Bir yöntem çağrısı, önceki örnekteki gibi bir ad olarak veya başka bir ifadenin sonucu olarak, parantez ve herhangi bir yöntem parametresi olarak yöntemin adını gerektirir. Daha fazla bilgi için bkz. [Yöntemler](../classes-and-structs/methods.md). Bir temsilci çağrısı, parantez içinde bir temsilci ve yöntem parametrelerinin adını kullanır. Daha fazla bilgi için bkz. [Temsilciler](../delegates/index.md). Yöntem etkinleştirmeleri ve temsilci etkinleştirmeleri, yöntemi bir değer döndürürse yöntemin dönüş değeri olarak değerlendirilir. Void döndüren yöntemler bir ifadede bir değer yerine kullanılamaz.  

## <a name="query-expressions"></a>Sorgu ifadeleri

 Genel içindeki ifadelerle ilgili kuralların aynı kuralları sorgu ifadeleri için de geçerlidir. Daha fazla bilgi için bkz. [LINQ](../../linq/index.md).  
  
## <a name="lambda-expressions"></a>Lambda ifadeleri

 Lambda ifadeleri, adı olmayan ancak giriş parametreleri ve birden çok deyim içeren "satır içi yöntemleri" temsil eder. Bağımsız değişkenleri yöntemlere geçirmek için LINQ 'ta kapsamlı olarak kullanılırlar. Lambda ifadeleri, kullanıldıkları içeriğe bağlı olarak temsilciler ya da ifade ağaçları için derlenir. Daha fazla bilgi için bkz. [lambda ifadeleri](lambda-expressions.md).  
  
## <a name="expression-trees"></a>İfade ağaçları

İfade ağaçları, ifadelerin veri yapıları olarak temsil olmasını sağlar. Sorgu ifadelerini, SQL veritabanı gibi başka bir bağlamda anlamlı koda dönüştürmek için, LINQ sağlayıcıları tarafından kapsamlı olarak kullanılır. Daha fazla bilgi için bkz. [Ifade ağaçları (C#)](../concepts/expression-trees/index.md).
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

C#, metotlar, oluşturucular, sonlandırıcılar, Özellikler ve Dizin oluşturucular için kısa ifade gövdesi açıklaması sunmanıza olanak tanıyan *Expression-Bodied üyelerini*destekler. Daha fazla bilgi için bkz. [Expression-Bodied Üyeler](expression-bodied-members.md).

## <a name="remarks"></a>Açıklamalar

 Bir ifadeden bir değişken, nesne özelliği veya nesne Dizin Oluşturucu erişimi tanımlandığında, bu öğenin değeri ifadenin değeri olarak kullanılır. İfade, son olarak gerekli türü değerlendirirken, bir değer veya nesne gerekli olduğunda C# ' ta herhangi bir yere yerleştirilebilir.  

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [ifadeler](~/_csharplang/spec/expressions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [İşleçler](../../language-reference/operators/index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [Temsilciler](../delegates/index.md)
- [Türler](../types/index.md)
- [LINQ](../../linq/index.md)
