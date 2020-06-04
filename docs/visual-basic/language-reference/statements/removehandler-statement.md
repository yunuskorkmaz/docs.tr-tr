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
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404258"
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
- [Olaylar](../../programming-guide/language-features/events/index.md)
