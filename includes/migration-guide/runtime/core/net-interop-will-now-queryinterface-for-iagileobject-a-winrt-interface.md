---
ms.openlocfilehash: 65fa5d8629ce8e426cf1623590a056e5cad0b91f
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496966"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop artık IAgileObject için QueryInterface (bir WinRT arabirimi)

#### <a name="details"></a>Ayrıntılar

.NET temsilcisiyle bir WinRT olayı kullanırken, Windows, .NET Framework 4,8 ' den başlayarak IAgileObject için QI olur.  .NET Framework önceki sürümlerinde, çalışma zamanı bu QI başarısız olur ve olay abone olunamaz.<ul><li>[x] süslenmiş</li></ul>

#### <a name="suggestion"></a>Öneri

IAgileObject sonlarının yürütülmesi için QI etkinleştirmek için aşağıdaki yapılandırmayı ayarlayarak bu kodu devre dışı bırakabilirsiniz. <h4>Yöntem 1: ortam değişkeni</h4> Şu ortam değişkenini ayarlayın: COMPLUS_DisableCCWSupportIAgileObject = 1Bu Yöntem, bu ortam değişkenini devralan ortamları etkiler. Bu yalnızca tek bir konsol oturumu olabilir veya ortam değişkenini küresel olarak ayarlarsanız makinenin tamamını etkileyebilir. Ortam değişkeni adı büyük/küçük harfe duyarlı değildir. <h4>Yöntem 2: kayıt defteri</h4> Kayıt Defteri Düzenleyicisi 'Ni (regedit.exe) kullanarak, aşağıdaki alt anahtarlardan birini bulun: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER \SOFTWARE\Microsoft.NETFrameworkThen şunu ekleyin: değer adı: Disableccwsupportıagileobject Type: DWORD (32-bit) değeri (aynı zamanda REG_WORD olarak da bilinir) değeri: 1Bu değeri bir komut satırından veya betik ortamından eklemek için Windows REG.EXE aracını kullanabilirsiniz. Örneğin:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Bu durumda, <code>HKLM</code> yerine kullanılır <code>HKEY_LOCAL_MACHINE</code> . <code>reg add /?</code>Bu söz dizimi hakkındaki Yardımı görmek için kullanın. Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.

| Name    | Değer       |
|:--------|:------------|
| Kapsam   |Edge|
|Sürüm|4,8|
|Tür|Çalışma Zamanı|

#### <a name="affected-apis"></a>Etkilenen API’ler

API analizi aracılığıyla algılanamaz.

<!--

#### Affected APIs

Not detectable via API analysis.

-->
