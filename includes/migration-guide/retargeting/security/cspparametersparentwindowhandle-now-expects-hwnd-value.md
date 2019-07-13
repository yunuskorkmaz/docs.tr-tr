---
ms.openlocfilehash: 06a21b664ea0981663219a697fbc1bfc9be50287
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859119"
---
### <a name="cspparametersparentwindowhandle-now-expects-hwnd-value"></a>CspParameters.ParentWindowHandle artık HWND değeri bekliyor

|   |   |
|---|---|
|Ayrıntılar|<xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> Değeri, .NET Framework 2.0 sürümünde sunulan herhangi bir UI anahtara erişmek için gerekli olduğunu bir üst pencere tanıtıcısı değer kaydetmek bir uygulama sağlar (gibi bir PIN istemi veya iletişim kutusu onayı) kalıcı alt öğesi olarak belirtilen pencere açar. .NET Framework 4.7 hedefleyen uygulamaları ile başlayarak, bir Windows Forms uygulaması ayarlayabilirsiniz <xref:System.Security.Cryptography.CspParameters.ParentWindowHandle> özelliğini aşağıdaki gibi kod ile:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Önceki .NET Framework sürümlerinde değeri olması bekleniyordu bir <xref:System.IntPtr?displayProperty=name> bellekte bir konumu temsil eden burada [HWND](https://docs.microsoft.com/windows/desktop/WinProg/windows-data-types#HWND) belgeler değeri. Özelliği, forma ayarlanıyor. Windows 7'de işlemek ve önceki sürümleri olan etkisi, ancak Windows 8 ve sonraki sürümlerinde, sonuçları bir &quot; <xref:System.Security.Cryptography.CryptographicException?displayProperty=name>: Parametresi geçersiz.&quot;|
|Öneri|.NET Framework 4.7 targeting veya üst pencere ilişkisi kaydettirmek daha yüksek isteyen uygulamalar, basit form kullanımı önerilir:<pre><code class="lang-csharp">cspParameters.ParentWindowHandle = form.Handle;&#13;&#10;</code></pre>Geçirmek için doğru değeri, değerin tutulan bir bellek konumunun adresini olduğunu tanımlanmış kullanıcılar <code>form.Handle</code> dışında davranış değişikliği AppContext anahtarı ayarlayarak iyileştirilmiş <code>Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle</code> için <code>true</code>:<ol><li>Programlı olarak ayarlayarak compat AppContext üzerinde açıklandığı gibi geçer [burada](https://devblogs.microsoft.com/dotnet/net-announcements-at-build-2015/#dotnet46).</li><li>Aşağıdaki satırı ekleyerek <code>&lt;runtime&gt;</code> app.config dosyasının:</li></ol><pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Security.Cryptography.DoNotAddrOfCspParentWindowHandle=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>Uygulama yük altında daha eski .NET Framework sürümlerini AppContext ayarlayabilirsiniz, .NET Framework 4.7 çalışma zamanı üzerinde yeni davranış kabul etmek isteyen kullanıcılar buna karşılık, geçiş <code>false</code>.|
|`Scope`|Küçük|
|Version|4.7|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Security.Cryptography.CspParameters.ParentWindowHandle?displayProperty=nameWithType></li></ul>|

