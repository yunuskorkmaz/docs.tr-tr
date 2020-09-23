---
title: 'Nasıl yapılır: Bayt Dizisini Dizeye Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- string conversion [Visual Basic], arrays
- byte arrays [Visual Basic], converting to strings
- examples [Visual Basic], strings
- arrays [Visual Basic], converting to strings
ms.assetid: d0dc8317-9ab3-4324-99f7-3f5788c0e72a
ms.openlocfilehash: 49c1e454b845bd545d7a8dccb3a3d9a39ff2db21
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91085665"
---
# <a name="how-to-convert-an-array-of-bytes-into-a-string-in-visual-basic"></a><span data-ttu-id="20ae7-102">Nasıl yapılır: Visual Basic'de Bir Bayt Dizisini Dizeye Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="20ae7-102">How to: Convert an Array of Bytes into a String in Visual Basic</span></span>

<span data-ttu-id="20ae7-103">Bu konu, bayt dizisindeki baytların dizeye nasıl dönüştürüleceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="20ae7-103">This topic shows how to convert the bytes from a byte array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="20ae7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="20ae7-104">Example</span></span>  

 <span data-ttu-id="20ae7-105">Bu örnek, <xref:System.Text.Encoding.GetString%2A> <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> bir bayt dizisinden tüm baytları dizeye dönüştürmek için Encoding sınıfının yöntemini kullanır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-105">This example uses the <xref:System.Text.Encoding.GetString%2A> method of the <xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType> encoding class to convert all the bytes from a byte array into a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#72](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#72)]  
  
 <span data-ttu-id="20ae7-106">Bir bayt dizisini dizeye dönüştürmek için çeşitli kodlama seçenekleri arasından seçim yapabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="20ae7-106">You can choose from several encoding options to convert a byte array into a string:</span></span>  
  
- <span data-ttu-id="20ae7-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: ASCII (7 bit) karakter kümesi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-107"><xref:System.Text.Encoding.ASCII%2A?displayProperty=nameWithType>: Gets an encoding for the ASCII (7-bit) character set.</span></span>  
  
- <span data-ttu-id="20ae7-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Büyük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-108"><xref:System.Text.Encoding.BigEndianUnicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the big-endian byte order.</span></span>  
  
- <span data-ttu-id="20ae7-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Sistemin geçerli ANSI kod sayfası için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-109"><xref:System.Text.Encoding.Default%2A?displayProperty=nameWithType>: Gets an encoding for the system's current ANSI code page.</span></span>  
  
- <span data-ttu-id="20ae7-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Küçük endian bayt sırasını kullanarak UTF-16 biçimi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-110"><xref:System.Text.Encoding.Unicode%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-16 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="20ae7-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Küçük endian bayt sırasını kullanarak UTF-32 biçimi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-111"><xref:System.Text.Encoding.UTF32%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-32 format using the little-endian byte order.</span></span>  
  
- <span data-ttu-id="20ae7-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: UTF-7 biçimi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-112"><xref:System.Text.Encoding.UTF7%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-7 format.</span></span>  
  
- <span data-ttu-id="20ae7-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: UTF-8 biçimi için bir kodlama alır.</span><span class="sxs-lookup"><span data-stu-id="20ae7-113"><xref:System.Text.Encoding.UTF8%2A?displayProperty=nameWithType>: Gets an encoding for the UTF-8 format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20ae7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="20ae7-114">See also</span></span>

- <xref:System.Text.Encoding?displayProperty=nameWithType>
- <xref:System.Text.Encoding.GetString%2A>
- [<span data-ttu-id="20ae7-115">Nasıl yapılır: Visual Basic'de Dizeleri Bir Bayt Dizisine Dönüştürme</span><span class="sxs-lookup"><span data-stu-id="20ae7-115">How to: Convert Strings into an Array of Bytes in Visual Basic</span></span>](how-to-convert-strings-into-an-array-of-bytes.md)
