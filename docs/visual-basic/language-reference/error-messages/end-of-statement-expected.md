---
description: 'Şu konuda daha fazla bilgi edinin: BC30205: for ifadesinin sonu bekleniyor'
title: Deyim sonu bekleniyor
ms.date: 07/20/2015
f1_keywords:
- bc30205
- vbc30205
helpviewer_keywords:
- BC30205
ms.assetid: 53c7f825-a737-4b76-a1fa-f67745b8bd40
ms.openlocfilehash: a3f309a4674f6de34c0be8abfef31e293a10dec5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796554"
---
# <a name="bc30205-end-of-statement-expected"></a><span data-ttu-id="7b73e-103">BC30205: for ifadesinin sonu bekleniyor</span><span class="sxs-lookup"><span data-stu-id="7b73e-103">BC30205: End of statement expected</span></span>

<span data-ttu-id="7b73e-104">İfade sözdizimsel olarak tamamlanmıştır, ancak ek bir programlama öğesi, ifadesini tamamlayan öğesini izler.</span><span class="sxs-lookup"><span data-stu-id="7b73e-104">The statement is syntactically complete, but an additional programming element follows the element that completes the statement.</span></span> <span data-ttu-id="7b73e-105">Her deyimin sonunda bir satır Sonlandırıcı gereklidir.</span><span class="sxs-lookup"><span data-stu-id="7b73e-105">A line terminator is required at the end of every statement.</span></span>

 <span data-ttu-id="7b73e-106">Satır Sonlandırıcı Visual Basic kaynak dosyanın karakterlerini çizgilere böler.</span><span class="sxs-lookup"><span data-stu-id="7b73e-106">A line terminator divides the characters of a Visual Basic source file into lines.</span></span> <span data-ttu-id="7b73e-107">Satır sonlandırıcılar örnekleri, Unicode satır başı karakteri (&HD), Unicode satır besleme karakteri (&ha) ve ardından Unicode satır besleme karakteri ile Unicode satır başı karakteri.</span><span class="sxs-lookup"><span data-stu-id="7b73e-107">Examples of line terminators are the Unicode carriage return character (&HD), the Unicode linefeed character (&HA), and the Unicode carriage return character followed by the Unicode linefeed character.</span></span> <span data-ttu-id="7b73e-108">Satır sonlandırıcılar hakkında daha fazla bilgi için [Visual Basic dil belirtimine](~/_vblang/spec/lexical-grammar.md#line-terminators)bakın.</span><span class="sxs-lookup"><span data-stu-id="7b73e-108">For more information about line terminators, see the [Visual Basic Language Specification](~/_vblang/spec/lexical-grammar.md#line-terminators).</span></span>

 <span data-ttu-id="7b73e-109">**Hata kimliği:** BC30205</span><span class="sxs-lookup"><span data-stu-id="7b73e-109">**Error ID:** BC30205</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7b73e-110">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="7b73e-110">To correct this error</span></span>

1. <span data-ttu-id="7b73e-111">İki farklı deyimin yanlışlıkla aynı satıra yerleştirilip yerleştirilmediğini denetleyin.</span><span class="sxs-lookup"><span data-stu-id="7b73e-111">Check to see if two different statements have inadvertently been put on the same line.</span></span>

2. <span data-ttu-id="7b73e-112">İfadeyi tamamlayan öğeden sonra bir satır Sonlandırıcı ekleyin.</span><span class="sxs-lookup"><span data-stu-id="7b73e-112">Insert a line terminator after the element that completes the statement.</span></span>

## <a name="see-also"></a><span data-ttu-id="7b73e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7b73e-113">See also</span></span>

- [<span data-ttu-id="7b73e-114">Nasıl yapılır: Kodda Deyimleri Bölme ve Birleştirme</span><span class="sxs-lookup"><span data-stu-id="7b73e-114">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
- [<span data-ttu-id="7b73e-115">Deyimler</span><span class="sxs-lookup"><span data-stu-id="7b73e-115">Statements</span></span>](../../programming-guide/language-features/statements.md)
