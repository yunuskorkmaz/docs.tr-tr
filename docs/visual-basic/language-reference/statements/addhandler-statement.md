---
title: AddHandler Deyimi
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a>AddHandler Deyimi
Bir olayın olay işleyicisi ile çalışma zamanında ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Bölümler  
 `event`  
 İşlenecek Olay adı.  
  
 `eventhandler`  
 Olay işleme bir yordamın adı.  
  
## <a name="remarks"></a>Açıklamalar  
 `AddHandler` Ve `RemoveHandler` deyimleri program yürütme sırasında herhangi bir zamanda olay işleme durdurmak ve başlatmak izin.  
  
 İmzası `eventhandler` yordamı, olay imza eşleşmelidir `event`.  
  
 `Handles` Anahtar sözcüğü ve `AddHandler` deyimi hem belirli yordamları belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır. `AddHandler` Deyimi olaylarına yordamlar çalışma zamanında bağlanır. Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü. Daha fazla bilgi için bkz: [işleme](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Özel olaylar için `AddHandler` deyimi çağırır olayın `AddHandler` erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz: [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RemoveHandler deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
