---
title: Sub veya Function tanımlı değil (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 58e90d769d5a7f2d88b5c27d1ec7d0d28c8d7b03
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub veya Function tanımlı değil (Visual Basic)
A `Sub` veya `Function` çağrılması için tanımlanmalıdır. Bu hatanın olası nedenleri şunlardır:  
  
-   Yordam adı yazım hatası.  
  
-   Bu projeye ait bir başvuru açıkça eklemeden başka bir projeden bir yordam çağırma çalışılırken **başvuruları** iletişim kutusu.  
  
-   GetTypeId yordamını görünür değil bir yordam belirtme.  
  
-   Bir Windows dinamik bağlantı kitaplığı (DLL) yordamı veya belirtilen kitaplığı veya kod kaynağında değil Macintosh kod kaynak yordamı bildirme.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1.  Yordam adının doğru yazıldığından emin olun.  
  
2.  Bulmak istediğiniz çağırmak için yordamı içeren projesinin adı **başvuruları** iletişim kutusu. Görünmüyorsa, tıklatın **Gözat** aramak için düğmesi. Proje adının solundaki onay kutusunu seçin ve ardından **Tamam**.  
  
3.  Yordam adını kontrol edin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)  
 [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
