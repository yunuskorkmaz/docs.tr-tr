---
title: Platformlar arası P/Invoke
description: Çalışma zamanının P/Invoke aracılığıyla yerel kitaplıkları yüklerken hangi yolları arayılacağını öğrenin. Ayrıca Setdllımportresolver 'ı kullanmayı öğrenin.
author: saul
ms.date: 01/31/2021
ms.openlocfilehash: 40ad87fe537ad043a488e4086814a58ef8e0211e
ms.sourcegitcommit: 38999dc0ec4f7c4404de5ce0951b64c55997d9ab
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/02/2021
ms.locfileid: "99427487"
---
# <a name="writing-cross-platform-pinvoke-code"></a><span data-ttu-id="19ace-104">Platformlar arası P/Invoke kodu yazma</span><span class="sxs-lookup"><span data-stu-id="19ace-104">Writing cross platform P/Invoke code</span></span>

## <a name="library-name-variations"></a><span data-ttu-id="19ace-105">Kitaplık adı çeşitlemeleri</span><span class="sxs-lookup"><span data-stu-id="19ace-105">Library name variations</span></span>

<span data-ttu-id="19ace-106">Daha basit çapraz platform P/Invoke kodunu kolaylaştırmak için, çalışma zamanı kurallı Paylaşılan kitaplık uzantısını ( `.dll` `.so` veya `.dylib` ) yerel kitaplık adlarına ekler.</span><span class="sxs-lookup"><span data-stu-id="19ace-106">To facilitate simpler cross platform P/Invoke code, the runtime adds the canonical shared library extension (`.dll`, `.so` or `.dylib`) to native library names.</span></span> <span data-ttu-id="19ace-107">Linux ve macOS 'ta çalışma zamanı de önceden bekleyen ' i dener `lib` .</span><span class="sxs-lookup"><span data-stu-id="19ace-107">On Linux and macOS, the runtime will also try prepending `lib`.</span></span> <span data-ttu-id="19ace-108">Yönetilmeyen kitaplıkları (örn.) yükleyen API 'Leri kullandığınızda bu kitaplık adları çeşitlemeleri otomatik olarak aranır <xref:System.Runtime.InteropServices.DllImportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="19ace-108">These library names variations are automatically searched when you use APIs that load unmanaged libraries (e.g., <xref:System.Runtime.InteropServices.DllImportAttribute>).</span></span>

> [!NOTE]
> <span data-ttu-id="19ace-109">Kitaplık adlarındaki mutlak yollar (örn. `/usr/lib/libc` ) olduğu gibi değerlendirilir ve hiçbir değişim aranmaz.</span><span class="sxs-lookup"><span data-stu-id="19ace-109">Absolute paths in library names (e.g., `/usr/lib/libc`) are treated as-is and no variations will be searched.</span></span>

<span data-ttu-id="19ace-110">P/Invoke kullanma ile aşağıdaki örneği göz önünde bulundurun:</span><span class="sxs-lookup"><span data-stu-id="19ace-110">Consider the following example of using P/Invoke:</span></span>

```csharp
[DllImport("nativedep")]
static extern int ExportedFunction();
```

<span data-ttu-id="19ace-111">Windows üzerinde çalışırken, DLL aşağıdaki sırayla aranır:</span><span class="sxs-lookup"><span data-stu-id="19ace-111">When running on Windows, the DLL is searched for in the following order:</span></span>

1. `nativedep`
1. <span data-ttu-id="19ace-112">`nativedep.dll` (kitaplık adı zaten veya ile bitmezse `.dll` `exe` )</span><span class="sxs-lookup"><span data-stu-id="19ace-112">`nativedep.dll` (if the library name does not already end with `.dll` or .`exe`)</span></span>

<span data-ttu-id="19ace-113">Linux veya macOS üzerinde çalışırken, çalışma zamanı, önceden bekleyen `lib` ve kurallı Paylaşılan kitaplık uzantısını eklemeye çalışacaktır.</span><span class="sxs-lookup"><span data-stu-id="19ace-113">When running on Linux or macOS, the runtime will try prepending `lib` and appending the canonical shared library extension.</span></span> <span data-ttu-id="19ace-114">Bu OSE 'de, Kitaplık adı çeşitlemeleri aşağıdaki sırada denenir:</span><span class="sxs-lookup"><span data-stu-id="19ace-114">On these OSes, library name variations are tried in the following order:</span></span>

1. `nativedep.so` / `nativedep.dylib`
1. <span data-ttu-id="19ace-115">`libnativedep.so` / `libnativedep.dylib`<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19ace-115">`libnativedep.so` / `libnativedep.dylib` <sup>1</sup></span></span>
1. `nativedep`
1. <span data-ttu-id="19ace-116">`libnativedep`<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19ace-116">`libnativedep` <sup>1</sup></span></span>

<span data-ttu-id="19ace-117">Linux 'ta, Kitaplık adı ile `.so` veya Contains `.so.` (sondaki) ile bitiyorsa arama sırası farklı olur `.` .</span><span class="sxs-lookup"><span data-stu-id="19ace-117">On Linux, the search order is different if the library name ends with `.so` or contains `.so.` (note the trailing `.`).</span></span> <span data-ttu-id="19ace-118">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="19ace-118">Consider the following example:</span></span>

```csharp
[DllImport("nativedep.so.6")]
static extern int ExportedFunction();
```

<span data-ttu-id="19ace-119">Bu durumda, Kitaplık adı çeşitlemeleri aşağıdaki sırada denenir:</span><span class="sxs-lookup"><span data-stu-id="19ace-119">In this case, the library name variations are tried in the following order:</span></span>

1. `nativedep.so.6`
1. <span data-ttu-id="19ace-120">`libnativedep.so.6`<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19ace-120">`libnativedep.so.6` <sup>1</sup></span></span>
1. `nativedep.so.6.so`
1. <span data-ttu-id="19ace-121">`libnativedep.so.6.so`<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="19ace-121">`libnativedep.so.6.so` <sup>1</sup></span></span>

<span data-ttu-id="19ace-122"><sup>1</sup> yol, yalnızca kitaplık adı bir dizin ayırıcı karakteri () içermiyorsa denetlenir `/` .</span><span class="sxs-lookup"><span data-stu-id="19ace-122"><sup>1</sup> Path is checked only if the library name does not contain a directory separator character (`/`).</span></span>

## <a name="custom-import-resolver"></a><span data-ttu-id="19ace-123">Özel içeri aktarma Çözümleyicisi</span><span class="sxs-lookup"><span data-stu-id="19ace-123">Custom import resolver</span></span>

<span data-ttu-id="19ace-124">Daha karmaşık senaryolarda, <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> çalışma ZAMANıNDA DLL içeri aktarmaları çözümlemek için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="19ace-124">In more complex scenarios, you can use <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver%2A> to resolve DLL imports at runtime.</span></span> <span data-ttu-id="19ace-125">Aşağıdaki örnekte, `nativedep` `nativedep_avx2` CPU destekliyorsa olarak çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="19ace-125">In the following example, `nativedep` is resolved to `nativedep_avx2` if the CPU supports it.</span></span>

> [!TIP]
> <span data-ttu-id="19ace-126">Bu işlevsellik yalnızca .NET 5 ve .NET Core 3,1 veya üzeri sürümlerde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="19ace-126">This functionality is only available in .NET 5 and .NET Core 3.1 or later.</span></span>

[!code-csharp[import resolver](~/samples/snippets/standard/interop/pinvoke/import-resolver/Program.cs)]

## <a name="see-also"></a><span data-ttu-id="19ace-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="19ace-127">See also</span></span>

- [<span data-ttu-id="19ace-128">Platform çağırma (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="19ace-128">Platform Invoke (P/Invoke)</span></span>](pinvoke.md)
