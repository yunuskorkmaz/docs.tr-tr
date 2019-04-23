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
ms.openlocfilehash: 05184ceb3b32eb003951fff5cfdfbfb813992552
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216060"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="3b29b-102">CorDebugInternalFrameType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="3b29b-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="3b29b-103">Yığın çerçevesinin türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3b29b-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="3b29b-104">Bu sabit listesi tarafından kullanılan [Icordebugınternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="3b29b-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b29b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3b29b-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="3b29b-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="3b29b-106">Members</span></span>  
  
|<span data-ttu-id="3b29b-107">Üye</span><span class="sxs-lookup"><span data-stu-id="3b29b-107">Member</span></span>|<span data-ttu-id="3b29b-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b29b-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="3b29b-109">Bir null değer.</span><span class="sxs-lookup"><span data-stu-id="3b29b-109">A null value.</span></span> <span data-ttu-id="3b29b-110">`ICorDebugInternalFrame::GetFrameType` Yöntemi hiçbir zaman bu değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="3b29b-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="3b29b-111">Bir saplama yönetilmeyen çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="3b29b-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="3b29b-112">Bir saplama yönetilene çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="3b29b-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="3b29b-113">Uygulama etki alanları arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="3b29b-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="3b29b-114">Basit bir yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="3b29b-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="3b29b-115">İşlev değerlendirmesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="3b29b-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="3b29b-116">Ortak dil çalışma zamanı bir iç çağrı.</span><span class="sxs-lookup"><span data-stu-id="3b29b-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="3b29b-117">Sınıf başlatması başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="3b29b-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="3b29b-118">Oluşturulan bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="3b29b-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="3b29b-119">Kod erişimi güvenliği için kullanılan bir çerçeve.</span><span class="sxs-lookup"><span data-stu-id="3b29b-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="3b29b-120">Çalışma zamanı JIT-derleme bir yöntem var.</span><span class="sxs-lookup"><span data-stu-id="3b29b-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3b29b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b29b-121">Requirements</span></span>  
 <span data-ttu-id="3b29b-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b29b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b29b-123">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b29b-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b29b-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b29b-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b29b-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b29b-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b29b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b29b-126">See also</span></span>

- [<span data-ttu-id="3b29b-127">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="3b29b-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
