---
title: "Nasıl yapılır: Sorgu İfadesinde Türü Örtük Olarak Belirlenmiş Yerel Değişkenleri Kullanma (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 754698fc423fb2dfc9bf50ed15be610831cefeda
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Nasıl yapılır: Sorgu İfadesinde Türü Örtük Olarak Belirlenmiş Yerel Değişkenleri Kullanma (C# Programlama Kılavuzu)
Yerel bir değişken türünü belirlemek için derleyici istediğinizde türü örtük olarak belirlenmiş yerel değişkenleri kullanabilirsiniz. Sorgu ifadelerinde sık kullanılan anonim türler depolamak için örtük olarak yazılan yerel değişkenler kullanmanız gerekir. Aşağıdaki örnekler sorgularda örtük olarak yazılan yerel değişkenler isteğe bağlıdır ve gerekli kullanımını gösterir.  
  
 Türü örtük olarak belirlenmiş yerel değişkenleri kullanarak bildirildiğinde [var](../../../csharp/language-reference/keywords/var.md) bağlamsal anahtar sözcüğü. Daha fazla bilgi için bkz: [örtük olarak yazılan yerel değişkenler](../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md) ve [örtük olarak yazılan diziler](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, yaygın bir senaryo gösterir `var` anahtar sözcüğü gereklidir: anonim türleri dizisi üreten bir sorgu ifadesi. Bu senaryoda, sorgu değişkeni ve yineleme değişkeni `foreach` deyimi dolaylı olarak belirlenmelidir kullanarak `var` anonim bir tür için bir tür adına erişim izni olmadığı için. Anonim türler hakkında daha fazla bilgi için bkz: [anonim türler](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_1.cs)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `var` benzer bir durumda, ancak, anahtar kullanımını `var` isteğe bağlıdır. Çünkü `student.LastName` bir dize, sorgunun döndürdüğü yürütülmesi dizeleri dizisidir. Bu nedenle, türü `queryID` olarak bildirilmesi `System.Collections.Generic.IEnumerable<string>` yerine `var`. Anahtar sözcüğü `var` kolaylık sağlamak için kullanılır. Örnekte, yineleme değişkeni `foreach` deyimi bir dize olarak açıkça belirtilmiş, ancak bunun yerine kullanarak bildirilmesi `var`. Yineleme değişkeni türü kullanımını anonim bir tür olduğundan `var` bir seçenek, bir gereksinim değil. Unutmayın, `var` kendisini bir tür, ancak bir yönerge derleyici Infer ve atamak için değil.  
  
 [!code-csharp[csProgGuideLINQ#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Genişletme yöntemleri](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)  
 [LINQ (dil ile tümleşik sorgu)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)  
 [var](../../../csharp/language-reference/keywords/var.md)  
 [LINQ Sorgu ifadeleri](../../../csharp/programming-guide/linq-query-expressions/index.md)
