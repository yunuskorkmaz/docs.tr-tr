---
title: 'Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: a067474d6b32589a34b031d5c3ea4e5a4be55834
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611468"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma
Bu örnek, tek tek karakteri "abcd" dize oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem, hiçbir özel gereksinimleri vardır.  
  
 Söz dizimi `"a"c`, tek bir yerde `c` izleyen tırnak işaretleri içindeki tek bir karakter, karakter değişmez değeri oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Boş karakterler (eşdeğer `Chr(0)`) dize, dize kullanılırken beklenmeyen sonuçlara neden. Null karakteri ile dizeyi dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.String>
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
