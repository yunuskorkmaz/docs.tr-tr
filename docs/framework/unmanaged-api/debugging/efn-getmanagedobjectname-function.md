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
ms.openlocfilehash: c7333f8f7b95655ac821e9a2977d5db3794486a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123000"
---
# <a name="_efn_getmanagedobjectname-function"></a><span data-ttu-id="b4fa0-102">\_EFN\_GetManagedObjectName Işlevi</span><span class="sxs-lookup"><span data-stu-id="b4fa0-102">\_EFN\_GetManagedObjectName Function</span></span>
<span data-ttu-id="b4fa0-103">Belirtilen yönetilen nesne işaretçisini kullanarak bir türün adını alır.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-103">Gets the name of a type using the provided managed object pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4fa0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4fa0-104">Syntax</span></span>  
  
```cpp  
HRESULT _EFN_GetManagedObjectName(  
    [in]  PDEBUG_CLIENT  Client,  
    [in]  ULONG64        objAddr,  
    [out] __out_ecount(cbName) PSTR szName,  
    [out] ULONG          cbName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4fa0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4fa0-105">Parameters</span></span>  
 `Client`  
 <span data-ttu-id="b4fa0-106">'ndaki Hata ayıklama istemcisine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-106">[in] A pointer to the debug client.</span></span>  
  
 `objAddr`  
 <span data-ttu-id="b4fa0-107">'ndaki Yönetilen nesne işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-107">[in] A managed object pointer.</span></span>  
  
 <span data-ttu-id="b4fa0-108">szName</span><span class="sxs-lookup"><span data-stu-id="b4fa0-108">szName</span></span>  
 <span data-ttu-id="b4fa0-109">dışı Türün adı.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-109">[out] The name of the type.</span></span>  
  
 `cbName`  
 <span data-ttu-id="b4fa0-110">dışı Dize arabelleğinde kullanılabilir olan karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-110">[out] The number of characters available in the string buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4fa0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4fa0-111">Remarks</span></span>  
 <span data-ttu-id="b4fa0-112">Şu anda bağlamda olan iş parçacığında yönetilen kod yoksa, işlev, bir 0xa0 tesis değeri ve 0x1000 hata kodu ile HRESULT SOS_E_NOMANAGEDCODE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-112">If there is no managed code on the thread currently in context, the function returns HRESULT SOS_E_NOMANAGEDCODE with a facility value of 0xa0 and an error code of 0x1000.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4fa0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4fa0-113">Requirements</span></span>  
 <span data-ttu-id="b4fa0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4fa0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4fa0-115">**Üst bilgi:** SOS_Stacktrace. h</span><span class="sxs-lookup"><span data-stu-id="b4fa0-115">**Header:** SOS_Stacktrace.h</span></span>  
  
 <span data-ttu-id="b4fa0-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4fa0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4fa0-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b4fa0-117">See also</span></span>

- [<span data-ttu-id="b4fa0-118">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="b4fa0-118">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
