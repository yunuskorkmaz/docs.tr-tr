---
description: 'Şu konuda daha fazla bilgi edinin: IManagedObject:: GetSerializedBuffer yöntemi'
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
ms.openlocfilehash: f324b6ed1e9cea21fec9027a954fbad54174dd0c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753776"
---
# <a name="imanagedobjectgetserializedbuffer-method"></a><span data-ttu-id="50db3-103">IManagedObject::GetSerializedBuffer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="50db3-103">IManagedObject::GetSerializedBuffer Method</span></span>

<span data-ttu-id="50db3-104">Bu yönetilen nesnenin dize temsilini alır.</span><span class="sxs-lookup"><span data-stu-id="50db3-104">Gets the string representation of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50db3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="50db3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSerializedBuffer (  
    [out] BSTR *pBSTR  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50db3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="50db3-106">Parameters</span></span>  

 `pBSTR`  
 <span data-ttu-id="50db3-107">dışı Serileştirilmiş nesne olan dize işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="50db3-107">[out] A pointer to a string that is the serialized object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50db3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="50db3-108">Remarks</span></span>  

 <span data-ttu-id="50db3-109">`GetSerializedBuffer`Yöntemi, istemciye sıralanabilmesi için nesneyi seri hale getirir.</span><span class="sxs-lookup"><span data-stu-id="50db3-109">The `GetSerializedBuffer` method serializes the object so it can be marshaled to the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50db3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="50db3-110">Requirements</span></span>  

 <span data-ttu-id="50db3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50db3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50db3-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="50db3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="50db3-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="50db3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="50db3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50db3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50db3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="50db3-115">See also</span></span>

- [<span data-ttu-id="50db3-116">IManagedObject Arabirimi</span><span class="sxs-lookup"><span data-stu-id="50db3-116">IManagedObject Interface</span></span>](imanagedobject-interface.md)
