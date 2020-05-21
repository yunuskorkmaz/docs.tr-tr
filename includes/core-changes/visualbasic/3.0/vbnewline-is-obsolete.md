---
ms.openlocfilehash: 535a73c6b748166a1e4a4661a6bab0671c653278
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721691"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="303dc-101">Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="303dc-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="303dc-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>Sabit, .NET Core 3,0 Preview 8 ' den itibaren [ \[ eski \] ](xref:System.ObsoleteAttribute) olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="303dc-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked as [\[Obsolete\]](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="303dc-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="303dc-103">Version introduced</span></span>

<span data-ttu-id="303dc-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="303dc-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="303dc-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="303dc-105">Change description</span></span>

<span data-ttu-id="303dc-106">.NET Core 3,0 Preview 8 ' den başlayarak, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="303dc-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="303dc-107">Constant kullanımı bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="303dc-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="303dc-108">.NET Core 'un .NET Framework ve önceki sürümlerinde, eski olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="303dc-108">In .NET Framework and previous releases of .NET Core, it was not marked as obsolete.</span></span>

<span data-ttu-id="303dc-109">Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="303dc-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="303dc-110"><xref:Microsoft.VisualBasic.Constants.vbNewLine>Sabit, `\r\n` Windows 'ta yeni satır karakteri dizisi ile eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="303dc-110">The <xref:Microsoft.VisualBasic.Constants.vbNewLine> constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="303dc-111">UNIX tabanlı sistemlerde, yeni satır karakteri `\n` .</span><span class="sxs-lookup"><span data-stu-id="303dc-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="303dc-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="303dc-112">Recommended action</span></span>

<span data-ttu-id="303dc-113">İçin [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi <xref:Microsoft.VisualBasic.Constants.vbNewLine> aşağıdaki öneriyi içerir:</span><span class="sxs-lookup"><span data-stu-id="303dc-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for <xref:Microsoft.VisualBasic.Constants.vbNewLine> includes the following recommendation:</span></span>

<span data-ttu-id="303dc-114">Bir satır başı ve satır besleme için kullanın <xref:Microsoft.VisualBasic.Constants.vbCrLf> .</span><span class="sxs-lookup"><span data-stu-id="303dc-114">For a carriage return and line feed, use <xref:Microsoft.VisualBasic.Constants.vbCrLf>.</span></span> <span data-ttu-id="303dc-115">Geçerli platformun yeni satır için kullanın <xref:System.Environment.NewLine?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="303dc-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="303dc-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="303dc-116">Category</span></span>

<span data-ttu-id="303dc-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="303dc-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="303dc-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="303dc-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

#### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
