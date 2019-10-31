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
ms.openlocfilehash: cc839e9b2a28dc428ae7cc87c9d080c4b7612a9d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73098877"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="bdefb-102">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bdefb-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="bdefb-103">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="bdefb-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdefb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdefb-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="bdefb-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bdefb-105">Members</span></span>  
  
|<span data-ttu-id="bdefb-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bdefb-106">Member</span></span>|<span data-ttu-id="bdefb-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bdefb-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="bdefb-108">Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="bdefb-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="bdefb-109">--veya--</span><span class="sxs-lookup"><span data-stu-id="bdefb-109">--or--</span></span><br /><br /> <span data-ttu-id="bdefb-110">Üzerinde durmanın kolay bir yolu olmadığından, bu yöntemin çağırdığı bazı yönetilen koddan bazılarını kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="bdefb-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="bdefb-111">--veya--</span><span class="sxs-lookup"><span data-stu-id="bdefb-111">--or--</span></span><br /><br /> <span data-ttu-id="bdefb-112">Yöntemi hiçbir şekilde yönetilen kodu çağırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="bdefb-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="bdefb-113">Bu yöntem, bir dönüş yönergesi aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="bdefb-114">Adımlama, sonraki yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="bdefb-115">Bu yöntem, bir tail çağrısı aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="bdefb-116">Tüm çağrı yönergelerinin tek adımlamayı ve adımlamayı yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bdefb-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdefb-117">Remarks</span></span>  
 <span data-ttu-id="bdefb-118">Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bdefb-119">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="bdefb-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdefb-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdefb-120">Requirements</span></span>  
 <span data-ttu-id="bdefb-121">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdefb-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdefb-122">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="bdefb-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bdefb-123">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="bdefb-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdefb-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdefb-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdefb-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bdefb-125">See also</span></span>

- [<span data-ttu-id="bdefb-126">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bdefb-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="bdefb-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="bdefb-127">Debugging</span></span>](index.md)
