---
title: "Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün"
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: cd091d743b04ef9d9709bde2b5a1205f3d7ae292
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979521"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="98f87-102">Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün</span><span class="sxs-lookup"><span data-stu-id="98f87-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="98f87-103">Bu konuda, bayt bayt dizisinden bir dizeye dönüştürmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="98f87-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98f87-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="98f87-104">Example</span></span>  
 <span data-ttu-id="98f87-105">Bu örnekte <xref:System.Text.Encoding.GetString%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> tüm baytlar bir bayt dizisinden bir dizeye dönüştürmek için sınıfı kodlama.</span><span class="sxs-lookup"><span data-stu-id="98f87-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="98f87-106">Bir bayt dizisini dizeye dönüştürme için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="98f87-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="98f87-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Bir ASCII (7 bit) karakter kümesi için kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="98f87-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Kodlama büyük endian bayt sırası kullanarak UTF-16 biçimi alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="98f87-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="98f87-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama UTF-16 little endian bayt sırası kullanarak biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="98f87-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="98f87-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama biçimi UTF-7 alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="98f87-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.</span><span class="sxs-lookup"><span data-stu-id="98f87-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f87-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98f87-114">See also</span></span>
- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="98f87-115">Nasıl yapılır: Visual Basic'de bir bayt dizisi dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="98f87-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
