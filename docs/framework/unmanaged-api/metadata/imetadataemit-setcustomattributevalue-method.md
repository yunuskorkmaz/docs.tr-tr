---
description: ': Imetadatayayma:: SetCustomAttributeValue yöntemi hakkında daha fazla bilgi edinin'
title: IMetaDataEmit::SetCustomAttributeValue Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetCustomAttributeValue
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetCustomAttributeValue
helpviewer_keywords:
- SetCustomAttributeValue method [.NET Framework metadata]
- IMetaDataEmit::SetCustomAttributeValue method [.NET Framework metadata]
ms.assetid: f721c863-9642-4e64-917a-65f9e55c25b9
topic_type:
- apiref
ms.openlocfilehash: 1eede765f27b371deb670242086d59b3d4320530
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706584"
---
# <a name="imetadataemitsetcustomattributevalue-method"></a><span data-ttu-id="5c9f3-103">IMetaDataEmit::SetCustomAttributeValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c9f3-103">IMetaDataEmit::SetCustomAttributeValue Method</span></span>

<span data-ttu-id="5c9f3-104">[Imetadatayay::D efineCustomAttribute](imetadataemit-definecustomattribute-method.md)öğesine yapılan önceki çağrı tarafından tanımlanan özel bir özniteliğin değerini ayarlar veya güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="5c9f3-104">Sets or updates the value of a custom attribute defined by a prior call to [IMetaDataEmit::DefineCustomAttribute](imetadataemit-definecustomattribute-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c9f3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c9f3-105">Syntax</span></span>  
  
```cpp  
HRESULT SetCustomAttributeValue (
    [in]  mdCustomAttribute       pcv,
    [in]  void const              *pCustomAttribute,
    [in]  ULONG                   cbCustomAttribute
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c9f3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c9f3-106">Parameters</span></span>  

 `pcv`  
 <span data-ttu-id="5c9f3-107">'ndaki Hedef özel özniteliğin belirteci.</span><span class="sxs-lookup"><span data-stu-id="5c9f3-107">[in] The token of the target custom attribute.</span></span>  
  
 `pCustomAttribute`  
 <span data-ttu-id="5c9f3-108">'ndaki Özel özniteliği içeren dizi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c9f3-108">[in] A pointer to the array that contains the custom attribute.</span></span>  
  
 `cbCustomAttribute`  
 <span data-ttu-id="5c9f3-109">'ndaki Özel özniteliğin bayt cinsinden boyutu.</span><span class="sxs-lookup"><span data-stu-id="5c9f3-109">[in] The size, in bytes, of the custom attribute.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c9f3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c9f3-110">Requirements</span></span>  

 <span data-ttu-id="5c9f3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c9f3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c9f3-112">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5c9f3-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5c9f3-113">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="5c9f3-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5c9f3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c9f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c9f3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c9f3-115">See also</span></span>

- [<span data-ttu-id="5c9f3-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9f3-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="5c9f3-117">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c9f3-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
