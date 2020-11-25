---
title: 'Son değişiklik: Cryptography. OID yalnızca işlev olarak init'
description: Cryptography. OID sınıfındaki Özellik ayarlayıcılarının artık bir değeri değiştirmeye çalışırsanız bir özel durum oluşturması için .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/16/2020
ms.openlocfilehash: a3b5a393e2a84f7c9a60c2a821ecfda9c6acd2e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761397"
---
# <a name="systemsecuritycryptographyoid-is-functionally-init-only"></a><span data-ttu-id="952eb-103">System. Security. Cryptography. OID yalnızca işlev olarak init</span><span class="sxs-lookup"><span data-stu-id="952eb-103">System.Security.Cryptography.Oid is functionally init-only</span></span>

<span data-ttu-id="952eb-104"><xref:System.Security.Cryptography.Oid?displayProperty=fullName>ASN. 1 nesne tanımlayıcı değerlerini ve "kolay" adlarını temsil etmek için kullanılan sınıfı, daha önce tamamen kesilebilir.</span><span class="sxs-lookup"><span data-stu-id="952eb-104">The <xref:System.Security.Cryptography.Oid?displayProperty=fullName> class, which is used to represent ASN.1 Object Identifier values and their "friendly" names, was previously fully mutable.</span></span> <span data-ttu-id="952eb-105">Bu sıklık genellikle daha fazla bakmıştı veya sürpriz olarak geldi.</span><span class="sxs-lookup"><span data-stu-id="952eb-105">This mutability was often overlooked or came as a surprise.</span></span> <span data-ttu-id="952eb-106">Özellik ayarlayıcıları artık, <xref:System.PlatformNotSupportedException> zaten atandıktan sonra değeri değiştirmeye çalıştığınızda bir oluşturur.</span><span class="sxs-lookup"><span data-stu-id="952eb-106">The property setters now throw a <xref:System.PlatformNotSupportedException> when you attempt to change the value after it's already been assigned.</span></span>

## <a name="change-description"></a><span data-ttu-id="952eb-107">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="952eb-107">Change description</span></span>

<span data-ttu-id="952eb-108">Önceki sürümlerde özellik ayarlayıcıları, <xref:System.Security.Cryptography.Oid> ve özelliklerinin değerini değiştirmek için kullanılabilir <xref:System.Security.Cryptography.Oid.FriendlyName> <xref:System.Security.Cryptography.Oid.Value> .</span><span class="sxs-lookup"><span data-stu-id="952eb-108">In previous versions, the property setters on <xref:System.Security.Cryptography.Oid> can be used to change the value of the <xref:System.Security.Cryptography.Oid.FriendlyName> and <xref:System.Security.Cryptography.Oid.Value> properties.</span></span>

<span data-ttu-id="952eb-109">.NET 5,0 ve sonraki sürümlerinde, özellik ayarlayıcıları yalnızca değeri başlatmak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="952eb-109">In .NET 5.0 and later versions, the property setters can only be used to initialize the value.</span></span> <span data-ttu-id="952eb-110">Özelliğin bir oluşturucudan veya özellik ayarlayıcısına yapılan bir çağrıdan bir değere sahip olması durumunda, Özellik ayarlayıcısı her zaman bir oluşturur <xref:System.PlatformNotSupportedException> .</span><span class="sxs-lookup"><span data-stu-id="952eb-110">Once the property has a value, either from a constructor or a previous call to the property setter, the property setter always throws a <xref:System.PlatformNotSupportedException>.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="952eb-111">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="952eb-111">Reason for change</span></span>

<span data-ttu-id="952eb-112">Bu değişiklik, <xref:System.Security.Cryptography.Oid> nesne ayırma profillerini azaltmak için genel API 'lerde döndürülen değerlerin bir parçası olarak nesnelerin yeniden kullanılmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="952eb-112">This change enables the reuse of <xref:System.Security.Cryptography.Oid> objects as part of return values in public APIs to reduce object allocation profiles.</span></span> <span data-ttu-id="952eb-113">Değerler giriş olarak kullanıldığında geçici "savunma" kopyalarının oluşturulması gereksinimini önler <xref:System.Security.Cryptography.Oid> .</span><span class="sxs-lookup"><span data-stu-id="952eb-113">It avoids the need to create temporary "defensive" copies when <xref:System.Security.Cryptography.Oid> values are used as inputs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="952eb-114">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="952eb-114">Version introduced</span></span>

<span data-ttu-id="952eb-115">5.0</span><span class="sxs-lookup"><span data-stu-id="952eb-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="952eb-116">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="952eb-116">Recommended action</span></span>

<span data-ttu-id="952eb-117"><xref:System.Security.Cryptography.Oid>Nesne başlatma için dışında özellik ayarlayıcıları kullanmaktan kaçının.</span><span class="sxs-lookup"><span data-stu-id="952eb-117">Avoid using the <xref:System.Security.Cryptography.Oid> property setters other than for object initialization.</span></span> <span data-ttu-id="952eb-118">Yeni bir değeri göstermek için, varolan bir nesne üzerindeki değeri değiştirmek yerine yeni bir örnek kullanın.</span><span class="sxs-lookup"><span data-stu-id="952eb-118">To represent a new value, use a new instance instead of changing the value on an existing object.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="952eb-119">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="952eb-119">Affected APIs</span></span>

- <xref:System.Security.Cryptography.Oid.FriendlyName?displayProperty=fullName>
- <xref:System.Security.Cryptography.Oid.Value?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Security.Cryptography.Oid.FriendlyName`
- `P:System.Security.Cryptography.Oid.Value`

### Category

Cryptography

-->
