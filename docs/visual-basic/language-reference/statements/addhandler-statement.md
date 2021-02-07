---
description: 'Daha fazla bilgi edinin: AddHandler ekstresi'
title: AddHandler Deyimi
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: c0c34abd7ff225765ab36278825a555e2b84b0d1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674109"
---
# <a name="addhandler-statement"></a>AddHandler Deyimi

Çalışma zamanında bir olayı olay işleyicisiyle ilişkilendirir.  
  
## <a name="syntax"></a>Syntax  
  
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
- [Ekinlikler](../../programming-guide/language-features/events/index.md)
