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
ms.openlocfilehash: 53e8180fb55336eb05d0737110fd2fe07a4c5894
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441607"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="9a5fe-102">IManagedObject::GetSerializedBuffer Metodu</span><span class="sxs-lookup"><span data-stu-id="9a5fe-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="9a5fe-103">Bu yönetilen nesne dize gösterimini alır.</span><span class="sxs-lookup"><span data-stu-id="9a5fe-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a5fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9a5fe-104">Syntax</span></span>  
  
```  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a5fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9a5fe-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="9a5fe-106">[out] Serileştirilmiş nesne olan bir dize için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9a5fe-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9a5fe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9a5fe-107">Remarks</span></span>  
 <span data-ttu-id="9a5fe-108">`GetSerializedBuffer` Yöntemi istemciye sıralanabilir şekilde nesneyi serileştirir.</span><span class="sxs-lookup"><span data-stu-id="9a5fe-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9a5fe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9a5fe-109">Requirements</span></span>  
 <span data-ttu-id="9a5fe-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a5fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a5fe-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9a5fe-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9a5fe-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9a5fe-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9a5fe-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a5fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a5fe-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9a5fe-114">See Also</span></span>  
 [<span data-ttu-id="9a5fe-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9a5fe-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
