---
title: "Nasıl yapılır: Visual Basic'de bir bayt dizisi dizeleri dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: 83efc9e6b4d4433d5416f2f8b2612c76581586e3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648488"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de bir bayt dizisi dizeleri dönüştürme
Bu konuda, bir dizeyi bir bayt dizisine dönüştürme gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Text.Encoding.GetBytes%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> sınıfı bir dizeyi bir bayt dizisine dönüştürmek için kodlama.  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 Bir dizeyi bir bayt dizisine dönüştürmek için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Bir ASCII (7 bit) karakter kümesi için kodlama alır.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Kodlama büyük endian bayt sırası kullanarak UTF-16 biçimi alır.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama UTF-16 little endian bayt sırası kullanarak biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama biçimi UTF-7 alır.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetBytes%2A>
- [Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
