---
title: Anonim işlevler-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: c99aaf4f35d2d294a9f07de54129bb3b4fbfbfde
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241909"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonim işlevler (C# Programlama Kılavuzu)

Anonim bir işlev, bir temsilci türünün beklendiği her yerde kullanılabilecek bir "satır içi" deyim veya ifadedir. Adlandırılmış bir temsilciyi başlatmak veya bir yöntem parametresi olarak adlandırılmış bir temsilci türü yerine bunu geçirmek için kullanabilirsiniz.

Anonim bir işlev oluşturmak için bir [lambda ifadesi](lambda-expressions.md) veya [anonim yöntem](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz. Satır içi kod yazmak için daha kısa ve açıklayıcı bir yol sağlayan lambda ifadeleri kullanmanızı öneririz. Anonim yöntemlerin aksine, bazı lambda ifadesi türleri ifade ağacı türlerine dönüştürülebilir.

## <a name="the-evolution-of-delegates-in-c"></a>C 'deki temsilcilerin evrimi\#

 C# 1,0 ' de, bir temsilcinin örneğini kodun başka bir yerinde tanımlanmış bir yöntemle açıkça başlatarak oluşturdunuz. C# 2,0, anonim yöntemler kavramını bir temsilci çağrısında yürütülebilecek adlandırılmamış satır içi deyimler yazmak için bir yol olarak getirmiştir. C# 3,0, anonim metotlar kavramı, ancak daha açıklayıcı ve kısa bir kavram gibi lambda ifadeleri getirmiştir. Bu iki özellik topluca *Anonim işlevler*olarak bilinir. Genel olarak, .NET Framework 3,5 veya sonraki bir sürümü hedefleyen uygulamalar Lambda ifadelerini kullanmalıdır.  
  
 Aşağıdaki örnek, c# 1,0 ' den c# 3,0 ' e temsilci oluşturma gelişini göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler, Ifadeler ve Işleçler](./index.md)
- [Lambda Ifadeleri](./lambda-expressions.md)
- [Temsilciler](../delegates/index.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
