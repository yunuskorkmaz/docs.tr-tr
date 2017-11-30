---
title: "Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4133109ef334c7e87884deb7db963db3291da1d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="17a53-102">Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="17a53-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>
<span data-ttu-id="17a53-103">Bu konu, baytı bir bayt dizisinden bir dizeye dönüştürmek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="17a53-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="17a53-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="17a53-104">Example</span></span>  
 <span data-ttu-id="17a53-105">Bu örnekte <xref:System.Text.Encoding.GetString%2A> yöntemi <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> tüm baytlar bir bayt dizisinden bir dizeye dönüştürmek için sınıf kodlama.</span><span class="sxs-lookup"><span data-stu-id="17a53-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-an-array-of-bytes-into-a-string_1.vb)]  
  
 <span data-ttu-id="17a53-106">Bir bayt dizisine bir dizeye dönüştürmek için çeşitli kodlama seçenekler arasından seçim yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="17a53-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
-   <span data-ttu-id="17a53-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Alır ASCII (7 bit) karakter kodlama ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="17a53-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
-   <span data-ttu-id="17a53-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Bir kodlama big endian bayt sırasını kullanarak UTF-16 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
-   <span data-ttu-id="17a53-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Bir sistemin geçerli ANSI kod sayfası için kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
-   <span data-ttu-id="17a53-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-16 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="17a53-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Bir kodlama little endian bayt sırası kullanarak UTF-32 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
-   <span data-ttu-id="17a53-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Bir kodlama UTF-7 biçimini alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
-   <span data-ttu-id="17a53-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Bir kodlama için UTF-8 biçiminde alır.</span><span class="sxs-lookup"><span data-stu-id="17a53-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17a53-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="17a53-114">See Also</span></span>  
 <xref:System.Text.Encoding?displayProperty=nameWithType>  
 <xref:System.Text.Encoding.GetString%2A>  
 [<span data-ttu-id="17a53-115">Nasıl yapılır: Visual Basic'de bir bayt dizisi halinde dizeleri dönüştürme</span><span class="sxs-lookup"><span data-stu-id="17a53-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-strings-into-an-array-of-bytes.md)
