---
title: ICorDebugDataTarget::GetPlatform Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugDataTarget.GetPlatform Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugDataTarget::GetPlatform
helpviewer_keywords:
- GetPlatform method [.NET Framework debugging]
- ICorDebugDataTarget::GetPlatform method [.NET Framework debugging]
ms.assetid: 9ee96c9d-7a3d-4129-a6cc-7675c7f2dda4
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c19e472ef571def1011d2a00701fea3a6fadfea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="b635f-102">ICorDebugDataTarget::GetPlatform Metodu</span><span class="sxs-lookup"><span data-stu-id="b635f-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="b635f-103">İşlemci mimarisi ve hedef işlemin çalıştığı işletim sistemi dahil olmak üzere bu platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b635f-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b635f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b635f-104">Syntax</span></span>  
  
```  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b635f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b635f-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="b635f-106">[out] Bir işaretçi bir [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) hedef platformu açıklar numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b635f-106">[out] A pointer to a [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b635f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b635f-107">Remarks</span></span>  
 <span data-ttu-id="b635f-108">`CorDebugPlatformEnum` Numaralandırma dönüş değeri tarafından kullanılan [Icordebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) kendi işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, içerik düzeni gibi hedef işleminin ayrıntılarını belirlemek için arabirimi ve çağırma kuralları.</span><span class="sxs-lookup"><span data-stu-id="b635f-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="b635f-109">`pTargetPlatform` Değeri gerçek donanım kullanımda belirtmek yerine hedef için benzetilmiş bir platform başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="b635f-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="b635f-110">Örneğin, Windows işletim sisteminin 64 bit sürümünde Windows (WOW) ortamında Windows çalıştıran bir işlem kullanması gereken `CORDB_PLATFORM_WINDOWS_X86` değerini [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="b635f-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="b635f-111">Bu yöntem başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b635f-111">This method must succeed.</span></span> <span data-ttu-id="b635f-112">Başarısız olursa, hedef platformu kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b635f-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="b635f-113">Yöntemi, aşağıdaki nedenlerden dolayı başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="b635f-113">The method may fail for the following reasons:</span></span>  
  
-   <span data-ttu-id="b635f-114">Hedef benzetilmiş platform kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b635f-114">The platform that is being emulated for the target is unusable.</span></span>  
  
-   <span data-ttu-id="b635f-115">Hedef platformu üzerinde gerçek donanım kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b635f-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b635f-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b635f-116">Requirements</span></span>  
 <span data-ttu-id="b635f-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b635f-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b635f-118">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b635f-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b635f-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b635f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b635f-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b635f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b635f-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b635f-121">See Also</span></span>  
 [<span data-ttu-id="b635f-122">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b635f-122">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="b635f-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b635f-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b635f-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="b635f-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
