---
description: 'Şu konuda daha fazla bilgi edinin: ımetadatayayma::D efineTypeRefByName yöntemi'
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
ms.openlocfilehash: 836516e06105bb8ebc7c9bacf7b7d3837bf89eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784021"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="6f53f-103">IMetaDataEmit::DefineTypeRefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f53f-103">IMetaDataEmit::DefineTypeRefByName Method</span></span>

<span data-ttu-id="6f53f-104">Geçerli kapsamın dışında belirtilen kapsamda tanımlı bir tür için meta veri belirteci alır.</span><span class="sxs-lookup"><span data-stu-id="6f53f-104">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f53f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f53f-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineTypeRefByName (
    [in]  mdToken     tkResolutionScope,
    [in]  LPCWSTR     szName,
    [out] mdTypeRef   *ptr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f53f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f53f-106">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="6f53f-107">'ndaki Çözümleme kapsamını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="6f53f-107">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="6f53f-108">Aşağıdaki belirteç türleri geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="6f53f-108">The following token types are valid:</span></span>  
  
- <span data-ttu-id="6f53f-109">`mdModuleRef`, türü çağıranın tanımlandığı derlemede tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="6f53f-109">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
- <span data-ttu-id="6f53f-110">`mdAssemblyRef`tür, çağıranın tanımlandığı bir derlemede tanımlıysa.</span><span class="sxs-lookup"><span data-stu-id="6f53f-110">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
- <span data-ttu-id="6f53f-111">`mdTypeRef`türü, iç içe bir tür ise.</span><span class="sxs-lookup"><span data-stu-id="6f53f-111">`mdTypeRef`, if the type is a nested type.</span></span>  
  
- <span data-ttu-id="6f53f-112">`mdModule`, türü çağıranın tanımlandığı modülde tanımlanmışsa.</span><span class="sxs-lookup"><span data-stu-id="6f53f-112">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
- <span data-ttu-id="6f53f-113">Tür genel olarak tanımlanmışsa null.</span><span class="sxs-lookup"><span data-stu-id="6f53f-113">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="6f53f-114">'ndaki Unicode 'daki hedef türünün adı.</span><span class="sxs-lookup"><span data-stu-id="6f53f-114">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="6f53f-115">dışı `mdTypeRef` Türe atanmış belirtece yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6f53f-115">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f53f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f53f-116">Requirements</span></span>  

 <span data-ttu-id="6f53f-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f53f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f53f-118">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6f53f-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6f53f-119">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="6f53f-119">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6f53f-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f53f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f53f-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f53f-121">See also</span></span>

- [<span data-ttu-id="6f53f-122">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f53f-122">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="6f53f-123">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f53f-123">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
