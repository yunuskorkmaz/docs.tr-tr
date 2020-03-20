---
ms.openlocfilehash: 824d75585efd40937c1a48376ec7862cba1a8fa3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2020
ms.locfileid: "68235558"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>NullReferenceException imageSourceConverter.ConvertFrom gelen özel durum işleme kodu

|   |   |
|---|---|
|Ayrıntılar|Özel durum işleme kodundaki <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> bir <xref:System.NullReferenceException?displayProperty=name> hata, amaçlanan özel durum <xref:System.IO.DirectoryNotFoundException?displayProperty=name> <xref:System.IO.FileNotFoundException?displayProperty=name>(veya) yerine yanlış atılmasına neden oldu. Bu değişiklik, yöntemşimdi doğru özel durum atar, böylece bu hatayı düzeltir. <p/>Varsayılan olarak .NET Framework 4.6.2 ve daha önce <xref:System.NullReferenceException?displayProperty=name> hedefleyen tüm uygulamalar uyumluluk için atmaya devam eder. .NET Framework 4.7 ve üzerini hedefleyen geliştiriciler doğru özel durumları görmelidir.|
|Öneri|.NET Framework 4.7 <xref:System.NullReferenceException?displayProperty=name> veya daha sonrasını hedefalırken geri dönmek isteyen geliştiriciler, uygulamalarının App.config dosyasına aşağıdakileri ekleyebilir/birleştirebilirler:<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>|
|Kapsam|Edge|
|Sürüm|4.7|
|Tür|Yeniden Hedefleme|
|Etkilenen API’ler|<ul><li><xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType></li></ul>|
