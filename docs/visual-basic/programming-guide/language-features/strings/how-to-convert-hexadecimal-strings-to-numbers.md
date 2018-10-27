---
title: 'Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)'
ms.date: 01/31/2018
helpviewer_keywords:
- numbers [Visual Basic], hexadecimals
- hexadecimals [Visual Basic], decimals
- examples [Visual Basic], string conversion
- decimals [Visual Basic], hexadecimals
- string conversion [Visual Basic], hexadecimal to numbers
ms.assetid: 76675807-eadb-4c08-bd50-e6c6ff4b8ced
ms.openlocfilehash: 65184bbb742ad549a8398d55dc7bdeed05a9d973
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50048560"
---
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="c1d14-102">Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1d14-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="c1d14-103">Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1d14-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="c1d14-104">Bir sayıyı bir onaltılık dize dönüştürmek için</span><span class="sxs-lookup"><span data-stu-id="c1d14-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="c1d14-105">Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> temel-16 tamsayı cinsinden bir sayı dönüştürmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="c1d14-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="c1d14-106">İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemdir dönüştürülecek dize.</span><span class="sxs-lookup"><span data-stu-id="c1d14-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="c1d14-107">İkinci bağımsız değişken sayısı cinsinden temeli açıklar; onaltılık temel 16'dır.</span><span class="sxs-lookup"><span data-stu-id="c1d14-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="c1d14-108">Onaltılık dizeyi aşağıdaki kısıtlamalar olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="c1d14-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="c1d14-109">Dahil edemezsiniz `&h` önek.</span><span class="sxs-lookup"><span data-stu-id="c1d14-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="c1d14-110">Dahil edemezsiniz `_` basamak ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="c1d14-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="c1d14-111">Ön ek veya bir basamak ayıracı mevcutsa, çağrı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntem bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="c1d14-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c1d14-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c1d14-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
