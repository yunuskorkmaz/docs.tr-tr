---
ms.openlocfilehash: 5ef785f476b795a9c53e511d51b2683b99e6da05
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182059"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="1c94e-101">Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="1c94e-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="1c94e-102">Sabit <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> , .NET Core 3,0 Preview 8 ' den itibaren [kullanılmıyor](xref:System.ObsoleteAttribute) olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="1c94e-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) starting with .NET Core 3.0 Preview 8.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1c94e-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="1c94e-103">Version introduced</span></span>

<span data-ttu-id="1c94e-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="1c94e-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="1c94e-105">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="1c94e-105">Details</span></span>

<span data-ttu-id="1c94e-106">.NET Core 3,0 Preview 8 ' den başlayarak, [eski](xref:System.ObsoleteAttribute) öznitelik <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> sabitine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="1c94e-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant.</span></span> <span data-ttu-id="1c94e-107">Constant kullanımı bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c94e-107">Use of the constant produces a compiler warning.</span></span> <span data-ttu-id="1c94e-108">Hem .NET Core hem de .NET Framework önceki sürümlerinde, eski olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="1c94e-108">In previous releases of both .NET Core and .NET Framework, it was not marked as obsolete.</span></span>

<span data-ttu-id="1c94e-109">Bu değişiklik, çok platformlu geliştirme için bir dil olarak Visual Basic desteklemek üzere yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="1c94e-109">This change was made to support Visual Basic as a language for multi-platform development.</span></span> <span data-ttu-id="1c94e-110">Sabit, Windows 'ta yeni `\r\n`satır karakteri dizisi ile eşdeğerdir. `vbNewLine`</span><span class="sxs-lookup"><span data-stu-id="1c94e-110">The `vbNewLine` constant is equivalent to `\r\n`, the newline character sequence on Windows.</span></span> <span data-ttu-id="1c94e-111">UNIX tabanlı sistemlerde, yeni satır karakteri `\n`.</span><span class="sxs-lookup"><span data-stu-id="1c94e-111">On Unix-based systems, the newline character is `\n`.</span></span>
 
#### <a name="recommended-action"></a><span data-ttu-id="1c94e-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="1c94e-112">Recommended action</span></span>

<span data-ttu-id="1c94e-113">İçin`vbNewLine` [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:</span><span class="sxs-lookup"><span data-stu-id="1c94e-113">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="1c94e-114">Satır başı ve satır besleme için [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)kullanın.</span><span class="sxs-lookup"><span data-stu-id="1c94e-114">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="1c94e-115">Geçerli platformun yeni satır için kullanın <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="1c94e-115">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="1c94e-116">Kategori</span><span class="sxs-lookup"><span data-stu-id="1c94e-116">Category</span></span>

<span data-ttu-id="1c94e-117">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1c94e-117">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1c94e-118">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="1c94e-118">Affected APIs</span></span>

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

