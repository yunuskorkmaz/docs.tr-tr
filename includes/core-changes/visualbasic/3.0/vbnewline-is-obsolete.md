---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116374"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="56cca-101">Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="56cca-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="56cca-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabiti .NET Core 3,0 Preview 8 ' den itibaren [kullanımdan kalkmış\]\[](xref:System.ObsoleteAttribute) olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="56cca-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="56cca-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="56cca-103">Version introduced</span></span>

<span data-ttu-id="56cca-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="56cca-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="56cca-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="56cca-105">Change description</span></span>

<span data-ttu-id="56cca-106">.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="56cca-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="56cca-107">Constant kullanımı bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="56cca-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="56cca-108">.NET Core 'un .NET Framework ve önceki sürümlerinde, eski olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="56cca-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="56cca-109">Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="56cca-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="56cca-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine> sabiti, Windows 'ta yeni satır karakteri dizisi olan `\r\n`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="56cca-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="56cca-111">UNIX tabanlı sistemlerde, yeni satır karakteri `\n`.</span><span class="sxs-lookup"><span data-stu-id="56cca-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="56cca-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="56cca-112">Recommended action</span></span>

<span data-ttu-id="56cca-113"><xref:Microsoft.VisualBasic.Constants.vbNewLine> için [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:</span><span class="sxs-lookup"><span data-stu-id="56cca-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="56cca-114">Satır başı ve satır besleme için <xref:Microsoft.VisualBasic.Constants.vbCrLf>kullanın.</span><span class="sxs-lookup"><span data-stu-id="56cca-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="56cca-115">Geçerli platformun yeni satır için <xref:System.Environment.NewLine?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="56cca-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="56cca-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="56cca-116">Category</span></span>

<span data-ttu-id="56cca-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="56cca-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="56cca-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="56cca-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
