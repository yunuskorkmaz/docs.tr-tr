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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma

Yönetilmeyen kod özel durumu birlikte çalışması yalnızca Windows platformlarında desteklenir. Windows olmayan platformlarda taşınabilirlik sorunları ortaya çıkar. UNIX ABı özel durum işleme tanımına sahip olmadığından, yönetilen kod özel durum mekanizmalarının, kapsamaların altında nasıl çalıştığını bilmez. Bu nedenle, özel durumlar öngörülemeyen davranışlara ve kilitlenmelere neden olabilir.

## <a name="setjmplongjmp-behaviors"></a>Setjmp/longjmp davranışları

WITH `setjmp` ve `longjmp` C işlevleriyle birlikte çalışma desteklenmez. Yönetilen çerçeveleri atlamak `longjmp` için kullanamazsınız.

Daha fazla bilgi için bkz. [longjmp belgeleri](https://docs.microsoft.com/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
- [Yerel kitaplıklarla birlikte çalışma](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
