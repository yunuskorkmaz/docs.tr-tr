---
title: ICorDebugDebugEvent::GetThread Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: faf1ace6c65f38e9a1d5b958b633c95dbcd3dcf8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="8cba9-102">ICorDebugDebugEvent::GetThread Metodu</span><span class="sxs-lookup"><span data-stu-id="8cba9-102">ICorDebugDebugEvent::GetThread Method</span></span>
<span data-ttu-id="8cba9-103">Olayın oluştuğu iş parçacığı alır.</span><span class="sxs-lookup"><span data-stu-id="8cba9-103">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cba9-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8cba9-104">Syntax</span></span>  
  
```  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8cba9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8cba9-105">Parameters</span></span>  
 <span data-ttu-id="8cba9-106">ppThread</span><span class="sxs-lookup"><span data-stu-id="8cba9-106">ppThread</span></span>  
 <span data-ttu-id="8cba9-107">[out] Bir işaretçi adresine Icordebugthread nesnenin olayın oluştuğu iş parçacığı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8cba9-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8cba9-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8cba9-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8cba9-109">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8cba9-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cba9-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8cba9-110">Requirements</span></span>  
 <span data-ttu-id="8cba9-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8cba9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8cba9-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8cba9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8cba9-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8cba9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8cba9-114">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8cba9-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cba9-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8cba9-115">See Also</span></span>  
 [<span data-ttu-id="8cba9-116">ICorDebugDebugEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8cba9-116">ICorDebugDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 [<span data-ttu-id="8cba9-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8cba9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
