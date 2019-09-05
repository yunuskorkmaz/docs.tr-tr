---
ms.openlocfilehash: 994876457f9745de99be30e567f400f69a0192fa
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70259818"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirmede değişiklikler

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, çalışma zamanının yol normalleştirme yöntemi değişti. Bir yolun normalleştirilmesi, bir yolu veya dosyayı tanımlayan dizeyi, hedef işletim sisteminde geçerli bir yola uygun olacak şekilde değiştirmeyi içerir. Normalleştirme genellikle şunları içerir:<ul><li>Standart hale getirme bileşeni ve Dizin ayırıcıları.</li><li>Geçerli dizin göreli bir yola uygulanıyor.</li><li>Göreli dizin (.) veya üst dizin (..) bir yolda değerlendiriliyor.</li><li>Belirtilen karakterler kırpılırken.</li></ul>.NET Framework 4.6.2 hedefleyen uygulamalarla başlayarak, yol normalleştirmede aşağıdaki değişiklikler varsayılan olarak etkindir:<ul><li>Çalışma zamanı, yolları normalleştirmek için işletim sisteminin [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) işlevine erteler.</li><li>Normalleştirme artık Dizin segmentlerinin bitmesini (Dizin adının sonundaki bir boşluk gibi) kırpmasını kapsar.</li><li>Mscorlib. `\\.\` `\\?\`dll içindeki dosya g/ç API 'leri için ve dahil olmak üzere tam güvende cihaz yolu söz dizimi desteği.</li><li>Çalışma zamanı, cihaz sözdizimi yollarını doğrulamaz.</li><li>Alternatif veri akışlarına erişmek için cihaz sözdiziminin kullanılması desteklenir.</li></ul>Bu değişiklikler, daha önce erişilemeyen yollara erişme yöntemlerinin kullanılmasına izin verirken performansı geliştirir. .NET Framework 4.6.1 ve önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar bu değişiklikten etkilenmez.|
|Öneri|.NET Framework 4.6.2 veya üstünü hedefleyen uygulamalar bu değişikliği devre dışı bırakabilirsiniz ve uygulama yapılandırma dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdakini ekleyerek eski normalleştirmeyi kullanabilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.6.1 veya önceki sürümlerini hedefleyen ancak .NET Framework 4.6.2 veya üzeri sürümlerde çalışan uygulamalar, uygulama. yapılandırma dosyasının <code>&lt;runtime&gt;</code> bölümüne aşağıdaki satırı ekleyerek yol normalleştirmede yapılan değişiklikleri etkinleştirebilir:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
