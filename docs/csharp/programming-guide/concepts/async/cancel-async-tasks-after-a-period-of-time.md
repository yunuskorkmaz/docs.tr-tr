---
title: Zaman uyumsuz görevleri bir süre sonra iptal etme (C#) "
description: Bir süre içinde tamamlanmamış olan ilişkili görevlerin iptalinin nasıl planlanalınacağını öğrenin.
ms.date: 08/19/2020
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: ad9064f8f45a737982ffc35ab4ea2395ddae9016
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811424"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a><span data-ttu-id="5d486-103">Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="5d486-103">Cancel async tasks after a period of time (C#)</span></span>

<span data-ttu-id="5d486-104">İşlemin bitmesini beklemek istemiyorsanız yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5d486-104">You can cancel an asynchronous operation after a period of time by using the <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="5d486-105">Bu yöntem, ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar `CancelAfter` .</span><span class="sxs-lookup"><span data-stu-id="5d486-105">This method schedules the cancellation of any associated tasks that aren't complete within the period of time that's designated by the `CancelAfter` expression.</span></span>

<span data-ttu-id="5d486-106">Bu örnek, Web sitelerinin bir listesini indirmek ve her birinin içindekilerin uzunluğunu göstermek için [bir görev listesini Iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md) ' de geliştirilen koda ekler.</span><span class="sxs-lookup"><span data-stu-id="5d486-106">This example adds to the code that's developed in [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>

<span data-ttu-id="5d486-107">Bu öğreticinin içindekiler:</span><span class="sxs-lookup"><span data-stu-id="5d486-107">This tutorial covers:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5d486-108">Mevcut bir .NET konsol uygulamasını güncelleştirme</span><span class="sxs-lookup"><span data-stu-id="5d486-108">Updating an existing .NET console application</span></span>
> - <span data-ttu-id="5d486-109">İptal zamanlaması</span><span class="sxs-lookup"><span data-stu-id="5d486-109">Scheduling a cancellation</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5d486-110">Ön koşullar</span><span class="sxs-lookup"><span data-stu-id="5d486-110">Prerequisites</span></span>

<span data-ttu-id="5d486-111">Bu öğretici için aşağıdakiler gereklidir:</span><span class="sxs-lookup"><span data-stu-id="5d486-111">This tutorial requires the following:</span></span>

- <span data-ttu-id="5d486-112">[Görev listesini Iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md) öğreticisinde bir uygulama oluşturmanız bekleniyor</span><span class="sxs-lookup"><span data-stu-id="5d486-112">You're expected to have created an application in the [Cancel a list of tasks (C#)](cancel-an-async-task-or-a-list-of-tasks.md) tutorial</span></span>
- [<span data-ttu-id="5d486-113">.NET 5,0 veya sonraki bir SDK</span><span class="sxs-lookup"><span data-stu-id="5d486-113">.NET 5.0 or later SDK</span></span>](https://dotnet.microsoft.com/download/dotnet/5.0)
- <span data-ttu-id="5d486-114">Tümleşik geliştirme ortamı (IDE)</span><span class="sxs-lookup"><span data-stu-id="5d486-114">Integrated development environment (IDE)</span></span>
  - [<span data-ttu-id="5d486-115">Visual Studio, Visual Studio Code veya Mac için Visual Studio önerilir</span><span class="sxs-lookup"><span data-stu-id="5d486-115">We recommend Visual Studio, Visual Studio Code, or Visual Studio for Mac</span></span>](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a><span data-ttu-id="5d486-116">Uygulama giriş noktasını Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="5d486-116">Update application entry point</span></span>

<span data-ttu-id="5d486-117">Mevcut `Main` yöntemi aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="5d486-117">Replace the existing `Main` method with the following:</span></span>

```csharp
static async Task Main()
{
    Console.WriteLine("Application started.");

    try
    {
        s_cts.CancelAfter(3500);

        await SumPageSizesAsync();
    }
    catch (TaskCanceledException)
    {
        Console.WriteLine("\nTasks cancelled: timed out.\n");
    }

    Console.WriteLine("Application ending.");
}
```

<span data-ttu-id="5d486-118">Updated `Main` yöntemi konsola birkaç eğitici ileti yazar.</span><span class="sxs-lookup"><span data-stu-id="5d486-118">The updated `Main` method writes a few instructional messages to the console.</span></span> <span data-ttu-id="5d486-119">[Try catch](../../../language-reference/keywords/try-catch.md)içinde, bir <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> iptal zamanlaması için çağrısı yapın.</span><span class="sxs-lookup"><span data-stu-id="5d486-119">Within the [try catch](../../../language-reference/keywords/try-catch.md), a call to <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> to schedule a cancellation.</span></span> <span data-ttu-id="5d486-120">Bu, bir süre sonra iptali işaret eder.</span><span class="sxs-lookup"><span data-stu-id="5d486-120">This will signal cancellation after a period of time.</span></span>

<span data-ttu-id="5d486-121">Sonra, `SumPageSizesAsync` yöntemi beklemiş olur.</span><span class="sxs-lookup"><span data-stu-id="5d486-121">Next, the `SumPageSizesAsync` method is awaited.</span></span> <span data-ttu-id="5d486-122">Tüm URL 'Lerin işlenmesi zamanlanan iptalden daha hızlı oluşursa, uygulama sonlanır.</span><span class="sxs-lookup"><span data-stu-id="5d486-122">If processing all of the URLs occurs faster than the scheduled cancellation, the application ends.</span></span> <span data-ttu-id="5d486-123">Ancak, zamanlanan iptal, tüm URL 'Leri işlenmeden önce tetiklenirse, bir <xref:System.Threading.Tasks.TaskCanceledException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="5d486-123">However, if the scheduled cancellation is triggered before all of the URLs are processed, a <xref:System.Threading.Tasks.TaskCanceledException> is thrown.</span></span>

### <a name="example-application-output"></a><span data-ttu-id="5d486-124">Örnek uygulama çıkışı</span><span class="sxs-lookup"><span data-stu-id="5d486-124">Example application output</span></span>

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a><span data-ttu-id="5d486-125">Örnek Tamam</span><span class="sxs-lookup"><span data-stu-id="5d486-125">Complete example</span></span>

<span data-ttu-id="5d486-126">Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.</span><span class="sxs-lookup"><span data-stu-id="5d486-126">The following code is the complete text of the *Program.cs* file for the example.</span></span>

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a><span data-ttu-id="5d486-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5d486-127">See also</span></span>

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [<span data-ttu-id="5d486-128">Async ve await ile zaman uyumsuz programlama (C#)</span><span class="sxs-lookup"><span data-stu-id="5d486-128">Asynchronous programming with async and await (C#)</span></span>](index.md)
- [<span data-ttu-id="5d486-129">Görev listesini iptal etme (C#)</span><span class="sxs-lookup"><span data-stu-id="5d486-129">Cancel a list of tasks (C#)</span></span>](cancel-an-async-task-or-a-list-of-tasks.md)
