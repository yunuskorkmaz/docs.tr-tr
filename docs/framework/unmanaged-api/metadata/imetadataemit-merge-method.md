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
ms.openlocfilehash: 179cfc5c0725934e21d7b89a2f8d4c934b049f78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106061"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="165e3-102">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="165e3-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="165e3-103">Belirtilen içeri aktarılan kapsam birleştirilecek kapsamları listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="165e3-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="165e3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="165e3-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="165e3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="165e3-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="165e3-106">[in] Bir işaretçi bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) birleştirilecek içeri aktarılan kapsamını tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="165e3-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="165e3-107">[in] Bir işaretçi bir [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) belirteci yeniden eşlemeniz belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="165e3-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="165e3-108">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) hataları belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="165e3-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="165e3-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="165e3-109">Remarks</span></span>  
 <span data-ttu-id="165e3-110">Çağrı [Imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) birleşme meta verilerinin tek bir kapsam tetiklemek için.</span><span class="sxs-lookup"><span data-stu-id="165e3-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="165e3-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="165e3-111">Requirements</span></span>  
 <span data-ttu-id="165e3-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="165e3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="165e3-113">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="165e3-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="165e3-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="165e3-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="165e3-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="165e3-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="165e3-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="165e3-116">See also</span></span>

- [<span data-ttu-id="165e3-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="165e3-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="165e3-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="165e3-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
