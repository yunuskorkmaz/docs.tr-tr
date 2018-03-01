---
title: ICLRDebugging Arabirimi
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
- ICLRDebugging
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDebugging
helpviewer_keywords:
- ICLRDebugging interface [.NET Framework debugging]
ms.assetid: 429d8fce-b1b1-49d7-895c-28c1c1aa2dbd
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 325f6adf8fe3a357f903f0cb047a2255ef80e264
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugging-interface"></a><span data-ttu-id="7c115-102">ICLRDebugging Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c115-102">ICLRDebugging Interface</span></span>
<span data-ttu-id="7c115-103">Hata ayıklama amacıyla modülleri yükleme ve kaldırma işlemlerini yapan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="7c115-103">Provides methods that handle loading and unloading modules for debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c115-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7c115-104">Methods</span></span>  
  
|<span data-ttu-id="7c115-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7c115-105">Method</span></span>|<span data-ttu-id="7c115-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c115-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c115-107">OpenVirtualProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c115-107">OpenVirtualProcess Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)|<span data-ttu-id="7c115-108">Bir ortak dil çalışma zamanı (CLR) modülü işleminde yüklenen karşılık gelen "ICorDebugProcess" arabirimini alır.</span><span class="sxs-lookup"><span data-stu-id="7c115-108">Gets the "ICorDebugProcess" interface that corresponds to a common language runtime (CLR) module loaded in the process.</span></span>|  
|[<span data-ttu-id="7c115-109">CanUnloadNow Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7c115-109">CanUnloadNow Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-canunloadnow-method.md)|<span data-ttu-id="7c115-110">Tarafından sağlanan bir kitaplık olup olmadığını belirleyen bir [Iclrdebugginglibraryprovider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) arabirimi hala kullanımda veya kaldırılmış olabilir.</span><span class="sxs-lookup"><span data-stu-id="7c115-110">Determines whether a library that was provided by an [ICLRDebuggingLibraryProvider](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md) interface is still in use or can be unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c115-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c115-111">Remarks</span></span>  
 <span data-ttu-id="7c115-112">Bir örneği elde edebilirsiniz `ICLRDebugging` kullanarak arabirimi [Clrcreateınstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) işlevi.</span><span class="sxs-lookup"><span data-stu-id="7c115-112">You can obtain an instance of the `ICLRDebugging` interface by using the [CLRCreateInstance](../../../../docs/framework/unmanaged-api/hosting/clrcreateinstance-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c115-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c115-113">Requirements</span></span>  
 <span data-ttu-id="7c115-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c115-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c115-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c115-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c115-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c115-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c115-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c115-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c115-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c115-118">See Also</span></span>  
 [<span data-ttu-id="7c115-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c115-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="7c115-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="7c115-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
