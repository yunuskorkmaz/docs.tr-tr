---
title: AddHandler deyimi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: f731ff150bd901e325726fca5aa682ff1770f979
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43396493"
---
# <a name="addhandler-statement"></a>AddHandler Deyimi
Bir olay, çalışma zamanında bir olay işleyicisi ile ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Bölümler  
|||
|---|---|
|olay|İşlenecek Olay adı.|  
|`eventhandler`|Olayı işleyen bir yordamın adı.|
|||
  
## <a name="remarks"></a>Açıklamalar  
 `AddHandler` Ve `RemoveHandler` deyimleri, programın yürütülmesi sırasında herhangi bir zamanda olay işleme durdurmak ve başlatmak sağlar.  
  
 İmzası `eventhandler` yordamı olay imzası eşleşmelidir `event`.  
  
 `Handles` Anahtar sözcüğü ve `AddHandler` iki deyimi belirli bir yordam belirli olayları işleme, ancak bazı farklılıklar vardır belirtmenize olanak tanır. `AddHandler` Deyimi olayları yordamları çalışma zamanında bağlanır. Kullanım `Handles` , belirli bir olay işleme belirtmek için bir yordam tanımlarken anahtar sözcüğü. Daha fazla bilgi için [işler](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
>  Özel olaylar için `AddHandler` deyimi çağırır olayın `AddHandler` erişimcisi. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
