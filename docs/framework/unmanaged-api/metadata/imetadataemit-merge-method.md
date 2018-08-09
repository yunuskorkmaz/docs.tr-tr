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
ms.openlocfilehash: 98997bfbb7d3c9343f78438b1195222565c5b9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33444557"
---
# <a name="imetadataemitmerge-method"></a><span data-ttu-id="fae3f-102">IMetaDataEmit::Merge Metodu</span><span class="sxs-lookup"><span data-stu-id="fae3f-102">IMetaDataEmit::Merge Method</span></span>
<span data-ttu-id="fae3f-103">Belirtilen alınan kapsam birleştirilecek kapsamları listesine ekler.</span><span class="sxs-lookup"><span data-stu-id="fae3f-103">Adds the specified imported scope to the list of scopes to be merged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fae3f-104">Syntax</span></span>  
  
```  
HRESULT Merge (   
    [in]  IMetaDataImport  *pImport,   
    [in]  IMapToken        *pHostMapToken,   
    [in]  IUnknown         *pHandler   
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fae3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fae3f-105">Parameters</span></span>  
 `pImport`  
 <span data-ttu-id="fae3f-106">[in] Bir işaretçi bir [Imetadataımport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) birleştirilecek alınan kapsam tanımlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="fae3f-106">[in] A pointer to an [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) object that identifies the imported scope to be merged.</span></span>  
  
 `pIMap`  
 <span data-ttu-id="fae3f-107">[in] Bir işaretçi bir [Imaptoken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) belirteci yeniden eşleme belirtir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="fae3f-107">[in] A pointer to an [IMapToken](../../../../docs/framework/unmanaged-api/metadata/imaptoken-interface.md) object that specifies the token re-map.</span></span>  
  
 `pHandleer`  
 <span data-ttu-id="fae3f-108">[in] Bir işaretçi bir <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` hataları belirten nesne.</span><span class="sxs-lookup"><span data-stu-id="fae3f-108">[in] A pointer to an <!--<<!--zzxref:IUnknown --> `IUnknown`>--> `IUnknown` object that specifies the errors.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fae3f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fae3f-109">Remarks</span></span>  
 <span data-ttu-id="fae3f-110">Çağrı [Imetadataemit::mergeend](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) birleşme meta verilerin tek bir kapsam tetiklemek için.</span><span class="sxs-lookup"><span data-stu-id="fae3f-110">Call [IMetaDataEmit::MergeEnd](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-mergeend-method.md) to trigger the merger of metadata into a single scope.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae3f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fae3f-111">Requirements</span></span>  
 <span data-ttu-id="fae3f-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fae3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae3f-113">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="fae3f-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="fae3f-114">**Kitaplığı:** MSCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="fae3f-114">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fae3f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae3f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae3f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fae3f-116">See Also</span></span>  
 [<span data-ttu-id="fae3f-117">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fae3f-117">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="fae3f-118">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fae3f-118">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
