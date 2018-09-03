---
title: 'Nasıl yapılır: Sorgu İfadesinde Türü Örtük Olarak Belirlenmiş Yerel Değişkenleri Kullanma (C# Programlama Kılavuzu)'
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: ef3a411bc51fcc5f644f9d53bde67f7116289678
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481585"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Nasıl yapılır: Sorgu İfadesinde Türü Örtük Olarak Belirlenmiş Yerel Değişkenleri Kullanma (C# Programlama Kılavuzu)
Derleyici, bir yerel değişken türünü belirlemek için istediğiniz zaman, türü örtük olarak belirlenmiş yerel değişkenleri kullanabilirsiniz. Sorgu ifadelerinde sık kullanılan anonim türler depolamak için örtük olarak yazılan yerel değişkenler kullanmanız gerekir. Aşağıdaki örnekler sorgularda örtük olarak yazılan yerel değişkenler isteğe bağlıdır ve gerekli kullanımlarını gösterir.  
  
 Türü örtük olarak belirlenmiş yerel değişkenleri kullanarak bildirilir [var](../../../csharp/language-reference/keywords/var.md) bağlamsal anahtar sözcük. Daha fazla bilgi için [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek yaygın bir senaryo gösterilmektedir `var` anahtar sözcüğü gereklidir: Anonim türler bir dizi üreten bir sorgu ifadesi. Bu senaryoda, sorgu değişkeni hem de yineleme değişkeni `foreach` ifadesi örtük olarak belirlenmelidir kullanarak `var` anonim türünün bir türü adına erişim izni olmadığı için. Anonim türler hakkında daha fazla bilgi için bkz. [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `var` benzer bir durumda, ancak, anahtar sözcük kullanımını `var` isteğe bağlıdır. Çünkü `student.LastName` dize, sorgunun döndürdüğü yürütülmesini dizeler dizisidir. Bu nedenle, türü `queryID` olarak bildirilmesi `System.Collections.Generic.IEnumerable<string>` yerine `var`. Anahtar sözcüğü `var` kolaylık sağlamak için kullanılır. Örnekte, yineleme değişkeni `foreach` ifadesi bir dize olarak açıkça belirlenmiş ancak kullanarak bunun yerine bildirilebilir `var`. Yineleme değişkeni türü kullanımını anonim bir tür olmadığından `var` seçeneği, bir gereksinim değildir. Unutmayın, `var` kendisini çıkarır ve atamak için bir tür ancak derleyici bir yönerge değil.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme Yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (dil ile tümleşik sorgu)](../../../csharp/linq/index.md)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
