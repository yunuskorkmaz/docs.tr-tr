---
title: WithEvents (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.WithEvents
- WithEvents
helpviewer_keywords:
- WithEvents keyword [Visual Basic]
ms.assetid: 19d461f5-d72f-4de9-8c1d-0a6650316990
ms.openlocfilehash: 75d118ee2bd4918c3a936cb341864ddc5315726b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58826619"
---
# <a name="withevents-visual-basic"></a>WithEvents (Visual Basic)
Bir veya daha fazla bildirilmiş üye değişkenleri, olayları tetikleyebilen bir sınıf örneğine başvurduğunu belirtir.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir değişken kullanarak tanımlandığında `WithEvents`, bir yöntem kullanarak değişkenin olaylarını işler bildirimli olarak belirtebilirsiniz `Handles` anahtar sözcüğü.  
  
 Kullanabileceğiniz `WithEvents` yalnızca düzeyinde sınıfı veya modülü. Bildirim bağlamı başka bir deyişle bir `WithEvents` değişken bir sınıf veya modül olmalıdır ve bir kaynak dosyası, ad alanı, yapı ya da yordamın olamaz.  
  
 Kullanamazsınız `WithEvents` yapı üyesi üzerinde.  
  
 Yalnızca bağımsız değişkenleri bildirebilirsiniz; dizi değildir — ile `WithEvents`.  
  
## <a name="rules"></a>Kurallar  
  
-   **Öğe türleri.** Bildirmeniz gerekir `WithEvents` kabul edebilir, böylece nesne değişkenleri olmasını değişkenleri sınıfı örneği. Ancak, bunları olarak bildiremezsiniz `Object`. Bunları, olayları tetikleyebilen belirli sınıf olarak bildirilmelidir.  
  
 `WithEvents` Bu bağlamda değiştirici kullanılabilir: [Dim Deyimi](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İşleme](../../../visual-basic/language-reference/statements/handles-clause.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
- [Olaylar](../../../visual-basic/programming-guide/language-features/events/index.md)
