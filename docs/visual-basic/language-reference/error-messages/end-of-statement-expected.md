---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords: BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4934952015cb4871bcd90cef982eab5425b1617f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="c0c90-102">Deyim sonu bekleniyor</span><span class="sxs-lookup"><span data-stu-id="c0c90-102">End of statement expected</span></span>
<span data-ttu-id="c0c90-103">Deyim sözdizimsel olarak tamamlandı, ancak ek bir programlama öğesi deyim tamamlandıktan öğesi izler.</span><span class="sxs-lookup"><span data-stu-id="c0c90-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="c0c90-104">Satır Sonlandırıcı her deyimi sonunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="c0c90-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="c0c90-105">Satır Sonlandırıcı bir Visual Basic kaynak dosyası karakterlerinden satırlarına böler.</span><span class="sxs-lookup"><span data-stu-id="c0c90-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="c0c90-106">Satır sonlandırıcılar örnekler Unicode satır dönüş karakteri (& HD), Unicode satır besleme karakteri (& HA) ve Unicode satır başı karakteri Unicode satır besleme karakter.</span><span class="sxs-lookup"><span data-stu-id="c0c90-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="c0c90-107">Satır sonlandırıcılar hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](../../../visual-basic/reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c0c90-107">For more information about line terminators, see the [Visual Basic Language Specification](../../../visual-basic/reference/language-specification/index.md).</span></span>
  
 <span data-ttu-id="c0c90-108">**Hata Kimliği:** BC30205</span><span class="sxs-lookup"><span data-stu-id="c0c90-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c0c90-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="c0c90-109">To correct this error</span></span>
  
1.  <span data-ttu-id="c0c90-110">İki farklı deyimleri yanlışlıkla konmuş varsa aynı çizgi üzerinde denetleyin.</span><span class="sxs-lookup"><span data-stu-id="c0c90-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="c0c90-111">Satır Sonlandırıcı deyim tamamlayan öğeden sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c0c90-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c0c90-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0c90-112">See Also</span></span>  
 [<span data-ttu-id="c0c90-113">Nasıl yapılır: kodda deyimleri bölme ve birleştirme</span><span class="sxs-lookup"><span data-stu-id="c0c90-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="c0c90-114">Deyimleri</span><span class="sxs-lookup"><span data-stu-id="c0c90-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
