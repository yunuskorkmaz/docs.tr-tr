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
ms.openlocfilehash: e7fe5cbe27c0771a71e4c03d14ab68ada7d0741a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004198"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="e2f29-102">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2f29-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="e2f29-103">Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="e2f29-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2f29-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e2f29-104">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2f29-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2f29-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="e2f29-106">'ndaki Birleştirilecek kapsamı tanımlayan bir [IMetaDataImport](imetadataimport-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2f29-106">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="e2f29-107">'ndaki Belirteç yeniden eşlemesini belirten bir [IMapToken](imaptoken-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2f29-107">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="e2f29-108">'ndaki Hataları belirten [IUnknown](/cpp/atl/iunknown) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2f29-108">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e2f29-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e2f29-109">Remarks</span></span>  
 <span data-ttu-id="e2f29-110">Meta verilerin birleştiğini tek bir kapsamda tetiklemek için [ımetadatayayma:: MergeEnd](imetadataemit-mergeend-method.md) ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="e2f29-110">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2f29-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2f29-111">Requirements</span></span>  
 <span data-ttu-id="e2f29-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2f29-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2f29-113">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="e2f29-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="e2f29-114">**Kitaplık:** MSCorEE. dll içinde kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="e2f29-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2f29-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2f29-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2f29-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2f29-116">See also</span></span>

- [<span data-ttu-id="e2f29-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2f29-117">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="e2f29-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2f29-118">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
