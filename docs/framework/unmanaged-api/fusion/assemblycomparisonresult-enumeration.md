---
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
ms.openlocfilehash: 3d3fd88a2c1ac90f823b23d8d2bcb5b177a625c3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73109005"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="d6733-102">AssemblyComparisonResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d6733-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="d6733-103">[CompareAssemblyIdentity](compareassemblyidentity-function.md) işlevi tarafından belirlendiği şekilde, iki derleme kimliğinin denklik olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6733-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6733-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d6733-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="d6733-105">Members</span></span>  
  
|<span data-ttu-id="d6733-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="d6733-106">Member name</span></span>|<span data-ttu-id="d6733-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6733-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="d6733-108">Karşılaştırmayla eşleşen tüm derleme alanlarının eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="d6733-109">Derlemelerin .NET Framework sürüm 2,0 ' deki derleme sürüm numaralarının ortak dil çalışma zamanı sürümü 'ne (CLR) göre eşit kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="d6733-110">.NET Framework 2,0 ' deki derleme sürümü numaralarının CLR içeriğini temel alarak derlemelerin kısmi bir eşleşme olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="d6733-111">Derlemelerin kısmi bir eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="d6733-112">Sürüm numaralarının eski listesini temel alarak derlemelerin kısmi bir eşleşmesinin olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="d6733-113">Yalnızca adlandırılmış derlemelerin kısmi bir eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="d6733-114">Derlemelerin, .NET Framework eski sürümlerindeki sürüm numaralarının CLR 'ye göre eşit kabul edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="d6733-115">Sürüm numaraları yoksayılmış olan iki adet adlandırılmış derleme arasındaki eşleşmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="d6733-116">İki derleme arasında hiçbir eşleşme olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="d6733-117">İki derlemenin, yalnızca kısmen eşleşen sürüm numaraları hariç eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="d6733-118">Eşleşmeyen iki derlemenin sürüm numaraları hariç eşleştiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="d6733-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="d6733-119">Non-denkliği için nedenin bilinmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="d6733-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d6733-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6733-120">Requirements</span></span>  
 <span data-ttu-id="d6733-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6733-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6733-122">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d6733-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6733-123">**Kitaplık:** MsCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d6733-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d6733-124">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6733-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6733-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6733-125">See also</span></span>

- [<span data-ttu-id="d6733-126">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6733-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="d6733-127">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d6733-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
