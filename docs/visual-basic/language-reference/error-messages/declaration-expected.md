---
title: Bildirim bekleniyor
ms.date: 07/20/2015
f1_keywords:
- vbc30188
- bc30188
helpviewer_keywords:
- BC30188
ms.assetid: da6b1df3-fe6b-4415-88e6-0977e5189e0b
ms.openlocfilehash: ee8f1f9ec26dc6c938f0b412dfe30832e3cfe165
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874519"
---
# <a name="declaration-expected"></a><span data-ttu-id="00764-102">Bildirim bekleniyor</span><span class="sxs-lookup"><span data-stu-id="00764-102">Declaration expected</span></span>

<span data-ttu-id="00764-103">Atama veya döngü deyimi gibi bildirime dayalı olmayan bir ifade, herhangi bir yordamın dışında meydana gelir.</span><span class="sxs-lookup"><span data-stu-id="00764-103">A nondeclarative statement, such as an assignment or loop statement, occurs outside any procedure.</span></span> <span data-ttu-id="00764-104">Yordamların dışında yalnızca bildirimlere izin verilir.</span><span class="sxs-lookup"><span data-stu-id="00764-104">Only declarations are allowed outside procedures.</span></span>  
  
 <span data-ttu-id="00764-105">Alternatif olarak, bir programlama öğesi veya gibi bir bildirim anahtar sözcüğü olmadan `Dim` bildirilmiştir `Const` .</span><span class="sxs-lookup"><span data-stu-id="00764-105">Alternatively, a programming element is declared without a declaration keyword such as `Dim` or `Const`.</span></span>  
  
 <span data-ttu-id="00764-106">**Hata kimliği:** BC30188</span><span class="sxs-lookup"><span data-stu-id="00764-106">**Error ID:** BC30188</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="00764-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="00764-107">To correct this error</span></span>  
  
- <span data-ttu-id="00764-108">Bildirim temelli olmayan deyimi bir yordamın gövdesine taşıyın.</span><span class="sxs-lookup"><span data-stu-id="00764-108">Move the nondeclarative statement to the body of a procedure.</span></span>  
  
- <span data-ttu-id="00764-109">Bildirime uygun bir bildirim anahtar sözcüğüyle başlayın.</span><span class="sxs-lookup"><span data-stu-id="00764-109">Begin the declaration with an appropriate declaration keyword.</span></span>  
  
- <span data-ttu-id="00764-110">Bildirim anahtar sözcüğünün yanlış yazılmadığından emin olun.</span><span class="sxs-lookup"><span data-stu-id="00764-110">Ensure that a declaration keyword is not misspelled.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00764-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="00764-111">See also</span></span>

- [<span data-ttu-id="00764-112">Yordamlar</span><span class="sxs-lookup"><span data-stu-id="00764-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="00764-113">Dim Deyimi</span><span class="sxs-lookup"><span data-stu-id="00764-113">Dim Statement</span></span>](../statements/dim-statement.md)
