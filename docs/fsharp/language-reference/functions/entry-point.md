---
title: Girdi Noktası (F#)
description: 'Giriş noktası yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir F # programına öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 3d6cab755dd89f2d3d669a8763aa08660432a0ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563626"
---
# <a name="entry-point"></a><span data-ttu-id="2778c-103">Girdi Noktası</span><span class="sxs-lookup"><span data-stu-id="2778c-103">Entry Point</span></span>

<span data-ttu-id="2778c-104">Bu konuda bir F # programı için giriş noktası ayarlamak için kullandığınız yöntem açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2778c-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>


## <a name="syntax"></a><span data-ttu-id="2778c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2778c-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="2778c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2778c-106">Remarks</span></span>
<span data-ttu-id="2778c-107">Önceki sözdiziminde *olanak sağlayan işlev bağlama* bir işlev tanımı bir `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="2778c-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="2778c-108">Yürütülebilir bir dosyanın yürütme resmi olarak başladığı olarak derlenmiş bir program için giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="2778c-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="2778c-109">Uygulayarak bir F # uygulama giriş noktasını belirtmek `EntryPoint` özniteliği programın `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="2778c-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="2778c-110">Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenmiş dosyasındaki son işlevi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="2778c-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="2778c-111">Son derlenmiş projesinde son dosya veya komut satırı geçirilen son dosya dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="2778c-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="2778c-112">Giriş noktası işlevi türüne sahip `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="2778c-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="2778c-113">Komut satırında sağlanan bağımsız değişkenler geçirilecek `main` işlevinde bir dizeler dizisi.</span><span class="sxs-lookup"><span data-stu-id="2778c-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="2778c-114">Dizinin ilk öğesi ilk bağımsız değişkeni olan; diğer bazı dillerde olduğu gibi yürütülebilir dosyanın adını dizisinde dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="2778c-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="2778c-115">Dönüş değeri çıkış kodu işlemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2778c-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="2778c-116">Sıfır genellikle başarılı olduğunu gösterir; sıfır olmayan değerler bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="2778c-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="2778c-117">Belirli bir anlamı, sıfır olmayan dönüş kodları için hiçbir kuralı yoktur; dönüş kodları anlamları uygulamaya özgü.</span><span class="sxs-lookup"><span data-stu-id="2778c-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="2778c-118">Aşağıdaki örnekte basit bir gösterilmektedir `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="2778c-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="2778c-119">Ne zaman bu kodu yürütüldüğünde komut satırıyla `EntryPoint.exe 1 2 3`, çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2778c-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="2778c-120">Örtük giriş noktası</span><span class="sxs-lookup"><span data-stu-id="2778c-120">Implicit Entry Point</span></span>
<span data-ttu-id="2778c-121">Bir program yok olduğunda **EntryPoint** derlenecek son dosyanın üst düzey bağlamaları giriş noktası açıkça belirten özniteliği giriş noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2778c-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>


## <a name="see-also"></a><span data-ttu-id="2778c-122">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2778c-122">See Also</span></span>
[<span data-ttu-id="2778c-123">İşlevler</span><span class="sxs-lookup"><span data-stu-id="2778c-123">Functions</span></span>](index.md)

[<span data-ttu-id="2778c-124">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="2778c-124">let Bindings</span></span>](let-bindings.md)
