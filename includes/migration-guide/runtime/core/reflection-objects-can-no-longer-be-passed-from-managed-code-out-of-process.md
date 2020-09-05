---
ms.openlocfilehash: f011f6ebe0fa85a59f3e69c93bba9eddc4c1689b
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496417"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="4fcfb-101">Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez</span><span class="sxs-lookup"><span data-stu-id="4fcfb-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="4fcfb-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="4fcfb-102">Details</span></span>

<span data-ttu-id="4fcfb-103">Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="4fcfb-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="4fcfb-104">Aşağıdaki türler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="4fcfb-104">The following types are affected:</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <span data-ttu-id="4fcfb-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (ve,,, ve dahil olmak üzere türetilmiş türleri <xref:System.Reflection.FieldInfo?displayProperty=fullName> <xref:System.Reflection.MethodInfo?displayProperty=fullName> <xref:System.Type?displayProperty=fullName> <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</span><span class="sxs-lookup"><span data-stu-id="4fcfb-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>

<span data-ttu-id="4fcfb-106"><code>IMarshal</code>Nesne dönüşü için öğesine çağrılar <code>E_NOINTERFACE</code> .</span><span class="sxs-lookup"><span data-stu-id="4fcfb-106">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4fcfb-107">Öneri</span><span class="sxs-lookup"><span data-stu-id="4fcfb-107">Suggestion</span></span>

<span data-ttu-id="4fcfb-108">Yansıtma olmayan nesnelerle çalışmak için sıralama kodunu güncelleştirin.</span><span class="sxs-lookup"><span data-stu-id="4fcfb-108">Update marshaling code to work with non-reflection objects.</span></span>

| <span data-ttu-id="4fcfb-109">Name</span><span class="sxs-lookup"><span data-stu-id="4fcfb-109">Name</span></span>    | <span data-ttu-id="4fcfb-110">Değer</span><span class="sxs-lookup"><span data-stu-id="4fcfb-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4fcfb-111">Kapsam</span><span class="sxs-lookup"><span data-stu-id="4fcfb-111">Scope</span></span>   |<span data-ttu-id="4fcfb-112">İkincil</span><span class="sxs-lookup"><span data-stu-id="4fcfb-112">Minor</span></span>|
|<span data-ttu-id="4fcfb-113">Sürüm</span><span class="sxs-lookup"><span data-stu-id="4fcfb-113">Version</span></span>|<span data-ttu-id="4fcfb-114">4.6</span><span class="sxs-lookup"><span data-stu-id="4fcfb-114">4.6</span></span>|
|<span data-ttu-id="4fcfb-115">Tür</span><span class="sxs-lookup"><span data-stu-id="4fcfb-115">Type</span></span>|<span data-ttu-id="4fcfb-116">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="4fcfb-116">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="4fcfb-117">Etkilenen API’ler</span><span class="sxs-lookup"><span data-stu-id="4fcfb-117">Affected APIs</span></span>

- <xref:System.Reflection.Assembly?displayProperty=fullName>
- <xref:System.Reflection.FieldInfo?displayProperty=fullName>
- <xref:System.Reflection.MemberInfo?displayProperty=fullName>
- <xref:System.Reflection.MethodBody?displayProperty=fullName>
- <xref:System.Reflection.MethodInfo?displayProperty=fullName>
- <xref:System.Reflection.Module?displayProperty=fullName>
- <xref:System.Reflection.ParameterInfo?displayProperty=fullName>
- <xref:System.Reflection.TypeInfo?displayProperty=fullName>
- <xref:System.Type?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Reflection.Assembly`
- `T:System.Reflection.FieldInfo`
- `T:System.Reflection.MemberInfo`
- `T:System.Reflection.MethodBody`
- `T:System.Reflection.MethodInfo`
- `T:System.Reflection.Module`
- `T:System.Reflection.ParameterInfo`
- `T:System.Reflection.TypeInfo`
- `T:System.Type`

-->
