---
title: unchecked anahtar sözcüğü - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unchecked_CSharpKeyword
- unchecked
helpviewer_keywords:
- unchecked keyword [C#]
ms.assetid: 0c021f7c-923f-4b3d-a58f-55336f5ac27e
ms.openlocfilehash: 44301333f7a36e6b0baa6ea9e089d930bb485a45
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660482"
---
# <a name="unchecked-c-reference"></a>unchecked (C# Başvurusu)

`unchecked` Anahtar sözcüğü, Tamsayı türünde aritmetik işlemler ve dönüştürmeler için taşma denetimi gizlemek için kullanılır.

Bir ifade hedef türün aralığı dışında bir değer veriyorsa işaretlenmemiş bir bağlamda taşma işaretlenmemiştir. Örneğin, aşağıdaki örnekte hesaplama yapıldığından bir `unchecked` blok veya ifade, bir tamsayı göz ardı edilir için sonuç çok büyük olduğunu ve `int1` -2,147,483,639 değeri atanır.

[!code-csharp[csrefKeywordsChecked#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#5)]

Varsa `unchecked` ortam kaldırılır, bir derleme hatası oluşur. İfadenin tüm koşulları sabitleri olduğundan overflow derleme zamanında algılanabilir.

Sabit olmayan terimleri içeren ifadeler, derleme zamanında varsayılan olarak işaretli ve çalışma zamanı. Bkz: [işaretli](checked.md) denetlenmiş bir ortamda etkinleştirme hakkında bilgi için.

Taşma sürüyor, durumlarda denetlenmeyen kod kullanımı için denetimi olduğundan, tehlike olduğu taşma performansı iyileştirebilir. Ancak, denetlenmiş bir ortamda taşma olasılığı varsa kullanılmalıdır.

## <a name="example"></a>Örnek

Bu örnek nasıl kullanılacağını gösterir `unchecked` anahtar sözcüğü.

[!code-csharp[csrefKeywordsChecked#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsChecked/CS/csrefKeywordsChecked.cs#2)]

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../../csharp/language-reference/index.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [İşaretli ve İşaretsiz](checked-and-unchecked.md)
- [checked](checked.md)