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
ms.openlocfilehash: 49b42a7fc54af56149b602b337e4a6c853c270cd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33406363"
---
# <a name="cordebuginternalframetype-enumeration"></a><span data-ttu-id="bc2d0-102">CorDebugInternalFrameType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bc2d0-102">CorDebugInternalFrameType Enumeration</span></span>
<span data-ttu-id="bc2d0-103">Yığın çerçevesi türünü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-103">Identifies the type of stack frame.</span></span> <span data-ttu-id="bc2d0-104">Bu numaralandırma tarafından kullanılan [Icordebugınternalframe::getframetype](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-104">This enumeration is used by the [ICorDebugInternalFrame::GetFrameType](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-getframetype-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc2d0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bc2d0-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="bc2d0-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bc2d0-106">Members</span></span>  
  
|<span data-ttu-id="bc2d0-107">Üye</span><span class="sxs-lookup"><span data-stu-id="bc2d0-107">Member</span></span>|<span data-ttu-id="bc2d0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bc2d0-108">Description</span></span>|  
|------------|-----------------|  
|`STUBFRAME_NONE`|<span data-ttu-id="bc2d0-109">Bir null değer.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-109">A null value.</span></span> <span data-ttu-id="bc2d0-110">`ICorDebugInternalFrame::GetFrameType` Yöntemi, hiçbir zaman bu değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-110">The `ICorDebugInternalFrame::GetFrameType` method never returns this value.</span></span>|  
|`STUBFRAME_M2U`|<span data-ttu-id="bc2d0-111">Yönetilmeyen saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-111">A managed-to-unmanaged stub frame.</span></span>|  
|`STUBFRAME_U2M`|<span data-ttu-id="bc2d0-112">Bir yönetilen için yönetilmeyen saplama çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-112">An unmanaged-to-managed stub frame.</span></span>|  
|`STUBFRAME_APPDOMAIN_TRANSITION`|<span data-ttu-id="bc2d0-113">Uygulama etki alanları arasında geçiş.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-113">A transition between application domains.</span></span>|  
|`STUBFRAME_LIGHTWEIGHT_FUNCTION`|<span data-ttu-id="bc2d0-114">Basit yöntem çağrısı.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-114">A lightweight method call.</span></span>|  
|`STUBFRAME_FUNC_EVAL`|<span data-ttu-id="bc2d0-115">İşlev değerlendirmesi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-115">The start of function evaluation.</span></span>|  
|`STUBFRAME_INTERNALCALL`|<span data-ttu-id="bc2d0-116">Ortak dil çalışma zamanı iç çağrısından.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-116">An internal call into the common language runtime.</span></span>|  
|`STUBFRAME_CLASS_INIT`|<span data-ttu-id="bc2d0-117">Bir sınıf başlatma başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-117">The start of a class initialization.</span></span>|  
|`STUBFRAME_EXCEPTION`|<span data-ttu-id="bc2d0-118">Oluşturulan bir özel durum.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-118">An exception that is thrown.</span></span>|  
|`STUBFRAME_SECURITY`|<span data-ttu-id="bc2d0-119">Kod erişim güvenliği için kullanılan çerçeve.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-119">A frame used for code access security.</span></span>|  
|`STUBFRAME_JIT_COMPILATION`|<span data-ttu-id="bc2d0-120">Çalışma zamanı JIT-derleme bir yöntem ' dir.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-120">The runtime is JIT-compiling a method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bc2d0-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bc2d0-121">Requirements</span></span>  
 <span data-ttu-id="bc2d0-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc2d0-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc2d0-123">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc2d0-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc2d0-124">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc2d0-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc2d0-125">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc2d0-125">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc2d0-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bc2d0-126">See Also</span></span>  
 [<span data-ttu-id="bc2d0-127">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="bc2d0-127">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
