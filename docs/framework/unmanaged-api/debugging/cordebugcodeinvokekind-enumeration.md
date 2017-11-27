---
title: "CorDebugCodeInvokeKind Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugCodeInvokeKind
api_location: mscordbi.dll
api_type: COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d46a47c7c655a960224bb836be0ea37cd07c8038
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="19d04-102">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="19d04-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="19d04-103">Yönetilen kod nasıl verilen işlevi çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="19d04-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d04-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="19d04-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="19d04-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="19d04-105">Members</span></span>  
  
|<span data-ttu-id="19d04-106">Üye</span><span class="sxs-lookup"><span data-stu-id="19d04-106">Member</span></span>|<span data-ttu-id="19d04-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="19d04-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="19d04-108">Bu yöntem tarafından yönetilen kod çağrılırsa, açık olayları veya kesme noktaları tarafından daha sonra bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="19d04-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="19d04-109">--veya--</span><span class="sxs-lookup"><span data-stu-id="19d04-109">--or--</span></span><br /><br /> <span data-ttu-id="19d04-110">Biz yalnızca üzerinde durdurmak için kolay bir yolu olduğundan bu yöntemi çağırır yönetilen kod bazıları kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="19d04-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="19d04-111">--veya--</span><span class="sxs-lookup"><span data-stu-id="19d04-111">--or--</span></span><br /><br /> <span data-ttu-id="19d04-112">Yöntemi, hiçbir zaman yönetilen kod çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="19d04-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="19d04-113">Bu yöntemin dönüş yönergesi aracılığıyla yönetilen koda çağıracaktır.</span><span class="sxs-lookup"><span data-stu-id="19d04-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="19d04-114">Atlama sonraki yönetilen koda ulaşması.</span><span class="sxs-lookup"><span data-stu-id="19d04-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="19d04-115">Bu yöntem, yönetilen kodu bir kuyruk çağrısı aracılığıyla çağırır.</span><span class="sxs-lookup"><span data-stu-id="19d04-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="19d04-116">Tek atlama ve herhangi bir Adımlama çağrısı yönergeleri yönetilen kodu ulaşması.</span><span class="sxs-lookup"><span data-stu-id="19d04-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19d04-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="19d04-117">Remarks</span></span>  
 <span data-ttu-id="19d04-118">Bu numaralandırma tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi doğruluk hakkında bilgi sağlamak için yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="19d04-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="19d04-119">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="19d04-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19d04-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="19d04-120">Requirements</span></span>  
 <span data-ttu-id="19d04-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d04-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d04-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="19d04-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="19d04-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19d04-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19d04-124">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19d04-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d04-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="19d04-125">See Also</span></span>  
 [<span data-ttu-id="19d04-126">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="19d04-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="19d04-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="19d04-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
