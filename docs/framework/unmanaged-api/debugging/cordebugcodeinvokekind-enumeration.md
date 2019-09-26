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
ms.openlocfilehash: 22eeb8aba318d53efbc699d4492a86b2667bcfff
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274130"
---
# <a name="cordebugcodeinvokekind-enumeration"></a><span data-ttu-id="360a8-102">CorDebugCodeInvokeKind Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="360a8-102">CorDebugCodeInvokeKind Enumeration</span></span>
<span data-ttu-id="360a8-103">Bir içe aktarılmış işlevin yönetilen kodu nasıl çağırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="360a8-103">Describes how an exported function invokes managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="360a8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="360a8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokeKind  
{  
    CODE_INVOKE_KIND_NONE,       
    CODE_INVOKE_KIND_RETURN,     
    CODE_INVOKE_KIND_TAILCALL,   
} CorDebugCodeInvokeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="360a8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="360a8-105">Members</span></span>  
  
|<span data-ttu-id="360a8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="360a8-106">Member</span></span>|<span data-ttu-id="360a8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="360a8-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_KIND_NONE`|<span data-ttu-id="360a8-108">Bu yöntem tarafından herhangi bir yönetilen kod çağrılırsa, daha sonra açık olaylar veya kesme noktaları tarafından bulunması gerekecektir.</span><span class="sxs-lookup"><span data-stu-id="360a8-108">If any managed code is invoked by this method, it will have to be located by explicit events or breakpoints later.</span></span><br /><br /> <span data-ttu-id="360a8-109">--veya--</span><span class="sxs-lookup"><span data-stu-id="360a8-109">--or--</span></span><br /><br /> <span data-ttu-id="360a8-110">Üzerinde durmanın kolay bir yolu olmadığından, bu yöntemin çağırdığı bazı yönetilen koddan bazılarını kaçırabilir.</span><span class="sxs-lookup"><span data-stu-id="360a8-110">We may just miss some of the managed code this method calls because there is no easy way to stop on it.</span></span><br /><br /> <span data-ttu-id="360a8-111">--veya--</span><span class="sxs-lookup"><span data-stu-id="360a8-111">--or--</span></span><br /><br /> <span data-ttu-id="360a8-112">Yöntemi hiçbir şekilde yönetilen kodu çağırmayabilir.</span><span class="sxs-lookup"><span data-stu-id="360a8-112">The method may never invoke managed code.</span></span>|  
|`CODE_INVOKE_KIND_RETURN`|<span data-ttu-id="360a8-113">Bu yöntem, bir dönüş yönergesi aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="360a8-113">This method will invoke managed code via a return instruction.</span></span> <span data-ttu-id="360a8-114">Adımlama, sonraki yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="360a8-114">Stepping out should arrive at the next managed code.</span></span>|  
|`CODE_INVOKE_KIND_TAILCALL`|<span data-ttu-id="360a8-115">Bu yöntem, bir tail çağrısı aracılığıyla yönetilen kodu çağırır.</span><span class="sxs-lookup"><span data-stu-id="360a8-115">This method will invoke managed code via a tail-call.</span></span> <span data-ttu-id="360a8-116">Tüm çağrı yönergelerinin tek adımlamayı ve adımlamayı yönetilen koda ulaşmalıdır.</span><span class="sxs-lookup"><span data-stu-id="360a8-116">Single-stepping and stepping over any call instructions should arrive at managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="360a8-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="360a8-117">Remarks</span></span>  
 <span data-ttu-id="360a8-118">Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="360a8-118">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="360a8-119">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="360a8-119">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="360a8-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="360a8-120">Requirements</span></span>  
 <span data-ttu-id="360a8-121">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="360a8-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="360a8-122">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="360a8-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="360a8-123">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="360a8-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="360a8-124">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="360a8-124">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="360a8-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="360a8-125">See also</span></span>

- [<span data-ttu-id="360a8-126">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="360a8-126">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="360a8-127">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="360a8-127">Debugging</span></span>](index.md)
