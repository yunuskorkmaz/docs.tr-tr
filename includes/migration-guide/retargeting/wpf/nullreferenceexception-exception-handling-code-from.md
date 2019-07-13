---
ms.openlocfilehash: 122741d13294c8b137ce48e28f0aa39c6e36265a
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67859203"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException özel durum işleme ImageSourceConverter.ConvertFrom koddan

|   |   |
|---|---|
|Ayrıntılar|Özel durum işleme kodunu hata <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> yanlış bir neden <xref:System.NullReferenceException?displayProperty=name> yerine amaçlanan özel durum için ( <xref:System.IO.DirectoryNotFoundException?displayProperty=name> veya <xref:System.IO.FileNotFoundException?displayProperty=name>). Böylece artık doğru özel çağırılıyorsa yöntem bu değişiklik bu hatayı düzeltir. <p/>Göre varsayılan .NET Framework 4.6.2'yi hedefleyen tüm uygulamalar ve daha önce throw devam <xref:System.NullReferenceException?displayProperty=name> uyumluluk için. .NET Framework 4.7 hedefleyen geliştiricilere ve yukarıdaki doğru özel durumları görmeniz gerekir.|
|Öneri|Geri alma için isteyen geliştiriciler <xref:System.NullReferenceException?displayProperty=name> ne zaman .NET Framework 4.7 veya sonraki bir sürümü hedefleme ekleme/merge, uygulamanın App.config dosyasına aşağıdaki:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|`Scope`|Kenar|
|Version|4.7|
|Type|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|

