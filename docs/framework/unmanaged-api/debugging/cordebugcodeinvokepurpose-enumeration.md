---
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
ms.openlocfilehash: 2e59d02093b9c2e2bda72c45de25975cbbdb7a29
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82796021"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="855e8-102">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="855e8-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="855e8-103">Bir içe aktarılmış işlevin neden yönetilen kodu çağırıyor olduğunu açıklar.</span><span class="sxs-lookup"><span data-stu-id="855e8-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="855e8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="855e8-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="855e8-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="855e8-105">Members</span></span>  
  
|<span data-ttu-id="855e8-106">Üye</span><span class="sxs-lookup"><span data-stu-id="855e8-106">Member</span></span>|<span data-ttu-id="855e8-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="855e8-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="855e8-108">Hiçbiri veya bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="855e8-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="855e8-109">Yönetilen kod, ters p-Invoke gibi herhangi bir yönetilen giriş noktasını çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="855e8-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="855e8-110">Daha ayrıntılı bir amaç çalışma zamanı tarafından bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="855e8-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="855e8-111">Yönetilen kod statik bir Oluşturucu çalıştıracak.</span><span class="sxs-lookup"><span data-stu-id="855e8-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="855e8-112">Yönetilen kod, çağrılan bazı arabirim yöntemleri için uygulamayı çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="855e8-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="855e8-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="855e8-113">Remarks</span></span>  
 <span data-ttu-id="855e8-114">Bu numaralandırma, yönetilen kod üzerinden atlama hakkında bilgi sağlamak için [ICorDebugProcess6:: GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="855e8-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="855e8-115">Bu numaralandırma yalnızca .NET Native hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="855e8-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="855e8-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="855e8-116">Requirements</span></span>  
 <span data-ttu-id="855e8-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="855e8-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="855e8-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="855e8-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="855e8-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="855e8-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="855e8-120">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="855e8-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="855e8-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="855e8-121">See also</span></span>

- [<span data-ttu-id="855e8-122">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="855e8-122">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="855e8-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="855e8-123">Debugging</span></span>](index.md)
