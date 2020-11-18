---
title: Özel durumlar birlikte çalışabilirlik
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: db7c9943c298607aa91a4bd08ddc12bbafc872be
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830629"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="85876-102">Yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="85876-102">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="85876-103">Yönetilmeyen kod özel durumu birlikte çalışması yalnızca Windows platformlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="85876-103">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="85876-104">Windows olmayan platformlarda taşınabilirlik sorunları ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="85876-104">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="85876-105">UNIX ABı özel durum işleme tanımına sahip olmadığından, yönetilen kod özel durum mekanizmalarının, kapsamaların altında nasıl çalıştığını bilmez.</span><span class="sxs-lookup"><span data-stu-id="85876-105">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="85876-106">Bu nedenle, özel durumlar öngörülemeyen davranışlara ve kilitlenmelere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="85876-106">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="85876-107">Setjmp/longjmp davranışları</span><span class="sxs-lookup"><span data-stu-id="85876-107">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="85876-108">WITH `setjmp` ve `longjmp` C işlevleriyle birlikte çalışma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="85876-108">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="85876-109">`longjmp`Yönetilen çerçeveleri atlamak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="85876-109">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="85876-110">Daha fazla bilgi için bkz. [longjmp belgeleri](/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="85876-110">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="85876-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85876-111">See also</span></span>

- [<span data-ttu-id="85876-112">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="85876-112">Exceptions</span></span>](index.md)
- [<span data-ttu-id="85876-113">Yerel kitaplıklarla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="85876-113">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
