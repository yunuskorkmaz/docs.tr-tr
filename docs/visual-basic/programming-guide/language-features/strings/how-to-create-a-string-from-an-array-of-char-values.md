---
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: d9ec897467f0caac0afc089a028516c0316a2bda
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410599"
---
# <a name="how-to-create-a-string-from-an-array-of-char-values-visual-basic"></a>Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma (Visual Basic)
Bu örnek, bağımsız karakterlerden "abcd" dizesini oluşturur.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbVbalrStrings#61](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#61)]  
  
## <a name="compile-the-code"></a>Kodu derle  
 Bu yöntemin özel gereksinimleri yoktur.  
  
 Tek bir `"a"c` `c` karakteri tırnak işareti içinde izleyen sözdizimi, bir karakter sabit değeri oluşturmak için kullanılır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 Dizedeki null karakterler (eşdeğer `Chr(0)` ), dize kullanılırken beklenmeyen sonuçlara neden olur. Dize ile null karakter dahil edilecek, ancak null karakteri izleyen karakterler bazı durumlarda görüntülenmez.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String>
- [Char Veri Türü](../../../language-reference/data-types/char-data-type.md)
- [Veri türleri](../data-types/index.md)
