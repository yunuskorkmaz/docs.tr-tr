---
description: 'Hakkında daha fazla bilgi edinin: yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma'
title: Özel durumlar birlikte çalışabilirlik
ms.date: 01/16/2020
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- interop, exceptions
- exceptions, interop
ms.openlocfilehash: 3062aea2632771605c5a3c942c8471309e043f60
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99713201"
---
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a><span data-ttu-id="4dd28-103">Yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma</span><span class="sxs-lookup"><span data-stu-id="4dd28-103">Working with Interop Exceptions in Unmanaged Code</span></span>

<span data-ttu-id="4dd28-104">Yönetilmeyen kod özel durumu birlikte çalışması yalnızca Windows platformlarında desteklenir.</span><span class="sxs-lookup"><span data-stu-id="4dd28-104">Unmanaged code exception interop is supported on Windows platforms only.</span></span> <span data-ttu-id="4dd28-105">Windows olmayan platformlarda taşınabilirlik sorunları ortaya çıkar.</span><span class="sxs-lookup"><span data-stu-id="4dd28-105">Portability issues arise on non-Windows platforms.</span></span> <span data-ttu-id="4dd28-106">UNIX ABı özel durum işleme tanımına sahip olmadığından, yönetilen kod özel durum mekanizmalarının, kapsamaların altında nasıl çalıştığını bilmez.</span><span class="sxs-lookup"><span data-stu-id="4dd28-106">Since the Unix ABI has no definition for exception handling, managed code can't know how exception mechanisms work under the covers.</span></span> <span data-ttu-id="4dd28-107">Bu nedenle, özel durumlar öngörülemeyen davranışlara ve kilitlenmelere neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="4dd28-107">Therefore, exceptions can end up resulting in unpredictable behaviors and crashes.</span></span>

## <a name="setjmplongjmp-behaviors"></a><span data-ttu-id="4dd28-108">Setjmp/longjmp davranışları</span><span class="sxs-lookup"><span data-stu-id="4dd28-108">Setjmp/Longjmp Behaviors</span></span>

<span data-ttu-id="4dd28-109">WITH `setjmp` ve `longjmp` C işlevleriyle birlikte çalışma desteklenmez.</span><span class="sxs-lookup"><span data-stu-id="4dd28-109">Interop with `setjmp` and `longjmp` C functions is not supported.</span></span> <span data-ttu-id="4dd28-110">`longjmp`Yönetilen çerçeveleri atlamak için kullanamazsınız.</span><span class="sxs-lookup"><span data-stu-id="4dd28-110">You can't use `longjmp` to skip over managed frames.</span></span>

<span data-ttu-id="4dd28-111">Daha fazla bilgi için bkz. [longjmp belgeleri](/cpp/c-runtime-library/reference/longjmp).</span><span class="sxs-lookup"><span data-stu-id="4dd28-111">For more information, see [longjmp documentation](/cpp/c-runtime-library/reference/longjmp).</span></span>

## <a name="see-also"></a><span data-ttu-id="4dd28-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd28-112">See also</span></span>

- [<span data-ttu-id="4dd28-113">Özel durumlar</span><span class="sxs-lookup"><span data-stu-id="4dd28-113">Exceptions</span></span>](index.md)
- [<span data-ttu-id="4dd28-114">Yerel kitaplıklarla birlikte çalışma</span><span class="sxs-lookup"><span data-stu-id="4dd28-114">Interop with Native Libraries</span></span>](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
