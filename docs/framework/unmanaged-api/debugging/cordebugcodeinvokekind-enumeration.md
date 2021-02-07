---
description: 'Hakkında daha fazla bilgi edinin: Cordebugcodeınvokekind numaralandırması'
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
ms.openlocfilehash: d3fc3fe6f7568adcb2d1bbbe18c98d9d84bac337
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747094"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="1f187-103">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="1f187-103">CorDebugCodeInvokeKind Enumeration</span></span>

<span data-ttu-id="1f187-104">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="1f187-104">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f187-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1f187-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,
    CODE_INVOKE_KIND_RETURN,
    CODE_INVOKE_KIND_TAILCALL,
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="1f187-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="1f187-106">Members</span></span>  
  
|<span data-ttu-id="1f187-107">Üye</span><span class="sxs-lookup"><span data-stu-id="1f187-107">Member</span></span>|<span data-ttu-id="1f187-108">Description</span><span class="sxs-lookup"><span data-stu-id="1f187-108">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="1f187-109">Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="1f187-109">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="1f187-110">--veya--</span><span class="sxs-lookup"><span data-stu-id="1f187-110">--or--</span></span><br /><br /> <span data-ttu-id="1f187-111">Üzerinde durmanın kolay bir yolu olmadığından, bu yöntemin çağırdığı bazı yönetilen koddan bazılarını kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="1f187-111">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="1f187-112">--veya--</span><span class="sxs-lookup"><span data-stu-id="1f187-112">--or--</span></span><br /><br /> <span data-ttu-id="1f187-113">Yöntemi hiçbir şekilde yönetilen kodu çağırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="1f187-113">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="1f187-114">Bu yöntem, bir dönüş yönergesi aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f187-114">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="1f187-115">Adımlama, sonraki yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f187-115">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="1f187-116">Bu yöntem, bir tail çağrısı aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="1f187-116">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="1f187-117">Tüm çağrı yönergelerinin tek adımlamayı ve adımlamayı yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="1f187-117">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f187-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f187-118">Remarks</span></span>  

 <span data-ttu-id="1f187-119">Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="1f187-119">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1f187-120">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="1f187-120">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f187-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f187-121">Requirements</span></span>  

 <span data-ttu-id="1f187-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f187-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f187-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1f187-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f187-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1f187-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f187-125">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f187-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f187-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f187-126">See also</span></span>

- [<span data-ttu-id="1f187-127">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="1f187-127">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="1f187-128">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="1f187-128">Debugging</span></span>](index.md)
