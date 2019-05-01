---
ms.openlocfilehash: e4cf139d308a1c12425d966a84d59a0c3bb89712
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61640059"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException özel durum işleme ImageSourceConverter.ConvertFrom koddan

|   |   |
|---|---|
|Ayrıntılar|Özel durum işleme kodunu hata <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> yanlış bir neden <xref:System.NullReferenceException?displayProperty=name> yerine amaçlanan özel durum için (örneğin <xref:System.IO.DirectoryNotFoundException?displayProperty=name>, <xref:System.IO.FileNotFoundException?displayProperty=name>). Böylece artık doğru özel çağırılıyorsa yöntem bu değişiklik bu hatayı düzeltir. <p/>Göre varsayılan .NET Framework 4.6.2'yi hedefleyen tüm uygulamalar ve daha önce throw devam <xref:System.NullReferenceException?displayProperty=name> uyumluluk için. .NET Framework 4.7 hedefleyen geliştiricilere ve yukarıdaki doğru özel durumları görmeniz gerekir.|
|Öneri|Geri alma için isteyen geliştiriciler <xref:System.NullReferenceException?displayProperty=name> ne zaman .NET Framework 4.7 targeting ekleme/merge, uygulamanın App.config dosyasına aşağıdaki:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Kenar|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
