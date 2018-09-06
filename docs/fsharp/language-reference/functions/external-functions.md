---
title: Dış İşlevler (F#)
description: 'Yerel kodda işlevleri çağırmak için F # dil desteği hakkında bilgi edinin.'
ms.date: 05/16/2016
ms.openlocfilehash: db0d3362d867b07b333951f3380c6735ff471d5e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43747388"
---
# <a name="external-functions"></a><span data-ttu-id="d9bc1-103">Dış İşlevler</span><span class="sxs-lookup"><span data-stu-id="d9bc1-103">External Functions</span></span>

<span data-ttu-id="d9bc1-104">Bu konuda, yerel kodda işlevleri çağırmak için F # dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d9bc1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9bc1-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="d9bc1-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9bc1-106">Remarks</span></span>

<span data-ttu-id="d9bc1-107">Önceki sözdiziminde, *bağımsız değişkenleri* için sağlanan bağımsız değişkenleri temsil eden `System.Runtime.InteropServices.DllImportAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="d9bc1-108">İlk bağımsız değişkeni, .dll uzantısı olmadan, bu işlevi içeren dll Dosyasının adını temsil eden bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="d9bc1-109">Herhangi bir genel özellikleri için ek bağımsız değişkenler sağlanabilir `System.Runtime.InteropServices.DllImportAttribute` çağırma kuralı gibi bir sınıf.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="d9bc1-110">Yerel C++ aşağıdaki dışarı aktarılan işlevin içeren DLL olduğu varsayılır.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="d9bc1-111">Bu işleve F #'den aşağıdaki kodu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="d9bc1-112">Yerel kod ile birlikte çalışabilirlik olarak adlandırılır *platform çağırma* ve CLR özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="d9bc1-113">Daha fazla bilgi için [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9bc1-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="d9bc1-114">Bu bölümdeki bilgiler, F # için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="d9bc1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d9bc1-115">See also</span></span>

- [<span data-ttu-id="d9bc1-116">İşlevler</span><span class="sxs-lookup"><span data-stu-id="d9bc1-116">Functions</span></span>](index.md)
