---
title: unchecked anahtar sözcüğü C# -başvuru
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: c31f1243b1394bfe826b02c14c73faf402640849
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608421"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)

Anahtar `unchecked` sözcüğü, tamsayı türü aritmetik işlemler ve dönüştürmeler için taşma denetlemeyi gizlemek için kullanılır.

İşaretlenmemiş bir bağlamda, bir ifade hedef türü aralığının dışında bir değer üretirse, taşma işaretlenir. Örneğin, aşağıdaki örnekteki hesaplama bir `unchecked` blok veya ifadede gerçekleştirildiğinden, sonucun bir tamsayı için çok büyük olması ve `int1` -2.147.483.639 değeri atanır.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

`unchecked` Ortam kaldırılırsa, bir derleme hatası oluşur. İfadenin tüm terimleri sabitler olduğundan, derleme sırasında taşma tespit edilebilir.

Sabit olmayan terimleri içeren ifadeler, derleme zamanında ve çalışma zamanında varsayılan olarak işaretli değildir. Denetlenen bir ortamı etkinleştirme hakkında bilgi için bkz. [denetlenir](checked.md) .

Taşma için denetim zaman alacağından, hiçbir tehlike olmaması durumunda Denetlenmemiş kod kullanımı performansı iyileştirebilir. Ancak, taşma olasılığa karşı, denetlenen bir ortam kullanılmalıdır.

## <a name="example"></a>Örnek

Bu örnek, `unchecked` anahtar sözcüğünün nasıl kullanılacağını gösterir.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [İşaretli ve İşaretsiz](checked-and-unchecked.md)
- [checked](checked.md)
