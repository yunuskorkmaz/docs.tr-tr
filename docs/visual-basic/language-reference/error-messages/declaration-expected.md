---
description: 'Hakkında daha fazla bilgi edinin: BC30188: bildirim bekleniyor'
title: Bildirim bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: b86c182fb9dc8ab7d624833136f0e87b072aed92
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796671"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="01ca7-103">BC30188: bildirim bekleniyor</span><span class="sxs-lookup"><span data-stu-id="01ca7-103">BC30188: Declaration expected</span></span>

<span data-ttu-id="01ca7-104">Atama veya döngü deyimi gibi bildirime dayalı olmayan bir ifade, herhangi bir yordamın dışında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="01ca7-104">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="01ca7-105">Yordamların dışında yalnızca bildirimlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="01ca7-105">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="01ca7-106">Alternatif olarak, bir programlama öğesi veya gibi bir bildirim anahtar sözcüğü olmadan `Dim` bildirilmiştir `Const` .</span><span class="sxs-lookup"><span data-stu-id="01ca7-106">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="01ca7-107">**Hata kimliği:** BC30188</span><span class="sxs-lookup"><span data-stu-id="01ca7-107">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="01ca7-108">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="01ca7-108">To correct this error</span></span>

- <span data-ttu-id="01ca7-109">Bildirim temelli olmayan deyimi bir yordamın gövdesine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="01ca7-109">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="01ca7-110">Bildirime uygun bir bildirim anahtar sözcüğüyle başlayın.</span><span class="sxs-lookup"><span data-stu-id="01ca7-110">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="01ca7-111">Bildirim anahtar sözcüğünün yanlış yazılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="01ca7-111">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="01ca7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01ca7-112">See also</span></span>

- [<span data-ttu-id="01ca7-113">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="01ca7-113">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="01ca7-114">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="01ca7-114">Dim Statement</span></span>](../statements/dim-statement.md)
