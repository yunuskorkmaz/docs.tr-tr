---
description: 'Daha fazla bilgi edinin: Cordebugcodeınvokeamaç numaralandırması'
title: CorDebugCodeInvokePurpose Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInvokePurpose
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 31833a2d-a0d6-48a1-b05f-995ca307a08f
topic_type:
- apiref
ms.openlocfilehash: 1402343cc15e451975567564e6ce353900454bf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801728"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="c544a-103">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="c544a-103">CorDebugCodeInvokePurpose Enumeration</span></span>

<span data-ttu-id="c544a-104">Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="c544a-104">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c544a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c544a-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="c544a-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="c544a-106">Members</span></span>  
  
|<span data-ttu-id="c544a-107">Üye</span><span class="sxs-lookup"><span data-stu-id="c544a-107">Member</span></span>|<span data-ttu-id="c544a-108">Description</span><span class="sxs-lookup"><span data-stu-id="c544a-108">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="c544a-109">Hiçbiri veya bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="c544a-109">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="c544a-110">Yönetilen kod, ters p-Invoke gibi herhangi bir yönetilen giriş noktasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c544a-110">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="c544a-111">Daha ayrıntılı bir amaç çalışma zamanı tarafından bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="c544a-111">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="c544a-112">Yönetilen kod statik bir Oluşturucu çalıştıracak.</span><span class="sxs-lookup"><span data-stu-id="c544a-112">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="c544a-113">Yönetilen kod, çağrılan bazı arabirim yöntemleri için uygulamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="c544a-113">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c544a-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c544a-114">Remarks</span></span>  

 <span data-ttu-id="c544a-115">Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c544a-115">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c544a-116">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="c544a-116">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c544a-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c544a-117">Requirements</span></span>  

 <span data-ttu-id="c544a-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c544a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c544a-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c544a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c544a-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c544a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c544a-121">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c544a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c544a-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c544a-122">See also</span></span>

- [<span data-ttu-id="c544a-123">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="c544a-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c544a-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c544a-124">Debugging</span></span>](index.md)
