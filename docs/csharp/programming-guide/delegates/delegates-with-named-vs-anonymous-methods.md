---
title: Temsilcilerin Adlandırılmış ve Anonim yöntemler - C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- delegates [C#], with named vs. anonymous methods
- methods [C#], in delegates
ms.assetid: 98fa8c61-66b6-4146-986c-3236c4045733
ms.openlocfilehash: 8d3cecbaecc8cf5af1e06f29c9bb8a151523d3e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61680707"
---
# <a name="delegates-with-named-vs-anonymous-methods-c-programming-guide"></a>Temsilcilerin Adlandırılmış ve Anonim Yöntemler (C# Programlama Kılavuzu)
A [temsilci](../../../csharp/language-reference/keywords/delegate.md) adlandırılmış bir yöntemle ilişkili olabilir. Adlandırılmış bir yöntemi kullanarak bir temsilci örneğini oluştururken yöntemi örneğin bir parametre olarak geçirilir:  
  
 [!code-csharp[csProgGuideDelegates#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#1)]  
  
 Bu işlem, adlandırılmış bir yöntemi kullanılarak çağrılır. Temsilcilerin adlandırılmış bir yöntem ile oluşturulmuş ya da kapsüllemek bir [statik](../../../csharp/language-reference/keywords/static.md) yöntem veya oluşum yöntemi. Adlandırılmış yöntemler, C# ' ın önceki sürümlerinde bir temsilci tek yoludur. Ancak, yeni bir yöntem oluşturma ek yükü istenmeyen olduğu bir durumda C#, bir temsilci ve hemen çağrıldığında, bu temsilci işleyecek bir kod bloğu belirtmenize olanak sağlar. Bir lambda ifadesi veya anonim yöntemi blok içerebilir. Daha fazla bilgi için [anonim işlevler](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="remarks"></a>Açıklamalar  
 Temsilcinin parametre olarak geçen yöntemi temsilci bildirimi aynı imzaya sahip olmalıdır.  
  
 Bir temsilci örneği kapsülleyen ya da statik veya örnek yöntemi olabilir.  
  
 Temsilci kullanmanız mümkün olmakla birlikte bir [kullanıma](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametresi değil öneririz kullanımı ile çok noktaya yayın olay temsilcileri çünkü hangi temsilcinin çağrılacağı bilemezsiniz.  
  
## <a name="example-1"></a>Örnek 1  
 Bildirme ve bir temsilci kullanarak basit bir örnek verilmiştir. Dikkat her iki temsilci `Del`ve ilişkili yöntem `MultiplyNumbers`, aynı imzaya sahip  
  
 [!code-csharp[csProgGuideDelegates#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#2)]  
  
## <a name="example-2"></a>Örnek 2  
 Aşağıdaki örnekte, bir temsilci hem statik olarak eşleştirilir ve örneği her belirli bilgiler yöntemleri ve döndürür.  
  
 [!code-csharp[csProgGuideDelegates#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDelegates/CS/Delegates.cs#3)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
- [Anonim Metotlar](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Nasıl yapılır: Temsilcileri (çok noktaya yayın temsilcileri) birleştirme](../../../csharp/programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
