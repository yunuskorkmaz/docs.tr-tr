---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords: WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68a58fd130c04f2ed0cb1f2e5b9250f6c85f120d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Anahtar sözcükler](../../../visual-basic/language-reference/keywords/index.md)  
 [Olayları](../../../visual-basic/programming-guide/language-features/events/index.md)
