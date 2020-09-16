---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702460"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a><span data-ttu-id="6798e-101">WinForms özellikleri artık ArgumentOutOfRangeException oluşturur</span><span class="sxs-lookup"><span data-stu-id="6798e-101">WinForms properties now throw ArgumentOutOfRangeException</span></span>

<span data-ttu-id="6798e-102">Bazı Windows Forms özellikleri artık <xref:System.ArgumentOutOfRangeException> , daha önce olmadıkları durumlarda geçersiz bağımsız değişkenler oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6798e-102">Some Windows Forms properties now throw an <xref:System.ArgumentOutOfRangeException> for invalid arguments, where previously they did not.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6798e-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="6798e-103">Change description</span></span>

<span data-ttu-id="6798e-104">Daha önce, bu özellikler <xref:System.NullReferenceException> <xref:System.IndexOutOfRangeException> <xref:System.ArgumentException> Aralık dışı bağımsız değişkenler geçirildiğinde, veya gibi çeşitli özel durumlar oluşturdu.</span><span class="sxs-lookup"><span data-stu-id="6798e-104">Previously, these properties threw various exceptions, such as <xref:System.NullReferenceException>, <xref:System.IndexOutOfRangeException>, or <xref:System.ArgumentException>, when passed out-of-range arguments.</span></span> <span data-ttu-id="6798e-105">.NET 5,0 ' den itibaren, bu özellikler artık <xref:System.ArgumentOutOfRangeException> Aralık dışı olan bağımsız değişkenleri geçtiğinde bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="6798e-105">Starting in .NET 5.0, these properties now throw an <xref:System.ArgumentOutOfRangeException> when passed arguments that are out of range.</span></span>

<span data-ttu-id="6798e-106"><xref:System.ArgumentOutOfRangeException>.NET çalışma zamanının davranışına uygun bir şekilde oluşturuluyor.</span><span class="sxs-lookup"><span data-stu-id="6798e-106">Throwing an <xref:System.ArgumentOutOfRangeException> conforms to the behavior of the .NET runtime.</span></span> <span data-ttu-id="6798e-107">Ayrıca, hangi bağımsız değişkenin geçersiz olduğu açıkça iletişim kurarak hata ayıklama deneyimini geliştirir.</span><span class="sxs-lookup"><span data-stu-id="6798e-107">It also improves the debugging experience by clearly communicating which argument is invalid.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6798e-108">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="6798e-108">Version introduced</span></span>

<span data-ttu-id="6798e-109">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="6798e-109">.NET 5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6798e-110">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="6798e-110">Recommended action</span></span>

- <span data-ttu-id="6798e-111">Geçersiz bağımsız değişkenlerin geçirilmesini engellemek için kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="6798e-111">Update the code to prevent passing invalid arguments.</span></span>
- <span data-ttu-id="6798e-112">Gerekirse, <xref:System.ArgumentOutOfRangeException> özelliği ayarlarken bir işleyin.</span><span class="sxs-lookup"><span data-stu-id="6798e-112">If necessary, handle an <xref:System.ArgumentOutOfRangeException> when setting the property.</span></span>

#### <a name="category"></a><span data-ttu-id="6798e-113">Kategori</span><span class="sxs-lookup"><span data-stu-id="6798e-113">Category</span></span>

<span data-ttu-id="6798e-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6798e-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6798e-115">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="6798e-115">Affected APIs</span></span>

<span data-ttu-id="6798e-116">Aşağıdaki tabloda etkilenen özellikler ve parametreler listelenmektedir:</span><span class="sxs-lookup"><span data-stu-id="6798e-116">The following table lists the affected properties and parameters:</span></span>

> [!div class="mx-tdBreakAll"]
> | <span data-ttu-id="6798e-117">Özellik</span><span class="sxs-lookup"><span data-stu-id="6798e-117">Property</span></span> | <span data-ttu-id="6798e-118">Parametre adı</span><span class="sxs-lookup"><span data-stu-id="6798e-118">Parameter name</span></span> | <span data-ttu-id="6798e-119">Sürüm eklendi</span><span class="sxs-lookup"><span data-stu-id="6798e-119">Version added</span></span> |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | <span data-ttu-id="6798e-120">5,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="6798e-120">5.0 Preview 5</span></span> |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="6798e-121">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="6798e-121">5.0 Preview 6</span></span> |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | <span data-ttu-id="6798e-122">5,0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="6798e-122">5.0 Preview 6</span></span> |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
