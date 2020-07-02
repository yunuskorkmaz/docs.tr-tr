---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614843"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a>Imaosurceconverter. Convertkaynağından özel durum işleme kodunda NullReferenceException

#### <a name="details"></a>Ayrıntılar

Özel durum işleme kodundaki bir hata, <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> <xref:System.NullReferenceException?displayProperty=fullName> amaçlanan özel durum yerine yanlış bir şekilde oluşturulmasına neden oldu ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> veya <xref:System.IO.FileNotFoundException?displayProperty=fullName> ). Bu değişiklik, yöntemin şimdi doğru özel durumu oluşturmaları için bu hatayı düzeltir. <p/>Varsayılan olarak, .NET Framework 4.6.2 ve önceki sürümleri hedefleyen tüm uygulamalar uyumluluk için throw ile devam eder <xref:System.NullReferenceException?displayProperty=fullName> . .NET Framework 4,7 ve üzeri hedefleme geliştiricilerin doğru özel durumları görmeniz gerekir.

#### <a name="suggestion"></a>Öneri

<xref:System.NullReferenceException?displayProperty=fullName>.NET Framework 4,7 veya sonraki bir sürümü hedeflerken almak üzere dönmek isteyen geliştiriciler aşağıdakini uygulamanın App.config dosyasına ekleyebilir/birleştirebilir:

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| Name    | Değer       |
|:--------|:------------|
| Kapsam   | Edge        |
| Sürüm | 4,7         |
| Tür    | Yeniden Hedefleme |

#### <a name="affected-apis"></a>Etkilenen API’ler

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
