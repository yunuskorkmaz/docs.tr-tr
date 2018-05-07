---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 104b329011d69e10a2926f31ce5d296759a3cce8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)
Bu örnek, tek tek karakteri "abcd" dize oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-create-a-string-from-an-array-of-char-values_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu yöntem, özel bir gereksinimi yoktur.  
  
 Sözdizimi `"a"c`, tek bir yerde `c` tırnak işaretleri içindeki tek bir karakter izler, bir karakter değişmez değer oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Boş karakterler (eşdeğer `Chr(0)`) dizesinde dize kullanırken beklenmeyen sonuçlara neden. Null karakter dizesiyle dahil edilir, ancak bazı durumlarda null karakterden sonraki karakterler görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String>  
 [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
