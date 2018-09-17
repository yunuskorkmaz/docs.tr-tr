---
title: Girdi Noktası (F#)
description: 'Yürütme resmi olarak başladığı bir yürütülebilir dosyası olarak derlenmiş bir F # programına giriş noktası kurmayı öğrenin.'
ms.date: 05/16/2016
ms.openlocfilehash: 298500931d49c891a7a243295333df3a9f5d413e
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45675944"
---
# <a name="entry-point"></a><span data-ttu-id="6e44c-103">Girdi Noktası</span><span class="sxs-lookup"><span data-stu-id="6e44c-103">Entry Point</span></span>

<span data-ttu-id="6e44c-104">Bu konuda, bir F # programına giriş noktası ayarlamak için kullandığınız yöntemin açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e44c-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="6e44c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e44c-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="6e44c-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e44c-106">Remarks</span></span>

<span data-ttu-id="6e44c-107">Önceki sözdiziminde, *let işlevi bağlaması* içinde bir işlev tanımı bir `let` bağlama.</span><span class="sxs-lookup"><span data-stu-id="6e44c-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="6e44c-108">Yürütme resmi olarak başladığı bir yürütülebilir dosya olduğu gibi derlenmiş bir programın giriş noktası.</span><span class="sxs-lookup"><span data-stu-id="6e44c-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="6e44c-109">Uygulayarak bir F # uygulaması giriş noktası belirtme `EntryPoint` özniteliği programın `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="6e44c-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="6e44c-110">Bu işlev (kullanılarak oluşturulan bir `let` bağlama) son derlenen dosyayı son işlev olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6e44c-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="6e44c-111">Son derlenen son proje dosyasına veya komut satırına geçirilen dosyanın son dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="6e44c-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="6e44c-112">Giriş noktası işlevini türünde `string array -> int`.</span><span class="sxs-lookup"><span data-stu-id="6e44c-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="6e44c-113">Komut satırında sağlanan bağımsız değişkenler geçirilen `main` işlevi bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="6e44c-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="6e44c-114">Dizinin ilk öğesi olmayan ilk bağımsız değişken; diğer dillerde olduğu gibi yürütülebilir dosyanın adını dizide dahil edilmez.</span><span class="sxs-lookup"><span data-stu-id="6e44c-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="6e44c-115">Dönüş değeri çıkış kodu işlemi için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e44c-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="6e44c-116">Sıfır, genellikle başarılı gösterir; sıfır olmayan değerler, bir hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="6e44c-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="6e44c-117">Özel bir anlamı sıfır dönüş kodları için hiçbir kural yoktur; dönüş kodları anlamı, uygulamaya özgü olur.</span><span class="sxs-lookup"><span data-stu-id="6e44c-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="6e44c-118">Aşağıdaki örnekte basit bir `main` işlevi.</span><span class="sxs-lookup"><span data-stu-id="6e44c-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="6e44c-119">Ne zaman bu kod yürütüldüğünde komut satırından `EntryPoint.exe 1 2 3`, çıktı aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="6e44c-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="6e44c-120">Örtük giriş noktası</span><span class="sxs-lookup"><span data-stu-id="6e44c-120">Implicit Entry Point</span></span>

<span data-ttu-id="6e44c-121">Bir program, Hayır olduğunda **EntryPoint** giriş noktası, derlenecek dosyanın son en üst düzey bağlamaları açıkça belirten bir özniteliği, giriş noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="6e44c-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="6e44c-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e44c-122">See also</span></span>

- [<span data-ttu-id="6e44c-123">İşlevler</span><span class="sxs-lookup"><span data-stu-id="6e44c-123">Functions</span></span>](index.md)
- [<span data-ttu-id="6e44c-124">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="6e44c-124">let Bindings</span></span>](let-bindings.md)
