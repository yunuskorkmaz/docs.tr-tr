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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="a6513-103">Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a6513-103">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>

<span data-ttu-id="a6513-104">Bu örnek, yöntemini kullanarak bir onaltılı dizeyi tamsayıya dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a6513-104">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>

## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="a6513-105">Bir onaltılık dizeyi sayıya dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="a6513-105">To convert a hexadecimal string to a number</span></span>

- <span data-ttu-id="a6513-106"><xref:System.Convert.ToInt32(System.String,System.Int32)>Base-16 ' da ifade edilen sayıyı bir tamsayıya dönüştürmek için yöntemini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a6513-106">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>

  <span data-ttu-id="a6513-107">Metodun ilk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> dönüştürülecek dizedir.</span><span class="sxs-lookup"><span data-stu-id="a6513-107">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="a6513-108">İkinci bağımsız değişken, sayının ifade edildiği temeli açıklar; onaltılı tabanı 16 ' dır.</span><span class="sxs-lookup"><span data-stu-id="a6513-108">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>

  [!code-vb[VbVbalrStrings#62](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#62)]

- <span data-ttu-id="a6513-109">Onaltılık dizenin aşağıdaki kısıtlamalara sahip olduğunu unutmayın:</span><span class="sxs-lookup"><span data-stu-id="a6513-109">Note that the hexadecimal string has the following restrictions:</span></span>

  - <span data-ttu-id="a6513-110">`&h`Ön eki içeremez.</span><span class="sxs-lookup"><span data-stu-id="a6513-110">It cannot include the `&h` prefix.</span></span>
  - <span data-ttu-id="a6513-111">`_`Rakam ayırıcısını içeremez.</span><span class="sxs-lookup"><span data-stu-id="a6513-111">It cannot include the `_` digit separator.</span></span>

  <span data-ttu-id="a6513-112">Ön ek veya bir rakam ayırıcısı varsa, yöntemine yapılan çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> bir atar <xref:System.FormatException> .</span><span class="sxs-lookup"><span data-stu-id="a6513-112">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="a6513-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6513-113">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
