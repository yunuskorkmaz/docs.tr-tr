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
ms.openlocfilehash: 759358822ed865c89f6f55084d1e7f6143506e93
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175713"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="815cf-102">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="815cf-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="815cf-103">Belirtilen alınan kapsamı birleştirilecek kapsamlar listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="815cf-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815cf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="815cf-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="815cf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="815cf-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="815cf-106">[içinde] Birleştirilecek dışa aktarılan kapsamı tanımlayan bir [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) nesnesinin işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="815cf-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="815cf-107">[içinde] Belirteç yeniden eşlemi belirten bir [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="815cf-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="815cf-108">[içinde] Hataları belirten [bir IUnknown](/cpp/atl/iunknown) nesnesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="815cf-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="815cf-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="815cf-109">Remarks</span></span>  
 <span data-ttu-id="815cf-110">Çağrı [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) tek bir kapsamda meta verilerin birleşmesi tetiklemek için.</span><span class="sxs-lookup"><span data-stu-id="815cf-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="815cf-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="815cf-111">Requirements</span></span>  
 <span data-ttu-id="815cf-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="815cf-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="815cf-113">**Üstbilgi:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="815cf-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="815cf-114">**Kütüphane:** MSCorEE.dll'de kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="815cf-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="815cf-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="815cf-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="815cf-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="815cf-116">See also</span></span>

- [<span data-ttu-id="815cf-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="815cf-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="815cf-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="815cf-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
