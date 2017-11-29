---
title: "Girdi Noktası (F#)"
description: "Giriş noktası yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir F # programına öğrenin."
keywords: "Visual f #, f # işlevsel programlama"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 91455443-ff9d-4510-a7e9-1560bdcd0bb0
ms.openlocfilehash: 685fd4da67119aa5fcaaffd142a0a17c8f5dc7f6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="entry-point"></a><span data-ttu-id="dc197-104">Girdi Noktası</span><span class="sxs-lookup"><span data-stu-id="dc197-104">Entry Point</span></span>

<span data-ttu-id="dc197-105">Bu konuda bir F # programı için giriş noktası ayarlamak için kullandığınız yöntem açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc197-105">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="dc197-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc197-106">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="dc197-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc197-107">Remarks</span></span>
<span data-ttu-id="dc197-108">Önceki sözdiziminde *olanak sağlayan işlev bağlama* bir işlev tanımı bir `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="dc197-108">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="dc197-109">Yürütülebilir bir dosyanın yürütme resmi olarak başladığı olarak derlenmiş bir program için giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="dc197-109">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="dc197-110">Uygulayarak bir F # uygulama giriş noktasını belirtmek `EntryPoint` özniteliği programın `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="dc197-110">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="dc197-111">Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenmiş dosyasındaki son işlevi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc197-111">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="dc197-112">Son derlenmiş projesinde son dosya veya komut satırı geçirilen son dosya dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="dc197-112">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="dc197-113">Giriş noktası işlevi türüne sahip `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="dc197-113">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="dc197-114">Komut satırında sağlanan bağımsız değişkenler geçirilecek `main` işlevinde bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="dc197-114">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="dc197-115">Dizinin ilk öğesi ilk bağımsız değişkeni olan; diğer bazı dillerde olduğu gibi yürütülebilir dosyanın adını dizisinde dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="dc197-115">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="dc197-116">Dönüş değeri çıkış kodu işlemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc197-116">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="dc197-117">Sıfır genellikle başarılı olduğunu gösterir; sıfır olmayan değerler bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="dc197-117">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="dc197-118">Belirli bir anlamı, sıfır olmayan dönüş kodları için hiçbir kuralı yoktur; dönüş kodları anlamları uygulamaya özgü.</span><span class="sxs-lookup"><span data-stu-id="dc197-118">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="dc197-119">Aşağıdaki örnekte basit bir gösterilmektedir `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="dc197-119">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="dc197-120">Ne zaman bu kodu yürütüldüğünde komut satırıyla `EntryPoint.exe 1 2 3`, çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="dc197-120">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="dc197-121">Örtük giriş noktası</span><span class="sxs-lookup"><span data-stu-id="dc197-121">Implicit Entry Point</span></span>
<span data-ttu-id="dc197-122">Bir program yok olduğunda **EntryPoint** derlenecek son dosyanın üst düzey bağlamaları giriş noktası açıkça belirten özniteliği giriş noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dc197-122">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="dc197-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dc197-123">See Also</span></span>
[<span data-ttu-id="dc197-124">İşlevler</span><span class="sxs-lookup"><span data-stu-id="dc197-124">Functions</span></span>](index.md)

[<span data-ttu-id="dc197-125">let bağlamaları</span><span class="sxs-lookup"><span data-stu-id="dc197-125">let Bindings</span></span>](let-bindings.md)
