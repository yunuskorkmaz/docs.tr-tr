---
title: ICorDebugDataTarget::GetPlatform Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugDataTarget.GetPlatform Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 309c31dacd801f1c46a2d37932124638bc157cd6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59214033"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="826b4-102">ICorDebugDataTarget::GetPlatform Metodu</span><span class="sxs-lookup"><span data-stu-id="826b4-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="826b4-103">İşlemci mimarisi ve hedef işlem üzerinde çalıştığı işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="826b4-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="826b4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="826b4-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="826b4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="826b4-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="826b4-106">[out] Bir işaretçi bir [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) hedef platform açıklayan sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="826b4-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="826b4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="826b4-107">Remarks</span></span>  
 <span data-ttu-id="826b4-108">`CorDebugPlatformEnum` Numaralandırma dönüş değeri tarafından kullanılan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) arabirimi, işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, içerik düzeni, hedef işlemin ayrıntılarını belirlemek için ve çağırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="826b4-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="826b4-109">`pTargetPlatform` Değeri, gerçek donanım kullanımda belirtmek yerine hedef için benzetilmiş bir platforma başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="826b4-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="826b4-110">Örneğin, Windows (WOW) ortamında Windows 64-bit Windows işletim sistemi sürümünde çalışan bir işlemin kullanmalıdır `CORDB_PLATFORM_WINDOWS_X86` değerini [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="826b4-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="826b4-111">Bu yöntem başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="826b4-111">This method must succeed.</span></span> <span data-ttu-id="826b4-112">Başarısız olursa, hedef platform kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="826b4-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="826b4-113">Yöntemi, aşağıdaki nedenlerden dolayı başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="826b4-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="826b4-114">Hedef benzetilip benzetilmediğini platformu kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="826b4-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="826b4-115">Gerçek donanım hedef platformda kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="826b4-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="826b4-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="826b4-116">Requirements</span></span>  
 <span data-ttu-id="826b4-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="826b4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="826b4-118">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="826b4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="826b4-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="826b4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="826b4-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="826b4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826b4-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="826b4-121">See also</span></span>

- [<span data-ttu-id="826b4-122">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="826b4-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="826b4-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="826b4-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="826b4-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="826b4-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
