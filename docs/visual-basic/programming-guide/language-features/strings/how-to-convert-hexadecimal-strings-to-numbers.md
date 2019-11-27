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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="825f9-102">Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="825f9-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="825f9-103">Bu örnek, <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemini kullanarak onaltılık dizeyi tamsayıya dönüştürür.</span><span class="sxs-lookup"><span data-stu-id="825f9-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="825f9-104">Bir onaltılık dizeyi sayıya dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="825f9-104">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="825f9-105">Base-16 ' da ifade edilen sayıyı bir tamsayıya dönüştürmek için <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="825f9-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="825f9-106"><xref:System.Convert.ToInt32(System.String,System.Int32)> yönteminin ilk bağımsız değişkeni dönüştürülecek dizedir.</span><span class="sxs-lookup"><span data-stu-id="825f9-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="825f9-107">İkinci bağımsız değişken, sayının ifade edildiği temeli açıklar; onaltılı tabanı 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="825f9-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="825f9-108">Onaltılık dizenin aşağıdaki kısıtlamalara sahip olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="825f9-108">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="825f9-109">`&h` önekini içeremez.</span><span class="sxs-lookup"><span data-stu-id="825f9-109">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="825f9-110">`_` basamak ayırıcısını içeremez.</span><span class="sxs-lookup"><span data-stu-id="825f9-110">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="825f9-111">Ön ek veya bir rakam ayırıcısı varsa, <xref:System.Convert.ToInt32(System.String,System.Int32)> metoduna yapılan çağrı bir <xref:System.FormatException>oluşturur.</span><span class="sxs-lookup"><span data-stu-id="825f9-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="825f9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="825f9-112">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
