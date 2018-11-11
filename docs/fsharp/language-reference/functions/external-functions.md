---
title: Dış İşlevler (F#)
description: Yerel kodda işlevleri çağırmak için F# dil desteği hakkında bilgi edinin.
ms.date: 05/16/2016
ms.openlocfilehash: db0d3362d867b07b333951f3380c6735ff471d5e
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "45973111"
---
# <a name="external-functions"></a>Dış İşlevler

Bu konuda, yerel kodda işlevleri çağırmak için F# dil desteği açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde, *bağımsız değişkenleri* için sağlanan bağımsız değişkenleri temsil eden `System.Runtime.InteropServices.DllImportAttribute` özniteliği. İlk bağımsız değişkeni, .dll uzantısı olmadan, bu işlevi içeren dll Dosyasının adını temsil eden bir dizedir. Herhangi bir genel özellikleri için ek bağımsız değişkenler sağlanabilir `System.Runtime.InteropServices.DllImportAttribute` çağırma kuralı gibi bir sınıf.

Yerel C++ aşağıdaki dışarı aktarılan işlevin içeren DLL olduğu varsayılır.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Bu işleve F#'den aşağıdaki kodu kullanarak çağırabilirsiniz.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Yerel kod ile birlikte çalışabilirlik olarak adlandırılır *platform çağırma* ve CLR özelliğidir. Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md). Bu bölümdeki bilgiler, F# için geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)
