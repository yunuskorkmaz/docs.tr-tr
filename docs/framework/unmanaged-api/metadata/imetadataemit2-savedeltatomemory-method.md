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
ms.openlocfilehash: fa95a737747e9153eb844cddd8e0684585b9108b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049979"
---
# <a name="imetadataemit2savedeltatomemory-method"></a><span data-ttu-id="26994-102">IMetaDataEmit2::SaveDeltaToMemory Yöntemi</span><span class="sxs-lookup"><span data-stu-id="26994-102">IMetaDataEmit2::SaveDeltaToMemory Method</span></span>
<span data-ttu-id="26994-103">Değişiklikleri geçerli Düzenle ve devam et oturumdan bellek kaydeder.</span><span class="sxs-lookup"><span data-stu-id="26994-103">Saves changes from the current edit-and-continue session to memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26994-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26994-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToMemory (  
    [out] void        *pbData,   
    [in]  ULONG       cbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26994-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26994-105">Parameters</span></span>  
 `pbData`  
 <span data-ttu-id="26994-106">[out] Meta veri değişim yazmaya başlanacak adresi.</span><span class="sxs-lookup"><span data-stu-id="26994-106">[out] The address at which to begin writing the metadata delta.</span></span>  
  
 `cbData`  
 <span data-ttu-id="26994-107">[in] Değişiklikleri boyutu.</span><span class="sxs-lookup"><span data-stu-id="26994-107">[in] The size of the changes.</span></span> <span data-ttu-id="26994-108">Kullanım [Imetadataemit2::getdeltasavesize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) boyutunu belirlemek için.</span><span class="sxs-lookup"><span data-stu-id="26994-108">Use [IMetaDataEmit2::GetDeltaSaveSize](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-getdeltasavesize-method.md) to determine the size.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26994-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26994-109">Requirements</span></span>  
 <span data-ttu-id="26994-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26994-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26994-111">**Üst bilgi:** COR.h</span><span class="sxs-lookup"><span data-stu-id="26994-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26994-112">**Kitaplığı:** Bir kaynak olarak MsCorEE.dll kullanılan</span><span class="sxs-lookup"><span data-stu-id="26994-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26994-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26994-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26994-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26994-114">See also</span></span>

- [<span data-ttu-id="26994-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26994-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
- [<span data-ttu-id="26994-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26994-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
