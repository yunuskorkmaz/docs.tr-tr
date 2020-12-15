---
title: Sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma-C# Programlama Kılavuzu
description: Derleyicinin yerel bir değişken türünü belirlemesini sağlamak Için C# dilinde örtük olarak yazılan yerel değişkenler kullanın. Anonim türleri depolamak için bunları kullanmanız gerekir.
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: bd68c913c6f0d410d97973fb28789218f88903b5
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512391"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Bir sorgu ifadesinde örtük olarak yazılan yerel değişkenleri ve dizileri kullanma (C# Programlama Kılavuzu)

Derleyicinin yerel bir değişken türünü belirlemesini istediğinizde örtülü olarak yazılan yerel değişkenleri kullanabilirsiniz. Genellikle sorgu ifadelerinde kullanılan anonim türleri depolamak için örtük olarak belirlenmiş yerel değişkenleri kullanmanız gerekir. Aşağıdaki örneklerde, sorgularda örtük olarak belirlenmiş yerel değişkenlerin hem isteğe bağlı hem de gerekli kullanımları gösterilmektedir.  
  
 Örtük olarak yazılan yerel değişkenler, [var](../../language-reference/keywords/var.md) olan anahtar sözcüğü kullanılarak bildirilmiştir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](./implicitly-typed-local-variables.md) ve [örtük olarak yazılan diziler](../arrays/implicitly-typed-arrays.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, anahtar sözcüğünün gerekli olduğu ortak bir senaryoyu göstermektedir `var` : anonim türler dizisi üreten bir sorgu ifadesi. Bu senaryoda, `foreach` `var` anonim türdeki bir tür adına erişiminizin olmadığı için, hem sorgu değişkeni hem de deyimdeki yineleme değişkeni kullanılarak örtük olarak yazılmalıdır. Anonim türler hakkında daha fazla bilgi için bkz. [anonim türler](./anonymous-types.md).  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `var` anahtar sözcüğünü benzer bir durumda kullanır, ancak öğesinin kullanımı `var` isteğe bağlıdır. `student.LastName`Bir dize olduğundan, sorgunun yürütülmesi bir dizi dizeyi döndürür. Bu nedenle, türü `queryID` yerine olarak bildirilemez `System.Collections.Generic.IEnumerable<string>` `var` . Anahtar sözcüğü `var` kolaylık sağlamak için kullanılır. Örnekte, deyimindeki yineleme değişkeni `foreach` açıkça bir dize olarak yazılır, ancak bunun yerine kullanılarak bildirilebilecek `var` . Yineleme değişkeninin türü anonim bir tür olmadığından, öğesinin kullanımı `var` bir seçenek değildir. Unutmayın, `var` bir tür değil, türü çıkarsanmak ve atamak için derleyicinin bir yönergesi.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Uzantı Metotları](./extension-methods.md)
- [LINQ (dil ile tümleşik sorgu)](../../linq/index.md)
- [l](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
