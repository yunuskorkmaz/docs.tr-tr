---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 1ce5c793a09df34ac17e70e3253e98108bf76fb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59321488"
---
# <a name="end-of-statement-expected"></a>Deyim sonu bekleniyor
Deyim sözdizimi kurallarına göre tamamlandı, ancak ek bir programlama öğesi deyimi tamamlar öğesi izler. Bir satır Sonlandırıcı her deyim sonunda gereklidir.
  
 Bir satır Sonlandırıcı karakterleri bir Visual Basic kaynak dosyası satırlarına böler. Unicode satır başı dönüş karakteri (& HD), satır sonlandırıcılar örnekleri olan Unicode satır besleme karakteri (& HA) ve Unicode satır başı karakteri sonrasında Unicode satır besleme karakteri döndürür. Satır sonlandırıcılar hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **Hata Kimliği:** BC30205
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
  
1. İki farklı deyimleri aynı satırda yanlışlıkla konmuş olmadığını denetleyin.
  
2. Bir satır Sonlandırıcı bildirimi tamamlayan öğeden sonra ekleyin.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
