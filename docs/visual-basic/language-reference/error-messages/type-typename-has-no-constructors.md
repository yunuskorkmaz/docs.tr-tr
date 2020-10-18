---
title: "'<typename>' türünün yapıcısı yok"
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 249bcb7020f26c7c43d560e91ef7a34e4dc64470
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161185"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="46b03-102">BC30251: ' \<typename> ' türünün oluşturucusu yok</span><span class="sxs-lookup"><span data-stu-id="46b03-102">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="46b03-103">Bir tür, çağrısını desteklemez `Sub New()` .</span><span class="sxs-lookup"><span data-stu-id="46b03-103">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="46b03-104">Olası bir neden, bozuk bir derleyici veya ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="46b03-104">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="46b03-105">**Hata kimliği:** BC30251</span><span class="sxs-lookup"><span data-stu-id="46b03-105">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="46b03-106">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="46b03-106">To correct this error</span></span>

1. <span data-ttu-id="46b03-107">Tür farklı bir projede veya başvurulan bir dosyada yer alıyorsa, projeyi veya dosyayı yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="46b03-107">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="46b03-108">Tür aynı projem ise, türü içeren derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="46b03-108">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="46b03-109">Hata yinelenirse Visual Basic derleyicisini yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="46b03-109">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="46b03-110">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="46b03-110">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="46b03-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46b03-111">See also</span></span>

- [<span data-ttu-id="46b03-112">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="46b03-112">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="46b03-113">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="46b03-113">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
