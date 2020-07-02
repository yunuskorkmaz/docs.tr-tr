---
ms.openlocfilehash: 9c9c4ec55143ef991e9b69a389e0f3368263bb4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614843"
---
### <a name="nullreferenceexception-in-exception-handling-code-from-imagesourceconverterconvertfrom"></a><span data-ttu-id="27939-101">Imaosurceconverter. Convertkaynağından özel durum işleme kodunda NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="27939-101">NullReferenceException in exception handling code from ImageSourceConverter.ConvertFrom</span></span>

#### <a name="details"></a><span data-ttu-id="27939-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="27939-102">Details</span></span>

<span data-ttu-id="27939-103">Özel durum işleme kodundaki bir hata, <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> <xref:System.NullReferenceException?displayProperty=fullName> amaçlanan özel durum yerine yanlış bir şekilde oluşturulmasına neden oldu ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> veya <xref:System.IO.FileNotFoundException?displayProperty=fullName> ).</span><span class="sxs-lookup"><span data-stu-id="27939-103">An error in the exception handling code for <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)> caused an incorrect <xref:System.NullReferenceException?displayProperty=fullName> to be thrown instead of the intended exception ( <xref:System.IO.DirectoryNotFoundException?displayProperty=fullName> or <xref:System.IO.FileNotFoundException?displayProperty=fullName>).</span></span> <span data-ttu-id="27939-104">Bu değişiklik, yöntemin şimdi doğru özel durumu oluşturmaları için bu hatayı düzeltir.</span><span class="sxs-lookup"><span data-stu-id="27939-104">This change corrects that error so that the method now throws the right exception.</span></span> <p/><span data-ttu-id="27939-105">Varsayılan olarak, .NET Framework 4.6.2 ve önceki sürümleri hedefleyen tüm uygulamalar uyumluluk için throw ile devam eder <xref:System.NullReferenceException?displayProperty=fullName> .</span><span class="sxs-lookup"><span data-stu-id="27939-105">By default all applications targeting .NET Framework 4.6.2 and earlier continue to throw <xref:System.NullReferenceException?displayProperty=fullName> for compatibility.</span></span> <span data-ttu-id="27939-106">.NET Framework 4,7 ve üzeri hedefleme geliştiricilerin doğru özel durumları görmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="27939-106">Developers targeting .NET Framework 4.7 and above should see the right exceptions.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="27939-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="27939-107">Suggestion</span></span>

<span data-ttu-id="27939-108"><xref:System.NullReferenceException?displayProperty=fullName>.NET Framework 4,7 veya sonraki bir sürümü hedeflerken almak üzere dönmek isteyen geliştiriciler aşağıdakini uygulamanın App.config dosyasına ekleyebilir/birleştirebilir:</span><span class="sxs-lookup"><span data-stu-id="27939-108">Developers who wish to revert to getting <xref:System.NullReferenceException?displayProperty=fullName> when targeting .NET Framework 4.7 or later can add/merge the following to their application's App.config file:</span></span>

<pre><code class="lang-xml">&lt;configuration&gt;&#13;&#10;&lt;runtime&gt;&#13;&#10;&lt;AppContextSwitchOverrides value=&quot;Switch.System.Windows.Media.ImageSourceConverter.OverrideExceptionWithNullReferenceException=true&quot;/&gt;&#13;&#10;&lt;/runtime&gt;&#13;&#10;&lt;/configuration&gt;&#13;&#10;</code></pre>

| <span data-ttu-id="27939-109">Name</span><span class="sxs-lookup"><span data-stu-id="27939-109">Name</span></span>    | <span data-ttu-id="27939-110">Değer</span><span class="sxs-lookup"><span data-stu-id="27939-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="27939-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="27939-111">Scope</span></span>   | <span data-ttu-id="27939-112">Edge</span><span class="sxs-lookup"><span data-stu-id="27939-112">Edge</span></span>        |
| <span data-ttu-id="27939-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="27939-113">Version</span></span> | <span data-ttu-id="27939-114">4,7</span><span class="sxs-lookup"><span data-stu-id="27939-114">4.7</span></span>         |
| <span data-ttu-id="27939-115">Tür</span><span class="sxs-lookup"><span data-stu-id="27939-115">Type</span></span>    | <span data-ttu-id="27939-116">Yeniden Hedefleme</span><span class="sxs-lookup"><span data-stu-id="27939-116">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="27939-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="27939-117">Affected APIs</span></span>

- <xref:System.Windows.Media.ImageSourceConverter.ConvertFrom(System.ComponentModel.ITypeDescriptorContext,System.Globalization.CultureInfo,System.Object)?displayProperty=nameWithType>
