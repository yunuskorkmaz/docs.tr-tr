---
title: Dış İşlevler
description: Hakkında bilgi edinin F# yerel kodda işlevleri çağırmak için dil desteği.
ms.date: 05/16/2016
ms.openlocfilehash: 86ea78844fb812361233f8360c377465d83be203
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53611738"
---
# <a name="external-functions"></a>Dış İşlevler

Bu konu başlığı altında açıklanır F# yerel kodda işlevleri çağırmak için dil desteği.

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

Bu işlevi çağırabilirsiniz F# aşağıdaki kodu kullanarak.

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

Yerel kod ile birlikte çalışabilirlik olarak adlandırılır *platform çağırma* ve CLR özelliğidir. Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md). Bu bölümdeki bilgiler, geçerlidir F#.

## <a name="see-also"></a>Ayrıca bkz.

- [İşlevler](index.md)