---
title: 'Son değişiklik: Multicastop. Group null bir değer kabul etmez'
description: Çok kanallı bir değeri artık boş bir değer kabul etmeyen .NET 5,0 ' deki Son değişiklik hakkında bilgi edinin.
ms.date: 08/18/2020
ms.openlocfilehash: 164ac8c2c8dd14f9e0758017e54eeb377f88a7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95761438"
---
# <a name="multicastoptiongroup-doesnt-accept-a-null-value"></a><span data-ttu-id="bf56a-103">Multicastop. Group null bir değer kabul etmez</span><span class="sxs-lookup"><span data-stu-id="bf56a-103">MulticastOption.Group doesn't accept a null value</span></span>

<span data-ttu-id="bf56a-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> Artık değerini kabul etmez `null` .</span><span class="sxs-lookup"><span data-stu-id="bf56a-104"><xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> no longer accepts a value of `null`.</span></span> <span data-ttu-id="bf56a-105">Özelliğini öğesine ayarlarsanız `null` , bir oluşturulur <xref:System.ArgumentNullException> .</span><span class="sxs-lookup"><span data-stu-id="bf56a-105">If you set the property to `null`, an <xref:System.ArgumentNullException> is thrown.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bf56a-106">Sunulan sürüm</span><span class="sxs-lookup"><span data-stu-id="bf56a-106">Version introduced</span></span>

<span data-ttu-id="bf56a-107">5.0</span><span class="sxs-lookup"><span data-stu-id="bf56a-107">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="bf56a-108">Açıklamayı Değiştir</span><span class="sxs-lookup"><span data-stu-id="bf56a-108">Change description</span></span>

<span data-ttu-id="bf56a-109">.NET 'in önceki sürümlerinde <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> özelliğini olarak ayarlayabilirsiniz `null` .</span><span class="sxs-lookup"><span data-stu-id="bf56a-109">In previous versions of .NET, you can set the <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> property to `null`.</span></span> <span data-ttu-id="bf56a-110"><xref:System.Net.Sockets.MulticastOption>Daha sonra öğesine geçirilirse <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> , çalışma zamanı bir oluşturur <xref:System.NullReferenceException> .</span><span class="sxs-lookup"><span data-stu-id="bf56a-110">If the <xref:System.Net.Sockets.MulticastOption> is later passed to <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType>, the runtime throws a <xref:System.NullReferenceException>.</span></span>

<span data-ttu-id="bf56a-111">.NET 5,0 ve üzeri sürümlerde, <xref:System.ArgumentNullException> özelliği olarak ayarlarsanız oluşturulur `null` .</span><span class="sxs-lookup"><span data-stu-id="bf56a-111">In .NET 5.0 and later, an <xref:System.ArgumentNullException> is thrown if you set the property to `null`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bf56a-112">Değişiklik nedeni</span><span class="sxs-lookup"><span data-stu-id="bf56a-112">Reason for change</span></span>

<span data-ttu-id="bf56a-113">Framework Tasarım yönergeleriyle tutarlı olması için, özelliği değeri ise oluşturmak üzere güncelleştirilmiştir <xref:System.ArgumentNullException> `null` .</span><span class="sxs-lookup"><span data-stu-id="bf56a-113">To be consistent with the Framework Design Guidelines, the property has been updated to throw an <xref:System.ArgumentNullException> if the value is `null`.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bf56a-114">Önerilen eylem</span><span class="sxs-lookup"><span data-stu-id="bf56a-114">Recommended action</span></span>

<span data-ttu-id="bf56a-115">' A ayarladığınızdan emin olun <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> `null` .</span><span class="sxs-lookup"><span data-stu-id="bf56a-115">Make sure that you don't set <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=nameWithType> to `null`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bf56a-116">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="bf56a-116">Affected APIs</span></span>

- <xref:System.Net.Sockets.MulticastOption.Group?displayProperty=fullName>

<!--

### Affected APIs

- `P:System.Net.Sockets.MulticastOption.Group`

### Category

Networking

-->
