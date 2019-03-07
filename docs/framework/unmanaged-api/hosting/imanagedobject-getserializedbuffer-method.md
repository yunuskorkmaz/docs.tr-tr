---
title: IManagedObject::GetSerializedBuffer Yöntemi
ms.date: 03/30/2017
api_name:
- IManagedObject.GetSerializedBuffer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetSerializedBuffer
helpviewer_keywords:
- IManagedObject::GetSerializedBuffer method [.NET Framework hosting]
- GetSerializedBuffer method [.NET Framework hosting]
ms.assetid: c17105bb-b49f-434e-8f9b-77f8c85b9220
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7930e993640e1ae88ce65b6c2025a5b62a0d0999
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57502468"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="1dd8d-102">IManagedObject::GetSerializedBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1dd8d-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="1dd8d-103">Bu yönetilen bir nesnenin dize gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="1dd8d-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1dd8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1dd8d-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1dd8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1dd8d-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="1dd8d-106">[out] Serileştirilmiş nesne bir dizeye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1dd8d-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1dd8d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1dd8d-107">Remarks</span></span>  
 <span data-ttu-id="1dd8d-108">`GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="1dd8d-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1dd8d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1dd8d-109">Requirements</span></span>  
 <span data-ttu-id="1dd8d-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1dd8d-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1dd8d-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1dd8d-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1dd8d-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1dd8d-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1dd8d-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1dd8d-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1dd8d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1dd8d-114">See also</span></span>
- [<span data-ttu-id="1dd8d-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1dd8d-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
