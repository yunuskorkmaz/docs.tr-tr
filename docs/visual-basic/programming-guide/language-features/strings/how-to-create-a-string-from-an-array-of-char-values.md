---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: Char değerleri dizisinden dize oluşturma (Visual Basic)'
title: 'Nasıl yapılır: Karakter Değerleri Dizisinden Bir Dize Oluşturma'
ms.date: 07/20/2015
helpviewer_keywords:
- examples [Visual Basic], arrays
- examples [Visual Basic], Char data type
ms.assetid: 69f94e85-d57c-4ccc-a62a-426e829f5c5e
ms.openlocfilehash: 67b675f5f02c92b785e374b99f49248d43d12fb4
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100429838"
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
