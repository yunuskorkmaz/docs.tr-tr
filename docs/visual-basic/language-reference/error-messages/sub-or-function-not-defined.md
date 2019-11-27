---
title: Yordam veya İşlev tanımlı değil
ms.date: 07/20/2015
f1_keywords:
- vbrID35
ms.assetid: 661fdb90-ee7d-40ce-b30b-5e7267bd957a
ms.openlocfilehash: 8b81460eccb6be8baa2ea7bc68d0f80c9d16398e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349570"
---
# <a name="sub-or-function-not-defined-visual-basic"></a>Sub veya Function tanımlı değil (Visual Basic)
Çağrılabilmesi için bir `Sub` veya `Function` tanımlanmalıdır. Bu hatanın olası nedenleri şunlardır:  
  
- Yordam adı yanlış hatalı.  
  
- **Başvurular** iletişim kutusunda ilgili projeye açıkça bir başvuru eklemek zorunda kalmadan başka bir projeden yordam çağrılmaya çalışılıyor.  
  
- Çağıran yordama görünmeyen bir yordam belirtme.  
  
- Belirtilen kitaplıkta veya kod kaynağında olmayan bir Windows dinamik bağlantı kitaplığı (DLL) yordamını veya Macintosh kodu-kaynak yordamını bildirme.  
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için  
  
1. Yordam adının doğru yazıldığından emin olun.  
  
2. **Başvurular** iletişim kutusunda çağırmak istediğiniz yordamı içeren projenin adını bulun. Görünmezse, aramak için, **Gözden** geçirme düğmesine tıklayın. Projenin adının solundaki onay kutusunu seçin ve ardından **Tamam**' a tıklayın.  
  
3. Yordamın adını denetleyin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Hata Türleri](../../../visual-basic/programming-guide/language-features/error-types.md)
- [Bir projedeki başvuruları yönetme](/visualstudio/ide/managing-references-in-a-project)
- [Sub Deyimi](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function Deyimi](../../../visual-basic/language-reference/statements/function-statement.md)
