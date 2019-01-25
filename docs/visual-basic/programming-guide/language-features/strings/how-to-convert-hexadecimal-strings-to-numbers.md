---
title: 'Nasıl yapılır: Onaltılık dizeleri sayılara (Visual Basic) dönüştürme'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: 76acee8913df35d4d071017078b38a3c474c3357
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633832"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Nasıl yapılır: Onaltılık dizeleri sayılara (Visual Basic) dönüştürme
Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Bir sayıyı bir onaltılık dize dönüştürmek için  
  
-   Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> temel-16 tamsayı cinsinden bir sayı dönüştürmek için yöntemi.  
  
     İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemdir dönüştürülecek dize. İkinci bağımsız değişken sayısı cinsinden temeli açıklar; onaltılık temel 16'dır.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Onaltılık dizeyi aşağıdaki kısıtlamalar olduğuna dikkat edin:

   - Dahil edemezsiniz `&h` önek.
   - Dahil edemezsiniz `_` basamak ayırıcı.

   Ön ek veya bir basamak ayıracı mevcutsa, çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntem bir <xref:System.FormatException>.

## <a name="see-also"></a>Ayrıca bkz.
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
