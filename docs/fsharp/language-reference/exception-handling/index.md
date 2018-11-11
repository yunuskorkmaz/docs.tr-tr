---
title: Özel Durum İşleme (F#)
description: Özel durum olarak işlemeyi temel bilgileri öğrenmek F# ve özel durum ifadeler ve İşlevler işleme bağlantılarını bulabilirsiniz.
ms.date: 05/16/2016
ms.openlocfilehash: fc89feb0d21bc823cb105e435413f8309cd6174c
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2018
ms.locfileid: "33564332"
---
# <a name="exception-handling"></a><span data-ttu-id="067d5-103">Özel Durum İşleme</span><span class="sxs-lookup"><span data-stu-id="067d5-103">Exception Handling</span></span>

<span data-ttu-id="067d5-104">Bu bölümde, özel durum işleme desteği hakkında bilgi içeren F# dili.</span><span class="sxs-lookup"><span data-stu-id="067d5-104">This section contains information about exception handling support in the F# language.</span></span>


## <a name="exception-handling-basics"></a><span data-ttu-id="067d5-105">Özel durum işleme temelleri</span><span class="sxs-lookup"><span data-stu-id="067d5-105">Exception Handling Basics</span></span>
<span data-ttu-id="067d5-106">Özel durum işleme, .NET Framework'teki hata koşullarını işleme, standart bir yoludur.</span><span class="sxs-lookup"><span data-stu-id="067d5-106">Exception handling is the standard way of handling error conditions in the .NET Framework.</span></span> <span data-ttu-id="067d5-107">Bu nedenle, herhangi bir .NET dil Bu mekanizma desteklemelidir dahil olmak üzere F#.</span><span class="sxs-lookup"><span data-stu-id="067d5-107">Thus, any .NET language must support this mechanism, including F#.</span></span> <span data-ttu-id="067d5-108">Bir *özel durum* hatayla ilgili bilgileri yalıtan bir nesne.</span><span class="sxs-lookup"><span data-stu-id="067d5-108">An *exception* is an object that encapsulates information about an error.</span></span> <span data-ttu-id="067d5-109">Hatalar oluştuğunda durumlardır yükseltilmiş ve normal yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="067d5-109">When errors occur, exceptions are raised and regular execution stops.</span></span> <span data-ttu-id="067d5-110">Bunun yerine, çalışma zamanı özel durum için uygun tanıtıcının arar.</span><span class="sxs-lookup"><span data-stu-id="067d5-110">Instead, the runtime searches for an appropriate handler for the exception.</span></span> <span data-ttu-id="067d5-111">Arama geçerli işlevde başlar ve yığınına çağıranlar katmanları ile eşleşen bir işleyici bulunana kadar devam eder.</span><span class="sxs-lookup"><span data-stu-id="067d5-111">The search starts in the current function, and proceeds up the stack through the layers of callers until a matching handler is found.</span></span> <span data-ttu-id="067d5-112">İşleyicisi yürütülür.</span><span class="sxs-lookup"><span data-stu-id="067d5-112">Then the handler is executed.</span></span>

<span data-ttu-id="067d5-113">Yığın geriye doğru izlenirken, herhangi bir kod Ayrıca, çalışma zamanının yürüttüğü `finally` blokları, nesnelerin doğru geriye doğru işlem sırasında temizlenmesini garanti etmek için.</span><span class="sxs-lookup"><span data-stu-id="067d5-113">In addition, as the stack is unwound, the runtime executes any code in `finally` blocks, to guarantee that objects are cleaned up correctly during the unwinding process.</span></span>


## <a name="related-topics"></a><span data-ttu-id="067d5-114">İlgili Konular</span><span class="sxs-lookup"><span data-stu-id="067d5-114">Related Topics</span></span>

|<span data-ttu-id="067d5-115">Başlık</span><span class="sxs-lookup"><span data-stu-id="067d5-115">Title</span></span>|<span data-ttu-id="067d5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067d5-116">Description</span></span>|
|-----|-----------|
|[<span data-ttu-id="067d5-117">Özel Durum Türleri</span><span class="sxs-lookup"><span data-stu-id="067d5-117">Exception Types</span></span>](exception-types.md)|<span data-ttu-id="067d5-118">Bir özel durum türü bildirmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="067d5-118">Describes how to declare an exception type.</span></span>|
|[<span data-ttu-id="067d5-119">Özel durumlar: `try...with` ifadesi</span><span class="sxs-lookup"><span data-stu-id="067d5-119">Exceptions: The `try...with` Expression</span></span>](the-try-with-expression.md)|<span data-ttu-id="067d5-120">Özel durum işleme destekleyen dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="067d5-120">Describes the language construct that supports exception handling.</span></span>|
|[<span data-ttu-id="067d5-121">Özel durumlar: `try...finally` ifadesi</span><span class="sxs-lookup"><span data-stu-id="067d5-121">Exceptions: The `try...finally` Expression</span></span>](the-try-finally-expression.md)|<span data-ttu-id="067d5-122">Bir özel durum oluştuğunda yığının geriye doğru izler gibi temizleme kodu yürütme olanak tanıyan dil yapısı açıklar.</span><span class="sxs-lookup"><span data-stu-id="067d5-122">Describes the language construct that enables you to execute clean-up code as the stack unwinds when an exception is thrown.</span></span>|
|[<span data-ttu-id="067d5-123">Özel durumlar: `raise` işlevi</span><span class="sxs-lookup"><span data-stu-id="067d5-123">Exceptions: the `raise` Function</span></span>](the-raise-Function.md)|<span data-ttu-id="067d5-124">Bir özel durum nesnesi oluşturmak nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="067d5-124">Describes how to throw an exception object.</span></span>|
|[<span data-ttu-id="067d5-125">Özel durumlar: `failwith` işlevi</span><span class="sxs-lookup"><span data-stu-id="067d5-125">Exceptions: The `failwith` Function</span></span>](the-failwith-function.md)|<span data-ttu-id="067d5-126">Genel oluşturmayı açıklar F# özel durum.</span><span class="sxs-lookup"><span data-stu-id="067d5-126">Describes how to generate a general F# exception.</span></span>|
|[<span data-ttu-id="067d5-127">Özel durumlar: `invalidArg` işlevi</span><span class="sxs-lookup"><span data-stu-id="067d5-127">Exceptions: The `invalidArg` Function</span></span>](the-invalidArg-function.md)|<span data-ttu-id="067d5-128">Geçersiz bağımsız değişken özel oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="067d5-128">Describes how to generate an invalid argument exception.</span></span>|
