---
ms.openlocfilehash: 13d3799aeede86b01aa81ce1cd69b3c4c22311ca
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620712"
---
### <a name="wpf-textbox-defaults-to-undo-limit-of-100"></a><span data-ttu-id="b3d24-101">WPF metin kutusu varsayılan olarak 100 limitini geri alır</span><span class="sxs-lookup"><span data-stu-id="b3d24-101">WPF TextBox defaults to undo limit of 100</span></span>

#### <a name="details"></a><span data-ttu-id="b3d24-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="b3d24-102">Details</span></span>

<span data-ttu-id="b3d24-103">.NET Framework 4,5 ' de, WPF metin kutusu için varsayılan geri alma sınırı 100 ' dir (.NET Framework 4,0 ' de sınırsız olacak şekilde)</span><span class="sxs-lookup"><span data-stu-id="b3d24-103">In .NET Framework 4.5, the default undo limit for a WPF textbox is 100 (as opposed to being unlimited in .NET Framework 4.0)</span></span>

#### <a name="suggestion"></a><span data-ttu-id="b3d24-104">Öneri</span><span class="sxs-lookup"><span data-stu-id="b3d24-104">Suggestion</span></span>

<span data-ttu-id="b3d24-105">100 'nin bir geri alma sınırı çok düşükse, sınır şu şekilde açık şekilde ayarlanabilir<xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span><span class="sxs-lookup"><span data-stu-id="b3d24-105">If an undo limit of 100 is too low, the limit can be set explicitly with <xref:System.Windows.Controls.Primitives.TextBoxBase.UndoLimit></span></span>

| <span data-ttu-id="b3d24-106">Name</span><span class="sxs-lookup"><span data-stu-id="b3d24-106">Name</span></span>    | <span data-ttu-id="b3d24-107">Değer</span><span class="sxs-lookup"><span data-stu-id="b3d24-107">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="b3d24-108">Kapsam</span><span class="sxs-lookup"><span data-stu-id="b3d24-108">Scope</span></span>   |<span data-ttu-id="b3d24-109">Edge</span><span class="sxs-lookup"><span data-stu-id="b3d24-109">Edge</span></span>|
|<span data-ttu-id="b3d24-110">Sürüm</span><span class="sxs-lookup"><span data-stu-id="b3d24-110">Version</span></span>|<span data-ttu-id="b3d24-111">4,5</span><span class="sxs-lookup"><span data-stu-id="b3d24-111">4.5</span></span>|
|<span data-ttu-id="b3d24-112">Tür</span><span class="sxs-lookup"><span data-stu-id="b3d24-112">Type</span></span>|<span data-ttu-id="b3d24-113">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="b3d24-113">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b3d24-114">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="b3d24-114">Affected APIs</span></span>

-<xref:System.Windows.Controls.TextBox?displayProperty=nameWithType></li></ul>|
