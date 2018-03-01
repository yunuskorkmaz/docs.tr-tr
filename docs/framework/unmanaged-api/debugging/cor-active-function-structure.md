---
title: "COR_ACTIVE_FUNCTION Yapısı"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COR_ACTIVE_FUNCTION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_ACTIVE_FUNCTION
helpviewer_keywords:
- COR_ACTIVE_FUNCTION structure [.NET Framework debugging]
ms.assetid: ed86185f-2152-459c-961f-10c06d62e83f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7bb587f485427d9fd88e2f834d844ece18d336ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="coractivefunction-structure"></a><span data-ttu-id="7ed80-102">COR_ACTIVE_FUNCTION Yapısı</span><span class="sxs-lookup"><span data-stu-id="7ed80-102">COR_ACTIVE_FUNCTION Structure</span></span>
<span data-ttu-id="7ed80-103">Bir iş parçacığının çerçevelere şu an etkin olan işlevler hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="7ed80-103">Contains information about the functions that are currently active in a thread's frames.</span></span> <span data-ttu-id="7ed80-104">Bu yapı tarafından kullanılan [Icordebugthread2::getactivefunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ed80-104">This structure is used by the [ICorDebugThread2::GetActiveFunctions](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ed80-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7ed80-105">Syntax</span></span>  
  
```  
typedef struct  _COR_ACTIVE_FUNCTION {  
    ICorDebugAppDomain   *pAppDomain;  
    ICorDebugModule      *pModule;  
    ICorDebugFunction2   *pFunction;  
    ULONG32              ilOffset;  
    ULONG32              flags;  
} COR_ACTIVE_FUNCTION;  
```  
  
## <a name="members"></a><span data-ttu-id="7ed80-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7ed80-106">Members</span></span>  
  
|<span data-ttu-id="7ed80-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7ed80-107">Member</span></span>|<span data-ttu-id="7ed80-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ed80-108">Description</span></span>|  
|------------|-----------------|  
|`pAppDomain`|<span data-ttu-id="7ed80-109">Uygulama etki alanı sahibi işaretçi `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="7ed80-109">Pointer to the application domain owner of the `ilOffset` field.</span></span>|  
|`pModule`|<span data-ttu-id="7ed80-110">Modül sahibi işaretçi `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="7ed80-110">Pointer to the module owner of the `ilOffset` field.</span></span>|  
|`pFunction`|<span data-ttu-id="7ed80-111">İşaretçi işlevi sahibine `ilOffset` alan.</span><span class="sxs-lookup"><span data-stu-id="7ed80-111">Pointer to the function owner of the `ilOffset` field.</span></span>|  
|`ilOffset`|<span data-ttu-id="7ed80-112">Çerçeve Microsoft Ara dili (MSIL) uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="7ed80-112">The Microsoft intermediate language (MSIL) offset of the frame.</span></span>|  
|`flags`|<span data-ttu-id="7ed80-113">Gelecekteki genişletilebilirliği için ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="7ed80-113">Reserved for future extensibility.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7ed80-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ed80-114">Requirements</span></span>  
 <span data-ttu-id="7ed80-115">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ed80-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ed80-116">**Başlık:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="7ed80-116">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="7ed80-117">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ed80-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ed80-118">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ed80-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ed80-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7ed80-119">See Also</span></span>  
 [<span data-ttu-id="7ed80-120">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="7ed80-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="7ed80-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7ed80-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
