---
title: ICorDebugHeapValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb130f11975eb95db7807126d6f163425439b0c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914907"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="ee811-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ee811-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="ee811-103">Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="ee811-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee811-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ee811-104">Methods</span></span>  
  
|<span data-ttu-id="ee811-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ee811-105">Method</span></span>|<span data-ttu-id="ee811-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ee811-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee811-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee811-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="ee811-108">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="ee811-108">Not implemented.</span></span>|  
|[<span data-ttu-id="ee811-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ee811-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="ee811-110">Tarafından `ICorDebugHeapValue` temsil edilen nesnenin geçerli olup olmadığını veya çöp toplayıcı tarafından geri kazanıldığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="ee811-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="ee811-111">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ee811-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee811-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ee811-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee811-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="ee811-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee811-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ee811-114">Requirements</span></span>  
 <span data-ttu-id="ee811-115">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee811-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee811-116">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ee811-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee811-117">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ee811-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee811-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee811-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee811-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ee811-119">See also</span></span>

- [<span data-ttu-id="ee811-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ee811-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
