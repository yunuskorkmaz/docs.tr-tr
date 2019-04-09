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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156175"
---
# <a name="imetadataemitdefinetyperefbyname-method"></a><span data-ttu-id="b29b7-102">IMetaDataEmit::DefineTypeRefByName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b29b7-102">IMetaDataEmit::DefineTypeRefByName Method</span></span>
<span data-ttu-id="b29b7-103">Bir meta veri geçerli kapsamı dışında olan Belirtilen kapsam içinde tanımlanan bir tür için belirteç alır.</span><span class="sxs-lookup"><span data-stu-id="b29b7-103">Gets a metadata token for a type that is defined in the specified scope, which is outside the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b29b7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b29b7-104">Syntax</span></span>  
  
```  
HRESULT DefineTypeRefByName (   
    [in]  mdToken     tkResolutionScope,   
    [in]  LPCWSTR     szName,   
    [out] mdTypeRef   *ptr   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b29b7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b29b7-105">Parameters</span></span>  
 `tkResolutionScope`  
 <span data-ttu-id="b29b7-106">[in] Çözüm kapsamını belirten belirteç.</span><span class="sxs-lookup"><span data-stu-id="b29b7-106">[in] The token specifying the resolution scope.</span></span> <span data-ttu-id="b29b7-107">Aşağıdaki belirteç türlerini geçerlidir:</span><span class="sxs-lookup"><span data-stu-id="b29b7-107">The following token types are valid:</span></span>  
  
-   `mdModuleRef`<span data-ttu-id="b29b7-108">, çağıran tanımlanır aynı bütünleştirilmiş kodda tür tanımlı ise.</span><span class="sxs-lookup"><span data-stu-id="b29b7-108">, if the type is defined in the same assembly in which the caller is defined.</span></span>  
  
-   `mdAssemblyRef`<span data-ttu-id="b29b7-109">, bir çağıranın tanımlanır dışındaki bir bütünleştirilmiş kodda tür tanımlı ise.</span><span class="sxs-lookup"><span data-stu-id="b29b7-109">, if the type is defined in an assembly other than the one in which the caller is defined.</span></span>  
  
-   `mdTypeRef`<span data-ttu-id="b29b7-110">, iç içe türü türü ise.</span><span class="sxs-lookup"><span data-stu-id="b29b7-110">, if the type is a nested type.</span></span>  
  
-   `mdModule`<span data-ttu-id="b29b7-111">, türü çağıran tanımlanır aynı modülde tanımlandıysa.</span><span class="sxs-lookup"><span data-stu-id="b29b7-111">, if the type is defined in the same module in which the caller is defined.</span></span>  
  
-   <span data-ttu-id="b29b7-112">Türü genel olarak tanımlanmışsa null.</span><span class="sxs-lookup"><span data-stu-id="b29b7-112">Null, if the type is defined globally.</span></span>  
  
 `szName`  
 <span data-ttu-id="b29b7-113">[in] Unicode hedef türünün adı.</span><span class="sxs-lookup"><span data-stu-id="b29b7-113">[in] The name of the target type in Unicode.</span></span>  
  
 `ptr`  
 <span data-ttu-id="b29b7-114">[out] Bir işaretçi `mdTypeRef` türüne atanan belirteci.</span><span class="sxs-lookup"><span data-stu-id="b29b7-114">[out] A pointer to the `mdTypeRef` token that is assigned to the type.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b29b7-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b29b7-115">Requirements</span></span>  
 <span data-ttu-id="b29b7-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b29b7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b29b7-117">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="b29b7-117">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b29b7-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="b29b7-118">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b29b7-119">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b29b7-119">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b29b7-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b29b7-120">See also</span></span>

- [<span data-ttu-id="b29b7-121">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b29b7-121">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="b29b7-122">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b29b7-122">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
