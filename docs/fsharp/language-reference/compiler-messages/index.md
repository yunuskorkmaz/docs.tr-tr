---
title: Derleyici hataları ve uyarıları
description: 'F # derleyicisinin yayalacak hataların ve uyarıların açıklamaları ve çözümleri'
ms.date: 12/21/2019
ms.openlocfilehash: 9769ddee989f0774cfae8842e60dbd3fd2065f9c
ms.sourcegitcommit: e3cf8227573e13b8e1f4e3dc007404881cdafe47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/11/2021
ms.locfileid: "103190183"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="76000-103">F # derleyici iletileri</span><span class="sxs-lookup"><span data-stu-id="76000-103">F# compiler messages</span></span>

<span data-ttu-id="76000-104">Bu bölümde, F # derleyicisinin belirli yapılar için yayacaktır derleyicisi hataları ve uyarıları ayrıntılı olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="76000-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="76000-105">Varsayılan hata kümeleri şu şekilde değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="76000-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="76000-106">Derleyici seçeneğini kullanarak belirli uyarıları hatalar gibi davranma `-warnaserror+`</span><span class="sxs-lookup"><span data-stu-id="76000-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="76000-107">Derleyici seçeneğini kullanarak belirli uyarıları yok sayma `-nowarn`</span><span class="sxs-lookup"><span data-stu-id="76000-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="76000-108">Bu bölümde belirli bir uyarı veya hata henüz kaydedilmediyse:</span><span class="sxs-lookup"><span data-stu-id="76000-108">If a particular warning or error is not yet recorded in this section:</span></span>

- <span data-ttu-id="76000-109">Bu sayfanın sonuna gidin ve hatanın numarasını veya metnini içeren geri bildirim gönderin veya</span><span class="sxs-lookup"><span data-stu-id="76000-109">Go to the end of this page and send feedback that includes the number or text of the error, or</span></span>
- <span data-ttu-id="76000-110">[Create-New-FSharp-Compiler-Message. FSX](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) içindeki yönergeleri izleyerek ve bu depo için bir çekme isteği açarak kendiniz ekleyin.</span><span class="sxs-lookup"><span data-stu-id="76000-110">Add it yourself by following the instructions in [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/main/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) and opening a pull request for this repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="76000-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="76000-111">See also</span></span>

- [<span data-ttu-id="76000-112">F # derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="76000-112">F# Compiler Options</span></span>](../compiler-options.md)
