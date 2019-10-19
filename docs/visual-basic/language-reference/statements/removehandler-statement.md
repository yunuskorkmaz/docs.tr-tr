---
title: RemoveHandler ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 47f35bd76d7734878e7b5b206b4aecd856276593
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582017"
---
# <a name="removehandler-statement"></a>RemoveHandler Deyimi
Bir olay ve olay işleyicisi arasındaki ilişkiyi kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`event`|İşlenmekte olan olayın adı.|  
|`eventhandler`|Şu anda olayı işleyen yordamın adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 @No__t_0 ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.  
  
> [!NOTE]
> Özel olaylar için `RemoveHandler` ifade, olayın `RemoveHandler` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
