---
ms.openlocfilehash: 88a0b7e04c7015ca3fa5abd8a6897dafcbe41c49
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557977"
---
### <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="d536e-101">Multicastop. Group null bir değer kabul etmez</span><span class="sxs-lookup"><span data-stu-id="d536e-101">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="d536e-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Artık değerini kabul etmez `null` .</span><span class="sxs-lookup"><span data-stu-id="d536e-102"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="d536e-103">Özelliğini öğesine ayarlarsanız `null` , bir oluşturulur <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="d536e-103">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d536e-104">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="d536e-104">Version introduced</span></span>

<span data-ttu-id="d536e-105">5.0</span><span class="sxs-lookup"><span data-stu-id="d536e-105">5.0</span></span>

#### <a name="change-description"></a><span data-ttu-id="d536e-106">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="d536e-106">Change description</span></span>

<span data-ttu-id="d536e-107">.NET 'in önceki sürümlerinde <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> özelliğini olarak ayarlayabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="d536e-107">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="d536e-108"><xref:System.Net.Sockets.MulticastOption>Daha sonra öğesine geçirilirse <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , çalışma zamanı bir oluşturur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="d536e-108">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="d536e-109">.NET 5,0 ve üzeri sürümlerde, <xref:System.ArgumentNullException> özelliği olarak ayarlarsanız oluşturulur `null` .</span><span class="sxs-lookup"><span data-stu-id="d536e-109">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d536e-110">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="d536e-110">Reason for change</span></span>

<span data-ttu-id="d536e-111">Framework Tasarım yönergeleriyle tutarlı olması için, özelliği değeri ise oluşturmak üzere güncelleştirilmiştir <xref:System.ArgumentNullException> `null` .</span><span class="sxs-lookup"><span data-stu-id="d536e-111">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d536e-112">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="d536e-112">Recommended action</span></span>

<span data-ttu-id="d536e-113">' A ayarladığınızdan emin olun <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="d536e-113">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

#### <a name="category"></a><span data-ttu-id="d536e-114">Kategori</span><span class="sxs-lookup"><span data-stu-id="d536e-114">Category</span></span>

<span data-ttu-id="d536e-115">Ağ</span><span class="sxs-lookup"><span data-stu-id="d536e-115">Networking</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d536e-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="d536e-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

-->
