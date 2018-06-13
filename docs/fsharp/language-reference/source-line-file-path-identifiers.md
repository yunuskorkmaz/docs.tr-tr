---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları (F#)
description: 'Kaynak satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik F # tanımlayıcı değerlerini kullanmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 76b705fec0d951b12655edbe69e7c9212f50779d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33565223"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="44c27-103">Kaynak Satırı, Dosya ve Yol Tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="44c27-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="44c27-104">Tanımlayıcılar `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__` kaynağı satır numarası, dizin ve dosya adı kodunuzdaki erişim sağlayan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="44c27-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>


## <a name="syntax"></a><span data-ttu-id="44c27-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44c27-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="44c27-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="44c27-106">Remarks</span></span>
<span data-ttu-id="44c27-107">Bu değerlerin her birini türüne sahip `string`.</span><span class="sxs-lookup"><span data-stu-id="44c27-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="44c27-108">Kaynak satırı, dosya ve F #'da kullanılabilir yol tanımlayıcıları aşağıdaki tabloda özetlenmiştir.</span><span class="sxs-lookup"><span data-stu-id="44c27-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="44c27-109">Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar derleyici tarafından tanınan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="44c27-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="44c27-110">Önceden tanımlanmış tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="44c27-110">Predefined identifier</span></span>|<span data-ttu-id="44c27-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="44c27-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="44c27-112">Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="44c27-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="44c27-113">Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="44c27-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="44c27-114">Geçerli kaynak dosya adını ve yolunu değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="44c27-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|
<span data-ttu-id="44c27-115">Hakkında daha fazla bilgi için `#line` yönerge, bkz: [derleyici yönergeleri](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="44c27-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="44c27-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="44c27-116">Example</span></span>

<span data-ttu-id="44c27-117">Aşağıdaki kod örneği, bu değerleri kullanımını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="44c27-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="44c27-118">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="44c27-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="44c27-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="44c27-119">See Also</span></span>
[<span data-ttu-id="44c27-120">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="44c27-120">Compiler Directives</span></span>](compiler-directives.md)

[<span data-ttu-id="44c27-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="44c27-121">F# Language Reference</span></span>](index.md)
