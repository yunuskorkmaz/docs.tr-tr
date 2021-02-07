---
description: ': Imetadatayayma:: Merge yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 6b78dd20555acf1eaf610ed05d8a37ab6cdeee5c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99745950"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="51d63-103">IMetaDataEmit::Merge Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51d63-103">IMetaDataEmit::Merge Method</span></span>

<span data-ttu-id="51d63-104">Belirtilen içeri aktarılan kapsamı birleştirilecek kapsamlar listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="51d63-104">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d63-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51d63-105">Syntax</span></span>  
  
```cpp  
HRESULT Merge (
    [in]  IMetaDataImport  *pImport,
    [in]  IMapToken        *pHostMapToken,
    [in]  IUnknown         *pHandler
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51d63-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51d63-106">Parameters</span></span>  

 `pImport`  
 <span data-ttu-id="51d63-107">'ndaki Birleştirilecek kapsamı tanımlayan bir [IMetaDataImport](imetadataimport-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51d63-107">[in] A pointer to an [IMetaDataImport](imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="51d63-108">'ndaki Belirteç yeniden eşlemesini belirten bir [IMapToken](imaptoken-interface.md) nesnesine yönelik işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51d63-108">[in] A pointer to an [IMapToken](imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandler`  
 <span data-ttu-id="51d63-109">'ndaki Hataları belirten [IUnknown](/cpp/atl/iunknown) nesnesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51d63-109">[in] A pointer to an [IUnknown](/cpp/atl/iunknown) object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51d63-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51d63-110">Remarks</span></span>  

 <span data-ttu-id="51d63-111">Meta verilerin birleştiğini tek bir kapsamda tetiklemek için [ımetadatayayma:: MergeEnd](imetadataemit-mergeend-method.md) ' i çağırın.</span><span class="sxs-lookup"><span data-stu-id="51d63-111">Call [IMetaDataEmit::MergeEnd](imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51d63-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51d63-112">Requirements</span></span>  

 <span data-ttu-id="51d63-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51d63-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d63-114">**Üst bilgi:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="51d63-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="51d63-115">**Kitaplık:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="51d63-115">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="51d63-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d63-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d63-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51d63-117">See also</span></span>

- [<span data-ttu-id="51d63-118">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51d63-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="51d63-119">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51d63-119">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
