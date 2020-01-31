---
title: Özel durumlar birlikte çalışabilirlik
ms.date: 01/16/2020
ms.technology: dotnet-standard
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 2aff71e97e1be0dbb584f4fe43c322cea86d2480
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76795177"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="f749c-102">Yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="f749c-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="f749c-103">Yönetilmeyen kod özel durumu birlikte çalışması yalnızca Windows platformlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="f749c-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="f749c-104">Windows olmayan platformlarda taşınabilirlik sorunları ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="f749c-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="f749c-105">UNIX ABı özel durum işleme tanımına sahip olmadığından, yönetilen kod özel durum mekanizmalarının, kapsamaların altında nasıl çalıştığını bilmez.</span><span class="sxs-lookup"><span data-stu-id="f749c-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="f749c-106">Bu nedenle, özel durumlar öngörülemeyen davranışlara ve kilitlenmelere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="f749c-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="f749c-107">Setjmp/longjmp davranışları</span><span class="sxs-lookup"><span data-stu-id="f749c-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="f749c-108">`setjmp` ve `longjmp` C işlevleriyle birlikte çalışma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="f749c-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="f749c-109">Yönetilen çerçeveleri atlamak için `longjmp` kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="f749c-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="f749c-110">Daha fazla bilgi için bkz. [longjmp belgeleri](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="f749c-110">For more information, see [longjmp documentation](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="f749c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f749c-111">See also</span></span>

- [<span data-ttu-id="f749c-112">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="f749c-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="f749c-113">Yerel kitaplıklarla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="f749c-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
