---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 03138a851afc55f735cc66edeb345817428a0452
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344394"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)
Bu örnek, bağımsız karakterlerden "abcd" dizesini oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu yöntemin özel gereksinimleri yoktur.  
  
 Tek bir `c` tek bir karakteri tırnak işaretleri içinde izleyen `"a"c`sözdizimi, bir karakter sabit değeri oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dizedeki null karakterler (`Chr(0)`eşdeğerdir), dize kullanılırken beklenmeyen sonuçlara yol açabilir. Dize ile null karakter dahil edilecek, ancak null karakteri izleyen karakterler bazı durumlarda görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- [Char Veri Türü](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
