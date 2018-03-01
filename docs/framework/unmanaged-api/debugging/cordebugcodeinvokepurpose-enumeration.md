---
title: "CorDebugCodeInvokePurpose Numaralandırması"
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
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e87e5d8baf3ff7c87efe8f6bd96f8fd806527363
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="a3143-102">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="a3143-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="a3143-103">Yönetilen kod neden verilen işlevi çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="a3143-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3143-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a3143-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="a3143-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="a3143-105">Members</span></span>  
  
|<span data-ttu-id="a3143-106">Üye</span><span class="sxs-lookup"><span data-stu-id="a3143-106">Member</span></span>|<span data-ttu-id="a3143-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a3143-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="a3143-108">None veya bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="a3143-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="a3143-109">Yönetilen kod ters p-invoke gibi herhangi bir yönetilen giriş noktasını çalışır.</span><span class="sxs-lookup"><span data-stu-id="a3143-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="a3143-110">Daha ayrıntılı herhangi bir amaçla çalışma zamanı tarafından bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="a3143-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="a3143-111">Yönetilen kod statik Oluşturucu çalışır.</span><span class="sxs-lookup"><span data-stu-id="a3143-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="a3143-112">Yönetilen kod çağrıldı bazı arabirim yöntemi uygulamasını çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a3143-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3143-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a3143-113">Remarks</span></span>  
 <span data-ttu-id="a3143-114">Bu numaralandırma tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi doğruluk hakkında bilgi sağlamak için yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="a3143-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a3143-115">Bu numaralandırma .NET senaryoları yalnızca hata ayıklama yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="a3143-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3143-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a3143-116">Requirements</span></span>  
 <span data-ttu-id="a3143-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3143-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3143-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a3143-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a3143-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a3143-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a3143-120">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3143-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3143-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a3143-121">See Also</span></span>  
 [<span data-ttu-id="a3143-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="a3143-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="a3143-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="a3143-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
