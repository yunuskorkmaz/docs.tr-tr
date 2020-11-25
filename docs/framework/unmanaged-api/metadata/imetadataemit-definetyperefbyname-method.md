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
ms.openlocfilehash: b83c868f1a804d4e6f32adffc190ae086aa5e0a0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719345"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="a55f9-102">IMetaDataEmit::DefineTypeRefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a55f9-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="a55f9-103">Geçerli kapsamın dışında belirtilen kapsamda tanımlı bir tür için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="a55f9-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a55f9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="a55f9-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a55f9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a55f9-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="a55f9-106">'ndaki Çözümleme kapsamını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="a55f9-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="a55f9-107">Aşağıdaki belirteç türleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="a55f9-107">The following token types are valid:</span></span>  
  
- <span data-ttu-id="a55f9-108">`mdModuleRef`, türü çağıranın tanımlandığı derlemede tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="a55f9-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a55f9-109">`mdAssemblyRef`tür, çağıranın tanımlandığı bir derlemede tanımlıysa.</span><span class="sxs-lookup"><span data-stu-id="a55f9-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a55f9-110">`mdTypeRef`türü, iç içe bir tür ise.</span><span class="sxs-lookup"><span data-stu-id="a55f9-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="a55f9-111">`mdModule`, türü çağıranın tanımlandığı modülde tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="a55f9-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="a55f9-112">Tür genel olarak tanımlanmışsa null.</span><span class="sxs-lookup"><span data-stu-id="a55f9-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="a55f9-113">'ndaki Unicode 'daki hedef türünün adı.</span><span class="sxs-lookup"><span data-stu-id="a55f9-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="a55f9-114">dışı `mdTypeRef` Türe atanmış belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a55f9-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a55f9-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a55f9-115">Requirements</span></span>  

 <span data-ttu-id="a55f9-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a55f9-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a55f9-117">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="a55f9-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a55f9-118">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="a55f9-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a55f9-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a55f9-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a55f9-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a55f9-120">See also</span></span>

- [<span data-ttu-id="a55f9-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a55f9-121">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="a55f9-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a55f9-122">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
