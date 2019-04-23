---
title: Sub veya Function tanımlı değil (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 397648618ea3764efafb5cff41deaef320bbeff3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59294684"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub veya Function tanımlı değil (Visual Basic)
A `Sub` veya `Function` çağrılması için tanımlanmalıdır. Bu hatanın olası nedenleri şunlardır:  
  
-   Yordam adı yazım hatası.  
  
-   Bu projeye bir başvuru eklemeden açıkça başka bir projeden bir yordam çağırma çalışılırken **başvuruları** iletişim kutusu.  
  
-   Çağıran yordama görünür değil bir yordam belirtme.  
  
-   Bir Windows dinamik bağlantı kitaplığı (DLL) yordamı veya belirtilen kitaplık veya kod kaynağı Macintosh kod kaynak yordamı bildirme.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordam adının doğru yazıldığından emin olun.  
  
2. Bulmak istediğiniz çağırmak için yordam içeren projenin adı **başvuruları** iletişim kutusu. Görünmüyorsa, tıklayın **Gözat** aramak için düğme. Proje adının sol tarafındaki onay kutusunu işaretleyin ve ardından **Tamam**.  
  
3. Yordam adını kontrol edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
