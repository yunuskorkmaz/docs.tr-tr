---
title: Otomatik (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Auto
helpviewer_keywords:
- Auto keyword [Visual Basic], external references
- Declare statement [Visual Basic], marshaling strings
- Auto keyword [Visual Basic]
- Auto keyword [Visual Basic], marshaling strings
ms.assetid: bf79ba95-a62c-48a5-916f-0ac7a52c13ec
ms.openlocfilehash: e4beb320b3aa0cadb790dd3ab92255496bc32f05
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802713"
---
# <a name="auto-visual-basic"></a>Otomatik (Visual Basic)
Visual Basic dizeleri dış bildirilen dış yordam adına göre .NET Framework kurallarına göre sıralaması olduğunu belirtir.  
  
 Projenizin dışında tanımlı bir yordamı çağırdığınızda, Visual Basic Derleyicisi yordamı doğru şekilde çağrılacak olmalıdır bilgilere erişimi yok. Bu bilgileri yordamı bulunduğu, nasıl tanımlandığını, çağrı sırası ve dönüş türü içeren ve isteğe bağlı olarak dize karakteri kullanır ayarlayın. [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md) bir dış yordam bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier` Kısmını `Declare` deyimi bir dış yordam çağrısı sırasında dizelerini hazırlama için karakter kümesi bilgileri sağlar. Ayrıca, Visual Basic dış dosya için dış yordam adının nasıl arama etkiler. `Auto` Değiştiricisi, Visual Basic dizeleri .NET Framework kurallarına göre sıralaması ve ilk arama yaparsanız ve büyük olasılıkla çalışma zamanı platformunun temel karakter belirlemelisiniz, dış yordam adının değiştirilmesi gerektiğini belirtir başarısız olur. Daha fazla bilgi için bkz: "Karakter kümesi" [Declare Deyimi'nin](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Herhangi bir karakter kümesi değiştiricisi belirtilmişse `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Auto` Bu bağlamda değiştirici kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
