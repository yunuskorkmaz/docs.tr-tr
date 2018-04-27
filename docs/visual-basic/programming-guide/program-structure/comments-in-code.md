---
title: Kod Açıklamaları (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Uncomment button
- REM statement [Visual Basic]
- comments [Visual Basic], in code
- comments [Visual Basic], Visual Basic code
- Comment button
- buttons [Visual Basic], Uncomment
- buttons [Visual Basic], Comment
- code comments [Visual Basic], Visual Basic
- Visual Basic code, comments
- comments
- code comments
ms.assetid: 90136fba-22eb-49f9-ba81-63db629b4a47
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9cd3277ea61ac9b46d8d20028bd100811988f611
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/26/2018
---
# <a name="comments-in-code-visual-basic"></a>Kod Açıklamaları (Visual Basic)
Kod örnekleri okurken Yorum simgesinin sık karşılaşırsanız (`'`). Bu simge, aşağıdaki metni yoksaymak için Visual Basic derleyici söyler veya *açıklama*. Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.  
  
 Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır. Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur. Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız. Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.  
  
 Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir. Her ikisi de aşağıdaki kodda gösterilmiştir.  
  
 [!code-vb[VbVbcnConventions#16](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_1.vb)]  
  
 Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.  
  
 [!code-vb[VbVbcnConventions#17](../../../visual-basic/programming-guide/language-features/codesnippet/VisualBasic/comments-in-code_2.vb)]  
  
## <a name="commenting-guidelines"></a>Açıklamalara İlişkin Kurallar  
 Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir. Bunlar önerilerdir; Visual Basic açıklamaları eklemek için kuralları uygulamaz. Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.  
  
|||  
|---|---|  
|Açıklama türü|Açıklama tanımı|  
|Amaç|Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)|  
|Varsayımlar|Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler|  
|Etkiler|Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler|  
|Girişler|Bağımsız değişkenin amacını belirtir|  
|Döndürür|Yordamın döndürdüğü değerleri açıklar|  
  
 Aşağıdaki hususları unutmayın:  
  
-   Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.  
  
-   Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.  
  
-   Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.  
  
 Ekleyebilir veya bir veya daha fazla kod satırı bulunmaktadır ve seçerek bir kod bloğunun açıklama simgelerini kaldırmak **açıklama** (![VisualBasicWinAppCodeEditorCommentButton](../../../visual-basic/programming-guide/program-structure/media/vacommentbutton.gif "vaCommentButton ")) ve **açıklamasını kaldırın** (![VisualStudioWinAppProjectUncommentButton](../../../visual-basic/programming-guide/program-structure/media/vauncommentbutton.gif "vaUncommentButton")) üzerinde düğmeleri **Düzenle**  araç.  
  
> [!NOTE]
>  Metinle koyarak kodunuzu yorumlar ekleyebilirsiniz `REM` anahtar sözcüğü. Ancak, `'` simgesi ve **açıklama**/**açıklamasını kaldırın** düğmelerini kullanın ve daha az alan ve bellek gerektirir daha kolay olur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [XML açıklamaları ile kodunuzu belgeleme](http://msdn.microsoft.com/magazine/dd722812.aspx)  
 [Nasıl yapılır: XML Belgesi Oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)  
 [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [REM Deyimi](../../../visual-basic/language-reference/statements/rem-statement.md)
