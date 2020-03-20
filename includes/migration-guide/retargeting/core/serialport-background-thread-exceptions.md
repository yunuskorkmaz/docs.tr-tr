---
ms.openlocfilehash: 81b104d8e5a9ccc8e790c3b16e4837cfa0c0def5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "67859023"
---
### <a name="serialport-background-thread-exceptions"></a>SerialPort arka plan iş parçacığı özel durumları

|   |   |
|---|---|
|Ayrıntılar|Akışlarla <xref:System.IO.Ports.SerialPort> oluşturulan arka plan iş parçacıkları, işletim sistemi özel durumları atıldığında işlemi artık sonlandırmaz. <br/>.NET Framework 4.7 ve önceki sürümleri hedefleyen uygulamalarda, <xref:System.IO.Ports.SerialPort> bir akışla oluşturulan bir arka plan iş parçacığına bir işletim sistemi özel durumu atıldığında bir işlem sonlandırılır. <br/>.NET Framework 4.7.1 veya daha sonraki bir sürümü hedefleyen uygulamalarda, arka plan iş parçacıkları etkin seri bağlantı noktasıyla ilgili işletim sistemi olaylarını bekler ve seri bağlantı noktasının ani olarak kaldırılması gibi bazı durumlarda çökebilir.|
|Öneri|.NET Framework 4.7.1'i hedefleyen uygulamalar için, dosyanızın <code>&lt;runtime&gt;</code> <code>app.config</code> bölümüne aşağıdakileri ekleyerek istenmeyen durumlar sayılsa bile özel durum işlemeyi devre dışı kullanabilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework'ün önceki sürümlerini hedefleyen ancak .NET Framework 4.7.1 veya sonraki sürümlerde çalışan uygulamalar için, <code>&lt;runtime&gt;</code> dosyanızın <code>app.config</code> bölümüne aşağıdakileri ekleyerek özel durum işlemeyi tercih edebilirsiniz:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.Ports.DoNotCatchSerialStreamThreadExceptions=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.7.1|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.IO.Ports.SerialPort?displayProperty=nameWithType></li></ul>|
