---
title: ICorDebugCode4 arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name:
- ICorDebugCode4
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode4
helpviewer_keywords:
- ICorDebugCode4 interface [.NET Framework debugging]
ms.assetid: a3fdf523-274a-449c-920b-9fcb0aed1d97
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 30c0599e183d51030ac5b063a2aca4352ad95eca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcode4-interface"></a><span data-ttu-id="0b02a-102">ICorDebugCode4 arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b02a-102">ICorDebugCode4 Interface</span></span>
<span data-ttu-id="0b02a-103">Yerel değişkenleri ve bir işlev bağımsız değişkenleri numaralandırmak bir hata ayıklayıcısı sağlayan bir yöntem sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b02a-103">Provides a method that enables a debugger to enumerate the local variables and arguments in a function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0b02a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0b02a-104">Methods</span></span>  
  
|<span data-ttu-id="0b02a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0b02a-105">Method</span></span>|<span data-ttu-id="0b02a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b02a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0b02a-107">EnumerateVariableHomes Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b02a-107">EnumerateVariableHomes Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-enumeratevariablehomes-method.md)|<span data-ttu-id="0b02a-108">Bir numaralandırıcı bir işlevde yerel değişkenleri ve bağımsız değişkenleri alır.</span><span class="sxs-lookup"><span data-stu-id="0b02a-108">Gets an enumerator to the local variables and arguments in a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b02a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b02a-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0b02a-110">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="0b02a-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b02a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b02a-111">Requirements</span></span>  
 <span data-ttu-id="0b02a-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b02a-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b02a-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b02a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b02a-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b02a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b02a-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b02a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b02a-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0b02a-116">See Also</span></span>  
    
    
 [<span data-ttu-id="0b02a-117">ICorDebugCode3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b02a-117">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="0b02a-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0b02a-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
