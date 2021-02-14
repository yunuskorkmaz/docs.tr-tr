---
description: 'Hakkında daha fazla bilgi edinin: nasıl yapılır: onaltılık dizeleri sayılara dönüştürme (Visual Basic)'
title: 'Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: cf1648b5f85f189f203f56cf569041e4f2db5ac3
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100425549"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)

Bu örnek, yöntemini kullanarak bir onaltılı dizeyi tamsayıya dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> .

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Bir onaltılık dizeyi sayıya dönüştürmek için

- <xref:System.Convert.ToInt32(System.String,System.Int32)>Base-16 ' da ifade edilen sayıyı bir tamsayıya dönüştürmek için yöntemini kullanın.

  Metodun ilk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> dönüştürülecek dizedir. İkinci bağımsız değişken, sayının ifade edildiği temeli açıklar; onaltılı tabanı 16 ' dır.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Onaltılık dizenin aşağıdaki kısıtlamalara sahip olduğunu unutmayın:

  - `&h`Ön eki içeremez.
  - `_`Rakam ayırıcısını içeremez.

  Ön ek veya bir rakam ayırıcısı varsa, yöntemine yapılan çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> bir atar <xref:System.FormatException> .

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
