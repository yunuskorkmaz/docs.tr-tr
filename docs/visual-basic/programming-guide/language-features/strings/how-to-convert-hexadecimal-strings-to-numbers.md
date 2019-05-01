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
ms.openlocfilehash: ddb7b39f7a47234c003ca16e1d7ea013e113c108
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054048"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Nasıl yapılır: Onaltılık dizeleri sayılara (Visual Basic) dönüştürme

Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Bir sayıyı bir onaltılık dize dönüştürmek için

- Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> temel-16 tamsayı cinsinden bir sayı dönüştürmek için yöntemi.

  İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemdir dönüştürülecek dize. İkinci bağımsız değişken sayısı cinsinden temeli açıklar; onaltılık temel 16'dır.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Onaltılık dizeyi aşağıdaki kısıtlamalar olduğuna dikkat edin:

  - Dahil edemezsiniz `&h` önek.
  - Dahil edemezsiniz `_` basamak ayırıcı.

  Ön ek veya bir basamak ayıracı mevcutsa, çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntem bir <xref:System.FormatException>.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
