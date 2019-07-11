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
ms.openlocfilehash: 65ac35e254368b53ac2751e84be7dfe052fa0b53
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67749075"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="0b587-102">IManagedObject::GetSerializedBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b587-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="0b587-103">Bu yönetilen bir nesnenin dize gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="0b587-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b587-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b587-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b587-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b587-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="0b587-106">[out] Serileştirilmiş nesne bir dizeye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0b587-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b587-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b587-107">Remarks</span></span>  
 <span data-ttu-id="0b587-108">`GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="0b587-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b587-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b587-109">Requirements</span></span>  
 <span data-ttu-id="0b587-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b587-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b587-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0b587-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b587-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0b587-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b587-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b587-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b587-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b587-114">See also</span></span>

- [<span data-ttu-id="0b587-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b587-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
