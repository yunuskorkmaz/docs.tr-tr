---
title: "Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün"
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 577cce6322bf80bf2abdb963f07938b1a8b5d174
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718357"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün
Bu konuda, bayt bayt dizisinden bir dizeye dönüştürmek gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnekte <xref:System.Text.Encoding.GetString%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> tüm baytlar bir bayt dizisinden bir dizeye dönüştürmek için sınıfı kodlama.  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 Bir bayt dizisini dizeye dönüştürme için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:  
  
-   <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Bir ASCII (7 bit) karakter kümesi için kodlama alır.  
  
-   <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Kodlama büyük endian bayt sırası kullanarak UTF-16 biçimi alır.  
  
-   <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.  
  
-   <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama UTF-16 little endian bayt sırası kullanarak biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.  
  
-   <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama biçimi UTF-7 alır.  
  
-   <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Nasıl yapılır: Visual Basic'de bir bayt dizisi dizeleri dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
