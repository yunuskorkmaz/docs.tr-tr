---
title: Girdi Noktası
description: Yürütme resmi 'nin başladığı çalıştırılabilir dosya olarak derlenmiş bir F# programa giriş noktası ayarlamayı öğrenin.
ms.date: 05/16/2016
ms.openlocfilehash: 5e13416131d4dfd22583439fedf51f18f7a461da
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630526"
---
# <a name="entry-point"></a><span data-ttu-id="2dfcd-103">Girdi Noktası</span><span class="sxs-lookup"><span data-stu-id="2dfcd-103">Entry Point</span></span>

<span data-ttu-id="2dfcd-104">Bu konuda, giriş noktasını bir F# programa ayarlamak için kullandığınız yöntem açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-104">This topic describes the method that you use to set the entry point to an F# program.</span></span>

## <a name="syntax"></a><span data-ttu-id="2dfcd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2dfcd-105">Syntax</span></span>

```fsharp
[<EntryPoint>]
let-function-binding
```

## <a name="remarks"></a><span data-ttu-id="2dfcd-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2dfcd-106">Remarks</span></span>

<span data-ttu-id="2dfcd-107">Önceki sözdiziminde, *Let-işlev-bağlama* bir `let` bağlamadaki bir işlevin tanımıdır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-107">In the previous syntax, *let-function-binding* is the definition of a function in a `let` binding.</span></span>

<span data-ttu-id="2dfcd-108">Yürütülebilir dosya olarak derlenen bir programa giriş noktası, yürütmenin resmi olarak başladığı yerdir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-108">The entry point to a program that is compiled as an executable file is where execution formally starts.</span></span> <span data-ttu-id="2dfcd-109">F# `EntryPoint` Programın işlevine`main` özniteliğini uygulayarak giriş noktasını bir uygulamaya belirlersiniz.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-109">You specify the entry point to an F# application by applying the `EntryPoint` attribute to the program's `main` function.</span></span> <span data-ttu-id="2dfcd-110">Bu işlev (bir `let` bağlama kullanılarak oluşturulan), son derlenmiş dosyadaki son işlev olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-110">This function (created by using a `let` binding) must be the last function in the last compiled file.</span></span> <span data-ttu-id="2dfcd-111">Son derlenen dosya, projedeki son dosya veya komut satırına geçirilen son dosyadır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-111">The last compiled file is the last file in the project or the last file that is passed to the command line.</span></span>

<span data-ttu-id="2dfcd-112">Giriş noktası işlevinde tür `string array -> int`vardır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-112">The entry point function has type `string array -> int`.</span></span> <span data-ttu-id="2dfcd-113">Komut satırında verilen bağımsız değişkenler, dizeler dizisindeki `main` işleve geçirilir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-113">The arguments provided on the command line are passed to the `main` function in the array of strings.</span></span> <span data-ttu-id="2dfcd-114">Dizinin ilk öğesi ilk bağımsız değişkendir; yürütülebilir dosyanın adı, başka dillerde olduğu gibi diziye dahil değildir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-114">The first element of the array is the first argument; the name of the executable file is not included in the array, as it is in some other languages.</span></span> <span data-ttu-id="2dfcd-115">Dönüş değeri, işlem için çıkış kodu olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-115">The return value is used as the exit code for the process.</span></span> <span data-ttu-id="2dfcd-116">Sıfır genellikle başarıyı gösterir; sıfır olmayan değerler bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-116">Zero usually indicates success; nonzero values indicate an error.</span></span> <span data-ttu-id="2dfcd-117">Sıfır olmayan dönüş kodlarının belirli anlamı için bir kural yoktur; dönüş kodlarının anlamları uygulamaya özgüdür.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-117">There is no convention for the specific meaning of nonzero return codes; the meanings of the return codes are application-specific.</span></span>

<span data-ttu-id="2dfcd-118">Aşağıdaki örnekte basit `main` bir işlev gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-118">The following example illustrates a simple `main` function.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/entry-point/snippet501.fs)]

<span data-ttu-id="2dfcd-119">Bu kod komut satırıyla `EntryPoint.exe 1 2 3`yürütüldüğünde, çıkış aşağıdaki gibidir.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-119">When this code is executed with the command line `EntryPoint.exe 1 2 3`, the output is as follows.</span></span>

```console
Arguments passed to function : [|"1"; "2"; "3"|]
```

## <a name="implicit-entry-point"></a><span data-ttu-id="2dfcd-120">Örtük giriş noktası</span><span class="sxs-lookup"><span data-stu-id="2dfcd-120">Implicit Entry Point</span></span>

<span data-ttu-id="2dfcd-121">Bir programın giriş noktasını açıkça belirten bir **entryPoint** özniteliği olmadığında, Derlenecek son dosyadaki en üst düzey bağlamalar giriş noktası olarak kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-121">When a program has no **EntryPoint** attribute that explicitly indicates the entry point, the top level bindings in the last file to be compiled are used as the entry point.</span></span>

## <a name="see-also"></a><span data-ttu-id="2dfcd-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2dfcd-122">See also</span></span>

- [<span data-ttu-id="2dfcd-123">İşlevler</span><span class="sxs-lookup"><span data-stu-id="2dfcd-123">Functions</span></span>](index.md)
- [<span data-ttu-id="2dfcd-124">let Bağlamaları</span><span class="sxs-lookup"><span data-stu-id="2dfcd-124">let Bindings</span></span>](let-bindings.md)
