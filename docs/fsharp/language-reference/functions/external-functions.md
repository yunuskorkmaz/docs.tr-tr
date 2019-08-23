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
# <a name="external-functions"></a><span data-ttu-id="f2057-103">Dış İşlevler</span><span class="sxs-lookup"><span data-stu-id="f2057-103">External Functions</span></span>

<span data-ttu-id="f2057-104">Bu konuda yerel F# kodda işlev çağırma için dil desteği açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2057-104">This topic describes F# language support for calling functions in native code.</span></span>

## <a name="syntax"></a><span data-ttu-id="f2057-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2057-105">Syntax</span></span>

```fsharp
[<DllImport( arguments )>]
extern declaration
```

## <a name="remarks"></a><span data-ttu-id="f2057-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2057-106">Remarks</span></span>

<span data-ttu-id="f2057-107">Önceki sözdiziminde *bağımsız değişkenler* `System.Runtime.InteropServices.DllImportAttribute` özniteliğe sağlanan bağımsız değişkenleri temsil eder.</span><span class="sxs-lookup"><span data-stu-id="f2057-107">In the previous syntax, *arguments* represents arguments that are supplied to the `System.Runtime.InteropServices.DllImportAttribute` attribute.</span></span> <span data-ttu-id="f2057-108">İlk bağımsız değişken,. dll uzantısı olmadan bu işlevi içeren DLL 'nin adını temsil eden bir dizedir.</span><span class="sxs-lookup"><span data-stu-id="f2057-108">The first argument is a string that represents the name of the DLL that contains this function, without the .dll extension.</span></span> <span data-ttu-id="f2057-109">`System.Runtime.InteropServices.DllImportAttribute` Sınıf için çağrı kuralı gibi genel özelliklerden herhangi biri için ek bağımsız değişkenler sağlanabilir.</span><span class="sxs-lookup"><span data-stu-id="f2057-109">Additional arguments can be supplied for any of the public properties of the `System.Runtime.InteropServices.DllImportAttribute` class, such as the calling convention.</span></span>

<span data-ttu-id="f2057-110">Aşağıdaki içe aktarılmış işlevi içeren C++ bir yerel dll dosyanız olduğunu varsayalım.</span><span class="sxs-lookup"><span data-stu-id="f2057-110">Assume you have a native C++ DLL that contains the following exported function.</span></span>

```cpp
#include <stdio.h>
extern "C" void __declspec(dllexport) HelloWorld()
{
    printf("Hello world, invoked by F#!\n");
}
```

<span data-ttu-id="f2057-111">Aşağıdaki kodu kullanarak bu işlevi F# çağırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2057-111">You can call this function from F# by using the following code.</span></span>

```fsharp
open System.Runtime.InteropServices

module InteropWithNative =
    [<DllImport(@"C:\bin\nativedll", CallingConvention = CallingConvention.Cdecl)>]
    extern void HelloWorld()

InteropWithNative.HelloWorld()
```

<span data-ttu-id="f2057-112">Yerel kodla birlikte çalışabilirlik *Platform çağrısı* olarak ADLANDıRıLıR ve clr 'nin bir özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="f2057-112">Interoperability with native code is referred to as *platform invoke* and is a feature of the CLR.</span></span> <span data-ttu-id="f2057-113">Daha fazla bilgi için bkz. [yönetilmeyen kodla birlikte çalışma](../../../framework/interop/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2057-113">For more information, see [Interoperating with Unmanaged Code](../../../framework/interop/index.md).</span></span> <span data-ttu-id="f2057-114">Bu bölümdeki bilgiler için F#geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f2057-114">The information in that section is applicable to F#.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2057-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2057-115">See also</span></span>

- [<span data-ttu-id="f2057-116">İşlevler</span><span class="sxs-lookup"><span data-stu-id="f2057-116">Functions</span></span>](index.md)
