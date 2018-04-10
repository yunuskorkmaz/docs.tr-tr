---
title: Özel Durum İşleme (F#)
description: "Özel durum işleme F #'de temel bilgileri öğrenmek ve özel durum işleme deyimleri ve işlevleri bağlantılarını bulabilirsiniz."
keywords: 'Visual f #, f # işlevsel programlama'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ad475c4a-d94e-47d9-b27b-3ff000b65f8e
ms.openlocfilehash: b61af66e0a70fdf9b86df37418c0284957d1f99e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="exception-handling"></a><span data-ttu-id="ee8a5-104">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="ee8a5-104">Exception Handling</span></span>

<span data-ttu-id="ee8a5-105">Bu bölüm, özel durum işleme F # dili desteği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-105">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="ee8a5-106">Özel durum işleme temelleri</span><span class="sxs-lookup"><span data-stu-id="ee8a5-106">Exception Handling Basics</span></span>
<span data-ttu-id="ee8a5-107">Özel durum işleme, .NET Framework'teki hata koşullarını işleme, standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-107">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="ee8a5-108">Bu nedenle, herhangi bir .NET dil F # dahil olmak üzere, bu mekanizma desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-108">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="ee8a5-109">Bir *özel durum* hata ile ilgili bilgileri yalıtan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-109">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="ee8a5-110">Hatalar oluştuğunda, yükseltilmiş ve normal yürütme durakları durumlardır.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-110">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="ee8a5-111">Bunun yerine, çalışma zamanı özel durum için uygun bir işleyici arar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-111">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="ee8a5-112">Arama geçerli işlevinde başlatır ve arayanlar katmandan yığınından yukarı eşleşen bir işleyici bulunana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-112">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="ee8a5-113">İşleyici sonra yürütülür.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-113">Then the handler is executed.</span></span>

<span data-ttu-id="ee8a5-114">Ayrıca, çalışma zamanı herhangi kodu çalıştırır yığın unwound olduğu gibi `finally` nesneleri doğru unwinding işlemi sırasında temizlendiğinden emin güvence altına almak için blokları.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-114">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="ee8a5-115">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="ee8a5-115">Related Topics</span></span>

|<span data-ttu-id="ee8a5-116">Başlık</span><span class="sxs-lookup"><span data-stu-id="ee8a5-116">Title</span></span>|<span data-ttu-id="ee8a5-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee8a5-117">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="ee8a5-118">Özel durum türleri</span><span class="sxs-lookup"><span data-stu-id="ee8a5-118">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="ee8a5-119">Bir özel durum türünü bildirmesine açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-119">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="ee8a5-120">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="ee8a5-120">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="ee8a5-121">Özel durum işleme destekleyen dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-121">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="ee8a5-122">Özel durumlar: `try...finally` ifade</span><span class="sxs-lookup"><span data-stu-id="ee8a5-122">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="ee8a5-123">Bir özel durum yakalandığında yığın unwinds temizleyin kod yürütmek üzere sağlar dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-123">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="ee8a5-124">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="ee8a5-124">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="ee8a5-125">Bir özel durum nesnesi oluşturmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-125">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="ee8a5-126">Özel durumlar: `failwith` işlevi</span><span class="sxs-lookup"><span data-stu-id="ee8a5-126">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="ee8a5-127">Genel bir F # özel durum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-127">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="ee8a5-128">Özel durumlar: `invalidArg` işlevi</span><span class="sxs-lookup"><span data-stu-id="ee8a5-128">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="ee8a5-129">Geçersiz bağımsız değişken özel durum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="ee8a5-129">Describes how to generate an invalid argument exception.</span></span>|
