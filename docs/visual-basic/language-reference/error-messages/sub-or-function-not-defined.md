---
description: 'Daha fazla bilgi edinin: Sub veya Function tanımsız (Visual Basic)'
title: Yordam veya İşlev tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 5726e8b23283b419577c468eee2344b234493425
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641388"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub veya Function tanımlı değil (Visual Basic)

Bir `Sub` veya `Function` çağrılabilmesi için tanımlanması gerekir. Bu hatanın olası nedenleri şunlardır:  
  
- Yordam adı yanlış hatalı.  
  
- **Başvurular** iletişim kutusunda ilgili projeye açıkça bir başvuru eklemek zorunda kalmadan başka bir projeden yordam çağrılmaya çalışılıyor.  
  
- Çağıran yordama görünmeyen bir yordam belirtme.  
  
- Belirtilen kitaplıkta veya kod kaynağında olmayan bir Windows dinamik bağlantı kitaplığı (DLL) yordamını veya Macintosh kodu-kaynak yordamını bildirme.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordam adının doğru yazıldığından emin olun.  
  
2. **Başvurular** iletişim kutusunda çağırmak istediğiniz yordamı içeren projenin adını bulun. Görünmezse, aramak için, **Gözden** geçirme düğmesine tıklayın. Projenin adının solundaki onay kutusunu seçin ve ardından **Tamam**' a tıklayın.  
  
3. Yordamın adını denetleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../programming-guide/language-features/error-types.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Sub Deyimi](../statements/sub-statement.md)
- [Function Deyimi](../statements/function-statement.md)
