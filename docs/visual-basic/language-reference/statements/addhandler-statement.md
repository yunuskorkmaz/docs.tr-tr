---
title: AddHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
