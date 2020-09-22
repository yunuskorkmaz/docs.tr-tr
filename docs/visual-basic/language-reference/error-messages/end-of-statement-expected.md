---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 9141400afc651629df381e0a655e2d7b9da2e45d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874422"
---
# <a name="end-of-statement-expected"></a>Deyim sonu bekleniyor

İfade sözdizimsel olarak tamamlanmıştır, ancak ek bir programlama öğesi, ifadesini tamamlayan öğesini izler. Her deyimin sonunda bir satır Sonlandırıcı gereklidir.
  
 Satır Sonlandırıcı Visual Basic kaynak dosyanın karakterlerini çizgilere böler. Satır sonlandırıcılar örnekleri, Unicode satır başı karakteri (&HD), Unicode satır besleme karakteri (&ha) ve ardından Unicode satır besleme karakteri ile Unicode satır başı karakteri. Satır sonlandırıcılar hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/lexical-grammar.md#line-terminators)bakın.
  
 **Hata kimliği:** BC30205
  
## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için
  
1. İki farklı deyimin yanlışlıkla aynı satıra yerleştirilip yerleştirilmediğini denetleyin.
  
2. İfadeyi tamamlayan öğeden sonra bir satır Sonlandırıcı ekleyin.
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
