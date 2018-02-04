---
title: "Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)"
ms.custom: 
ms.date: 01/31/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
author: petrusha
ms.author: ronpet
ms.manager: wpickett
ms.openlocfilehash: c35ac615e3f87710f934a1cf66e6546625298bd0
ms.sourcegitcommit: d2da0142247ef42a219a5d2907f153e62dc6ea0d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/01/2018
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)
Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Bir onaltılık dize bir sayıya dönüştürme  
  
-   Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> base-16 bir tamsayı olarak ifade edilen numarası dönüştürmek için yöntem.  
  
     İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> dönüştürülecek dizeyi bir yöntemdir. İkinci bağımsız değişken sayısı cinsinden ifade edilir temeli açıklar; onaltılık temel 16'dır.  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- Onaltılık dize aşağıdaki kısıtlamalar olduğuna dikkat edin:

   - Dahil edilemiyor `&h` öneki.
   - Dahil edilemiyor `_` basamak ayırıcı.

   Önek veya bir basamak ayırıcı mevcutsa, çağrısı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemi atar bir <xref:System.FormatException>.

## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
