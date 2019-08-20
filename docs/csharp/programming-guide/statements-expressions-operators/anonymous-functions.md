---
title: Anonim işlevler- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: 078596dcbfd907be53cae2ab3e7dcaa9e311c3f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588823"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonim işlevler (C# Programlama Kılavuzu)

Anonim bir işlev, bir temsilci türünün beklendiği her yerde kullanılabilecek bir "satır içi" deyim veya ifadedir. Adlandırılmış bir temsilciyi başlatmak veya bir yöntem parametresi olarak adlandırılmış bir temsilci türü yerine bunu geçirmek için kullanabilirsiniz.

Anonim bir işlev oluşturmak için bir [lambda ifadesi](lambda-expressions.md) veya [anonim yöntem](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz. Satır içi kod yazmak için daha kısa ve açıklayıcı bir yol sağlayan lambda ifadeleri kullanmanızı öneririz. Anonim yöntemlerin aksine, bazı lambda ifadesi türleri ifade ağacı türlerine dönüştürülebilir.

## <a name="the-evolution-of-delegates-in-c"></a>C 'deki temsilcilerin evrimi\#

 1,0 C# ' de, bir temsilci örneğini kodun başka bir yerinde tanımlanmış bir yöntemle açıkça başlatarak oluşturdunuz. C#2,0, anonim yöntemler kavramını bir temsilci çağrısında yürütülebilecek adlandırılmamış satır içi deyimler yazmak için bir yol olarak sunmuştur. C#3,0, anonim yöntemlere kavram olarak benzeyen, ancak daha açıklayıcı ve kısa olan lambda ifadeleri sunmuştur. Bu iki özellik topluca *Anonim işlevler*olarak bilinir. Genel olarak, .NET Framework sürüm 3,5 ve üstünü hedefleyen uygulamalar Lambda ifadelerini kullanmalıdır.  
  
 Aşağıdaki örnek 1,0 ile C# C# 3,0 arasında temsilci oluşturma gelişini göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Deyimler, İfadeler ve İşleçler](./index.md)
- [Lambda İfadeleri](./lambda-expressions.md)
- [Temsilciler](../delegates/index.md)
- [İfade ağaçları (C#)](../concepts/expression-trees/index.md)
