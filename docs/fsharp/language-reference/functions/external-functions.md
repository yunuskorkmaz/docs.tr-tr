---
title: Dış İşlevler
description: Yerel kodda çağırma F# işlevleri için dil desteği hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: 3c8edaba25e07b6ca2c44a58c4b55dc98a13b4fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968728"
---
# <a name="external-functions"></a>Dış İşlevler

Bu konuda yerel F# kodda işlev çağırma için dil desteği açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *bağımsız değişkenler* `System.Runtime.InteropServices.DllImportAttribute` özniteliğe sağlanan bağımsız değişkenleri temsil eder. İlk bağımsız değişken,. dll uzantısı olmadan bu işlevi içeren DLL 'nin adını temsil eden bir dizedir. `System.Runtime.InteropServices.DllImportAttribute` Sınıf için çağrı kuralı gibi genel özelliklerden herhangi biri için ek bağımsız değişkenler sağlanabilir.

Aşağıdaki içe aktarılmış işlevi içeren C++ bir yerel dll dosyanız olduğunu varsayalım.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Aşağıdaki kodu kullanarak bu işlevi F# çağırabilirsiniz.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Yerel kodla birlikte çalışabilirlik *Platform çağrısı* olarak ADLANDıRıLıR ve clr 'nin bir özelliğidir. Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../../framework/interop/index.md). Bu bölümdeki bilgiler için F#geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
