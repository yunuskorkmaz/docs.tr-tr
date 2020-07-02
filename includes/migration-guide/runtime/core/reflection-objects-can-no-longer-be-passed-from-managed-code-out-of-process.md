---
ms.openlocfilehash: a54b17b2002bd0f85b8b47c5e37e040470d6c494
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621435"
---
### <a name="reflection-objects-can-no-longer-be-passed-from-managed-code-to-out-of-process-dcom-clients"></a><span data-ttu-id="5eb15-101">Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez</span><span class="sxs-lookup"><span data-stu-id="5eb15-101">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients</span></span>

#### <a name="details"></a><span data-ttu-id="5eb15-102">Ayrıntılar</span><span class="sxs-lookup"><span data-stu-id="5eb15-102">Details</span></span>

<span data-ttu-id="5eb15-103">Yansıma nesneleri artık yönetilen koddan işlem dışı DCOM istemcilerine geçirilemez.</span><span class="sxs-lookup"><span data-stu-id="5eb15-103">Reflection objects can no longer be passed from managed code to out-of-process DCOM clients.</span></span> <span data-ttu-id="5eb15-104">Aşağıdaki türler etkilenir:</span><span class="sxs-lookup"><span data-stu-id="5eb15-104">The following types are affected:</span></span><ul><li><xref:System.Reflection.Assembly?displayProperty=fullName></li><li><span data-ttu-id="5eb15-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName>(ve,,, ve dahil olmak üzere türetilmiş türleri <xref:System.Reflection.FieldInfo?displayProperty=fullName> <xref:System.Reflection.MethodInfo?displayProperty=fullName> <xref:System.Type?displayProperty=fullName> <xref:System.Reflection.TypeInfo?displayProperty=fullName> )</span><span class="sxs-lookup"><span data-stu-id="5eb15-105"><xref:System.Reflection.MemberInfo?displayProperty=fullName> (and its derived types, including <xref:System.Reflection.FieldInfo?displayProperty=fullName>, <xref:System.Reflection.MethodInfo?displayProperty=fullName>, <xref:System.Type?displayProperty=fullName>, and <xref:System.Reflection.TypeInfo?displayProperty=fullName>)</span></span></li><li><xref:System.Reflection.MethodBody?displayProperty=fullName></li><li><xref:System.Reflection.Module?displayProperty=fullName></li><li><span data-ttu-id="5eb15-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span><span class="sxs-lookup"><span data-stu-id="5eb15-106"><xref:System.Reflection.ParameterInfo?displayProperty=fullName>.</span></span></li></ul><span data-ttu-id="5eb15-107"><code>IMarshal</code>Nesne dönüşü için öğesine çağrılar <code>E_NOINTERFACE</code> .</span><span class="sxs-lookup"><span data-stu-id="5eb15-107">Calls to <code>IMarshal</code> for the object return <code>E_NOINTERFACE</code>.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="5eb15-108">Öneri</span><span class="sxs-lookup"><span data-stu-id="5eb15-108">Suggestion</span></span>

<span data-ttu-id="5eb15-109">Yansıtma olmayan nesnelerle çalışacak sıralama kodunu Güncelleştir</span><span class="sxs-lookup"><span data-stu-id="5eb15-109">Update marshaling code to work with non-reflection objects</span></span>

| <span data-ttu-id="5eb15-110">Name</span><span class="sxs-lookup"><span data-stu-id="5eb15-110">Name</span></span>    | <span data-ttu-id="5eb15-111">Değer</span><span class="sxs-lookup"><span data-stu-id="5eb15-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="5eb15-112">Kapsam</span><span class="sxs-lookup"><span data-stu-id="5eb15-112">Scope</span></span>   |<span data-ttu-id="5eb15-113">İkincil</span><span class="sxs-lookup"><span data-stu-id="5eb15-113">Minor</span></span>|
|<span data-ttu-id="5eb15-114">Sürüm</span><span class="sxs-lookup"><span data-stu-id="5eb15-114">Version</span></span>|<span data-ttu-id="5eb15-115">4.6</span><span class="sxs-lookup"><span data-stu-id="5eb15-115">4.6</span></span>|
|<span data-ttu-id="5eb15-116">Tür</span><span class="sxs-lookup"><span data-stu-id="5eb15-116">Type</span></span>|<span data-ttu-id="5eb15-117">Çalışma Zamanı</span><span class="sxs-lookup"><span data-stu-id="5eb15-117">Runtime</span></span>|
