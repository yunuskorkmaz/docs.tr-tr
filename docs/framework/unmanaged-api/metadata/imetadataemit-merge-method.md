---
title: IMetaDataEmit::Merge Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.Merge
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::Merge
helpviewer_keywords:
- IMetaDataEmit::Merge method [.NET Framework metadata]
- Merge method [.NET Framework metadata]
ms.assetid: 7596220c-f699-4b6c-8ae7-c83220610650
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3fee3c0b82bec102d8e292a76d3df5a14d40ace8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67757678"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="77153-102">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="77153-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="77153-103">Belirtilen içeri aktarılan kapsam birleştirilecek kapsamları listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="77153-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77153-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="77153-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77153-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="77153-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="77153-106">[in] Bir işaretçi bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) birleştirilecek içeri aktarılan kapsamını tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="77153-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="77153-107">[in] Bir işaretçi bir [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) belirteci yeniden eşlemeniz belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="77153-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="77153-108">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) hataları belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="77153-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77153-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="77153-109">Remarks</span></span>  
 <span data-ttu-id="77153-110">Çağrı [Imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) birleşme meta verilerinin tek bir kapsam tetiklemek için.</span><span class="sxs-lookup"><span data-stu-id="77153-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77153-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="77153-111">Requirements</span></span>  
 <span data-ttu-id="77153-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77153-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77153-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="77153-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77153-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="77153-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="77153-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77153-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77153-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="77153-116">See also</span></span>

- [<span data-ttu-id="77153-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77153-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="77153-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="77153-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
