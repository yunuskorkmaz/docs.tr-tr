---
title: IMetaDataEmit2::SaveDeltaToMemory Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToMemory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToMemory
helpviewer_keywords:
- SaveDeltaToMemory method [.NET Framework metadata]
- IMetaDataEmit2::SaveDeltaToMemory method [.NET Framework metadata]
ms.assetid: e2146726-0084-4c9e-a2d2-e8d461b13b21
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 84972388f90ea23032ed0524723d59077c732e59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498901"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="c12b0-102">IMetaDataEmit2::SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c12b0-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="c12b0-103">Değişiklikleri geçerli Düzenle ve devam et oturumdan bellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="c12b0-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c12b0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c12b0-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c12b0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c12b0-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="c12b0-106">[out] Meta veri değişim yazmaya başlanacak adresi.</span><span class="sxs-lookup"><span data-stu-id="c12b0-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="c12b0-107">[in] Değişiklikleri boyutu.</span><span class="sxs-lookup"><span data-stu-id="c12b0-107">[in] The size of the changes.</span></span> <span data-ttu-id="c12b0-108">Kullanım [Imetadataemit2::getdeltasavesize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) boyutunu belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="c12b0-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c12b0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c12b0-109">Requirements</span></span>  
 <span data-ttu-id="c12b0-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c12b0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c12b0-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="c12b0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c12b0-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="c12b0-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c12b0-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c12b0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c12b0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c12b0-114">See also</span></span>
- [<span data-ttu-id="c12b0-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c12b0-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="c12b0-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c12b0-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
