---
title: Adlandırılmış ve anonim yöntemler ile Temsilciler-C# Programlama Kılavuzu
description: Adlandırılmış ve anonim yöntemlere sahip Temsilciler hakkında bilgi edinin. Kod örneklerine bakın ve kullanılabilir ek kaynakları görüntüleyin.
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: d8d2c6d8c7792b81f2fc2e25d0836e3780e58e52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202506"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Adlandırılmış ve Anonim Yöntemler ile Temsilciler (C# Programlama Kılavuzu)

Bir [temsilci](../../language-reference/builtin-types/reference-types.md) , adlandırılmış bir yöntemle ilişkilendirilebilir. Adlandırılmış bir yöntemi kullanarak bir temsilciyi örneklediğinizde, yöntemi parametre olarak geçirilir, örneğin:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Bu, adlandırılmış bir yöntem kullanılarak çağrılır. Adlandırılmış bir yöntemle oluşturulan temsilciler [statik](../../language-reference/keywords/static.md) bir yöntem veya örnek yöntemi kapsülleyebilirsiniz. Adlandırılmış Yöntemler C# ' nin önceki sürümlerinde bir temsilci örneketmenin tek yoludur. Bununla birlikte, yeni bir yöntemin oluşturulması istenmeyen ek yüktür bir durumda, C# bir temsilci örneklemenize ve her çağrıldığında temsilcinin işlemesini sağlayacak bir kod bloğunu hemen belirtmenize olanak sağlar. Blok bir lambda ifadesi veya anonim bir yöntem içerebilir. Daha fazla bilgi için bkz. [Anonim işlevler](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Açıklamalar  

 Temsilci parametresi olarak geçirdiğiniz yöntemin, temsilci bildirimiyle aynı imzaya sahip olması gerekir.  
  
 Bir temsilci örneği, statik veya örnek yöntemini kapsülleyebilirsiniz.  
  
 Temsilci bir [Out](../../language-reference/keywords/out-parameter-modifier.md) parametresi kullanabilse de, hangi temsilcinin çağrlanmasını bilemediğinizde çok noktaya yayın olay temsilcilerle kullanımını önermiyoruz.  
  
## <a name="example-1"></a>Örnek 1  

 Aşağıda, bir temsilciyi bildirme ve kullanma konusunda basit bir örnek verilmiştir. Hem temsilcinin hem de `Del` ilişkili yöntemin `MultiplyNumbers` aynı imzaya sahip olduğuna dikkat edin  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Örnek 2  

 Aşağıdaki örnekte, bir temsilci hem statik hem de örnek yöntemlerine eşlenir ve her birinden belirli bilgileri döndürür.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Temsilciler](./index.md)
- [Temsilcileri birleştirme (çok noktaya yayın temsilcileri)](./how-to-combine-delegates-multicast-delegates.md)
- [Olaylar](../events/index.md)
