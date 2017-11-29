---
title: "Nasıl yapılır: Dize İçinde Arama (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], finding
- strings [Visual Basic], searching
- examples [Visual Basic], strings
ms.assetid: ae4c79e0-08ea-489f-bdb2-5eb6d355f284
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2c828d0b32fdf90e121e9d5da0bb60ab11c212f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-search-within-a-string-visual-basic"></a><span data-ttu-id="5f4be-102">Nasıl yapılır: Dize İçinde Arama (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f4be-102">How to: Search Within a String (Visual Basic)</span></span>
<span data-ttu-id="5f4be-103">Bu örnek çağırır <xref:System.String.IndexOf%2A> yöntemi bir <xref:System.String> bir alt dizenin ilk örneğinin dizinini bildirmek için nesne.</span><span class="sxs-lookup"><span data-stu-id="5f4be-103">This example calls the <xref:System.String.IndexOf%2A> method on a <xref:System.String> object to report the index of the first occurrence of a substring.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f4be-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5f4be-104">Example</span></span>  
 [!code-vb[VbVbalrStrings#71](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-search-within-a-string_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5f4be-105">Kod Derleniyor</span><span class="sxs-lookup"><span data-stu-id="5f4be-105">Compiling the Code</span></span>  
 <span data-ttu-id="5f4be-106">Bu örnek gerektirir:</span><span class="sxs-lookup"><span data-stu-id="5f4be-106">This example requires:</span></span>  
  
-   <span data-ttu-id="5f4be-107">Bir `Imports` deyimi belirtme <xref:System> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="5f4be-107">An `Imports` statement specifying the <xref:System> namespace.</span></span> <span data-ttu-id="5f4be-108">Daha fazla bilgi için bkz: [Imports deyimi (.NET Namespace ve türü)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="5f4be-108">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="5f4be-109">Güçlü Programlama</span><span class="sxs-lookup"><span data-stu-id="5f4be-109">Robust Programming</span></span>  
 <span data-ttu-id="5f4be-110"><xref:System.String.IndexOf%2A> Yöntemi raporları alt dizenin ilk örneğinin ilk karakterin konumu.</span><span class="sxs-lookup"><span data-stu-id="5f4be-110">The <xref:System.String.IndexOf%2A> method reports the location of the first character of the first occurrence of the substring.</span></span> <span data-ttu-id="5f4be-111">Bir dizenin ilk karakter 0 dizini sahip olduğu anlamına 0 tabanlı dizinidir.</span><span class="sxs-lookup"><span data-stu-id="5f4be-111">The index is 0-based, which means the first character of a string has an index of 0.</span></span>  
  
 <span data-ttu-id="5f4be-112">Varsa <xref:System.String.IndexOf%2A> alt dizeyi bulur değil -1 döndürür.</span><span class="sxs-lookup"><span data-stu-id="5f4be-112">If <xref:System.String.IndexOf%2A> does not find the substring, it returns -1.</span></span>  
  
 <span data-ttu-id="5f4be-113"><xref:System.String.IndexOf%2A> Yöntemi küçük harfe duyarlıdır ve geçerli kültürü kullanır.</span><span class="sxs-lookup"><span data-stu-id="5f4be-113">The <xref:System.String.IndexOf%2A> method is case-sensitive and uses the current culture.</span></span>  
  
 <span data-ttu-id="5f4be-114">En iyi hata denetimi için dize aramada içine isteyebilirsiniz `Try` , engelleme bir [deneyin... Catch... Finally ifadesi](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) oluşturma.</span><span class="sxs-lookup"><span data-stu-id="5f4be-114">For optimal error control, you might want to enclose the string search in the `Try` block of a [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md) construction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f4be-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5f4be-115">See Also</span></span>  
 <xref:System.String.IndexOf%2A>  
 [<span data-ttu-id="5f4be-116">Try... Catch... Finally ifadesi</span><span class="sxs-lookup"><span data-stu-id="5f4be-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="5f4be-117">Visual Basic'de dizelere giriş</span><span class="sxs-lookup"><span data-stu-id="5f4be-117">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="5f4be-118">Dizeleri</span><span class="sxs-lookup"><span data-stu-id="5f4be-118">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
