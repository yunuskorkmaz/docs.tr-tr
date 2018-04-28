---
title: Özel Durum İşleme (F#)
description: "Özel durum işleme F #'de temel bilgileri öğrenmek ve özel durum işleme deyimleri ve işlevleri bağlantılarını bulabilirsiniz."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 37b33f9387956ee462ff4977dd4ba34a82e89ec6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2018
---
# <a name="exception-handling"></a><span data-ttu-id="fe72d-103">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="fe72d-103">Exception Handling</span></span>

<span data-ttu-id="fe72d-104">Bu bölüm, özel durum işleme F # dili desteği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="fe72d-104">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="fe72d-105">Özel durum işleme temelleri</span><span class="sxs-lookup"><span data-stu-id="fe72d-105">Exception Handling Basics</span></span>
<span data-ttu-id="fe72d-106">Özel durum işleme, .NET Framework'teki hata koşullarını işleme, standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="fe72d-106">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="fe72d-107">Bu nedenle, herhangi bir .NET dil F # dahil olmak üzere, bu mekanizma desteklemesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="fe72d-107">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="fe72d-108">Bir *özel durum* hata ile ilgili bilgileri yalıtan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="fe72d-108">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="fe72d-109">Hatalar oluştuğunda, yükseltilmiş ve normal yürütme durakları durumlardır.</span><span class="sxs-lookup"><span data-stu-id="fe72d-109">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="fe72d-110">Bunun yerine, çalışma zamanı özel durum için uygun bir işleyici arar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-110">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="fe72d-111">Arama geçerli işlevinde başlatır ve arayanlar katmandan yığınından yukarı eşleşen bir işleyici bulunana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="fe72d-111">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="fe72d-112">İşleyici sonra yürütülür.</span><span class="sxs-lookup"><span data-stu-id="fe72d-112">Then the handler is executed.</span></span>

<span data-ttu-id="fe72d-113">Ayrıca, çalışma zamanı herhangi kodu çalıştırır yığın unwound olduğu gibi `finally` nesneleri doğru unwinding işlemi sırasında temizlendiğinden emin güvence altına almak için blokları.</span><span class="sxs-lookup"><span data-stu-id="fe72d-113">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="fe72d-114">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="fe72d-114">Related Topics</span></span>

|<span data-ttu-id="fe72d-115">Başlık</span><span class="sxs-lookup"><span data-stu-id="fe72d-115">Title</span></span>|<span data-ttu-id="fe72d-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fe72d-116">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="fe72d-117">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="fe72d-117">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="fe72d-118">Bir özel durum türünü bildirmesine açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-118">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="fe72d-119">Özel durumlar: `try...with` ifade</span><span class="sxs-lookup"><span data-stu-id="fe72d-119">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="fe72d-120">Özel durum işleme destekleyen dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-120">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="fe72d-121">Özel durumlar: `try...finally` ifade</span><span class="sxs-lookup"><span data-stu-id="fe72d-121">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="fe72d-122">Bir özel durum yakalandığında yığın unwinds temizleyin kod yürütmek üzere sağlar dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-122">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="fe72d-123">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="fe72d-123">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="fe72d-124">Bir özel durum nesnesi oluşturmak açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-124">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="fe72d-125">Özel durumlar: `failwith` işlevi</span><span class="sxs-lookup"><span data-stu-id="fe72d-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="fe72d-126">Genel bir F # özel durum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-126">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="fe72d-127">Özel durumlar: `invalidArg` işlevi</span><span class="sxs-lookup"><span data-stu-id="fe72d-127">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="fe72d-128">Geçersiz bağımsız değişken özel durum oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="fe72d-128">Describes how to generate an invalid argument exception.</span></span>|
