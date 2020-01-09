---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: bf37ceba901e712df10ad4b39f9ad74194843136
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346765"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)
Bu örnek, bağımsız karakterlerden "abcd" dizesini oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Kod derleme  
 Bu yöntemin özel gereksinimleri yoktur.  
  
 Tek bir `c` tek bir karakteri tırnak işaretleri içinde izleyen `"a"c`sözdizimi, bir karakter sabit değeri oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dizedeki null karakterler (`Chr(0)`eşdeğerdir), dize kullanılırken beklenmeyen sonuçlara yol açabilir. Dize ile null karakter dahil edilecek, ancak null karakteri izleyen karakterler bazı durumlarda görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
