---
description: "Hakkında daha fazla bilgi edinin: BC31122: ' Custom ' değiştiricisi açık temsilci türleri olmadan belirtilen olaylarda geçerli değildir"
title: "'Custom' değiştiricisi açık temsilci türleri olmadan bildirilen olaylarda geçerli değil"
ms.date: 07/20/2015
f1_keywords:
- vbc31122
- bc31122
helpviewer_keywords:
- BC31122
ms.assetid: 6911f0d1-641a-473b-906d-8ee5681194be
ms.openlocfilehash: 6cbddd31dfa9c923038f8ea706bfc49233574cfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796684"
---
# <a name="bc31122-custom-modifier-is-not-valid-on-events-declared-without-explicit-delegate-types"></a>BC31122: ' Custom ' değiştiricisi açık temsilci türleri olmadan belirtilen olaylarda geçerli değil

Özel olmayan bir olaydan farklı olarak, `Custom Event` bildirim, `As` olayın temsilci türünü açıkça belirten olay adından sonra bir yan tümce gerektirir.

 Özel olmayan olaylar `As` , bir yan tümce ve açık bir temsilci türü ile ya da olay adından hemen sonra gelen bir parametre listesi ile tanımlanabilir.

 **Hata kimliği:** BC31122

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. Özel olayla aynı parametre listesine sahip bir temsilci tanımlayın.

     Örneğin, `Custom Event` tarafından tanımlanmışsa, `Custom Event Test(ByVal sender As Object, ByVal i As Integer)` ilgili temsilci aşağıdaki gibi olacaktır.

     [!code-vb[VbVbalrEventError#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#18)]

2. Özel olayın parametre listesini, `As` temsilci türünü belirten bir yan tümce ile değiştirin.

     Örnekle devam edildiğinde, `Custom Event` bildirim aşağıdaki şekilde yeniden yazılır.

     [!code-vb[VbVbalrEventError#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#19)]

## <a name="example"></a>Örnek

 Bu örnek bir bildirir `Custom Event` ve bir `As` temsilci türü ile gerekli yan tümceyi belirtir.

 [!code-vb[VbVbalrEventError#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEventError/VB/VbVbalrEventError.vb#2)]

## <a name="see-also"></a>Ayrıca bkz.

- [Event Deyimi](../statements/event-statement.md)
- [Delegate Deyimi](../statements/delegate-statement.md)
- [Ekinlikler](../../programming-guide/language-features/events/index.md)
