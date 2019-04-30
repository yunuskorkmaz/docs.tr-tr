---
title: 'Nasıl yapılır: olay örneklerini - depolamak için Sözlük kullanma C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 03/11/2019
helpviewer_keywords:
- events [C#], storing instances in a Dictionary
ms.assetid: 9512c64d-5aaf-40cd-b941-ca2a592f0064
ms.openlocfilehash: f8522e499887398402f63c7788bbc6c6c4f57782
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710783"
---
# <a name="how-to-use-a-dictionary-to-store-event-instances-c-programming-guide"></a>Nasıl yapılır: olay örneklerini depolamak için Sözlük kullanma (C# Programlama Kılavuzu)

Bir kullanımı `add` ve `remove` özel olay erişimcilerini olan çok sayıda olay her olay için bir alan ayırma, ancak bunun yerine kullanıma sunmak için bir <xref:System.Collections.Generic.Dictionary%602> aşağıdaki örnekte gösterildiği gibi olay örneklerini depolamak için örneği. Bu yalnızca çok sayıda olay türünde, ancak çoğu olayların abone değil, beklediğiniz yararlıdır.

[!code-csharp[csProgGuideEvents#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEvents/CS/Events.cs#9)]

Bu uygulama davranışını uyan [ekleme ve kaldırma Temsilciler](~/_csharplang/spec/delegates.md#delegate-invocation) içinde C# dil belirtimi.

Unutmayın [kilit](../../language-reference/keywords/lock-statement.md) deyimi yalnızca kullanılan *erişim* olay işleyicileri sahip sözlük. Gövdesi içinde bir olay işleyicisi çağırma yoksa `lock` ifadesi olarak müşteri adayı için kilitlenme veya kilit çakışması.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Olaylar](../../../csharp/programming-guide/events/index.md)
- [Temsilciler](../../../csharp/programming-guide/delegates/index.md)
