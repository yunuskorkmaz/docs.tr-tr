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
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350185"
---
# <a name="addhandler-statement"></a>AddHandler Deyimi
Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a>Bölümler  
|||
|---|---|
|olay|İşlenecek etkinliğin adı.|  
|`eventhandler`|Olayı işleyen yordamın adı.|
|||
  
## <a name="remarks"></a>Açıklamalar  
 `AddHandler` ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.  
  
 `eventhandler` yordamının imzası, olay `event`imzasıyla aynı olmalıdır.  
  
 `Handles` anahtar sözcüğü ve `AddHandler` deyimin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır. `AddHandler` ifade, çalışma zamanında yordamları olaylara bağlar. Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın. Daha fazla bilgi için bkz. [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Özel olaylar için `AddHandler` ifade, olayın `AddHandler` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
