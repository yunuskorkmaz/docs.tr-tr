---
description: unchecked anahtar sözcüğü-C# başvurusu
title: unchecked anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: bb66639e3657b247b9ebcad1594daf1f57a5c76b
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141991"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)

`unchecked`Anahtar sözcüğü, tamsayı türü aritmetik işlemler ve dönüştürmeler için taşma denetlemeyi gizlemek için kullanılır.

İşaretlenmemiş bir bağlamda, bir ifade hedef türü aralığının dışında bir değer üretirse, taşma işaretlenir. Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` blok veya ifadede gerçekleştirildiğinden, sonucun bir tamsayı için çok büyük olması ve `int1` -2.147.483.639 değeri atanır.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

`unchecked`Ortam kaldırılırsa, bir derleme hatası oluşur. İfadenin tüm terimleri sabitler olduğundan, derleme sırasında taşma tespit edilebilir.

Sabit olmayan terimleri içeren ifadeler, derleme zamanında ve çalışma zamanında varsayılan olarak işaretli değildir. Denetlenen bir ortamı etkinleştirme hakkında bilgi için bkz. [denetlenir](checked.md) .

Taşma için denetim zaman alacağından, hiçbir tehlike olmaması durumunda Denetlenmemiş kod kullanımı performansı iyileştirebilir. Ancak, taşma olasılığa karşı, denetlenen bir ortam kullanılmalıdır.

## <a name="example"></a>Örnek

Bu örnek, anahtar sözcüğünün nasıl kullanılacağını gösterir `unchecked` .

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Checked ve Unchecked](checked-and-unchecked.md)
- [edildikten](checked.md)
