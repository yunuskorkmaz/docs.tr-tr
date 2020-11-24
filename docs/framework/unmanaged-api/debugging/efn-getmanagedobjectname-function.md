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
ms.openlocfilehash: 0fb694cf85256c0f3ac5ae179e53ff504ab707e9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676211"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="bb7ac-102">\_EFN \_ getmanagedobjectname işlevi</span><span class="sxs-lookup"><span data-stu-id="bb7ac-102">\_EFN\_GetManagedObjectName Function</span></span>

<span data-ttu-id="bb7ac-103">Belirtilen yönetilen nesne işaretçisini kullanarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb7ac-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="bb7ac-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb7ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bb7ac-105">Parameters</span></span>  

 `Client`  
 <span data-ttu-id="bb7ac-106">'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="bb7ac-107">'ndaki Yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="bb7ac-108">szName</span><span class="sxs-lookup"><span data-stu-id="bb7ac-108">szName</span></span>  
 <span data-ttu-id="bb7ac-109">dışı Türün adı.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="bb7ac-110">dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb7ac-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb7ac-111">Remarks</span></span>  

 <span data-ttu-id="bb7ac-112">Şu anda bağlamda iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb7ac-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb7ac-113">Requirements</span></span>  

 <span data-ttu-id="bb7ac-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb7ac-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb7ac-115">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="bb7ac-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="bb7ac-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb7ac-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb7ac-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb7ac-117">See also</span></span>

- [<span data-ttu-id="bb7ac-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="bb7ac-118">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
