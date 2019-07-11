---
title: CorDebugInternalFrameType Numaralandırması
ms.date: 03/30/2017
api_name:
- CorDebugInternalFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugInternalFrameType
helpviewer_keywords:
- CorDebugInternalFrameType enumeration [.NET Framework debugging]
ms.assetid: e4412dc2-c338-4cfb-94d8-f682095dd2b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1dcbd8bb566331a6a2d4217eeec0441fbd3e6ff6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739863"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="9b960-102">CorDebugInternalFrameType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9b960-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="9b960-103">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9b960-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="9b960-104">Bu sabit listesi tarafından kullanılan [Icordebugınternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9b960-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b960-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b960-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugInternalFrameType {  
  
    STUBFRAME_NONE                 = 0x00000000,  
    STUBFRAME_M2U                  = 0x00000001,  
    STUBFRAME_U2M                  = 0x00000002,  
    STUBFRAME_APPDOMAIN_TRANSITION = 0x00000003,  
    STUBFRAME_LIGHTWEIGHT_FUNCTION = 0x00000004,  
    STUBFRAME_FUNC_EVAL            = 0x00000005,  
    STUBFRAME_INTERNALCALL         = 0x00000006,  
    STUBFRAME_CLASS_INIT           = 0x00000007,  
    STUBFRAME_EXCEPTION            = 0x00000008,  
    STUBFRAME_SECURITY             = 0x00000009,  
    STUBFRAME_JIT_COMPILATION     = 0x0000000a,  
} CorDebugInternalFrameType;  
```  
  
## <a name="members"></a><span data-ttu-id="9b960-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="9b960-106">Members</span></span>  
  
|<span data-ttu-id="9b960-107">Üye</span><span class="sxs-lookup"><span data-stu-id="9b960-107">Member</span></span>|<span data-ttu-id="9b960-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b960-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="9b960-109">Bir null değer.</span><span class="sxs-lookup"><span data-stu-id="9b960-109">A null value.</span></span> <span data-ttu-id="9b960-110">`ICorDebugInternalFrame::GetFrameType` Yöntemi hiçbir zaman bu değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b960-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="9b960-111">Bir saplama yönetilmeyen çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="9b960-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="9b960-112">Bir saplama yönetilene çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="9b960-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="9b960-113">Uygulama etki alanları arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="9b960-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="9b960-114">Basit bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="9b960-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="9b960-115">İşlev değerlendirmesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="9b960-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="9b960-116">Ortak dil çalışma zamanı bir iç çağrı.</span><span class="sxs-lookup"><span data-stu-id="9b960-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="9b960-117">Sınıf başlatması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="9b960-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="9b960-118">Oluşturulan bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="9b960-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="9b960-119">Kod erişimi güvenliği için kullanılan bir çerçeve.</span><span class="sxs-lookup"><span data-stu-id="9b960-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="9b960-120">Çalışma zamanı JIT-derleme bir yöntem var.</span><span class="sxs-lookup"><span data-stu-id="9b960-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9b960-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b960-121">Requirements</span></span>  
 <span data-ttu-id="9b960-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b960-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b960-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b960-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b960-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b960-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b960-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b960-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b960-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b960-126">See also</span></span>

- [<span data-ttu-id="9b960-127">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9b960-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
