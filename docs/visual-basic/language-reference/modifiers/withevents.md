---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 240058a534456ae20c9c129a068bae575ac45eda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596014"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Bir veya daha fazla bildirilen üye değişkenleri olayları yükseltebilirsiniz bir sınıfın bir örneğine başvuru belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir değişken kullanarak tanımlandığında `WithEvents`, bir yöntem kullanarak değişkenin olayları işleme bildirimli olarak belirtebilirsiniz `Handles` anahtar sözcüğü.  
  
 Kullanabileceğiniz `WithEvents` yalnızca düzeyinde sınıfı veya modülü. Bu bildirimi bağlamının anlamına gelir bir `WithEvents` değişkeni bir sınıf veya modülü olmalıdır ve kaynak dosyasını, ad alanı, yapı veya yordam olamaz.  
  
 Kullanamazsınız `WithEvents` yapısı üyede.  
  
 Yalnızca bağımsız değişkenleri bildirebilir — değil diziler — ile `WithEvents`.  
  
## <a name="rules"></a>Kurallar  
  
-   **Öğe türleri.** Bildirmelisiniz `WithEvents` bunlar kabul edebilmesi için nesne değişkenleri olmasını değişkenleri sınıf örnekleri. Ancak, bunları olarak bildiremezsiniz `Object`. Bunları olaylar oluşturabilir belirli sınıfı olarak bildirilmelidir.  
  
 `WithEvents` Bu bağlamda değiştirici kullanılabilir: [Dim deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
