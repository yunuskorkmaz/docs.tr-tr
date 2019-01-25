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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4eeecc3b1c248f4f0bf4372801f6bc71a22f260
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662238"
---
# <a name="cordebugcodeinvokepurpose-enumeration"></a><span data-ttu-id="72df0-102">CorDebugCodeInvokePurpose Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="72df0-102">CorDebugCodeInvokePurpose Enumeration</span></span>
<span data-ttu-id="72df0-103">Neden yönetilen kod dışa aktarılan bir işlevin çağrıları açıklar.</span><span class="sxs-lookup"><span data-stu-id="72df0-103">Describes why an exported function calls managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72df0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72df0-104">Syntax</span></span>  
  
```  
typedef enum CorDebugCodeInvokePurpose  
{  
    CODE_INVOKE_PURPOSE_NONE,  
    CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION,    
    CODE_INVOKE_PURPOSE_CLASS_INIT,  
    CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH,  
} CorDebugCodeInvokePurpose;  
```  
  
## <a name="members"></a><span data-ttu-id="72df0-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="72df0-105">Members</span></span>  
  
|<span data-ttu-id="72df0-106">Üye</span><span class="sxs-lookup"><span data-stu-id="72df0-106">Member</span></span>|<span data-ttu-id="72df0-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72df0-107">Description</span></span>|  
|------------|-----------------|  
|`CODE_INVOKE_PURPOSE_NONE`|<span data-ttu-id="72df0-108">Yok veya bilinmeyen.</span><span class="sxs-lookup"><span data-stu-id="72df0-108">None or unknown.</span></span>|  
|`CODE_INVOKE_PURPOSE_NATIVE_TO_MANAGED_TRANSITION`|<span data-ttu-id="72df0-109">Yönetilen kod ters p-invoke gibi herhangi bir yönetilen giriş noktasını çalışır.</span><span class="sxs-lookup"><span data-stu-id="72df0-109">The managed code will run any managed entry point, such as a reverse p-invoke.</span></span> <span data-ttu-id="72df0-110">Daha ayrıntılı herhangi bir amaç, çalışma zamanı tarafından bilinmiyor.</span><span class="sxs-lookup"><span data-stu-id="72df0-110">Any more detailed purpose is unknown by the runtime.</span></span>|  
|`CODE_INVOKE_PURPOSE_CLASS_INIT`|<span data-ttu-id="72df0-111">Yönetilen kod, bir statik Oluşturucu çalışır.</span><span class="sxs-lookup"><span data-stu-id="72df0-111">The managed code will run a static constructor.</span></span>|  
|`CODE_INVOKE_PURPOSE_INTERFACE_DISPATCH`|<span data-ttu-id="72df0-112">Yönetilen kod çağrıldı bazı arabirim yöntemi için uygulama çalışır.</span><span class="sxs-lookup"><span data-stu-id="72df0-112">The managed code will run the implementation for some interface method that was called.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72df0-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="72df0-113">Remarks</span></span>  
 <span data-ttu-id="72df0-114">Bu sabit listesi tarafından kullanılan [Icordebugprocess6::getexportstepınfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) yöntemi üzerinden Adımlama hakkında bilgi sağlamak için yönetilen kod.</span><span class="sxs-lookup"><span data-stu-id="72df0-114">This enumeration is used by the [ICorDebugProcess6::GetExportStepInfo](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-getexportstepinfo-method.md) method to provide information about stepping through managed code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72df0-115">Bu numaralandırma .NET hata ayıklama senaryoları yalnızca yerel olarak kullanıma yöneliktir.</span><span class="sxs-lookup"><span data-stu-id="72df0-115">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72df0-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72df0-116">Requirements</span></span>  
 <span data-ttu-id="72df0-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72df0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72df0-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="72df0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72df0-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="72df0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72df0-120">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72df0-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72df0-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72df0-121">See also</span></span>
- [<span data-ttu-id="72df0-122">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="72df0-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="72df0-123">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="72df0-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
