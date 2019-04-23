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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d93c55cec3d35fd4208a4a8a7c9b235dd10fb9ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156175"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="02905-102">IMetaDataEmit::DefineTypeRefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="02905-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="02905-103">Bir meta veri geçerli kapsamı dışında olan Belirtilen kapsam içinde tanımlanan bir tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="02905-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02905-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02905-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02905-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02905-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="02905-106">[in] Çözüm kapsamını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="02905-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="02905-107">Aşağıdaki belirteç türlerini geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="02905-107">The following token types are valid:</span></span>  
  
-   <span data-ttu-id="02905-108">`mdModuleRef`, çağıran tanımlanır aynı bütünleştirilmiş kodda tür tanımlı ise.</span><span class="sxs-lookup"><span data-stu-id="02905-108">`mdModuleRef`, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="02905-109">`mdAssemblyRef`, bir çağıranın tanımlanır dışındaki bir bütünleştirilmiş kodda tür tanımlı ise.</span><span class="sxs-lookup"><span data-stu-id="02905-109">`mdAssemblyRef`, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="02905-110">`mdTypeRef`, iç içe türü türü ise.</span><span class="sxs-lookup"><span data-stu-id="02905-110">`mdTypeRef`, if the type is a nested type.</span></span>  
  
-   <span data-ttu-id="02905-111">`mdModule`, türü çağıran tanımlanır aynı modülde tanımlandıysa.</span><span class="sxs-lookup"><span data-stu-id="02905-111">`mdModule`, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="02905-112">Türü genel olarak tanımlanmışsa null.</span><span class="sxs-lookup"><span data-stu-id="02905-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="02905-113">[in] Unicode hedef türünün adı.</span><span class="sxs-lookup"><span data-stu-id="02905-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="02905-114">[out] Bir işaretçi `mdTypeRef` türüne atanan belirteci.</span><span class="sxs-lookup"><span data-stu-id="02905-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02905-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02905-115">Requirements</span></span>  
 <span data-ttu-id="02905-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02905-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02905-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="02905-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="02905-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="02905-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="02905-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02905-119">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02905-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02905-120">See also</span></span>

- [<span data-ttu-id="02905-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02905-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="02905-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02905-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
