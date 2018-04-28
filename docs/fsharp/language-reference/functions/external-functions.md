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
# <a name="external-functions"></a><span data-ttu-id="d1e15-103">Dış İşlevler</span><span class="sxs-lookup"><span data-stu-id="d1e15-103">External Functions</span></span>

<span data-ttu-id="d1e15-104">Bu konuda yerel kodda işlevleri çağırma F # dili desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1e15-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="d1e15-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1e15-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="d1e15-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1e15-106">Remarks</span></span>

<span data-ttu-id="d1e15-107">Önceki sözdiziminde *bağımsız değişkenleri* için sağlanan değişkenlerini temsil eden `System.Runtime.InteropServices.DllImportAttribute` özniteliği.</span><span class="sxs-lookup"><span data-stu-id="d1e15-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="d1e15-108">İlk bağımsız değişken .dll uzantısı olmadan bu işlevi içeren dll Dosyasının adını temsil eden bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="d1e15-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="d1e15-109">Ek bağımsız değişkenler sağlanan herhangi bir ortak özellikleri için `System.Runtime.InteropServices.DllImportAttribute` çağırma gibi sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d1e15-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="d1e15-110">Yerel C++ aşağıdaki dışarı aktarılan işlevi içeren DLL olduğunu varsayın.</span><span class="sxs-lookup"><span data-stu-id="d1e15-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="d1e15-111">Bu işlev F # aşağıdaki kodu kullanarak çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d1e15-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="d1e15-112">Yerel kod ile birlikte çalışabilirlik olarak adlandırılır *platform çağırma* ve CLR özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="d1e15-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="d1e15-113">Daha fazla bilgi için bkz: [yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="d1e15-113">For more information, see [Interoperating with Unmanaged Code](../../../../docs/framework/interop/index.md).</span></span> <span data-ttu-id="d1e15-114">Bu bölümdeki bilgiler, F # için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d1e15-114">The information in that section is applicable to F#.</span></span>


## <a name="see-also"></a><span data-ttu-id="d1e15-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e15-115">See Also</span></span>

[<span data-ttu-id="d1e15-116">İşlevler</span><span class="sxs-lookup"><span data-stu-id="d1e15-116">Functions</span></span>](index.md)
