---
ms.openlocfilehash: 4fb1ffed97a5b7f906bed13a69f1e71563d11dae
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556219"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="f4162-101">SerializableAttribute bazı Windows Forms türlerinden kaldırıldı</span><span class="sxs-lookup"><span data-stu-id="f4162-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="f4162-102">, <xref:System.SerializableAttribute> Bilinen bir ikili serileştirme senaryosu olmayan bazı Windows Forms sınıflarından kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="f4162-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="f4162-103">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="f4162-103">Change description</span></span>

<span data-ttu-id="f4162-104">Aşağıdaki türler <xref:System.SerializableAttribute> .NET Framework içindeki ile tasarlanmıştır, ancak öznitelik .NET Core 'da kaldırılmıştır:</span><span class="sxs-lookup"><span data-stu-id="f4162-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="f4162-105">Tarihsel olarak, bu serileştirme mekanizması ciddi bakım ve güvenlik sorunlarına sahipti.</span><span class="sxs-lookup"><span data-stu-id="f4162-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="f4162-106">`SerializableAttribute`Türlerin sürdürülmesi, bu türlerin sürümden sürüme serileştirme değişiklikleri ve potansiyel olarak çerçeve serileştirme değişiklikleri için test olması gerektiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="f4162-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="f4162-107">Bu, bu türleri daha da gelişmesini zorlaştırır ve bakım açısından maliyetli olabilir.</span><span class="sxs-lookup"><span data-stu-id="f4162-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="f4162-108">Bu türlerin bilinen bir ikili serileştirme senaryosu yoktur, bu da özniteliği kaldırmanın etkilerini en aza indirir.</span><span class="sxs-lookup"><span data-stu-id="f4162-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="f4162-109">Daha fazla bilgi için bkz. [ikili serileştirme](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f4162-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="f4162-110">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="f4162-110">Version introduced</span></span>

<span data-ttu-id="f4162-111">3,0</span><span class="sxs-lookup"><span data-stu-id="f4162-111">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="f4162-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="f4162-112">Recommended action</span></span>

<span data-ttu-id="f4162-113">Seri hale getirilebilir olarak işaretlenmekte olan bu türlere bağlı olabilecek tüm kodları güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="f4162-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="f4162-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="f4162-114">Category</span></span>

<span data-ttu-id="f4162-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f4162-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="f4162-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="f4162-116">Affected APIs</span></span>

- <span data-ttu-id="f4162-117">Hiçbiri</span><span class="sxs-lookup"><span data-stu-id="f4162-117">None</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
