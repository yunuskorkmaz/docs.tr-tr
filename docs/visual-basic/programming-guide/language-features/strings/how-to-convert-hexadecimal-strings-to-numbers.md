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
# <a name="how-to-convert-hexadecimal-strings-to-numbers-visual-basic"></a><span data-ttu-id="cf0b7-102">Nasıl yapılır: Onaltılık Dizeleri Sayılara Dönüştürme (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cf0b7-102">How to: Convert Hexadecimal Strings to Numbers (Visual Basic)</span></span>
<span data-ttu-id="cf0b7-103">Bu örnek, bir tamsayı kullanarak bir onaltılık dize dönüştürür <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-103">This example converts a hexadecimal string to an integer using the <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="to-convert-a-hexadecimal-string-to-a-number"></a><span data-ttu-id="cf0b7-104">Bir onaltılık dize bir sayıya dönüştürme</span><span class="sxs-lookup"><span data-stu-id="cf0b7-104">To convert a hexadecimal string to a number</span></span>  
  
-   <span data-ttu-id="cf0b7-105">Kullanım <xref:System.Convert.ToInt32(System.String,System.Int32)> base-16 bir tamsayı olarak ifade edilen numarası dönüştürmek için yöntem.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-105">Use the <xref:System.Convert.ToInt32(System.String,System.Int32)> method to convert the number expressed in base-16 to an integer.</span></span>  
  
     <span data-ttu-id="cf0b7-106">İlk bağımsız değişkeni <xref:System.Convert.ToInt32(System.String,System.Int32)> dönüştürülecek dizeyi bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-106">The first argument of the <xref:System.Convert.ToInt32(System.String,System.Int32)> method is the string to convert.</span></span> <span data-ttu-id="cf0b7-107">İkinci bağımsız değişken sayısı cinsinden ifade edilir temeli açıklar; onaltılık temel 16'dır.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-107">The second argument describes what base the number is expressed in; hexadecimal is base 16.</span></span>  
  
     [!code-vb[HexConversion](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-hexadecimal-strings-to-numbers_1.vb)]  

- <span data-ttu-id="cf0b7-108">Onaltılık dize aşağıdaki kısıtlamalar olduğuna dikkat edin:</span><span class="sxs-lookup"><span data-stu-id="cf0b7-108">Note that the hexadecimal string has the following restrictions:</span></span>

   - <span data-ttu-id="cf0b7-109">Dahil edilemiyor `&h` öneki.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-109">It cannot include the `&h` prefix.</span></span>
   - <span data-ttu-id="cf0b7-110">Dahil edilemiyor `_` basamak ayırıcı.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-110">It cannot include the `_` digit separator.</span></span>

   <span data-ttu-id="cf0b7-111">Önek veya bir basamak ayırıcı mevcutsa, çağrısı <xref:System.Convert.ToInt32(System.String,System.Int32)> yöntemi atar bir <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-111">If the prefix or a digit separator is present, the call to the <xref:System.Convert.ToInt32(System.String,System.Int32)> method throws a <xref:System.FormatException>.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf0b7-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf0b7-112">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Hex%2A>  
 <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType>
