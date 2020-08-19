---
ms.openlocfilehash: cf51d5f6b3eee7189fd9613b3d780a829d197a04
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88558016"
---
### <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="393ae-101">System. Security. Cryptography. OID yalnızca işlev olarak init</span><span class="sxs-lookup"><span data-stu-id="393ae-101">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="393ae-102"><xref:System.Security.Cryptography.Oid?displayProperty=fullName>ASN. 1 nesne tanımlayıcı değerlerini ve "kolay" adlarını temsil etmek için kullanılan sınıfı, daha önce tamamen kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="393ae-102">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="393ae-103">Bu sıklık genellikle daha fazla bakmıştı veya sürpriz olarak geldi.</span><span class="sxs-lookup"><span data-stu-id="393ae-103">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="393ae-104">Özellik ayarlayıcıları artık, <xref:System.PlatformNotSupportedException> zaten atandıktan sonra değeri değiştirmeye çalıştığınızda bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="393ae-104">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

#### <a name="change-description"></a><span data-ttu-id="393ae-105">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="393ae-105">Change description</span></span>

<span data-ttu-id="393ae-106">Önceki sürümlerde özellik ayarlayıcıları, <xref:System.Security.Cryptography.Oid> ve özelliklerinin değerini değiştirmek için kullanılabilir <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> .</span><span class="sxs-lookup"><span data-stu-id="393ae-106">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="393ae-107">.NET 5,0 ve sonraki sürümlerinde, özellik ayarlayıcıları yalnızca değeri başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="393ae-107">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="393ae-108">Özelliğin bir oluşturucudan veya özellik ayarlayıcısına yapılan bir çağrıdan bir değere sahip olması durumunda, Özellik ayarlayıcısı her zaman bir oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="393ae-108">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="393ae-109">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="393ae-109">Reason for change</span></span>

<span data-ttu-id="393ae-110">Bu değişiklik, <xref:System.Security.Cryptography.Oid> nesne ayırma profillerini azaltmak için genel API 'lerde döndürülen değerlerin bir parçası olarak nesnelerin yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="393ae-110">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="393ae-111">Değerler giriş olarak kullanıldığında geçici "savunma" kopyalarının oluşturulması gereksinimini önler <xref:System.Security.Cryptography.Oid> .</span><span class="sxs-lookup"><span data-stu-id="393ae-111">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="393ae-112">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="393ae-112">Version introduced</span></span>

<span data-ttu-id="393ae-113">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="393ae-113">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="393ae-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="393ae-114">Recommended action</span></span>

<span data-ttu-id="393ae-115"><xref:System.Security.Cryptography.Oid>Nesne başlatma için dışında özellik ayarlayıcıları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="393ae-115">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="393ae-116">Yeni bir değeri göstermek için, varolan bir nesne üzerindeki değeri değiştirmek yerine yeni bir örnek kullanın.</span><span class="sxs-lookup"><span data-stu-id="393ae-116">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

#### <a name="category"></a><span data-ttu-id="393ae-117">Kategori</span><span class="sxs-lookup"><span data-stu-id="393ae-117">Category</span></span>

<span data-ttu-id="393ae-118">Şifreleme</span><span class="sxs-lookup"><span data-stu-id="393ae-118">Cryptography</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="393ae-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="393ae-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

#### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

-->
