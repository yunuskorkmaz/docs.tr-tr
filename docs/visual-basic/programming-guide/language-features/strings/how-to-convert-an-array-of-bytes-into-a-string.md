---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: bayt dizisini Visual Basic bir dizeye dönüştürme'
title: 'Nasıl yapılır: Bayt Dizisini Dizeye Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: ded4a2c4c235e560198ef2edd4c5031141554079
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425574"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme

Bu konu, bayt dizisindeki baytların dizeye nasıl dönüştürüleceğini gösterir.  
  
## <a name="example"></a>Örnek  

 Bu örnek, <xref:System.Text.Encoding.GetString%2A> <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> bir bayt dizisinden tüm baytları dizeye dönüştürmek için Encoding sınıfının yöntemini kullanır.  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 Bir bayt dizisini dizeye dönüştürmek için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:  
  
- <xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: ASCII (7 bit) karakter kümesi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Büyük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Sistemin geçerli ANSI kod sayfası için bir kodlama alır.  
  
- <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Küçük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Küçük endian bayt sırasını kullanarak UTF-32 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: UTF-7 biçimi için bir kodlama alır.  
  
- <xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: UTF-8 biçimi için bir kodlama alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme](how-to-convert-strings-into-an-array-of-bytes.md)
