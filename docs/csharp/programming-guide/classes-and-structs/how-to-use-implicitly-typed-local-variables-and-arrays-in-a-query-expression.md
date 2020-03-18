---
title: Sorgu ifadesinde örtülü olarak yazılan yerel değişkenler ve diziler nasıl kullanılır - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- implicitly-typed local variables [C#], how to use
ms.assetid: 6b7354d2-af79-427a-b6a8-f74eb8fd0b91
ms.openlocfilehash: f4ff71fc4dc1a0b2affa1f032ab1d3d6bb04d297
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705567"
---
# <a name="how-to-use-implicitly-typed-local-variables-and-arrays-in-a-query-expression-c-programming-guide"></a>Sorgu ifadesinde (C# Programlama Kılavuzu) örtülü olarak yazılan yerel değişkenler ve diziler nasıl kullanılır?
Derleyicinin yerel değişkenin türünü belirlemesini istediğinizde örtülü olarak yazılan yerel değişkenleri kullanabilirsiniz. Sorgu ifadelerinde genellikle kullanılan anonim türleri depolamak için örtülü olarak yazılan yerel değişkenleri kullanmanız gerekir. Aşağıdaki örnekler, sorgularda örtülü olarak yazılan yerel değişkenlerin hem isteğe bağlı hem de gerekli kullanımlarını göstermektedir.  
  
 Örtülü olarak yazılan yerel değişkenler [var](../../language-reference/keywords/var.md) bağlamsal anahtar kelime kullanılarak bildirilir. Daha fazla bilgi için bkz: [Örtülü Olarak Yazılan Yerel Değişkenler](./implicitly-typed-local-variables.md) ve Örtülü Olarak Yazılan [Diziler.](../arrays/implicitly-typed-arrays.md)  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, anahtar kelimenin `var` gerekli olduğu yaygın bir senaryo gösterilmektedir: anonim türlerin bir dizi sini oluşturan bir sorgu ifadesi. Bu senaryoda, anonim tür için bir tür `foreach` adı erişiminiz olmadığından, ifadedeki hem sorgu değişkeni hem de yineleme değişkeni kullanılarak `var` örtülü olarak yazılmalıdır. Anonim türleri hakkında daha fazla bilgi için [Bkz. Anonim Türleri.](./anonymous-types.md)  
  
 [!code-csharp[csProgGuideLINQ#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#32)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte, `var` anahtar kelime benzer bir durumda kullanılır, ancak `var` kullanımı isteğe bağlıdır. Bir `student.LastName` dize olduğundan, sorgunun yürütülmesi dizeleri bir dizi döndürür. Bu nedenle, `queryID` türü `System.Collections.Generic.IEnumerable<string>` yerine olarak `var`ilan edilebilir. Anahtar `var` kelime kolaylık sağlamak için kullanılır. Örnekte, `foreach` deyimdeki yineleme değişkeni açıkça dize olarak yazılır, ancak bunun yerine `var`kullanılarak bildirilebilir. Yineleme değişkeninin türü anonim bir tür olmadığından, kullanımı `var` bir seçenektir, gereksinim değil. Unutmayın, `var` kendisi bir tür değil, derlemeye bir yönerge çıkarve tür atamak için.  
  
 [!code-csharp[csProgGuideLINQ#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#33)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Genişletme Yöntemleri](./extension-methods.md)
- [LINQ (Dil-Entegre Sorgu)](../../linq/index.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
