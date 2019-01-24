---
title: 'Nasıl yapılır: (Visual Basic) dize içinde arama'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
ms.openlocfilehash: 6ac75c99270deb14e23691d32e8ebf4e8b0a91b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54542557"
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="b86a3-102">Nasıl yapılır: (Visual Basic) dize içinde arama</span><span class="sxs-lookup"><span data-stu-id="b86a3-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="b86a3-103">Bu örnek <xref:System.String.IndexOf%2A> metodunda bir <xref:System.String> bir alt dizenin ilk geçtiği dizini bildirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="b86a3-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b86a3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b86a3-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b86a3-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="b86a3-105">Compiling the Code</span></span>  
 <span data-ttu-id="b86a3-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="b86a3-106">This example requires:</span></span>  
  
-   <span data-ttu-id="b86a3-107">Bir `Imports` deyimi belirtme <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b86a3-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="b86a3-108">Daha fazla bilgi için [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="b86a3-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b86a3-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="b86a3-109">Robust Programming</span></span>  
 <span data-ttu-id="b86a3-110"><xref:System.String.IndexOf%2A> Yöntemi raporları alt dizenin ilk geçtiği ilk karakterin konumu.</span><span class="sxs-lookup"><span data-stu-id="b86a3-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="b86a3-111">Dizin 0 tabanlı bir dizenin ilk karakteri bir dizininin 0 olduğu anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="b86a3-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="b86a3-112">Varsa <xref:System.String.IndexOf%2A> substring bulamazsa -1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="b86a3-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="b86a3-113"><xref:System.String.IndexOf%2A> Yöntemi büyük küçük harfe duyarlıdır ve geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="b86a3-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="b86a3-114">En iyi hata denetimi için dize aramaya içine isteyebilirsiniz `Try` bloğu bir [deneyin... Catch... Finally deyimini](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="b86a3-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b86a3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b86a3-115">See also</span></span>
- <xref:System.String.IndexOf%2A>
- [<span data-ttu-id="b86a3-116">Try...Catch...Finally Deyimi</span><span class="sxs-lookup"><span data-stu-id="b86a3-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="b86a3-117">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="b86a3-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="b86a3-118">Dizeler</span><span class="sxs-lookup"><span data-stu-id="b86a3-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
