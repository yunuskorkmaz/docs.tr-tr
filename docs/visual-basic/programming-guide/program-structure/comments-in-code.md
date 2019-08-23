---
title: Kod Açıklamaları (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 3635d52532789133a345d9a9228efae869c8c223
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945612"
---
# <a name="comments-in-code-visual-basic"></a>Kod Açıklamaları (Visual Basic)
Kod örneklerini okurken genellikle açıklama simgesiyle (`'`) karşılaşırsınız. Bu simge, Visual Basic derleyicisine onu izleyen metni veya *yorumu*yoksaymasını söyler. Açıklamalar, okuyan kişinin yararına olması için koda eklenmiş kısa ve açıklayıcı notlardır.  
  
 Tüm yordamlara, ilgili yordamın işlevsel özelliklerini (neler yaptığını) açıklayan kısa bir açıklama ile başlanması iyi bir programlama uygulamasıdır. Bu hem sizin yararınıza, hem de kodu inceleyen herhangi bir kişinin yararına olur. Gerçekleştirme ayrıntılarını (yordamın bunu nasıl yaptığı), işlevsel özellikleri anlatan açıklamalardan ayırmalısınız. Açıklamaya gerçekleştirme ayrıntılarını eklediğinizde, işlevi güncelleştirirken bunları da güncelleştirmeyi unutmayın.  
  
 Açıklamalar aynı satırdaki bir deyimi izleyebilir veya tüm bir satırı kaplayabilir. Her ikisi de aşağıdaki kodda gösterilmiştir.  
  
 [!code-vb[VbVbcnConventions#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#16)]  
  
 Açıklamanız için birden fazla satır gerekiyorsa, aşağıdaki örnekte gösterildiği gibi her satırda açıklama sembolünü kullanın.  
  
 [!code-vb[VbVbcnConventions#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnConventions/VB/Class1.vb#17)]  
  
## <a name="commenting-guidelines"></a>Açıklamalara İlişkin Kurallar  
 Aşağıdaki tabloda, kodun bir bölümünden önce hangi tür açıklamaların gelebileceğine dair genel kurallar verilmektedir. Bunlar önerilerdir; Visual Basic, yorum eklemek için kuralları zorlamaz. Hem sizin, hem de kodu okuyan herhangi bir kişinin işine en çok yarayacak şeyleri yazın.  
  
|||  
|---|---|  
|Açıklama türü|Açıklama tanımı|  
|Amaç|Yordamın ne yaptığını açıklar (bunu nasıl yaptığını değil)|  
|Varsayımlar|Her bir dış bağımsız değişkeni, denetimi, dosya açmayı veya yordamın erişim sağladığı diğer öğeyi listeler|  
|Etkiler|Her bir etkilenen dış bağımsız değişkeni, denetimi veya dosyayı ve sahip olduğu etkiyi (bu etki bariz değilse) listeler|  
|Girişler|Bağımsız değişkenin amacını belirtir|  
|Döndürür|Yordamın döndürdüğü değerleri açıklar|  
  
 Aşağıdaki hususları unutmayın:  
  
- Her önemli değişken bildiriminin önünde, bildirilen değişkenin kullanımını anlatan bir açıklama bulunmalıdır.  
  
- Değişkenler, denetimler ve yordamlar, yalnızca karmaşık gerçekleştirme ayrıntıları için açıklamaya gerek duyulacak şekilde yeterince açık adlandırılmalıdır.  
  
- Açıklamalar, aynı satırdaki bir satır devamlılığı dizisinden sonra gelemez.  
  
 Bir veya daha fazla kod satırı seçip **açıklamayı** seçerek (![Visual Studio 'da Visual Basic Açıklama düğmesi) ve açıklama ' ![yı seçerek bir kod bloğu için açıklama sembolleri ekleyebilir veya kaldırabilirsiniz.](./media/comments-in-code/visual-basic-comment-button.gif) Visual Studio 'da temel açıklama Kaldır düğmesi. ) düğmelerini düzenleyin. ](./media/comments-in-code/visual-basic-uncomment-button.gif)  
  
> [!NOTE]
> Ayrıca, metin `REM` anahtar sözcüğüyle metinden önce kodunuza yorum ekleyebilirsiniz. Ancak simge ve **Açıklama açıklama**/ekleme düğmelerinin kullanımı daha kolaydır ve daha az alan ve bellek gerektirir. `'`  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Temel ınstınts-kodunuzu XML açıklamalarıyla belgeleme](https://msdn.microsoft.com/magazine/dd722812.aspx)
- [Nasıl yapılır: XML belgeleri oluşturma](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Açıklama Etiketleri](../../../visual-basic/language-reference/xmldoc/index.md)
- [Program Yapısı ve Kod Kuralları](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [REM Deyimi](../../../visual-basic/language-reference/statements/rem-statement.md)
