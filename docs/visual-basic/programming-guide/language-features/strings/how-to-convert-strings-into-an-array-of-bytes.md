---
title: "Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- arrays [Visual Basic], converting strings to
- byte arrays
- examples [Visual Basic], string conversion
- arrays [Visual Basic], byte arrays
ms.assetid: f477d35c-a3fc-4a30-b1d4-cd0d353aae1d
ms.openlocfilehash: da4a47b955b91f4bb39ecd7832da30d76e75d553
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647959"
---
# <a name="how-to-convert-strings-into-an-array-of-bytes-in-visual-basic"></a><span data-ttu-id="3e28e-102">Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="3e28e-102">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>
<span data-ttu-id="3e28e-103">Bu konuda, bir dizeyi bir bayt dizisine dönüştürme gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3e28e-103">This topic shows how to convert a string into an array of bytes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e28e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="3e28e-104">Example</span></span>  
 <span data-ttu-id="3e28e-105">Bu örnekte <xref:System.Text.Encoding.GetBytes%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> bir dizeyi bir bayt dizisine dönüştürme için sınıf kodlama.</span><span class="sxs-lookup"><span data-stu-id="3e28e-105">This example uses the <xref:System.Text.Encoding.GetBytes%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert a string into an array of bytes.</span></span>  
  
 [!code-vb[VbVbalrStrings#74](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-strings-into-an-array-of-bytes_1.vb)]  
  
 <span data-ttu-id="3e28e-106">Bir dizeyi bir bayt dizisine dönüştürme için kodlama çeşitli seçenekler arasından seçim yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="3e28e-106">You can choose from several encoding options to convert a string into a byte array:</span></span>  
  
-   <span data-ttu-id="3e28e-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Alır ASCII (7 bit) karakter kodlama ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="3e28e-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="3e28e-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Bir kodlama big endian bayt sırasını kullanarak UTF-16 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="3e28e-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="3e28e-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-16 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="3e28e-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="3e28e-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama UTF-7 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="3e28e-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.</span><span class="sxs-lookup"><span data-stu-id="3e28e-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e28e-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3e28e-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetBytes%2A>  
 [<span data-ttu-id="3e28e-115">Nasıl yapılır: Visual Basic'te bir dizeyi bir bayt dizisi dönüştürün</span><span class="sxs-lookup"><span data-stu-id="3e28e-115">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-an-array-of-bytes-into-a-string.md)
