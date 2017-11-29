---
title: "Kaynak Satırı, Dosya ve Yol Tanımlayıcıları (F#)"
description: "Kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik F # tanımlayıcı değerlerini kullanmayı öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4cfe7439-275c-4d08-980b-784e240bbf29
ms.openlocfilehash: 44cc0914226c120f2b877ce3decd25caa6817eec
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="c0802-104">Kaynak Satırı, Dosya ve Yol Tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="c0802-104">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="c0802-105">Tanımlayıcılar `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__` kaynağı satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c0802-105">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="c0802-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0802-106">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="c0802-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0802-107">Remarks</span></span>
<span data-ttu-id="c0802-108">Bu değerlerin her birini türüne sahip `string`.</span><span class="sxs-lookup"><span data-stu-id="c0802-108">Each of these values has type `string`.</span></span>

<span data-ttu-id="c0802-109">Kaynak satırı, dosya ve F #'da kullanılabilir yol tanımlayıcıları aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="c0802-109">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="c0802-110">Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar derleyici tarafından tanınan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="c0802-110">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="c0802-111">Önceden tanımlanmış tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="c0802-111">Predefined identifier</span></span>|<span data-ttu-id="c0802-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c0802-112">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="c0802-113">Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="c0802-113">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="c0802-114">Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="c0802-114">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="c0802-115">Geçerli kaynak dosya adını ve yolunu değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="c0802-115">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="c0802-116">Hakkında daha fazla bilgi için `#line` yönerge, bkz: [derleyici yönergeleri](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="c0802-116">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0802-117">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0802-117">Example</span></span>

<span data-ttu-id="c0802-118">Aşağıdaki kod örneği, bu değerleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="c0802-118">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="c0802-119">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="c0802-119">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="c0802-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c0802-120">See Also</span></span>
[<span data-ttu-id="c0802-121">Derleyici yönergeleri</span><span class="sxs-lookup"><span data-stu-id="c0802-121">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="c0802-122">F # dili başvurusu</span><span class="sxs-lookup"><span data-stu-id="c0802-122">F# Language Reference</span></span>](index.md)
