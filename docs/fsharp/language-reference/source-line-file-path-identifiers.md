---
title: Kaynak Satırı, Dosya ve Yol Tanımlayıcıları
description: Yerleşik kullanmayı öğrenin F# kaynağına erişmek etkinleştirdiğiniz tanımlayıcı değerlerini, sayı, dizin ve dosya adı, kodunuzda satır.
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663628"
---
# <a name="source-line-file-and-path-identifiers"></a><span data-ttu-id="865ca-103">Kaynak Satırı, Dosya ve Yol Tanımlayıcıları</span><span class="sxs-lookup"><span data-stu-id="865ca-103">Source Line, File, and Path Identifiers</span></span>

<span data-ttu-id="865ca-104">Tanımlayıcıları `__LINE__`, `__SOURCE_DIRECTORY__` ve `__SOURCE_FILE__` kodunuzda kaynak satırı numarasını, dizin ve dosya adına erişmenize olanak tanıyan yerleşik değerler.</span><span class="sxs-lookup"><span data-stu-id="865ca-104">The identifiers `__LINE__`, `__SOURCE_DIRECTORY__` and `__SOURCE_FILE__` are built-in values that enable you to access the source line number, directory and file name in your code.</span></span>

## <a name="syntax"></a><span data-ttu-id="865ca-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="865ca-105">Syntax</span></span>

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a><span data-ttu-id="865ca-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="865ca-106">Remarks</span></span>

<span data-ttu-id="865ca-107">Bu değerlerin her birini türünde `string`.</span><span class="sxs-lookup"><span data-stu-id="865ca-107">Each of these values has type `string`.</span></span>

<span data-ttu-id="865ca-108">Kullanılabilir kaynak satırı, dosya ve yol tanımlayıcıları aşağıdaki tabloda özetlenmiştir F#.</span><span class="sxs-lookup"><span data-stu-id="865ca-108">The following table summarizes the source line, file, and path identifiers that are available in F#.</span></span> <span data-ttu-id="865ca-109">Bu tanımlayıcılar Önişlemci makroları değildir; Bunlar, derleyici tarafından tanınan yerleşik değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="865ca-109">These identifiers are not preprocessor macros; they are built-in values that are recognized by the compiler.</span></span>

|<span data-ttu-id="865ca-110">Önceden tanımlanmış tanımlayıcısı</span><span class="sxs-lookup"><span data-stu-id="865ca-110">Predefined identifier</span></span>|<span data-ttu-id="865ca-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="865ca-111">Description</span></span>|
|---------------------|-----------|
|`__LINE__`|<span data-ttu-id="865ca-112">Geçerli satır numarası değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="865ca-112">Evaluates to the current line number, considering `#line` directives.</span></span>|
|`__SOURCE_DIRECTORY__`|<span data-ttu-id="865ca-113">Kaynak dizin geçerli tam yoluna değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="865ca-113">Evaluates to the current full path of the source directory, considering `#line` directives.</span></span>|
|`__SOURCE_FILE__`|<span data-ttu-id="865ca-114">Geçerli kaynak dosya adını ve yolunu da değerlendirir dikkate `#line` yönergeleri.</span><span class="sxs-lookup"><span data-stu-id="865ca-114">Evaluates to the current source file name and its path, considering `#line` directives.</span></span>|

<span data-ttu-id="865ca-115">Hakkında daha fazla bilgi için `#line` yönergesine bakın [derleyici yönergeleri](compiler-directives.md).</span><span class="sxs-lookup"><span data-stu-id="865ca-115">For more information about the `#line` directive, see [Compiler Directives](compiler-directives.md).</span></span>

## <a name="example"></a><span data-ttu-id="865ca-116">Örnek</span><span class="sxs-lookup"><span data-stu-id="865ca-116">Example</span></span>

<span data-ttu-id="865ca-117">Aşağıdaki kod örneği, bu değerlerin kullanımını gösterir.</span><span class="sxs-lookup"><span data-stu-id="865ca-117">The following code example demonstrates the use of these values.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

<span data-ttu-id="865ca-118">Çıktı:</span><span class="sxs-lookup"><span data-stu-id="865ca-118">Output:</span></span>

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a><span data-ttu-id="865ca-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="865ca-119">See also</span></span>

- [<span data-ttu-id="865ca-120">Derleyici Yönergeleri</span><span class="sxs-lookup"><span data-stu-id="865ca-120">Compiler Directives</span></span>](compiler-directives.md)
- [<span data-ttu-id="865ca-121">F# Dili Başvurusu</span><span class="sxs-lookup"><span data-stu-id="865ca-121">F# Language Reference</span></span>](index.md)
