---
title: CorDebugCodeInvokeKind Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugCodeInvokeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: e795e6a2-1008-4a81-af88-d777888e942e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3b4906f988d09f7b01aee40e8f63b589da5f33d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086422"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="46adc-102">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="46adc-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="46adc-103">Dışarı aktarılan bir işlevin yönetilen kod nasıl çağırır açıklar.</span><span class="sxs-lookup"><span data-stu-id="46adc-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46adc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="46adc-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="46adc-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="46adc-105">Members</span></span>  
  
|<span data-ttu-id="46adc-106">Üye</span><span class="sxs-lookup"><span data-stu-id="46adc-106">Member</span></span>|<span data-ttu-id="46adc-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="46adc-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="46adc-108">Herhangi bir yönetilen kod tarafından bu yöntemi çağrılırsa, açık olayları veya kesme noktaları tarafından daha sonra yer alması gerekir.</span><span class="sxs-lookup"><span data-stu-id="46adc-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="46adc-109">--veya--</span><span class="sxs-lookup"><span data-stu-id="46adc-109">--or--</span></span><br /><br /> <span data-ttu-id="46adc-110">Biz yalnızca bazı üzerinde durdurmak için kolay bir yolu yoktur çünkü bu yöntemi çağırır. yönetilen kodun kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="46adc-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="46adc-111">--veya--</span><span class="sxs-lookup"><span data-stu-id="46adc-111">--or--</span></span><br /><br /> <span data-ttu-id="46adc-112">Yöntemi, yönetilen kod asla çağırabilir.</span><span class="sxs-lookup"><span data-stu-id="46adc-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="46adc-113">Bu yöntem dönüş yönerge aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="46adc-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="46adc-114">Adımlama sonraki yönetilen koda ulaşacak.</span><span class="sxs-lookup"><span data-stu-id="46adc-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="46adc-115">Bir kuyruk çağrısı aracılığıyla yönetilen kodu bu yöntemi çağırır.</span><span class="sxs-lookup"><span data-stu-id="46adc-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="46adc-116">Tek adımlama ve herhangi bir Adımlama yönetilen koda çağrı yönergeleri ulaşacak.</span><span class="sxs-lookup"><span data-stu-id="46adc-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46adc-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="46adc-117">Remarks</span></span>  
 <span data-ttu-id="46adc-118">Bu sabit listesi tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi üzerinden Adımlama hakkında bilgi sağlamak için yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="46adc-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="46adc-119">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="46adc-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46adc-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="46adc-120">Requirements</span></span>  
 <span data-ttu-id="46adc-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46adc-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46adc-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46adc-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46adc-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46adc-123">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="46adc-124">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="46adc-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="46adc-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="46adc-125">See also</span></span>

- [<span data-ttu-id="46adc-126">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="46adc-126">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="46adc-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="46adc-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
