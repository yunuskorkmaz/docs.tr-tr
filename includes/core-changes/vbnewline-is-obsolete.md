---
ms.openlocfilehash: 82017569128937d344838df850445cf55aa9ea4c
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2019
ms.locfileid: "70930035"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a><span data-ttu-id="0ccdd-101">Microsoft. VisualBasic. sabitleri. Vbyeni satır artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="0ccdd-101">Microsoft.VisualBasic.Constants.vbNewLine is obsolete</span></span>

<span data-ttu-id="0ccdd-102">Sabit .NET Framework kullanılmıyor olarak işaretlenmiş, ancak .NET Core 3,0 kitaplığında öznitelik daha önce eksikti. [](xref:System.ObsoleteAttribute) <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="0ccdd-102">The <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant is marked [Obsolete](xref:System.ObsoleteAttribute) in .NET Framework, but the attribute was missing previously in the .NET Core 3.0 library.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0ccdd-103">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="0ccdd-103">Version introduced</span></span>

<span data-ttu-id="0ccdd-104">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="0ccdd-104">.NET Core 3.0 Preview 8</span></span>

#### <a name="details"></a><span data-ttu-id="0ccdd-105">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="0ccdd-105">Details</span></span>

<span data-ttu-id="0ccdd-106">.NET Core 3,0 Preview 8 ' den itibaren, [eski](xref:System.ObsoleteAttribute) öznitelik, .NET Framework ile uyumlu <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> `vbNewLine` olması için sabitine uygulandı.</span><span class="sxs-lookup"><span data-stu-id="0ccdd-106">Starting with .NET Core 3.0 Preview 8, the [Obsolete](xref:System.ObsoleteAttribute) attribute has been applied to the <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> constant to conform to `vbNewLine` in the .NET Framework.</span></span> <span data-ttu-id="0ccdd-107">`vbNewLine` Constant kullanımı bir derleyici uyarısı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0ccdd-107">Use of the `vbNewLine` constant produces a compiler warning.</span></span> 

<span data-ttu-id="0ccdd-108">.NET Core `vbNewLine` 'un önceki sürümlerinde bir derleyici uyarısı üretmedi.</span><span class="sxs-lookup"><span data-stu-id="0ccdd-108">In previous versions of .NET Core, `vbNewLine` did not produce a compiler warning.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0ccdd-109">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="0ccdd-109">Recommended action</span></span>

<span data-ttu-id="0ccdd-110">İçin`vbNewLine` [kullanılmayan](xref:System.ObsoleteAttribute) öznitelik iletisi aşağıdaki öneriyi içerir:</span><span class="sxs-lookup"><span data-stu-id="0ccdd-110">The [Obsolete](xref:System.ObsoleteAttribute) attribute message for `vbNewLine` includes the following recommendation:</span></span>

> <span data-ttu-id="0ccdd-111">Satır başı ve satır besleme için [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf)kullanın.</span><span class="sxs-lookup"><span data-stu-id="0ccdd-111">For a carriage return and line feed, use [vbCrLf](xref:Microsoft.VisualBasic.Constants.vbCrLf).</span></span> <span data-ttu-id="0ccdd-112">Geçerli platformun yeni satır için kullanın <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0ccdd-112">For the current platform's newline, use <xref:System.Environment.NewLine?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="0ccdd-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="0ccdd-113">Category</span></span>
<span data-ttu-id="0ccdd-114">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ccdd-114">Visual Basic</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0ccdd-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="0ccdd-115">Affected APIs</span></span>
- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-- >

