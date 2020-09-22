---
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: 9141400afc651629df381e0a655e2d7b9da2e45d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874422"
---
# <a name="end-of-statement-expected"></a><span data-ttu-id="a6a27-102">Deyim sonu bekleniyor</span><span class="sxs-lookup"><span data-stu-id="a6a27-102">End of statement expected</span></span>

<span data-ttu-id="a6a27-103">İfade sözdizimsel olarak tamamlanmıştır, ancak ek bir programlama öğesi, ifadesini tamamlayan öğesini izler.</span><span class="sxs-lookup"><span data-stu-id="a6a27-103">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="a6a27-104">Her deyimin sonunda bir satır Sonlandırıcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a6a27-104">A line terminator is required at the end of every statement.</span></span>
  
 <span data-ttu-id="a6a27-105">Satır Sonlandırıcı Visual Basic kaynak dosyanın karakterlerini çizgilere böler.</span><span class="sxs-lookup"><span data-stu-id="a6a27-105">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="a6a27-106">Satır sonlandırıcılar örnekleri, Unicode satır başı karakteri (&HD), Unicode satır besleme karakteri (&ha) ve ardından Unicode satır besleme karakteri ile Unicode satır başı karakteri.</span><span class="sxs-lookup"><span data-stu-id="a6a27-106">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="a6a27-107">Satır sonlandırıcılar hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/lexical-grammar.md#line-terminators)bakın.</span><span class="sxs-lookup"><span data-stu-id="a6a27-107">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>
  
 <span data-ttu-id="a6a27-108">**Hata kimliği:** BC30205</span><span class="sxs-lookup"><span data-stu-id="a6a27-108">**Error ID:** BC30205</span></span>
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a6a27-109">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="a6a27-109">To correct this error</span></span>
  
1. <span data-ttu-id="a6a27-110">İki farklı deyimin yanlışlıkla aynı satıra yerleştirilip yerleştirilmediğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="a6a27-110">Check to see if two different statements have inadvertently been put on the same line.</span></span>
  
2. <span data-ttu-id="a6a27-111">İfadeyi tamamlayan öğeden sonra bir satır Sonlandırıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="a6a27-111">Insert a line terminator after the element that completes the statement.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a6a27-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6a27-112">See also</span></span>

- [<span data-ttu-id="a6a27-113">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="a6a27-113">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="a6a27-114">Deyimler</span><span class="sxs-lookup"><span data-stu-id="a6a27-114">Statements</span></span>](../../programming-guide/language-features/statements.md)
