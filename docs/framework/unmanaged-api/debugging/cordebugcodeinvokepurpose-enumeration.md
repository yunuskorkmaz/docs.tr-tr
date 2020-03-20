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
ms.openlocfilehash: f1d4a1e08a63665a532c7aa3572f1e3f9c106ba6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179237"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="79a54-102">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="79a54-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="79a54-103">Dışa aktarılan bir işlevin yönetilen kodu neden aradığını açıklar.</span><span class="sxs-lookup"><span data-stu-id="79a54-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79a54-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="79a54-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="79a54-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="79a54-105">Members</span></span>  
  
|<span data-ttu-id="79a54-106">Üye</span><span class="sxs-lookup"><span data-stu-id="79a54-106">Member</span></span>|<span data-ttu-id="79a54-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="79a54-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="79a54-108">Hiç ya da bilinmeyen.</span><span class="sxs-lookup"><span data-stu-id="79a54-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="79a54-109">Yönetilen kod, ters p-çağırma gibi yönetilen herhangi bir giriş noktasını çalıştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="79a54-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="79a54-110">Daha ayrıntılı bir amaç çalışma süresine göre bilinmemektedir.</span><span class="sxs-lookup"><span data-stu-id="79a54-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="79a54-111">Yönetilen kod statik bir oluşturucu çalıştıracak.</span><span class="sxs-lookup"><span data-stu-id="79a54-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="79a54-112">Yönetilen kod, çağrılan bazı arabirim yöntemi için uygulamayı çalıştıracaktır.</span><span class="sxs-lookup"><span data-stu-id="79a54-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="79a54-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="79a54-113">Remarks</span></span>  
 <span data-ttu-id="79a54-114">Bu numaralandırma, yönetilen kodüzerinden adım atma hakkında bilgi sağlamak için [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="79a54-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79a54-115">Bu numaralandırma yalnızca .NET Yerel hata ayıklama senaryolarında kullanılmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="79a54-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79a54-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="79a54-116">Requirements</span></span>  
 <span data-ttu-id="79a54-117">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="79a54-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79a54-118">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79a54-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79a54-119">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79a54-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79a54-120">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79a54-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79a54-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="79a54-121">See also</span></span>

- [<span data-ttu-id="79a54-122">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="79a54-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="79a54-123">Hata ayıklama</span><span class="sxs-lookup"><span data-stu-id="79a54-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
