---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları
description: Kodunuzda kaynak satır numarası, dizin ve F# dosya adına erişmenizi sağlayan yerleşik tanımlayıcı değerlerini nasıl kullanacağınızı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 5ff36210edc75370f8baf9ee7be057f3ac0c3979
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627123"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="89e67-103">Kaynak Satırı, Dosya ve Yol Tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="89e67-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="89e67-104">`__LINE__`, Vekodunuzda`__SOURCE_FILE__` kaynak satır numarası, dizin ve dosya adına erişmenizi sağlayan yerleşik değerlerdir. `__SOURCE_DIRECTORY__`</span><span class="sxs-lookup"><span data-stu-id="89e67-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="89e67-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="89e67-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="89e67-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="89e67-106">Remarks</span></span>

<span data-ttu-id="89e67-107">Bu değerlerin her birinin türü `string`vardır.</span><span class="sxs-lookup"><span data-stu-id="89e67-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="89e67-108">Aşağıdaki tabloda, ' de F#bulunan kaynak satırı, dosya ve yol tanımlayıcıları özetlenmektedir.</span><span class="sxs-lookup"><span data-stu-id="89e67-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="89e67-109">Bu tanımlayıcılar Önişlemci makroları değildir; derleyici tarafından tanınan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="89e67-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="89e67-110">Önceden tanımlanmış tanımlayıcı</span><span class="sxs-lookup"><span data-stu-id="89e67-110">Predefined identifier</span></span>|<span data-ttu-id="89e67-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="89e67-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="89e67-112">, Yönergeleri dikkate alarak `#line` geçerli satır numarasını değerlendirir.</span><span class="sxs-lookup"><span data-stu-id="89e67-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="89e67-113">Kaynak dizinin geçerli tam yolu olarak değerlendirilir ve yönergeleri göz önünde `#line` bulundurur.</span><span class="sxs-lookup"><span data-stu-id="89e67-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="89e67-114">Yolu ve yönergeleri dikkate `#line` almadan geçerli kaynak dosya adı olarak değerlendirilir.</span><span class="sxs-lookup"><span data-stu-id="89e67-114">Evaluates to the current source file name, without its path, considering `#line` directives.</span></span>|

<span data-ttu-id="89e67-115">`#line` Yönergesi hakkında daha fazla bilgi için bkz. [derleyici yönergeleri](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="89e67-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="89e67-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="89e67-116">Example</span></span>

<span data-ttu-id="89e67-117">Aşağıdaki kod örneği, bu değerlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="89e67-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="89e67-118">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="89e67-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a><span data-ttu-id="89e67-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="89e67-119">See also</span></span>

- [<span data-ttu-id="89e67-120">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="89e67-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="89e67-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="89e67-121">F# Language Reference</span></span>](index.md)
