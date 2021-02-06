---
description: "Hakkında daha fazla bilgi edinin: BC30251: Type ' <typename> ' için Oluşturucu yok"
title: "'<typename>' türünün yapıcısı yok"
ms.date: 07/20/2015
f1_keywords:
- bc30251
- vbc30251
helpviewer_keywords:
- BC30251
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
ms.openlocfilehash: 32ae854e9f1b037a17d9c378ce7ee4a3f9b43ad2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99641180"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="e85a5-103">BC30251: ' \<typename> ' türünün oluşturucusu yok</span><span class="sxs-lookup"><span data-stu-id="e85a5-103">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="e85a5-104">Bir tür, çağrısını desteklemez `Sub New()` .</span><span class="sxs-lookup"><span data-stu-id="e85a5-104">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="e85a5-105">Olası bir neden, bozuk bir derleyici veya ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="e85a5-105">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="e85a5-106">**Hata kimliği:** BC30251</span><span class="sxs-lookup"><span data-stu-id="e85a5-106">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="e85a5-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="e85a5-107">To correct this error</span></span>

1. <span data-ttu-id="e85a5-108">Tür farklı bir projede veya başvurulan bir dosyada yer alıyorsa, projeyi veya dosyayı yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e85a5-108">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="e85a5-109">Tür aynı projem ise, türü içeren derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="e85a5-109">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="e85a5-110">Hata yinelenirse Visual Basic derleyicisini yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="e85a5-110">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="e85a5-111">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="e85a5-111">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="e85a5-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e85a5-112">See also</span></span>

- [<span data-ttu-id="e85a5-113">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="e85a5-113">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="e85a5-114">Bizimle iletişime geçin</span><span class="sxs-lookup"><span data-stu-id="e85a5-114">Talk to Us</span></span>](/visualstudio/ide/feedback-options)
