---
title: Dış İşlevler (F#)
description: 'Yerel kodda işlevleri çağırmak için F # dil desteği hakkında bilgi edinin.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 28e74258d91ff2d9742caa7a6c06f515cd987c0a
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="external-functions"></a>Dış İşlevler

Bu konuda yerel kodda işlevleri çağırma F # dili desteği açıklanmaktadır.

## <a name="syntax"></a>Sözdizimi

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a>Açıklamalar

Önceki sözdiziminde *bağımsız değişkenleri* için sağlanan değişkenlerini temsil eden `System.Runtime.InteropServices.DllImportAttribute` özniteliği. İlk bağımsız değişken .dll uzantısı olmadan bu işlevi içeren dll Dosyasının adını temsil eden bir dizedir. Ek bağımsız değişkenler sağlanan herhangi bir ortak özellikleri için `System.Runtime.InteropServices.DllImportAttribute` çağırma gibi sınıfı.

Yerel C++ aşağıdaki dışarı aktarılan işlevi içeren DLL olduğunu varsayın.

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

Bu işlev F # aşağıdaki kodu kullanarak çağırabilirsiniz.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Yerel kod ile birlikte çalışabilirlik olarak adlandırılır *platform çağırma* ve CLR özelliğidir. Daha fazla bilgi için bkz: [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md). Bu bölümdeki bilgiler, F # için geçerlidir.


## <a name="see-also"></a>Ayrıca Bkz.

[İşlevler](index.md)
