---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "70259818"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirmesindeki değişiklikler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, çalışma zamanının yolları normalleştirme şekli değişti. Bir yolu normalleştirmek, hedef işletim sistemindegeçerli bir yola uyacak şekilde bir yolu veya dosyayı tanımlayan dizeyi değiştirmeyi içerir. Normalleştirme genellikle içerir:<ul><li>Bileşen ve dizin ayırıcıları canonicalizing.</li><li>Geçerli dizini göreli bir yola uygulama.</li><li>Bir yolda göreli dizini (.) veya üst dizinin (..) değerlendirilmesi.</li><li>Belirtilen karakterleri kırpma.</li></ul>.NET Framework 4.6.2'yi hedefleyen uygulamalardan başlayarak, yol normalleştirmesinde aşağıdaki değişiklikler varsayılan olarak etkinleştirilir:<ul><li>Çalışma süresi, yolları normalleştirmek için işletim sisteminin [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.</li><li>Normalleştirme artık dizin kesimlerinin sonunda (dizin adının sonundaki boşluk gibi) kırpmayı içermez.</li><li>Aygıt yolu sözdizimini tam `\\.\` güven içinde ve mscorlib.dll'deki `\\?\`dosya G/Ç API'leri için destek.</li><li>Çalışma zamanı aygıt sözdizimi yollarını doğrulamaz.</li><li>Alternatif veri akışlarına erişmek için aygıt sözdizimi kullanımı desteklenir.</li></ul>Bu değişiklikler, yöntemlerin önceden erişilemeyen yollara erişmesine izin verirken performansı artırır. .NET Framework 4.6.1 ve önceki sürümleri hedefleyen ancak .NET Framework 4.6.2 veya daha sonra ları altında çalışan uygulamalar bu değişiklikten etkilenmez.|
|Öneri|.NET Framework 4.6.2 veya daha sonrasını hedefleyen uygulamalar bu değişikliği devre dışı bırakıp <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyasının bölümüne aşağıdakileri ekleyerek eski normalleştirmeyi kullanabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.6.1 veya daha öncesini hedefleyen ancak .NET Framework 4.6.2 veya sonraki bölümlerinde çalışan uygulamalar, <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının bölümüne aşağıdaki satırı ekleyerek normale döndürme yolunun değiştirilmesine olanak sağlayabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
