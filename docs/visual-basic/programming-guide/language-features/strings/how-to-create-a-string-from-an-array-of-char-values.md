---
title: 'Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 0d3a4caf0967ab77de7d91470e43e52521dbd2da
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975517"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: (Visual Basic) karakter değerleri dizisinden bir dize oluşturma
Bu örnek, tek tek karakteri "abcd" dize oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem, hiçbir özel gereksinimleri vardır.  
  
 Söz dizimi `"a"c`, tek bir yerde `c` izleyen tırnak işaretleri içindeki tek bir karakter, karakter değişmez değeri oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Boş karakterler (eşdeğer `Chr(0)`) dize, dize kullanılırken beklenmeyen sonuçlara neden. Null karakteri ile dizeyi dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.String>
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
