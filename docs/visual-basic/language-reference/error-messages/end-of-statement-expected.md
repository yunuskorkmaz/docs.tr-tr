---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 36883989fe5aa0b5c70aa9ab1f7c991fab99e778
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163135"
---
# <a name="bc30205-end-of-statement-expected"></a>BC30205: for ifadesinin sonu bekleniyor

İfade sözdizimsel olarak tamamlanmıştır, ancak ek bir programlama öğesi, ifadesini tamamlayan öğesini izler. Her deyimin sonunda bir satır Sonlandırıcı gereklidir.

 Satır Sonlandırıcı Visual Basic kaynak dosyanın karakterlerini çizgilere böler. Satır sonlandırıcılar örnekleri, Unicode satır başı karakteri (&HD), Unicode satır besleme karakteri (&ha) ve ardından Unicode satır besleme karakteri ile Unicode satır başı karakteri. Satır sonlandırıcılar hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/lexical-grammar.md#line-terminators)bakın.

 **Hata kimliği:** BC30205

## <a name="to-correct-this-error"></a>Bu hatayı düzeltmek için

1. İki farklı deyimin yanlışlıkla aynı satıra yerleştirilip yerleştirilmediğini denetleyin.

2. İfadeyi tamamlayan öğeden sonra bir satır Sonlandırıcı ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [Deyimler](../../programming-guide/language-features/statements.md)
