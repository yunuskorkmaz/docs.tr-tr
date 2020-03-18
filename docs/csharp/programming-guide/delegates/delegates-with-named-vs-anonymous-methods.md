---
title: Adlandırılmış ve Anonim Yöntemlerle Temsilciler - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 1ec366999ca6457471b705fa83f06fcde4293f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712383"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Adlandırılmış ve Anonim Yöntemler ile Temsilciler (C# Programlama Kılavuzu)
Bir [temsilci](../../language-reference/builtin-types/reference-types.md) adlı yöntemle ilişkilendirilebilir. Adlandırılmış bir yöntem kullanarak bir temsilciyi anında kullandığınızda, yöntem parametre olarak geçirilir, örneğin:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Buna adlandırılmış bir yöntem kullanılarak denir. Adlandırılmış bir yöntemle oluşturulmuş temsilciler [statik](../../language-reference/keywords/static.md) bir yöntem veya örnek yöntemi kapsajene edebilir. Adlandırılmış yöntemler, C#'ın önceki sürümlerinde bir temsilciyi anında atanın tek yoludur. Ancak, yeni bir yöntem oluşturmanın istenmeyen ek yükü olduğu bir durumda, C# bir temsilciyi anında oluşturmanızı ve çağrıldığında temsilcinin işleyecekleri bir kod bloğunu hemen belirtmenizi sağlar. Blok bir lambda ifadesi veya anonim bir yöntem içerebilir. Daha fazla bilgi için [Bkz. Anonim Fonksiyonlar.](../statements-expressions-operators/anonymous-functions.md)  
  
## <a name="remarks"></a>Açıklamalar  
 Temsilci parametresi olarak geçtiğiniz yöntem, temsilci bildirimiyle aynı imzaya sahip olmalıdır.  
  
 Bir temsilci örneği statik veya örnek yöntemini özetleyebilir.  
  
 Temsilci [çıkış](../../language-reference/keywords/out-parameter-modifier.md) parametresi kullanabilse de, hangi temsilcinin aranacağını bilmediğiniz için çok noktaya yayın olay temsilcileriyle kullanılmasını önermiyoruz.  
  
## <a name="example-1"></a>Örnek 1  
 Aşağıda, bir temsilciyi bildirme ve kullanmanın basit bir örneği verilmiştir. Hem temsilcinin `Del`hem de ilişkili yöntemin `MultiplyNumbers`aynı imzaya sahip olduğuna dikkat edin  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, bir temsilci hem statik hem de örnek yöntemleriyle eşlenir ve her birinden belirli bilgileri döndürür.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](./index.md)
- [Temsilciler nasıl birleştirilir (Çok Noktaya Yayın Temsilcileri)](./how-to-combine-delegates-multicast-delegates.md)
- [Olaylar](../events/index.md)
