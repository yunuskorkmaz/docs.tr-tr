---
title: IMetaDataEmit2::SaveDeltaToStream Yöntemi
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.SaveDeltaToStream
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::SaveDeltaToStream
helpviewer_keywords:
- IMetaDataEmit2::SaveDeltaToStream method [.NET Framework metadata]
- SaveDeltaToStream method [.NET Framework metadata]
ms.assetid: ecd786e8-f9a4-4190-a6ef-af18e8c6d654
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e9dfd97ce5b9b192b9a2e88e3d7e4f963d929f47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33449266"
---
# <a name="imetadataemit2savedeltatostream-method"></a><span data-ttu-id="dda79-102">IMetaDataEmit2::SaveDeltaToStream Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dda79-102">IMetaDataEmit2::SaveDeltaToStream Method</span></span>
<span data-ttu-id="dda79-103">Değişiklikleri geçerli Düzenle ve devam et oturumundan belirtilen akışa kaydeder.</span><span class="sxs-lookup"><span data-stu-id="dda79-103">Saves changes from the current edit-and-continue session to the specified stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dda79-104">Syntax</span></span>  
  
```  
HRESULT SaveDeltaToStream (  
    [in] IStream     *pIStream,   
    [in] DWORD       dwSaveFlags  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dda79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dda79-105">Parameters</span></span>  
 `pIStream`  
 <span data-ttu-id="dda79-106">[in] Değişiklikleri kaydetmek yazılabilir akış için bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="dda79-106">[in] An interface pointer to the writable stream to which to save changes.</span></span>  
  
 `dwSaveFlags`  
 <span data-ttu-id="dda79-107">[in] Ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="dda79-107">[in] Reserved.</span></span> <span data-ttu-id="dda79-108">Bu değer sıfır olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dda79-108">This value must be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda79-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dda79-109">Requirements</span></span>  
 <span data-ttu-id="dda79-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda79-111">**Başlık:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="dda79-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="dda79-112">**Kitaplığı:** MsCorEE.dll kaynak olarak kullanılır</span><span class="sxs-lookup"><span data-stu-id="dda79-112">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="dda79-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dda79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda79-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dda79-114">See Also</span></span>  
 [<span data-ttu-id="dda79-115">IMetaDataEmit2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda79-115">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)  
 [<span data-ttu-id="dda79-116">IMetaDataEmit Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dda79-116">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
