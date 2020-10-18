---
title: Bildirim bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: 2755f5afcb96ca7a6c4d140908649390dd66d571
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92162706"
---
# <a name="bc30188-declaration-expected"></a><span data-ttu-id="ec3f0-102">BC30188: bildirim bekleniyor</span><span class="sxs-lookup"><span data-stu-id="ec3f0-102">BC30188: Declaration expected</span></span>

<span data-ttu-id="ec3f0-103">Atama veya döngü deyimi gibi bildirime dayalı olmayan bir ifade, herhangi bir yordamın dışında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="ec3f0-104">Yordamların dışında yalnızca bildirimlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-104">Only declarations are allowed outside procedures.</span></span>

 <span data-ttu-id="ec3f0-105">Alternatif olarak, bir programlama öğesi veya gibi bir bildirim anahtar sözcüğü olmadan `Dim` bildirilmiştir `Const` .</span><span class="sxs-lookup"><span data-stu-id="ec3f0-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>

 <span data-ttu-id="ec3f0-106">**Hata kimliği:** BC30188</span><span class="sxs-lookup"><span data-stu-id="ec3f0-106">**Error ID:** BC30188</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="ec3f0-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="ec3f0-107">To correct this error</span></span>

- <span data-ttu-id="ec3f0-108">Bildirim temelli olmayan deyimi bir yordamın gövdesine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-108">Move the nondeclarative statement to the body of a procedure.</span></span>

- <span data-ttu-id="ec3f0-109">Bildirime uygun bir bildirim anahtar sözcüğüyle başlayın.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-109">Begin the declaration with an appropriate declaration keyword.</span></span>

- <span data-ttu-id="ec3f0-110">Bildirim anahtar sözcüğünün yanlış yazılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-110">Ensure that a declaration keyword is not misspelled.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec3f0-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ec3f0-111">See also</span></span>

- [<span data-ttu-id="ec3f0-112">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="ec3f0-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="ec3f0-113">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="ec3f0-113">Dim Statement</span></span>](../statements/dim-statement.md)
