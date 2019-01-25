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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="07f9e-102">Nasıl yapılır: Onaltılık dizeleri sayılara (Visual Basic) dönüştürme</span><span class="sxs-lookup"><span data-stu-id="07f9e-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="07f9e-103">Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07f9e-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="07f9e-104">Bir sayıyı bir onaltılık dize dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="07f9e-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="07f9e-105">Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> temel-16 tamsayı cinsinden bir sayı dönüştürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="07f9e-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="07f9e-106">İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemdir dönüştürülecek dize.</span><span class="sxs-lookup"><span data-stu-id="07f9e-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="07f9e-107">İkinci bağımsız değişken sayısı cinsinden temeli açıklar; onaltılık temel 16'dır.</span><span class="sxs-lookup"><span data-stu-id="07f9e-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="07f9e-108">Onaltılık dizeyi aşağıdaki kısıtlamalar olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="07f9e-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="07f9e-109">Dahil edemezsiniz `&h` önek.</span><span class="sxs-lookup"><span data-stu-id="07f9e-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="07f9e-110">Dahil edemezsiniz `_` basamak ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="07f9e-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="07f9e-111">Ön ek veya bir basamak ayıracı mevcutsa, çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntem bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="07f9e-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="07f9e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07f9e-112">See also</span></span>
- <xref:Microsoft.VisualBasic.Conversion.Hex%2A>
- <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
