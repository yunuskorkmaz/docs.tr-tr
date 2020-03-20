---
ms.openlocfilehash: 72f907c117748fb19ca0663f24445a8c978afd32
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235506"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle şimdi HWND değeri bekliyor

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 2.0'da tanıtılan <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> değer, bir uygulamanın anahtara erişmek için gereken kullanıcı bir kullanıcı ui'sinin (PIN istemi veya onay iletişim kutusu gibi) belirtilen pencereye modal bir alt öğe olarak açılabilmesi için bir ana pencere tutamacı değeri kaydetmesine olanak tanır. .NET Framework 4.7'yi hedefleyen uygulamalardan başlayarak, <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> Windows Forms uygulaması özelliği aşağıdaki gibi kodla ayarlayabilir:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>.NET Framework'ün önceki sürümlerinde, değerin <xref:System.IntPtr?displayProperty=name> [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) değerinin bulunduğu bellekteki bir konumu temsil etmesi bekleniyordu. Özelliği forma ayarı. Windows 7 ve önceki sürümlerinde tanıtıcı hiçbir etkisi yoktu, ancak &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>Windows 8 ve sonraki sürümlerinde, bir sonuçlanır : Parametre yanlıştır.&quot;|
|Öneri|.NET Framework 4.7 veya daha yüksek bir üst pencere ilişkisini kaydetmek isteyen uygulamaları basitleştirilmiş formu kullanmaya teşvik edilir:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Geçmek için doğru değerin, değeri <code>form.Handle</code> tutan bir bellek konumunun adresi olduğunu tespit eden kullanıcılar, AppContext <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> <code>true</code>anahtarını ayarlayarak davranış değişikliğini devre dışı bırakabilirsiniz:<ol><li>[Burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46)açıklandığı gibi, AppContext üzerinde compat anahtarları programlı olarak ayarlayarak .</li><li>app.config dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Tam tersine, .NET Framework 4.7 çalışma saatindeki yeni davranışı tercih etmek isteyen kullanıcılar, uygulama eski .NET Framework <code>false</code>sürümleri altında yüklendiğinde AppContext anahtarını .|
|Kapsam|İkincil|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|
