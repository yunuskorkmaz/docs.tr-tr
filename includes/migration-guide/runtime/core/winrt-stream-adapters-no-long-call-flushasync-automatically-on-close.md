---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59805323"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT stream bağdaştırıcıları en uzun FlushAsync otomatik olarak Kapat üzerinde çağrı

|   |   |
|---|---|
|Ayrıntılar|Windows Store uygulamalarında, Windows çalışma zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemi çağırın.|
|Öneri|Bu değişiklik, saydam olmalıdır. Geliştiriciler, şunun gibi kod yazarak önceki davranışı geri yükleyebilirsiniz:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
