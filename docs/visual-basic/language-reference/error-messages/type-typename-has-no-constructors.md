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
ms.openlocfilehash: 3961ba557ad2afd9c94f071b6615573419d7325b
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106585"
---
# <a name="bc30251-type-typename-has-no-constructors"></a><span data-ttu-id="46038-103">BC30251: ' \<typename> ' türünün oluşturucusu yok</span><span class="sxs-lookup"><span data-stu-id="46038-103">BC30251: Type '\<typename>' has no constructors</span></span>

<span data-ttu-id="46038-104">Bir tür, çağrısını desteklemez `Sub New()` .</span><span class="sxs-lookup"><span data-stu-id="46038-104">A type does not support a call to `Sub New()`.</span></span> <span data-ttu-id="46038-105">Olası bir neden, bozuk bir derleyici veya ikili dosyadır.</span><span class="sxs-lookup"><span data-stu-id="46038-105">One possible cause is a corrupted compiler or binary file.</span></span>

 <span data-ttu-id="46038-106">**Hata kimliği:** BC30251</span><span class="sxs-lookup"><span data-stu-id="46038-106">**Error ID:** BC30251</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="46038-107">Bu hatayı düzeltmek için</span><span class="sxs-lookup"><span data-stu-id="46038-107">To correct this error</span></span>

1. <span data-ttu-id="46038-108">Tür farklı bir projede veya başvurulan bir dosyada yer alıyorsa, projeyi veya dosyayı yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="46038-108">If the type is in a different project or in a referenced file, reinstall the project or file.</span></span>

2. <span data-ttu-id="46038-109">Tür aynı projem ise, türü içeren derlemeyi yeniden derleyin.</span><span class="sxs-lookup"><span data-stu-id="46038-109">If the type is in the same project, recompile the assembly containing the type.</span></span>

3. <span data-ttu-id="46038-110">Hata yinelenirse Visual Basic derleyicisini yeniden yükleyin.</span><span class="sxs-lookup"><span data-stu-id="46038-110">If the error recurs, reinstall the Visual Basic compiler.</span></span>

4. <span data-ttu-id="46038-111">Hata devam ederse, koşullar hakkındaki bilgileri toplayın ve Microsoft Ürün Destek Hizmetleri 'ne bildirin.</span><span class="sxs-lookup"><span data-stu-id="46038-111">If the error persists, gather information about the circumstances and notify Microsoft Product Support Services.</span></span>

## <a name="see-also"></a><span data-ttu-id="46038-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46038-112">See also</span></span>

- [<span data-ttu-id="46038-113">Nesneler ve sınıflar</span><span class="sxs-lookup"><span data-stu-id="46038-113">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="46038-114">Visual Studio geri bildirim seçenekleri</span><span class="sxs-lookup"><span data-stu-id="46038-114">Visual Studio feedback options</span></span>](/visualstudio/ide/feedback-options)
