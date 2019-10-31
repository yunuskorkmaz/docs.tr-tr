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
ms.openlocfilehash: 4a55ae265230c4da3cc0a19b06a7597be8661beb
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103254"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="0e3e1-102">IManagedObject::GetSerializedBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e3e1-102">IManagedObject::GetSerializedBuffer Method</span></span>
<span data-ttu-id="0e3e1-103">Bu yönetilen nesnenin dize temsilini alır.</span><span class="sxs-lookup"><span data-stu-id="0e3e1-103">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e3e1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e3e1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e3e1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e3e1-105">Parameters</span></span>  
 `pBSTR`  
 <span data-ttu-id="0e3e1-106">dışı Serileştirilmiş nesne olan dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="0e3e1-106">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e3e1-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e3e1-107">Remarks</span></span>  
 <span data-ttu-id="0e3e1-108">`GetSerializedBuffer` yöntemi, istemciye sıralanabilmesi için nesneyi seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="0e3e1-108">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e3e1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e3e1-109">Requirements</span></span>  
 <span data-ttu-id="0e3e1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e3e1-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e3e1-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e3e1-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e3e1-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0e3e1-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e3e1-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e3e1-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e3e1-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e3e1-114">See also</span></span>

- [<span data-ttu-id="0e3e1-115">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e3e1-115">IManagedObject Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)
