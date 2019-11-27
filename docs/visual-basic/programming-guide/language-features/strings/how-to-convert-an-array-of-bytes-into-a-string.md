---
title: 'Nasıl yapılır: bayt dizisini dizeye dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 8c1d9d1d2e89390873bc1c3dbb9623f047433a9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351984"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme
Bu konu, bayt dizisindeki baytların dizeye nasıl dönüştürüleceğini gösterir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir bayt dizisinden tüm baytları dizeye dönüştürmek için <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> Encoding sınıfının <xref:System.Text.Encoding.GetString%2A> yöntemini kullanır.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Bir bayt dizisini dizeye dönüştürmek için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: ASCII (7 bit) karakter kümesi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: büyük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: sistemin geçerli ANSI kod sayfası için bir kodlama alır.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: küçük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: küçük endian bayt sırasını kullanarak UTF-32 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: UTF-7 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: UTF-8 biçimi için bir kodlama alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Nasıl yapılır: dizeleri Visual Basic bayt dizisine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
