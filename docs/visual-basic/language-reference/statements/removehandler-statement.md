---
title: RemoveHandler deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 27cdd2753507c6fc4d5c5041607e2ccb425b81b8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54560626"
---
# <a name="removehandler-statement"></a>RemoveHandler Deyimi
Bir olay bir olay işleyicisi arasındaki ilişkiyi kaldırır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`event`|İşlenen olayın adı.|  
|`eventhandler`|Şu anda olay işleme yordamın adı.|  
  
## <a name="remarks"></a>Açıklamalar  
 `AddHandler` Ve `RemoveHandler` deyimleri, programın yürütülmesi sırasında herhangi bir zamanda belirli bir olay için olay işleme durdurmak ve başlatmak sağlar.  
  
> [!NOTE]
>  Özel olaylar için `RemoveHandler` deyimi çağırır olayın `RemoveHandler` erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
