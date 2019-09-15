---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70997735"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop artık IAgileObject için QueryInterface (bir WinRT arabirimi)

|   |   |
|---|---|
|Ayrıntılar|.NET temsilcisiyle bir WinRT olayı kullanırken, Windows, .NET Framework 4,8 ' den başlayarak IAgileObject için QI olur.  .NET Framework önceki sürümlerinde, çalışma zamanı bu QI başarısız olur ve olay abone olunamaz.<ul><li>[x] süslenmiş</li></ul>|
|Öneri|IAgileObject sonlarının yürütülmesi için QI etkinleştirmek için aşağıdaki yapılandırmayı ayarlayarak bu kodu devre dışı bırakabilirsiniz. <h4>Yöntem 1: Ortam değişkeni</h4> Şu ortam değişkenini ayarlayın: COMPLUS_DisableCCWSupportIAgileObject = 1Bu Yöntem, bu ortam değişkenini devralan ortamları etkiler. Bu yalnızca tek bir konsol oturumu olabilir veya ortam değişkenini küresel olarak ayarlarsanız makinenin tamamını etkileyebilir. Ortam değişkeni adı büyük/küçük harfe duyarlı değildir. <h4>Yöntem 2: Kayıt defteri</h4> Kayıt Defteri Düzenleyicisi 'Ni (Regedit. exe) kullanarak, şu alt anahtarlardan birini bulun: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen şunları ekleyin: değer adı: Disableccwsupportıagileobject türü: DWORD (32-bit) değeri (REG_WORD olarak da bilinir) değeri: 1Windows REG 'i kullanabilirsiniz. Bu değeri bir komut satırından veya betik ortamından eklemek için EXE aracı. Örneğin:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Bu durumda, <code>HKLM</code> <code>HKEY_LOCAL_MACHINE</code>yerine kullanılır. Bu <code>reg add /?</code> söz dizimi hakkındaki Yardımı görmek için kullanın. Kayıt defteri değer adı büyük/küçük harfe duyarlı değildir.|
|Kapsam|Kenar|
|Sürüm|4.8|
|Tür|Çalışma zamanı|
