---
title: IManagedObject::GetSerializedBuffer Metodu
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
ms.openlocfilehash: a94891b91f6ac14469e18ed6840a083ce5e9d64d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516927"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="1cb86-102">IManagedObject::GetSerializedBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="1cb86-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="1cb86-103">Bu yönetilen bir nesnenin dize gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="1cb86-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cb86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1cb86-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1cb86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1cb86-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="1cb86-106">[out] Serileştirilmiş nesne bir dizeye bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1cb86-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1cb86-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1cb86-107">Remarks</span></span>  
 <span data-ttu-id="1cb86-108">`GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="1cb86-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cb86-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1cb86-109">Requirements</span></span>  
 <span data-ttu-id="1cb86-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cb86-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cb86-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1cb86-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1cb86-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1cb86-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1cb86-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cb86-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cb86-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1cb86-114">See also</span></span>
- [<span data-ttu-id="1cb86-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1cb86-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
