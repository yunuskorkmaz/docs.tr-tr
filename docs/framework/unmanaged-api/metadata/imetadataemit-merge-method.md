---
title: IMetaDataEmit::Merge Metodu
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
ms.openlocfilehash: 899f2ca5ef1b987687f5c065ad3e1965e142d103
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43466119"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="16997-102">IMetaDataEmit::Merge Metodu</span><span class="sxs-lookup"><span data-stu-id="16997-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="16997-103">Belirtilen içeri aktarılan kapsam birleştirilecek kapsamları listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="16997-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16997-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16997-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16997-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16997-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="16997-106">[in] Bir işaretçi bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) birleştirilecek içeri aktarılan kapsamını tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="16997-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="16997-107">[in] Bir işaretçi bir [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) belirteci yeniden eşlemeniz belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="16997-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="16997-108">[in] Bir işaretçi bir [IUnknown](/cpp/atl/iunknown) hataları belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="16997-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16997-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16997-109">Remarks</span></span>  
 <span data-ttu-id="16997-110">Çağrı [Imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) birleşme meta verilerinin tek bir kapsam tetiklemek için.</span><span class="sxs-lookup"><span data-stu-id="16997-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16997-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16997-111">Requirements</span></span>  
 <span data-ttu-id="16997-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16997-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16997-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="16997-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="16997-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılan</span><span class="sxs-lookup"><span data-stu-id="16997-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="16997-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16997-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16997-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="16997-116">See Also</span></span>  
 [<span data-ttu-id="16997-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16997-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="16997-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="16997-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
