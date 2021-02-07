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
# <a name="working-with-interop-exceptions-in-unmanaged-code"></a>Yönetilmeyen koddaki birlikte çalışma özel durumlarıyla çalışma

Yönetilmeyen kod özel durumu birlikte çalışması yalnızca Windows platformlarında desteklenir. Windows olmayan platformlarda taşınabilirlik sorunları ortaya çıkar. UNIX ABı özel durum işleme tanımına sahip olmadığından, yönetilen kod özel durum mekanizmalarının, kapsamaların altında nasıl çalıştığını bilmez. Bu nedenle, özel durumlar öngörülemeyen davranışlara ve kilitlenmelere neden olabilir.

## <a name="setjmplongjmp-behaviors"></a>Setjmp/longjmp davranışları

WITH `setjmp` ve `longjmp` C işlevleriyle birlikte çalışma desteklenmez. `longjmp`Yönetilen çerçeveleri atlamak için kullanamazsınız.

Daha fazla bilgi için bkz. [longjmp belgeleri](/cpp/c-runtime-library/reference/longjmp).

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durumlar](index.md)
- [Yerel kitaplıklarla birlikte çalışma](https://www.mono-project.com/docs/advanced/pinvoke/#runtime-exception-propagation)
