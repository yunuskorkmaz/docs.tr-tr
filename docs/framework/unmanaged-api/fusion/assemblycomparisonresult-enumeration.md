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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b8ecc996e14263510e2d0a658cec020696c263
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914507"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="f4147-102">AssemblyComparisonResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="f4147-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="f4147-103">İki derleme kimliklerinin denklik tarafından belirlenen şekilde gösteren [Compareassemblyıdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="f4147-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4147-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f4147-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="f4147-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="f4147-105">Members</span></span>  
  
|<span data-ttu-id="f4147-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="f4147-106">Member name</span></span>|<span data-ttu-id="f4147-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4147-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="f4147-108">Tüm derleme karşılaştırma eşlemesinde alanları gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="f4147-109">Derlemeleri derleme sürüm numaralarının .NET Framework sürüm 2.0 ortak dil çalışma zamanı (CLR) sürümünü Birleştirici göre eşdeğer olarak kabul edilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="f4147-110">.NET Framework 2.0 derleme sürüm numaraları CLR birleştirmesi göre derlemelerin kısmi eşleşme gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="f4147-111">Kısmi eşleşme derlemelerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="f4147-112">Eski sürüm numaraları birleştirmesi alarak derlemeleri kısmi bir eşleşme belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4147-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="f4147-113">Kısmi eşleşme yalnızca adlandırılmış derlemelerin gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="f4147-114">Derlemeler sürüm numaraları .NET Framework'ün eski sürümlerinde CLR birleştirmesi göre eşdeğer olarak kabul edilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="f4147-115">Olan sürüm numaraları yoksayıldı iki yalnızca adlandırılmış derlemeler arasında bir eşleşme belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4147-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="f4147-116">İki derleme eşleşme oluştuğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="f4147-117">İki derlemenin yalnızca kısmen eşleşen kendi sürüm numaraları dışında eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="f4147-118">İki derlemenin eşleşmiyor, sürüm numaraları dışında eşleştiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="f4147-119">Denkliği olmayan nedeni bilinmiyor gösterir.</span><span class="sxs-lookup"><span data-stu-id="f4147-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4147-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4147-120">Requirements</span></span>  
 <span data-ttu-id="f4147-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4147-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4147-122">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="f4147-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f4147-123">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4147-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f4147-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4147-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4147-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f4147-125">See also</span></span>

- [<span data-ttu-id="f4147-126">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="f4147-126">CompareAssemblyIdentity Function</span></span>](../../../../docs/framework/unmanaged-api/fusion/compareassemblyidentity-function.md)
- [<span data-ttu-id="f4147-127">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="f4147-127">Fusion Enumerations</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-enumerations.md)
