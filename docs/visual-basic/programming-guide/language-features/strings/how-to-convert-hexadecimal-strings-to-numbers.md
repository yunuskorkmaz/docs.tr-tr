---
title: 'Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: f0a97a0c212a64bfa4db4606ee526b666f07877a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347167"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a>Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)

Bu örnek, <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemini kullanarak onaltılık dizeyi tamsayıya dönüştürür.

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a>Bir onaltılık dizeyi sayıya dönüştürmek için

- Base-16 ' da ifade edilen sayıyı bir tamsayıya dönüştürmek için <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemini kullanın.

  <xref:System.Convert.ToInt32(System.String,System.Int32)> yönteminin ilk bağımsız değişkeni dönüştürülecek dizedir. İkinci bağımsız değişken, sayının ifade edildiği temeli açıklar; onaltılı tabanı 16 ' dır.

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- Onaltılık dizenin aşağıdaki kısıtlamalara sahip olduğunu unutmayın:

  - `&h` önekini içeremez.
  - `_` basamak ayırıcısını içeremez.

  Ön ek veya bir rakam ayırıcısı varsa, <xref:System.Convert.ToInt32(System.String,System.Int32)> metoduna yapılan çağrı bir <xref:System.FormatException>oluşturur.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
