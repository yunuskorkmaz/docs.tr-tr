---
description: 'Daha fazla bilgi edinin: AssemblyComparisonResult numaralandırması'
title: AssemblyComparisonResult Numaralandırması
ms.date: 03/30/2017
api_name:
- AssemblyComparisonResult
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- AssemblyComparisonResult
helpviewer_keywords:
- AssemblyComparisonResult enumeration [.NET Framework fusion]
ms.assetid: bd042f89-10b1-40ca-946e-46da082f5263
topic_type:
- apiref
ms.openlocfilehash: 093cff830aa87d28ee86ecaeb6965887279a72d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761297"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="c0cb6-103">AssemblyComparisonResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c0cb6-103">AssemblyComparisonResult Enumeration</span></span>

<span data-ttu-id="c0cb6-104">[CompareAssemblyIdentity](compareassemblyidentity-function.md) işlevi tarafından belirlendiği şekilde, iki derleme kimliğinin denklik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-104">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0cb6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0cb6-105">Syntax</span></span>  
  
```cpp  
typedef enum _tagAssemblyComparisonResult {  
    ACR_Unknown,
    ACR_EquivalentFullMatch,  
    ACR_EquivalentWeakNamed,  
    ACR_EquivalentFXUnified,  
    ACR_EquivalentUnified,
    ACR_NonEquivalentVersion,  
    ACR_NonEquivalent,
    ACR_EquivalentPartialMatch,  
    ACR_EquivalentPartialWeakNamed,
    ACR_EquivalentPartialUnified,  
    ACR_EquivalentPartialFXUnified,  
    ACR_NonEquivalentPartialVersion
} AssemblyComparisonResult;  
```  
  
## <a name="members"></a><span data-ttu-id="c0cb6-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c0cb6-106">Members</span></span>  
  
|<span data-ttu-id="c0cb6-107">Üye adı</span><span class="sxs-lookup"><span data-stu-id="c0cb6-107">Member name</span></span>|<span data-ttu-id="c0cb6-108">Description</span><span class="sxs-lookup"><span data-stu-id="c0cb6-108">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="c0cb6-109">Karşılaştırmayla eşleşen tüm derleme alanlarının eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-109">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="c0cb6-110">Derlemelerin .NET Framework sürüm 2,0 ' deki derleme sürüm numaralarının ortak dil çalışma zamanı sürümü 'ne (CLR) göre eşit kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-110">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="c0cb6-111">.NET Framework 2,0 ' deki derleme sürümü numaralarının CLR içeriğini temel alarak derlemelerin kısmi bir eşleşme olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-111">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="c0cb6-112">Derlemelerin kısmi bir eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-112">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="c0cb6-113">Sürüm numaralarının eski listesini temel alarak derlemelerin kısmi bir eşleşmesinin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-113">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="c0cb6-114">Yalnızca adlandırılmış derlemelerin kısmi bir eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-114">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="c0cb6-115">Derlemelerin, .NET Framework eski sürümlerindeki sürüm numaralarının CLR 'ye göre eşit kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-115">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="c0cb6-116">Sürüm numaraları yoksayılmış olan iki adet adlandırılmış derleme arasındaki eşleşmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-116">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="c0cb6-117">İki derleme arasında hiçbir eşleşme olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-117">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="c0cb6-118">İki derlemenin, yalnızca kısmen eşleşen sürüm numaraları hariç eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-118">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="c0cb6-119">Eşleşmeyen iki derlemenin sürüm numaraları hariç eşleştiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-119">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="c0cb6-120">Non-denkliği için nedenin bilinmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-120">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0cb6-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0cb6-121">Requirements</span></span>  

 <span data-ttu-id="c0cb6-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0cb6-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0cb6-123">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c0cb6-123">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c0cb6-124">**Kitaplık:** MsCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c0cb6-124">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c0cb6-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0cb6-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0cb6-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0cb6-126">See also</span></span>

- [<span data-ttu-id="c0cb6-127">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="c0cb6-127">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="c0cb6-128">Fusion Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c0cb6-128">Fusion Enumerations</span></span>](fusion-enumerations.md)
