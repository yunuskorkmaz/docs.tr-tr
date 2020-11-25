---
title: 'Son değişiklik: CA2247: TaskCompletionSource oluşturucusuna bağımsız değişken TaskCreationOptions değeri olmalıdır'
description: Kod Analizi kuralı CA2247 'nin etkinleştirilmesi nedeniyle .NET 5,0 'deki Son değişiklik hakkında bilgi edinin.
ms.date: 09/03/2020
ms.openlocfilehash: 323fd5a05da4dfeb68ef75d88d5d293ba01c8ade
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761534"
---
# <a name="warning-ca2247-argument-to-taskcompletionsource-constructor-should-be-taskcreationoptions-value"></a>Uyarı CA2247: TaskCompletionSource oluşturucusunun bağımsız değişkeni TaskCreationOptions değeri olmalıdır

.Net Code Analyzer Rule [CA2247](/visualstudio/code-quality/ca2247) , varsayılan olarak .NET 5,0 ' den başlayarak etkindir. <xref:System.Threading.Tasks.TaskCompletionSource%601>Türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrılar için bir derleme uyarısı oluşturur <xref:System.Threading.Tasks.TaskContinuationOptions> .

## <a name="change-description"></a>Açıklamayı Değiştir

.NET SDK, .NET 5,0 'den başlayarak [.net kaynak kodu Çözümleyicileri](../../../../fundamentals/code-analysis/overview.md)içerir. Bu kuralların bazıları varsayılan olarak [CA2247](/visualstudio/code-quality/ca2247)dahil olmak üzere etkindir. Projeniz bu kuralı ihlal eden ve uyarıları hata olarak işleyecek şekilde yapılandırılan kodu içeriyorsa, bu değişiklik yapınızı bozabilir.

Rule CA2247, <xref:System.Threading.Tasks.TaskCompletionSource%601> türünde bir bağımsız değişken geçiren oluşturucuya yapılan çağrıları bulur <xref:System.Threading.Tasks.TaskContinuationOptions> . <xref:System.Threading.Tasks.TaskCompletionSource%601>Türün bir değeri kabul eden bir oluşturucusu <xref:System.Threading.Tasks.TaskCreationOptions> ve öğesini kabul eden başka bir Oluşturucu vardır <xref:System.Object> . Yanlışlıkla bir değer yerine bir <xref:System.Threading.Tasks.TaskContinuationOptions> değer geçirirseniz <xref:System.Threading.Tasks.TaskCreationOptions> , parametresine sahip Oluşturucu <xref:System.Object> çalışma zamanında çağırılır. Kodunuz derleyip çalıştırılır, ancak amaçlanan davranışa sahip olmayacaktır.

## <a name="version-introduced"></a>Sunulan sürüm

5.0

## <a name="recommended-action"></a>Önerilen eylem

- <xref:System.Threading.Tasks.TaskContinuationOptions>Bağımsız değişkenini karşılık gelen değerle değiştirin <xref:System.Threading.Tasks.TaskCreationOptions> . Kodunuzda bir hatayı neredeyse her zaman vurgudığından, bu uyarıyı göstermez. Daha fazla bilgi için bkz. [CA2247](/visualstudio/code-quality/ca2247).

- Kod analizini tamamen devre dışı bırakmak için `EnableNETAnalyzers` , `false` proje dosyanızda olarak ayarlayın. Daha fazla bilgi için bkz. [Enablenetçözümleyiciler](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Threading.Tasks.TaskCompletionSource%601.%23ctor(System.Object)>

<!--

### Affected APIs

- ``M:System.Threading.Tasks.TaskCompletionSource`1.#ctor(System.Object)``

### Category

Code analysis

-->
