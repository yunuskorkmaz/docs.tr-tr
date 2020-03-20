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
ms.openlocfilehash: 54332f5b3383f1c1513242a79cbd81eb8aa5c4f2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179257"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="30e36-102">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="30e36-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="30e36-103">Dışa aktarılan bir işlevin yönetilen kodu nasıl çağırdığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="30e36-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e36-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30e36-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="30e36-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="30e36-105">Members</span></span>  
  
|<span data-ttu-id="30e36-106">Üye</span><span class="sxs-lookup"><span data-stu-id="30e36-106">Member</span></span>|<span data-ttu-id="30e36-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="30e36-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="30e36-108">Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekir.</span><span class="sxs-lookup"><span data-stu-id="30e36-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="30e36-109">--veya--</span><span class="sxs-lookup"><span data-stu-id="30e36-109">--or--</span></span><br /><br /> <span data-ttu-id="30e36-110">Bu yöntemin aradığı yönetilen kodun bazılarını kaçırabiliriz, çünkü bunu durdurmanın kolay bir yolu yoktur.</span><span class="sxs-lookup"><span data-stu-id="30e36-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="30e36-111">--veya--</span><span class="sxs-lookup"><span data-stu-id="30e36-111">--or--</span></span><br /><br /> <span data-ttu-id="30e36-112">Yöntem yönetilen kodu hiçbir zaman çağıramayabilir.</span><span class="sxs-lookup"><span data-stu-id="30e36-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="30e36-113">Bu yöntem, bir iade yönergesi aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="30e36-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="30e36-114">Dışarı çıkmak bir sonraki yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="30e36-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="30e36-115">Bu yöntem, bir kuyruk çağrısı ile yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="30e36-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="30e36-116">Tek adımve herhangi bir çağrı yönergeleri üzerinden adım yönetilen kod almalısınız.</span><span class="sxs-lookup"><span data-stu-id="30e36-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30e36-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="30e36-117">Remarks</span></span>  
 <span data-ttu-id="30e36-118">Bu numaralandırma, yönetilen kodüzerinden adım atma hakkında bilgi sağlamak için [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="30e36-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30e36-119">Bu numaralandırma yalnızca .NET Yerel hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="30e36-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e36-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30e36-120">Requirements</span></span>  
 <span data-ttu-id="30e36-121">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30e36-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e36-122">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30e36-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30e36-123">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30e36-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30e36-124">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30e36-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30e36-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30e36-125">See also</span></span>

- [<span data-ttu-id="30e36-126">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="30e36-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="30e36-127">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="30e36-127">Debugging</span></span>](index.md)
