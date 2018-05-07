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
ms.openlocfilehash: 414998b4bef526060e7ba4f584fa071fbd0acaa5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="auto-visual-basic"></a>Otomatik (Visual Basic)
Visual Basic dizeleri bildirilen dış yordamı dış adını temel alarak .NET Framework kurallarına göre sıralama belirtir.  
  
 Projenizin dışında tanımlı bir yordam çağrısı, Visual Basic derleyici doğru yordam çağrısı için gereken bilgilere erişimi yok. Bu bilgiler yordamı bulunduğu, nasıl tanımlanır, kendi arama sırası ve dönüş türü içerir ve dize karakter kullanır ayarlayın. [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md) dış bir yordam için bir başvuru oluşturur ve bu gerekli bilgileri sağlar.  
  
 `charsetmodifier` Bölümün `Declare` deyimi dış yordamı yapılan bir çağrı sırasında dizeleri sıralama için karakter kümesi bilgileri sağlar. Visual Basic dış yordamı adı için dış dosyasını nasıl arayacağını etkiler. `Auto` Değiştiricisi belirtir Visual Basic .NET Framework kurallarına göre dizeleri sıralama ve gerekir temel karakter çalışma zamanı platform ve muhtemelen kümesini belirlemelisiniz ilk arıyorsanız dış yordam adı değiştirin, başarısız olur. Daha fazla bilgi için bkz: "Karakter kümesi" [Declare deyimi](../../../visual-basic/language-reference/statements/declare-statement.md).  
  
 Herhangi bir karakter kümesi değiştiricisi belirtilirse, `Ansi` varsayılandır.  
  
## <a name="remarks"></a>Açıklamalar  
 `Auto` Bu bağlamda değiştirici kullanılabilir:  
  
 [Declare Deyimi](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Akıllı Cihaz Geliştirici Notları  
 Bu anahtar sözcük desteklenmiyor.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Anahtar Sözcükler](../../../visual-basic/language-reference/keywords/index.md)
