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
ms.openlocfilehash: e3cdb648397ca4f4aa2326e4f2349a5a14c3edcc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178300"
---
# <a name="assemblycomparisonresult-enumeration"></a><span data-ttu-id="be424-102">AssemblyComparisonResult Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="be424-102">AssemblyComparisonResult Enumeration</span></span>
<span data-ttu-id="be424-103">[CompareAssemblyIdentity](compareassemblyidentity-function.md) işlevi tarafından belirlenen iki derleme kimliğinin eşdeğerliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-103">Indicates the equivalence of two assembly identities, as determined by the [CompareAssemblyIdentity](compareassemblyidentity-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be424-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="be424-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="be424-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="be424-105">Members</span></span>  
  
|<span data-ttu-id="be424-106">Üye adı</span><span class="sxs-lookup"><span data-stu-id="be424-106">Member name</span></span>|<span data-ttu-id="be424-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be424-107">Description</span></span>|  
|-----------------|-----------------|  
|`ACR_EquivalentFullMatch`|<span data-ttu-id="be424-108">Karşılaştırma daki tüm montaj alanlarının eşleşdiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-108">Indicates that all assembly fields in the comparison match.</span></span>|  
|`ACR_EquivalentFXUnified`|<span data-ttu-id="be424-109">Derlemelerin .NET Framework sürüm 2.0'daki derleme sürüm numaralarının ortak dil çalışma zamanı sürümüne (CLR) göre eşdeğer kabul edilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-109">Indicates that assemblies are considered equivalent based on the common language runtime version (CLR) unification of assembly version numbers in the .NET Framework version 2.0.</span></span>|  
|`ACR_EquivalentPartialFXUnified`|<span data-ttu-id="be424-110">.NET Framework 2.0'daki derleme sürüm numaralarının CLR birleşmesi temel alınca derlemelerin kısmi eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-110">Indicates a partial match of the assemblies based on the CLR unification of assembly version numbers in the .NET Framework 2.0.</span></span>|  
|`ACR_EquivalentPartialMatch`|<span data-ttu-id="be424-111">Derlemelerin kısmi eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-111">Indicates a partial match of the assemblies.</span></span>|  
|`ACR_EquivalentPartialUnified`|<span data-ttu-id="be424-112">Sürüm numaralarının eski birleşmesi temel alınarak derlemelerin kısmi eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-112">Indicates a partial match of the assemblies based on legacy unification of version numbers.</span></span>|  
|`ACR_EquivalentPartialWeakNamed`|<span data-ttu-id="be424-113">Yalnızca adlandırılmış derlemelerin kısmi eşleşmesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-113">Indicates a partial match of simply named assemblies.</span></span>|  
|`ACR_EquivalentUnified`|<span data-ttu-id="be424-114">Derlemelerin.NET Framework'ün eski sürümlerinde sürüm numaralarının CLR birleşmesi temel alınarak eşdeğer kabul edilir olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-114">Indicates that assemblies are considered equivalent based on the CLR unification of version numbers in legacy versions of the .NET Framework.</span></span>|  
|`ACR_EquivalentWeakNamed`|<span data-ttu-id="be424-115">Sürüm numaraları yoksayıldı iki basit adlandırılmış derlemeler arasındaki eşleşmeyi gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-115">Indicates a match between two simply named assemblies whose version numbers were ignored.</span></span>|  
|`ACR_NonEquivalent`|<span data-ttu-id="be424-116">İki derleme arasında eşleşme oluşmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-116">Indicates that no match occurred between the two assemblies.</span></span>|  
|`ACR_NonEquivalentPartialVersion`|<span data-ttu-id="be424-117">İki derlemenin, yalnızca kısmen eşleşen sürüm numaraları dışında eşleşin.</span><span class="sxs-lookup"><span data-stu-id="be424-117">Indicates that the two assemblies match except for their version numbers, which match only partially.</span></span>|  
|`ACR_NonEquivalentVersion`|<span data-ttu-id="be424-118">İki derlemenin, eşleşmeyan sürüm numaraları dışında eşleşin.</span><span class="sxs-lookup"><span data-stu-id="be424-118">Indicates that the two assemblies match except for their version numbers, which do not match.</span></span>|  
|`ACR_Unknown`|<span data-ttu-id="be424-119">Denklik nedeninin bilinmediğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="be424-119">Indicates that the reason for non-equivalency is not known.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="be424-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be424-120">Requirements</span></span>  
 <span data-ttu-id="be424-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be424-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be424-122">**Üstbilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="be424-122">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="be424-123">**Kütüphane:** MsCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="be424-123">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be424-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be424-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be424-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be424-125">See also</span></span>

- [<span data-ttu-id="be424-126">CompareAssemblyIdentity İşlevi</span><span class="sxs-lookup"><span data-stu-id="be424-126">CompareAssemblyIdentity Function</span></span>](compareassemblyidentity-function.md)
- [<span data-ttu-id="be424-127">Fusion Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="be424-127">Fusion Enumerations</span></span>](fusion-enumerations.md)
