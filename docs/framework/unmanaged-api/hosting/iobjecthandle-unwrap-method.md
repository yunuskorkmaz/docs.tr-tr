---
title: IObjectHandle::Unwrap Yöntemi
ms.date: 03/30/2017
api_name:
- IObjectHandle.Unwrap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Unwrap
helpviewer_keywords:
- Unwrap method [.NET Framework hosting]
- IObjectHandle::Unwrap method [.NET Framework hosting]
ms.assetid: 794c6f8e-ed58-416b-b756-e864f2c958f7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4c18607d5373b415228846350a3dd0637ade1b45
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150806"
---
# <a name="iobjecthandleunwrap-method"></a><span data-ttu-id="da33e-102">IObjectHandle::Unwrap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da33e-102">IObjectHandle::Unwrap Method</span></span>
<span data-ttu-id="da33e-103">Yöneltme değere göre sıralama nesneden açar.</span><span class="sxs-lookup"><span data-stu-id="da33e-103">Unwraps a marshal-by-value object from indirection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da33e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da33e-104">Syntax</span></span>  
  
```  
HRESULT Unwrap (  
    [out, retval] VARIANT *ppv  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da33e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da33e-105">Parameters</span></span>  
 `ppv`  
 <span data-ttu-id="da33e-106">[out] Sarmalanmış halden çıkarılması nesneye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="da33e-106">[out] A pointer to the object to be unwrapped.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da33e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da33e-107">Requirements</span></span>  
 <span data-ttu-id="da33e-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da33e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da33e-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da33e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da33e-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="da33e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="da33e-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="da33e-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
