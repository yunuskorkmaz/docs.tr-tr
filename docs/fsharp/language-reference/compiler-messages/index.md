---
title: Derleyici hataları ve uyarıları
description: 'F # derleyicisinin yayalacak hataların ve uyarıların açıklamaları ve çözümleri'
ms.date: 12/21/2019
ms.openlocfilehash: 58430297abe807027afdc52841d67d1233401ff1
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856126"
---
# <a name="f-compiler-messages"></a><span data-ttu-id="6be1a-103">F # derleyici iletileri</span><span class="sxs-lookup"><span data-stu-id="6be1a-103">F# compiler messages</span></span>

<span data-ttu-id="6be1a-104">Bu bölümde, F # derleyicisinin belirli yapılar için yayacaktır derleyicisi hataları ve uyarıları ayrıntılı olarak gösterilir.</span><span class="sxs-lookup"><span data-stu-id="6be1a-104">This section details compiler errors and warnings that the F# compiler will emit for certain constructs.</span></span> <span data-ttu-id="6be1a-105">Varsayılan hata kümeleri şu şekilde değiştirilebilir:</span><span class="sxs-lookup"><span data-stu-id="6be1a-105">The default sets of errors can be changed by:</span></span>

- <span data-ttu-id="6be1a-106">Derleyici seçeneğini kullanarak belirli uyarıları hatalar gibi davranma `-warnaserror+`</span><span class="sxs-lookup"><span data-stu-id="6be1a-106">Treating specific warnings as if they were errors by using the `-warnaserror+` compiler option,</span></span>

- <span data-ttu-id="6be1a-107">Derleyici seçeneğini kullanarak belirli uyarıları yok sayma `-nowarn`</span><span class="sxs-lookup"><span data-stu-id="6be1a-107">Ignoring specific warnings by using the `-nowarn` compiler option</span></span>

<span data-ttu-id="6be1a-108">Bu bölümde belirli bir uyarı veya hata henüz kaydedilmediyse:</span><span class="sxs-lookup"><span data-stu-id="6be1a-108">If a particular warning or error is not yet recorded in this section:</span></span>

- <span data-ttu-id="6be1a-109">Bu sayfanın sonuna gidin ve hatanın numarasını veya metnini içeren geri bildirim gönderin veya</span><span class="sxs-lookup"><span data-stu-id="6be1a-109">Go to the end of this page and send feedback that includes the number or text of the error, or</span></span>
- <span data-ttu-id="6be1a-110">[Create-New-FSharp-Compiler-Message. FSX](https://github.com/dotnet/docs/blob/master/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) içindeki yönergeleri izleyerek ve bu depo için bir çekme isteği açarak kendiniz ekleyin.</span><span class="sxs-lookup"><span data-stu-id="6be1a-110">Add it yourself by following the instructions in [create-new-fsharp-compiler-message.fsx](https://github.com/dotnet/docs/blob/master/docs/fsharp/language-reference/compiler-messages/util/create-new-fsharp-compiler-message.fsx) and opening a pull request for this repository.</span></span>

## <a name="see-also"></a><span data-ttu-id="6be1a-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6be1a-111">See also</span></span>

- [<span data-ttu-id="6be1a-112">F # derleyici seçenekleri</span><span class="sxs-lookup"><span data-stu-id="6be1a-112">F# Compiler Options</span></span>](../compiler-options.md)
