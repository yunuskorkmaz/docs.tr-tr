---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116374"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="0daca-101">Microsoft.VisualBasic.Constants.vbNewLine eski</span><span class="sxs-lookup"><span data-stu-id="0daca-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="0daca-102">Sabit <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> ,NET Core 3.0 Preview 8 ile başlayan [ \[Eski olarak\] ](xref:System.ObsoleteAttribute) işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="0daca-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0daca-103">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="0daca-103">Version introduced</span></span>

<span data-ttu-id="0daca-104">3.0 Önizleme 8</span><span class="sxs-lookup"><span data-stu-id="0daca-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="0daca-105">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="0daca-105">Change description</span></span>

<span data-ttu-id="0daca-106">.NET Core 3.0 Preview 8 ile başlayarak, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabite uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="0daca-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="0daca-107">Sabitin kullanımı derleyici uyarısı üretir.</span><span class="sxs-lookup"><span data-stu-id="0daca-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="0daca-108">.NET Framework ve .NET Core'un önceki sürümlerinde eski olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="0daca-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="0daca-109">Bu değişiklik, Visual Basic'i çok platformlu geliştirme dili olarak desteklemek için yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0daca-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="0daca-110">Sabit, <xref:Microsoft.VisualBasic.Constants.vbNewLine> Windows'daki yeni satır karakter dizisine `\r\n`eşittir.</span><span class="sxs-lookup"><span data-stu-id="0daca-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="0daca-111">Unix tabanlı sistemlerde, yeni satır `\n`karakteri .</span><span class="sxs-lookup"><span data-stu-id="0daca-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0daca-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0daca-112">Recommended action</span></span>

<span data-ttu-id="0daca-113">[Eski](xref:System.ObsoleteAttribute) öznitelik iletisi <xref:Microsoft.VisualBasic.Constants.vbNewLine> için aşağıdaki öneri içerir:</span><span class="sxs-lookup"><span data-stu-id="0daca-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="0daca-114">Bir satır başı ve satır <xref:Microsoft.VisualBasic.Constants.vbCrLf>beslemesi için.</span><span class="sxs-lookup"><span data-stu-id="0daca-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="0daca-115">Geçerli platformun yeni hattı için <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0daca-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="0daca-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="0daca-116">Category</span></span>

<span data-ttu-id="0daca-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0daca-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0daca-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0daca-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
