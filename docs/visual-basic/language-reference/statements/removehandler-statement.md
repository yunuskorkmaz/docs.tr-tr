---
title: RemoveHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: a815241f20be12b3b7b4f2b87d50a8965021bbf0
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90871933"
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

 `AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında istediğiniz zaman belirli bir olay için olay işlemeyi başlatıp durdurmalarını sağlar.  
  
> [!NOTE]
> Özel olaylar için, `RemoveHandler` ifade olayın `RemoveHandler` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).  
  
## <a name="example"></a>Örnek  

 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [AddHandler Deyimi](addhandler-statement.md)
- [Handles](handles-clause.md)
- [Event Deyimi](event-statement.md)
- [Ekinlikler](../../programming-guide/language-features/events/index.md)
