---
ms.openlocfilehash: d5ef5da90dd3fc39febf8e4cd4955b4113343976
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235580"
---
### <a name="changes-in-path-normalization"></a>Yol normalleştirme değişiklikleri

|   |   |
|---|---|
|Ayrıntılar|.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, çalışma zamanı yolu normalleştirir şekilde değişti. Bir yol normalleştirme, böylece geçerli bir yol hedef işletim sisteminde uyan bir yol veya dosya tanımlayan dize değiştirme içerir. Normalleştirme genellikle içerir:<ul><li>Bileşen ve dizin ayırıcı standart hale getirme.</li><li>Geçerli dizine göreli bir yol uygulanıyor.</li><li>Göreli dizini (.) veya üst dizin (.) bir yolda değerlendiriliyor.</li><li>Karakterleri kırpma belirtilmiş.</li></ul>.NET Framework 4.6.2'yi hedefleyen uygulamalar ile başlayarak, aşağıdaki değişiklikleri yolu normalleştirme varsayılan olarak etkindir:<ul><li>İşletim sistemi için çalışma zamanı erteler [GetFullPathName](https://docs.microsoft.com/windows/desktop/api/fileapi/nf-fileapi-getfullpathnamew) yolları'leri normalleştirmek için işlevi.</li><li>Artık normalleştirme directory Segment (örneğin, bir dizin adı, sonunda boşluk) sonuna kırpma içerir.</li><li>Cihaz yolu sözdizimi tam güven için destek dahil olmak üzere <code>\\.\</code> and, for file I/O APIs in mscorlib.dll, <code>\\?\</code>.</li><li>The runtime does not validate device syntax paths.</li><li>The use of device syntax to access alternate data streams is supported.</li></ul>These changes improve performance while allowing methods to access previously inaccessible paths. Apps that target the .NET Framework 4.6.1 and earlier versions but are running under the .NET Framework 4.6.2 or later are unaffected by this change.|
|Öneri|Daha sonra bu dışında seçebilirsiniz veya .NET Framework 4.6.2'yi hedefleyen uygulamalar değiştirin ve aşağıdaki ekleyerek eski normalleştirme kullanın <code>&lt;runtime&gt;</code> uygulama yapılandırma dosyası bölümünü:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=true&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>.NET Framework 4.6.1 veya önceki ancak hedefleyen uygulamaları .NET Framework 4.6.2 üzerinde çalışıyor veya aşağıdaki satırı ekleyerek yolu normalleştirme değişiklikleri daha sonra etkinleştirebilirsiniz <code>&lt;runtime&gt;</code> uygulama .configuration dosyasının:<pre><code class="lang-xml">&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.IO.UseLegacyPathHandling=false&quot; /&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;</code></pre>|
|Kapsam|İkincil|
|Sürüm|4.6.2|
|Tür|Yeniden Hedefleme|
