---
ms.openlocfilehash: 56127309c5f5993ffc2e2faedd1f481e8131e094
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400641"
---
### <a name="textformatflagsmodifystring-is-obsolete"></a><span data-ttu-id="3f490-101">TextFormatFlags. ModifyString artık kullanılmıyor</span><span class="sxs-lookup"><span data-stu-id="3f490-101">TextFormatFlags.ModifyString is obsolete</span></span>

<span data-ttu-id="3f490-102">Bu <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alan, bir uyarı olarak kullanımdan kalkmıştır ve gelecek bir .NET sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f490-102">The <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> field is obsolete, as a warning, and may be removed in a future .NET version.</span></span>

#### <a name="change-description"></a><span data-ttu-id="3f490-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="3f490-103">Change description</span></span>

<span data-ttu-id="3f490-104">Önceki .NET sürümlerinde, <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> Enumeration alanı kullanılmıyor olarak işaretlenmemiştir.</span><span class="sxs-lookup"><span data-stu-id="3f490-104">In previous .NET versions, the <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> enumeration field is not marked obsolete.</span></span> <span data-ttu-id="3f490-105">.NET 5,0 ve sonraki sürümlerinde, uyarı olarak artık kullanılmıyor olarak işaretlenir.</span><span class="sxs-lookup"><span data-stu-id="3f490-105">In .NET 5.0 and later versions, it is marked obsolete as a warning.</span></span> <span data-ttu-id="3f490-106">Bu alan, gelecekteki bir .NET sürümünde kaldırılabilir.</span><span class="sxs-lookup"><span data-stu-id="3f490-106">This field may be removed in a future .NET version.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="3f490-107">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="3f490-107">Reason for change</span></span>

<span data-ttu-id="3f490-108">İle bir dize geçirilmesi <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> , bazı durumlarda dizeyi değiştirir.</span><span class="sxs-lookup"><span data-stu-id="3f490-108">Passing a string to <xref:System.Windows.Forms.TextRenderer.MeasureText%2A?displayProperty=nameWithType> with <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> alters the string in some situations.</span></span> <span data-ttu-id="3f490-109">Bu davranış, dize imlik kullanılabilirliği taahhüdünü keser ve önemli bir .NET çalışma zamanı durumu bozulması oluşmasına neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="3f490-109">This behavior breaks the string immutability promise and may lead to a fatal .NET runtime state corruption.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="3f490-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="3f490-110">Version introduced</span></span>

<span data-ttu-id="3f490-111">.NET 5,0 RC1</span><span class="sxs-lookup"><span data-stu-id="3f490-111">.NET 5.0 RC1</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3f490-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="3f490-112">Recommended action</span></span>

<span data-ttu-id="3f490-113">' İ temel alan tüm kodları güncelleştirin <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3f490-113">Update any code that relies on <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="3f490-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="3f490-114">Category</span></span>

<span data-ttu-id="3f490-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3f490-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3f490-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="3f490-116">Affected APIs</span></span>

- <xref:System.Windows.Forms.TextFormatFlags.ModifyString?displayProperty=fullName>

<!--

#### Affected APIs

- `F:System.Windows.Forms.TextFormatFlags.ModifyString`

-->
