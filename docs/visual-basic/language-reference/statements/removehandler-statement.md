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
ms.openlocfilehash: c1e6ffec64bc01936955a2e94aa9c110b317109f
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925172"
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [AddHandler Deyimi](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
