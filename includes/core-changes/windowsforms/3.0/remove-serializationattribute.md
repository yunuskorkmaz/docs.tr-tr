---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643958"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="87b29-101">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="87b29-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="87b29-102">Bilinen <xref:System.SerializableAttribute> ikili serileştirme senaryoları olmayan bazı Windows Forms sınıflarından kaldırıldı.</span><span class="sxs-lookup"><span data-stu-id="87b29-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="87b29-103">Açıklamayı değiştir</span><span class="sxs-lookup"><span data-stu-id="87b29-103">Change description</span></span>

<span data-ttu-id="87b29-104">Aşağıdaki türler .NET Framework <xref:System.SerializableAttribute> ile dekore edilmiştir, ancak öznitelik .NET Core kaldırıldı:</span><span class="sxs-lookup"><span data-stu-id="87b29-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="87b29-105">Tarihsel olarak, bu serileştirme mekanizması ciddi bakım ve güvenlik endişeleri olmuştur.</span><span class="sxs-lookup"><span data-stu-id="87b29-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="87b29-106">`SerializableAttribute` Türleri korumak, bu türlerin sürümden sürüme serileştirme değişiklikleri ve potansiyel olarak çerçeveden çerçeveye serileştirme değişiklikleri için sınanması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="87b29-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="87b29-107">Bu, bu tür geliştirmek için daha zor hale getirir ve korumak için pahalıya mal olabilir.</span><span class="sxs-lookup"><span data-stu-id="87b29-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="87b29-108">Bu türler, özniteliği kaldırmanın etkisini en aza indiren bilinen ikili serileştirme senaryolarına sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="87b29-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="87b29-109">Daha fazla bilgi için [Ikili serileştirme](~/docs/standard/serialization/binary-serialization.md)ye bakın.</span><span class="sxs-lookup"><span data-stu-id="87b29-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="87b29-110">Sürüm tanıtıldı</span><span class="sxs-lookup"><span data-stu-id="87b29-110">Version introduced</span></span>

<span data-ttu-id="87b29-111">3.0 Önizleme 9</span><span class="sxs-lookup"><span data-stu-id="87b29-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="87b29-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="87b29-112">Recommended action</span></span>

<span data-ttu-id="87b29-113">Bu tür serileştirilebilir olarak işaretlenmiş bağlı olabilecek tüm kodu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="87b29-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="87b29-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="87b29-114">Category</span></span>

<span data-ttu-id="87b29-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="87b29-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="87b29-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="87b29-116">Affected APIs</span></span>

- <span data-ttu-id="87b29-117">None</span><span class="sxs-lookup"><span data-stu-id="87b29-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
