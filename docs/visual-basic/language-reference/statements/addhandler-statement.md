---
title: AddHandler ekstresi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: 95277f532488b0cf56114e5ee94dc3528e3a2e02
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004537"
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
 @No__t-0 ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.  
  
 @No__t-0 yordamının imzası, olay `event` ' in imzasıyla aynı olmalıdır.  
  
 @No__t-0 anahtar sözcüğü ve `AddHandler` deyimlerinin her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklar vardır. @No__t-0 ekstresi çalışma zamanında yordamları olaylara bağlar. Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken `Handles` anahtar sözcüğünü kullanın. Daha fazla bilgi için bkz. [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).  
  
> [!NOTE]
> Özel olaylar için `AddHandler` ifadesinde olayın `AddHandler` erişimcisi çağırılır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RemoveHandler Deyimi](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [İşlendiğini](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Event Deyimi](../../../visual-basic/language-reference/statements/event-statement.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
