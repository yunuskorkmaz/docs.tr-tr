---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 8df756009ebe3a0613ec47018d938151829214df
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50039029"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="238cb-102">Deyim sonu bekleniyor</span><span class="sxs-lookup"><span data-stu-id="238cb-102">End of statement expected</span></span>
<span data-ttu-id="238cb-103">Deyim sözdizimi kurallarına göre tamamlandı, ancak ek bir programlama öğesi deyimi tamamlar öğesi izler.</span><span class="sxs-lookup"><span data-stu-id="238cb-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="238cb-104">Bir satır Sonlandırıcı her deyim sonunda gereklidir.</span><span class="sxs-lookup"><span data-stu-id="238cb-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="238cb-105">Bir satır Sonlandırıcı karakterleri bir Visual Basic kaynak dosyası satırlarına böler.</span><span class="sxs-lookup"><span data-stu-id="238cb-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="238cb-106">Unicode satır başı dönüş karakteri (& HD), satır sonlandırıcılar örnekleri olan Unicode satır besleme karakteri (& HA) ve Unicode satır başı karakteri sonrasında Unicode satır besleme karakteri döndürür.</span><span class="sxs-lookup"><span data-stu-id="238cb-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="238cb-107">Satır sonlandırıcılar hakkında daha fazla bilgi için bkz: [Visual Basic dil belirtimi](~/_vblang/spec/lexical-grammar.md#line-terminators).</span><span class="sxs-lookup"><span data-stu-id="238cb-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="238cb-108">**Hata Kimliği:** BC30205</span><span class="sxs-lookup"><span data-stu-id="238cb-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="238cb-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="238cb-109">To correct this error</span></span>
  
1.  <span data-ttu-id="238cb-110">İki farklı deyimleri aynı satırda yanlışlıkla konmuş olmadığını denetleyin.</span><span class="sxs-lookup"><span data-stu-id="238cb-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2.  <span data-ttu-id="238cb-111">Bir satır Sonlandırıcı bildirimi tamamlayan öğeden sonra ekleyin.</span><span class="sxs-lookup"><span data-stu-id="238cb-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="238cb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="238cb-112">See Also</span></span>  
 [<span data-ttu-id="238cb-113">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="238cb-113">How to: Break and Combine Statements in Code</span></span>](../../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)  
 [<span data-ttu-id="238cb-114">Deyimler</span><span class="sxs-lookup"><span data-stu-id="238cb-114">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
