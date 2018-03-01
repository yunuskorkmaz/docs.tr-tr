---
title: "Sub veya Function tanımlı değil (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6237ca26b06bdffa06499607e634b3222725c189
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Hata türleri](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)  
 [Sub deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)  
 [Function deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
