---
title: Sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: c6022aaa4c37bc0c11c09375d3637d8287fce61a
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970429"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma (C# Programlama Kılavuzu)
Derleyicinin yerel bir değişken türünü belirlemesini istediğinizde örtülü olarak yazılan yerel değişkenleri kullanabilirsiniz. Genellikle sorgu ifadelerinde kullanılan anonim türleri depolamak için örtük olarak belirlenmiş yerel değişkenleri kullanmanız gerekir. Aşağıdaki örneklerde, sorgularda örtük olarak belirlenmiş yerel değişkenlerin hem isteğe bağlı hem de gerekli kullanımları gösterilmektedir.  
  
 Örtük olarak yazılan yerel değişkenler, [var](../../language-reference/keywords/var.md) olan anahtar sözcüğü kullanılarak bildirilmiştir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md) ve [örtük olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, `var` anahtar sözcüğünün gerekli olduğu ortak bir senaryoyu göstermektedir: anonim türler dizisi üreten bir sorgu ifadesi. Bu senaryoda, anonim türdeki bir tür adına erişiminizin olmadığı için, hem sorgu değişkeni hem de `foreach` deyimdeki yineleme değişkeni `var` kullanılarak örtük olarak yazılmalıdır. Anonim türler hakkında daha fazla bilgi için bkz. [anonim türler](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, benzer bir durumda `var` anahtar sözcüğünü kullanır, ancak `var` kullanımı isteğe bağlıdır. `student.LastName` bir dize olduğundan, sorgunun yürütülmesi dizeler dizisini döndürür. Bu nedenle `queryID` türü `var`yerine `System.Collections.Generic.IEnumerable<string>` olarak bildirilemez. Anahtar sözcük `var` kolaylık sağlamak için kullanılır. Örnekte, `foreach` deyimindeki yineleme değişkeni açıkça bir dize olarak yazılır, ancak bunun yerine `var`kullanılarak bildirilebilecek. Yineleme değişkeninin türü anonim bir tür olmadığından, `var` kullanımı gereksinim değil bir seçenektir. `var` kendisinin bir tür değil, ancak türü çıkarsanmak ve atamak için derleyicinin bir yönergesini unutmayın.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
