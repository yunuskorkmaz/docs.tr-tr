---
title: İfadeler - C# Programlama Kılavuzu
ms.date: 05/11/2017
helpviewer_keywords:
- expressions [C#]
- C# language, expressions
ms.assetid: c7d8feb0-0e58-4f94-8bf6-4d070550a832
ms.openlocfilehash: 4bbee8f15c2591e8b172df9a6759449d48697804
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75699099"
---
# <a name="expressions-c-programming-guide"></a>İfadeler (C# Programlama Kılavuzu)

*İfade,* tek bir değer, nesne, yöntem veya ad alanına değerlendirilebilecek bir veya daha fazla operand ve sıfır veya daha fazla [işleç](../../language-reference/operators/index.md) dizisidir. İfadeler bir edebi değer, bir yöntem çağırma, bir işleç ve operands veya basit bir *ad*dan oluşabilir. Basit adlar bir değişkenin adı, tür üyesi, yöntem parametresi, ad alanı veya tür olabilir.  
  
 İfadeler sırayla parametre olarak diğer ifadeleri kullanan işleçler veya parametreleri sırayla diğer yöntem çağrıları olan yöntem çağrıları kullanabilir, böylece ifadeler basitten çok karmaşıka kadar değişebilir. Aşağıda iki ifade örneği verilmiştir:  
  
```csharp  
((x < 10) && ( x > 5)) || ((x > 20) && (x < 25));

System.Convert.ToInt32("35");  
```  
  
## <a name="expression-values"></a>İfade değerleri

 İfadelerin kullanıldığı bağlamların çoğunda, örneğin deyimlerde veya yöntem parametrelerinde, ifadenin bazı değere göre değerlendirilmesi beklenir. X ve y tamsayılarsa, `x + y` ifade sayısal bir değere göre değerlendirilir. İfade, `new MyClass()` bir `MyClass` sınıfın yeni bir örneğine başvuruyu değerlendirir. Yöntemin `myClass.ToString()` dönüş türü olduğundan ifade bir dize değerlendirir. Ancak, bir ad alanı adı bir ifade olarak sınıflandırılsa da, bir değere değerlendirmeyapmaz ve bu nedenle hiçbir ifadenin nihai sonucu olamaz. Bir ad alanı adını yöntem parametresine geçiremez veya yeni bir ifadede kullanamaz veya bir değişkene atayamazsınız. Bunu yalnızca daha büyük bir ifadede alt ifade olarak kullanabilirsiniz. Aynı durum türler (nesnelerden <xref:System.Type?displayProperty=nameWithType> farklı olarak), yöntem grubu adları (belirli yöntemlerden farklı olarak) ve olay ekleme ve erişime erişime [ekleme](../../language-reference/keywords/add.md) ve [kaldırma](../../language-reference/keywords/remove.md) için de geçerlidir.  
  
 Her değerin ilişkili bir türü vardır. Örneğin, x ve y türünün `int`her iki değişkeni `x + y` ise, ifadenin `int`değeri de . Değer farklı türde bir değişkene atanmışsa veya x ve y farklı türlerdeyse, tür dönüştürme kuralları uygulanır. Bu tür dönüşümlerin nasıl çalıştığı hakkında daha fazla bilgi için [bkz.](../types/casting-and-type-conversions.md)  
  
## <a name="overflows"></a>Taşı -yor

 Değer, değerin türünün en büyük değerinden daha büyükse, sayısal ifadeler taşmaya neden olabilir. Daha fazla bilgi için bkz: [Denetlenmiş ve İşaretlenmemiş](../../language-reference/keywords/checked-and-unchecked.md) ve [Yerleşik sayısal dönüşümler](../../language-reference/builtin-types/numeric-conversions.md) makalesinin Açık sayısal [dönüşümler](../../language-reference/builtin-types/numeric-conversions.md#explicit-numeric-conversions) bölümüne bakın.
  
## <a name="operator-precedence-and-associativity"></a>Operatör önceliği ve bağlantı

 Bir ifadenin değerlendirilme şekli, bağlılık ve işleç önceliği kurallarına tabidir. Daha fazla bilgi için [Operatörler'e](../../language-reference/operators/index.md)bakın.  
  
 Atama ifadeleri ve yöntem çağırma ifadeleri dışında çoğu ifade bir deyime katışdırılmalıdır. Daha fazla bilgi için [Deyimler'e](./statements.md)bakın.  
  
## <a name="literals-and-simple-names"></a>Edebi ve basit isimler

 En basit iki ifade türü gerçek ve basit adlardır. Gerçek bir ad olmayan sabit bir değerdir. Örneğin, aşağıdaki kod örneğinde, `5` `"Hello World"` hem ve edebi değerler şunlardır:  
  
 [!code-csharp[csProgGuideStatements#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#2)]  
  
 Literals hakkında daha fazla bilgi için [Bkz.](/dotnet/csharp/language-reference/keywords)  
  
 Önceki örnekte, her `i` `s` ikisi de ve yerel değişkenleri tanımlayan basit adlar vardır. Bu değişkenler bir ifadede kullanıldığında, değişken adı, değişkenin bellekteki konumunda şu anda depolanan değeri değerlendirir. Bu, aşağıdaki örnekte gösterilmiştir:  
  
 [!code-csharp[csProgGuideStatements#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#3)]

## <a name="invocation-expressions"></a>Çağırma ifadeleri

 Aşağıdaki kod örneğinde, çağrı `DoWork` bir çağırma ifadesidir.  
  
```csharp
DoWork();  
```  
  
 Yöntem çağırma, önceki örnekte olduğu gibi bir ad olarak veya başka bir ifadenin sonucu olarak, ardından parantez ve herhangi bir yöntem parametreleri tarafından izlenen yöntemin adını gerektirir. Daha fazla bilgi için [Yöntemler'e](../classes-and-structs/methods.md)bakın. Temsilci çağırma, parantez içinde bir temsilcinin adını ve yöntem parametrelerini kullanır. Daha fazla bilgi için [bkz.](../delegates/index.md) Yöntem bir değer döndürürse, yöntem çağrıları ve temsilci çağrıları yöntemin geri dönüş değerine göre değerlendirilir. Geçersiz döndürülen yöntemler, bir ifadedeki değer yerine kullanılamaz.  

## <a name="query-expressions"></a>Sorgu ifadeleri

 Genel olarak ifadeler için aynı kurallar sorgu ifadeleri için geçerlidir. Daha fazla bilgi için [LINQ'ya](../../linq/index.md)bakın.  
  
## <a name="lambda-expressions"></a>Lambda ifadeleri

 Lambda ifadeleri, adı olmayan ancak giriş parametreleri ve birden çok deyimi olan "satır altı yöntemleri" temsil eder. Bağımsız değişkenleri metotlara aktarmak için LINQ'da yaygın olarak kullanılırlar. Lambda ifadeleri, kullanıldıkları bağlama bağlı olarak temsilcilere veya ifade ağaçlarına derlenir. Daha fazla bilgi için [Lambda İfadeleri'ne](lambda-expressions.md)bakın.  
  
## <a name="expression-trees"></a>İfade ağaçları

İfade ağaçları ifadelerin veri yapıları olarak temsil edilmesini sağlar. Bunlar, linq sağlayıcıları tarafından sorgu ifadelerini SQL veritabanı gibi başka bir bağlamda anlamlı olan koda çevirmek için yaygın olarak kullanılır. Daha fazla bilgi için Ifade [Ağaçları (C#)](../concepts/expression-trees/index.md)bakın.
  
## <a name="expression-body-definitions"></a>İfade gövdesi tanımları

C#, yöntemler, yapıcılar, sonlandırıcılar, özellikler ve dizin leyiciler için kısa bir ifade gövdesi tanımı sağlamanıza olanak tanıyan *ifade gövdeli üyeleri*destekler. Daha fazla bilgi için Bkz. [Expression gövdeli üyeler.](expression-bodied-members.md)

## <a name="remarks"></a>Açıklamalar

 Bir ifadeden bir değişken, nesne özelliği veya nesne dizinleyici erişimi tanımlandığında, bu öğenin değeri ifadenin değeri olarak kullanılır. İfade sonunda gerekli türe göre değerlendirildiği sürece, bir ifade C#'da bir değerin veya nesnenin gerekli olduğu herhangi bir yere yerleştirilebilir.  

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [İfadeler](~/_csharplang/spec/expressions.md) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [İşleçler](../../language-reference/operators/index.md)
- [Yöntemler](../classes-and-structs/methods.md)
- [Temsilciler](../delegates/index.md)
- [Türler](../types/index.md)
- [LINQ](../../linq/index.md)
