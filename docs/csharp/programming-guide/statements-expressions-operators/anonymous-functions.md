---
title: Anonim işlevler-C# Programlama Kılavuzu
description: Anonim işlevler hakkında bilgi edinin. Anonim bir işlev oluşturmak için bir lambda ifadesi veya anonim yöntem kullanabilirsiniz.
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 1fde7d535054f09d55018a010468776622ebfba7
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88063269"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonim işlevler (C# Programlama Kılavuzu)

Anonim bir işlev, bir temsilci türünün beklendiği her yerde kullanılabilecek bir "satır içi" deyim veya ifadedir. Adlandırılmış bir temsilciyi başlatmak veya bir yöntem parametresi olarak adlandırılmış bir temsilci türü yerine bunu geçirmek için kullanabilirsiniz.

Anonim bir işlev oluşturmak için bir [lambda ifadesi](../../language-reference/operators/lambda-expressions.md) veya [anonim yöntem](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz. Satır içi kod yazmak için daha kısa ve açıklayıcı bir yol sağlayan lambda ifadeleri kullanmanızı öneririz. Anonim yöntemlerin aksine, bazı lambda ifadesi türleri ifade ağacı türlerine dönüştürülebilir.

## <a name="the-evolution-of-delegates-in-c"></a>C 'deki temsilcilerin evrimi\#

 C# 1,0 ' de, bir temsilcinin örneğini kodun başka bir yerinde tanımlanmış bir yöntemle açıkça başlatarak oluşturdunuz. C# 2,0, anonim yöntemler kavramını bir temsilci çağrısında yürütülebilecek adlandırılmamış satır içi deyimler yazmak için bir yol olarak getirmiştir. C# 3,0, anonim metotlar kavramı, ancak daha açıklayıcı ve kısa bir kavram gibi lambda ifadeleri getirmiştir. Bu iki özellik topluca *Anonim işlevler*olarak bilinir. Genel olarak, .NET Framework 3,5 veya sonraki bir sürümü hedefleyen uygulamalar Lambda ifadelerini kullanmalıdır.  
  
 Aşağıdaki örnek, c# 1,0 ' den c# 3,0 ' e temsilci oluşturma gelişini göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler, Ifadeler ve Işleçler](./index.md)
- [Lambda Ifadeleri](../../language-reference/operators/lambda-expressions.md)
- [Temsilciler](../delegates/index.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
