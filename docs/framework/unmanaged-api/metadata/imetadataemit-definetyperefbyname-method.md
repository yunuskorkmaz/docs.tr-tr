---
title: IMetaDataEmit::DefineTypeRefByName Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineTypeRefByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineTypeRefByName
helpviewer_keywords:
- DefineTypeRefByName method [.NET Framework metadata]
- IMetaDataEmit::DefineTypeRefByName method [.NET Framework metadata]
ms.assetid: c30a4ce3-2d3e-411a-98df-e62ac4a5dd50
topic_type:
- apiref
ms.openlocfilehash: 3dfdd473b01bfe83def52f957c52e0f4d11375ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74434388"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="1d1b6-102">IMetaDataEmit::DefineTypeRefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1d1b6-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="1d1b6-103">Geçerli kapsamın dışında belirtilen kapsamda tanımlı bir tür için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d1b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1d1b6-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1d1b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1d1b6-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="1d1b6-106">'ndaki Çözümleme kapsamını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="1d1b6-107">Aşağıdaki belirteç türleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="1d1b6-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="1d1b6-108">`mdModuleRef`, çağıran tarafından tanımlanan derlemede tanımlanırsa.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="1d1b6-109">`mdAssemblyRef`, tür arayanın tanımlandığı bir derlemede tanımlıysa.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="1d1b6-110">tür iç içe bir tür ise `mdTypeRef`.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="1d1b6-111">`mdModule`, çağıran tarafından tanımlanan modül içinde tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="1d1b6-112">Tür genel olarak tanımlanmışsa null.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="1d1b6-113">'ndaki Unicode 'daki hedef türünün adı.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="1d1b6-114">dışı Türe atanan `mdTypeRef` belirtecine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1d1b6-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1d1b6-115">Requirements</span></span>  
 <span data-ttu-id="1d1b6-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1d1b6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1d1b6-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1d1b6-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1d1b6-118">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="1d1b6-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1d1b6-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1d1b6-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d1b6-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1d1b6-120">See also</span></span>

- [<span data-ttu-id="1d1b6-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d1b6-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="1d1b6-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1d1b6-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
