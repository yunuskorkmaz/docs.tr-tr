---
title: _EFN_GetManagedObjectName İşlevi
ms.date: 03/30/2017
api_name:
- _EFN_GetManagedObjectName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_GetManagedObjectName
helpviewer_keywords:
- _EFN_GetManagedObjectName function [.NET Framework debugging]
ms.assetid: 6e7c6bee-7ced-495f-bf6c-2a5f0c716f7e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4a95008d98436161ac919ef307273bc797519f15
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698349"
---
# <a name="efngetmanagedobjectname-function"></a><span data-ttu-id="35de8-102">_EFN_GetManagedObjectName İşlevi</span><span class="sxs-lookup"><span data-stu-id="35de8-102">_EFN_GetManagedObjectName Function</span></span>
<span data-ttu-id="35de8-103">Belirtilen yönetilen nesne işaretçisi kullanılarak bir tür adını alır.</span><span class="sxs-lookup"><span data-stu-id="35de8-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35de8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="35de8-104">Syntax</span></span>  
  
```  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35de8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="35de8-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="35de8-106">[in] Hata ayıklama istemci için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="35de8-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="35de8-107">[in] Bir yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="35de8-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="35de8-108">szName</span><span class="sxs-lookup"><span data-stu-id="35de8-108">szName</span></span>  
 <span data-ttu-id="35de8-109">[out] Tür adı.</span><span class="sxs-lookup"><span data-stu-id="35de8-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="35de8-110">[out] Dize arabellek kullanılabilir karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="35de8-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="35de8-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="35de8-111">Remarks</span></span>  
 <span data-ttu-id="35de8-112">Varsa yönetilen kod yok iş parçacığı üzerinde şu anda bağlamında, işlev HRESULT SOS_E_NOMANAGEDCODE 0xa0 tesis değerini ve 0x1000 hata kodu ile döndürür.</span><span class="sxs-lookup"><span data-stu-id="35de8-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35de8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="35de8-113">Requirements</span></span>  
 <span data-ttu-id="35de8-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35de8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35de8-115">**Üst bilgi:** SOS_Stacktrace.h</span><span class="sxs-lookup"><span data-stu-id="35de8-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="35de8-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35de8-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35de8-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="35de8-117">See also</span></span>

- [<span data-ttu-id="35de8-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="35de8-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
