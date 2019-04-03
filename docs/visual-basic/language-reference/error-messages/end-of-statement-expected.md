---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: ab6a4a0e6736e2af9c1fa0dd170b6aa4c42d9e4a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58817160"
---
# <a name="end-of-statement-expected"></a>Deyim sonu bekleniyor
Deyim sözdizimi kurallarına göre tamamlandı, ancak ek bir programlama öğesi deyimi tamamlar öğesi izler. Bir satır Sonlandırıcı her deyim sonunda gereklidir.
  
 Bir satır Sonlandırıcı karakterleri bir Visual Basic kaynak dosyası satırlarına böler. Unicode satır başı dönüş karakteri (& HD), satır sonlandırıcılar örnekleri olan Unicode satır besleme karakteri (& HA) ve Unicode satır başı karakteri sonrasında Unicode satır besleme karakteri döndürür. Satır sonlandırıcılar hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](~/_vblang/spec/lexical-grammar.md#line-terminators).
  
 **Hata Kimliği:** BC30205
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
  
1.  İki farklı deyimleri aynı satırda yanlışlıkla konmuş olmadığını denetleyin.
  
2.  Bir satır Sonlandırıcı bildirimi tamamlayan öğeden sonra ekleyin.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Deyimler](../../../visual-basic/programming-guide/language-features/statements.md)
