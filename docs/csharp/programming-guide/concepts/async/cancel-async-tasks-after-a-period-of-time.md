---
title: Zaman uyumsuz görevleri bir süre sonra iptal etme (C#) "
description: Bir süre içinde tamamlanmamış olan ilişkili görevlerin iptalinin nasıl planlanalınacağını öğrenin.
ms.date: 02/03/2021
ms.topic: tutorial
ms.assetid: 194282c2-399f-46da-a7a6-96674e00b0b3
ms.openlocfilehash: 98c42a2df6153d668b99b6dec49ffe380293b205
ms.sourcegitcommit: 65af0f0ad316858882845391d60ef7e303b756e8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/05/2021
ms.locfileid: "99585383"
---
# <a name="cancel-async-tasks-after-a-period-of-time-c"></a>Zaman uyumsuz görevleri bir süre sonra iptal etme (C#)

İşlemin bitmesini beklemek istemiyorsanız yöntemini kullanarak bir süre sonra zaman uyumsuz bir işlemi iptal edebilirsiniz <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=nameWithType> . Bu yöntem, ifadesi tarafından belirlenen süre içinde tamamlanmamış olan ilişkili görevlerin iptalini zamanlar `CancelAfter` .

Bu örnek, Web sitelerinin bir listesini indirmek ve her birinin içindekilerin uzunluğunu göstermek için [bir görev listesini Iptal etme (C#)](cancel-an-async-task-or-a-list-of-tasks.md) ' de geliştirilen koda ekler.

Bu öğreticinin içindekiler:

> [!div class="checklist"]
>
> - Mevcut bir .NET konsol uygulamasını güncelleştirme
> - İptal zamanlaması

## <a name="prerequisites"></a>Önkoşullar

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
    finally
    {
        s_cts.Dispose();
    }

    Console.WriteLine("Application ending.");
}
```

Updated `Main` yöntemi konsola birkaç eğitici ileti yazar. [Try catch](../../../language-reference/keywords/try-catch.md)içinde, <xref:System.Threading.CancellationTokenSource.CancelAfter(System.Int32)?displayProperty=nameWithType> bir iptal zamanlaması için bir çağrı. Bu, bir süre sonra iptali işaret eder.

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
