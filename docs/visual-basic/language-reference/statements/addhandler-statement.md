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
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408490"
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
|event|İşlenecek etkinliğin adı.|  
|`eventhandler`|Olayı işleyen yordamın adı.|
|||
  
## <a name="remarks"></a>Açıklamalar  
 `AddHandler`Ve `RemoveHandler` deyimleri, program yürütme sırasında herhangi bir zamanda olay işlemeyi başlatıp durdurmalarını sağlar.  
  
 Yordamın imzası, `eventhandler` olayın imzasıyla aynı olmalıdır `event` .  
  
 `Handles`Anahtar sözcüğü ve `AddHandler` deyimleri her ikisi de belirli olayları işleyen belirli yordamları belirtmenizi sağlar, ancak farklılık vardır. `AddHandler`İfade, çalışma zamanında yordamları olaylara bağlar. `Handles`Belirli bir olayı işlediğini belirtmek için bir yordam tanımlarken anahtar sözcüğünü kullanın. Daha fazla bilgi için bkz. [Handles](handles-clause.md).  
  
> [!NOTE]
> Özel olaylar için, `AddHandler` ifade olayın `AddHandler` erişimcisini çağırır. Özel olaylar hakkında daha fazla bilgi için bkz. [Event deyimi](event-statement.md).  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [RemoveHandler Deyimi](removehandler-statement.md)
- [Handles](handles-clause.md)
- [Event Deyimi](event-statement.md)
- [Olaylar](../../programming-guide/language-features/events/index.md)
