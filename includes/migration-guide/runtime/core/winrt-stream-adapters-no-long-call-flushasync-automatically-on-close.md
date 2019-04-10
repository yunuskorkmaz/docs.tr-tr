---
ms.openlocfilehash: 60759e3d03137bb5983703cbf04719ba4946cb6e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235879"
---
### <a name="winrt-stream-adapters-no-long-call-flushasync-automatically-on-close"></a>WinRT stream bağdaştırıcıları en uzun FlushAsync otomatik olarak Kapat üzerinde çağrı

|   |   |
|---|---|
|Ayrıntılar|Windows Store uygulamalarında, Windows çalışma zamanı akış bağdaştırıcıları artık Dispose yönteminden FlushAsync yöntemi çağırın.|
|Öneri|Bu değişiklik, saydam olmalıdır. Geliştiriciler, şunun gibi kod yazarak önceki davranışı geri yükleyebilirsiniz:<pre><code class="lang-csharp">using (var stream = GetWindowsRuntimeStream() as Stream)&#13;&#10;{&#13;&#10;// do something&#13;&#10;await stream.FlushAsync();&#13;&#10;}&#13;&#10;</code></pre>|
|Kapsam|Geçirgen|
|Sürüm|4.5.1|
|Tür|Çalışma zamanı|
