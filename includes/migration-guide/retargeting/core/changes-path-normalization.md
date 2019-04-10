---
ms.openlocfilehash: d57cd5a9d41a7d2d93f03216d534f14831bcefe0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59234986"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirme değişiklikleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, çalışma zamanı yolu normalleştirir şekilde değişti. Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir. Normalleştirme genellikle içerir:<ul><li>Bileşen ve dizin ayırıcı standart hale getirme.</li><li>Geçerli dizine göreli bir yol uygulanıyor.</li><li>Göreli dizini (.) veya üst dizin (.) bir yolda değerlendiriliyor.</li><li>Karakterleri kırpma belirtilmiş.</li></ul>.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, aşağıdaki değişiklikleri yolu normalleştirme varsayılan olarak etkindir:<ul><li>İşletim sistemi için çalışma zamanı erteler [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamea) yolları'leri normalleştirmek için işlevi.</li><li>Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.</li><li>Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere `\\.\` ve dosya g/ç API'leri mscorlib.dll için `\\?\`.</li><li>Çalışma zamanı, cihaz sözdizimi yolları doğrulamaz.</li><li>Alternatif veri akışları erişmek için cihaz sözdizimi desteklenmiyor.</li></ul>Bu değişiklikler, daha önce erişilemeyen yolları erişmek yöntemleri sağlarken performansını. .NET Framework 4.6.1 ve önceki sürümleri hedefleyen, ancak .NET Framework 4.6.2 altında çalışan ya da üzeri olan uygulamalar, bu değişiklikten etkilenmez.|
|Öneri|Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.6.2'yi hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski normalleştirme kullanın <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.6.1 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.6.2 üzerinde çalışıyor veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
