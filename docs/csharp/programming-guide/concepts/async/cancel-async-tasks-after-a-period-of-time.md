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
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)

İşlemin bitmesini beklemek istemiyorsanız yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> . Bu yöntem, ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar `CancelAfter` .

Bu örnek, Web sitelerinin bir listesini indirmek ve her birinin içindekilerin uzunluğunu göstermek için [bir görev listesini Iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md) ' de geliştirilen koda ekler.

Bu öğreticinin içindekiler:

> [!div class="checklist"]
>
> - Mevcut bir .NET konsol uygulamasını güncelleştirme
> - İptal zamanlaması

## <a name="prerequisites"></a>Ön koşullar

Bu öğretici için aşağıdakiler gereklidir:

- [Görev listesini Iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md) öğreticisinde bir uygulama oluşturmanız bekleniyor
- [.NET 5,0 veya sonraki bir SDK](https://dotnet.microsoft.com/download/dotnet/5.0)
- Tümleşik geliştirme ortamı (IDE)
  - [Visual Studio, Visual Studio Code veya Mac için Visual Studio önerilir](https://visualstudio.microsoft.com)

## <a name="update-application-entry-point"></a>Uygulama giriş noktasını Güncelleştir

Mevcut `Main` yöntemi aşağıdaki kodla değiştirin:

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

Updated `Main` yöntemi konsola birkaç eğitici ileti yazar. [Try catch](../../../language-reference/keywords/try-catch.md)içinde, bir <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> iptal zamanlaması için çağrısı yapın. Bu, bir süre sonra iptali işaret eder.

Sonra, `SumPageSizesAsync` yöntemi beklemiş olur. Tüm URL 'Lerin işlenmesi zamanlanan iptalden daha hızlı oluşursa, uygulama sonlanır. Ancak, zamanlanan iptal, tüm URL 'Leri işlenmeden önce tetiklenirse, bir <xref:System.Threading.Tasks.TaskCanceledException> oluşturulur.

### <a name="example-application-output"></a>Örnek uygulama çıkışı

```console
Application started.

https://docs.microsoft.com                                       37,357
https://docs.microsoft.com/aspnet/core                           85,589
https://docs.microsoft.com/azure                                398,939
https://docs.microsoft.com/azure/devops                          73,663

Tasks cancelled: timed out.

Application ending.
```

## <a name="complete-example"></a>Örnek Tamam

Aşağıdaki kod, örnek için *program.cs* dosyasının tüm metinkodudur.

:::code language="csharp" source="snippets/cancel-tasks/cancel-task-after-period-of-time/Program.cs":::

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Threading.CancellationToken>
- <xref:System.Threading.CancellationTokenSource>
- [Async ve await ile zaman uyumsuz programlama (C#)](index.md)
- [Görev listesini iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md)
