---
ms.openlocfilehash: 0036fc2b03dde64d24d883e55b9f00c931f0c218
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70997735"
---
### <a name="net-interop-will-now-queryinterface-for-iagileobject-a-winrt-interface"></a>.NET Interop şimdi IAgileObject (winrt arabirimi) için QueryInterface olacak

|   |   |
|---|---|
|Ayrıntılar|.NET temsilcisi olan bir WinRT olayı kullanırken, Windows IAgileObject için .NET Framework 4.8 ile başlayan QI olacaktır.  .NET Framework'ün önceki sürümlerinde, çalışma zamanı QI'de başarısız olur ve olay abone olamayacaktı.<ul><li>[ x ] Tuhaf</li></ul>|
|Öneri|IAgileObject için QI'yi etkinleştirmek yürütmeyi devre dışı bırakırsa, aşağıdaki yapılandırmayı ayarlayarak bu kodu devre dışı kullanabilirsiniz. <h4>Yöntem 1: Çevre değişkeni</h4> Aşağıdaki ortam değişkenini ayarlayın:COMPLUS_DisableCCWSupportIAgileObject=1Bu yöntem, bu ortam değişkenini devralan tüm ortamı etkiler. Bu sadece tek bir konsol oturumu olabilir veya ortam değişkenini genel olarak ayarlarsanız tüm makineyi etkileyebilir. Ortam değişkenadı büyük/küçük harf duyarlı değildir. <h4>Yöntem 2: Kayıt Defteri</h4> Kayıt Defteri Düzenleyicisi 'ni (regedit.exe) kullanarak aşağıdaki alt tuşlardan birini bulun:HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.NETFramework HKEY_CURRENT_USER\SOFTWARE\Microsoft.NETFrameworkThen aşağıdakileri ekleyin:Değer adı: DisableCCWSupportIAgileObject Tür: DWORD (32 bit) Değer (REG_WORD olarak da adlandırılır) Değer: 1Windows REG'i kullanabilirsiniz. EXE aracı bir komut satırı veya komut dosyası ortamından bu değeri eklemek için. Örnek:<pre><code class="lang-console">reg add HKLM\SOFTWARE\Microsoft\.NETFramework /v DisableCCWSupportIAgileObject /t REG_DWORD /d 1&#13;&#10;</code></pre>Bu durumda, <code>HKLM</code> <code>HKEY_LOCAL_MACHINE</code>yerine kullanılır. Bu <code>reg add /?</code> sözdiziminde yardım görmek için kullanın. Kayıt defteri değeri adı büyük/küçük harf duyarlı değildir.|
|Kapsam|Edge|
|Sürüm|4.8|
|Tür|Çalışma Zamanı|
