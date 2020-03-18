---
title: Anonim fonksiyonlar - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- lambda expressions [C#], as anonymous functions
- anonymous functions [C#]
- anonymous methods [C#]
ms.assetid: 6ce3f04d-0c71-4728-9127-634c7e9a8365
ms.openlocfilehash: cfb0190ee263e65e8130a8925f76357a382eafa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712006"
---
# <a name="anonymous-functions-c-programming-guide"></a>Anonim işlevler (C# Programlama Kılavuzu)

Anonim işlev, temsilci türünün beklendiği her yerde kullanılabilecek bir "satır çizgisi" ifadesi veya ifadesidir. Adlandırılmış bir temsilciyi başlatmak veya yöntem parametresi olarak adlandırılmış temsilci türü yerine geçmek için kullanabilirsiniz.

Anonim bir işlev oluşturmak için [lambda ifadesini](lambda-expressions.md) veya anonim bir [yöntemi](../../language-reference/operators/delegate-operator.md) kullanabilirsiniz. Lambda ifadelerini satır içinde kod yazmak için daha kısa ve anlamlı bir şekilde kullanmanızı öneririz. Anonim yöntemlerin aksine, bazı lambda ifadeleri türlerinde ifade ağacı türlerine dönüştürülebilir.

## <a name="the-evolution-of-delegates-in-c"></a>C'de Delegelerin Evrimi\#

 C# 1.0'da, kodun başka bir yerinde tanımlanan bir yöntemle açıkça baş harfe başlayarak bir temsilci örneği oluşturdunuz. C# 2.0, bir temsilci çağırmasında yürütülebilecek adsız satır lı ifade blokları yazmanın bir yolu olarak anonim yöntemler kavramını tanıttı. C# 3.0 anonim yöntemlere benzer ama daha anlamlı ve özlü lambda ifadeler tanıttı. Bu iki özellik topluca *anonim işlevler*olarak bilinir. Genel olarak, .NET Framework sürüm 3.5 ve daha sonrasını hedefleyen uygulamalar da lambda ifadeleri kullanmalıdır.  
  
 Aşağıdaki örnek, delege oluşturmanın C# 1.0'dan C# 3.0'a evrimini göstermektedir:  
  
 [!code-csharp[csProgGuideLINQ#65](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#65)]  
  
## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [Anonim işlev ifadeleri](~/_csharplang/spec/expressions.md#anonymous-function-expressions) bölümüne bakın.
  
## <a name="see-also"></a>Ayrıca bkz.

- [İfadeler, İfadeler ve Operatörler](./index.md)
- [Lambda İfadeler](./lambda-expressions.md)
- [Temsilciler](../delegates/index.md)
- [İfade Ağaçları (C#)](../concepts/expression-trees/index.md)
