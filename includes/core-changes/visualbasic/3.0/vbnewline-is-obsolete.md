---
ms.openlocfilehash: 86cdb845c436f424bbcc70e0736568031143b204
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74567446"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="71d40-101">Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="71d40-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="71d40-102"><xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabiti .NET Core 3,0 Preview 8 ' den itibaren [kullanılmıyor](xref:System.ObsoleteAttribute) olarak işaretlendi.</span><span class="sxs-lookup"><span data-stu-id="71d40-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="71d40-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="71d40-103">Version introduced</span></span>

<span data-ttu-id="71d40-104">3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="71d40-104">3.0 Preview 8</span></span>

#### <a name="change-description"></a><span data-ttu-id="71d40-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="71d40-105">Change description</span></span>

<span data-ttu-id="71d40-106">.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="71d40-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="71d40-107">Constant kullanımı bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71d40-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="71d40-108">Hem .NET Core hem de .NET Framework önceki sürümlerinde, eski olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="71d40-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="71d40-109">Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="71d40-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="71d40-110">`vbNewLine` sabiti, Windows 'ta yeni satır karakteri dizisi olan `\r\n`eşdeğerdir.</span><span class="sxs-lookup"><span data-stu-id="71d40-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="71d40-111">UNIX tabanlı sistemlerde, yeni satır karakteri `\n`.</span><span class="sxs-lookup"><span data-stu-id="71d40-111">On Unix-based systems, the newline character is `\n`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="71d40-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="71d40-112">Recommended action</span></span>

<span data-ttu-id="71d40-113">`vbNewLine` için [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:</span><span class="sxs-lookup"><span data-stu-id="71d40-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="71d40-114">Satır başı ve satır besleme için [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)kullanın.</span><span class="sxs-lookup"><span data-stu-id="71d40-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="71d40-115">Geçerli platformun yeni satır için <xref:System.Environment.NewLine?displayProperty=nameWithType>kullanın.</span><span class="sxs-lookup"><span data-stu-id="71d40-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="71d40-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="71d40-116">Category</span></span>

<span data-ttu-id="71d40-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71d40-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="71d40-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="71d40-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
