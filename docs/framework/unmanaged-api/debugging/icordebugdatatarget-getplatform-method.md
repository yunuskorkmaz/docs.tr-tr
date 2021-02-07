---
description: ': ICorDebugDataTarget:: GetPlatform yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: dec691238009ad69d2e48d994ac250bfb6641863
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764534"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="c9556-103">ICorDebugDataTarget::GetPlatform Metodu</span><span class="sxs-lookup"><span data-stu-id="c9556-103">ICorDebugDataTarget::GetPlatform Method</span></span>

<span data-ttu-id="c9556-104">Hedef işlemin çalıştığı işlemci mimarisi ve işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c9556-104">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9556-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9556-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c9556-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9556-106">Parameters</span></span>  

 `pTargetPlatform`  
 <span data-ttu-id="c9556-107">dışı Hedef platformu açıklayan [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9556-107">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9556-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9556-108">Remarks</span></span>  

 <span data-ttu-id="c9556-109">`CorDebugPlatformEnum`Sabit listesi dönüş değeri, kendi işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, bağlam düzeni ve çağırma kuralları gibi hedef işlemin ayrıntılarını belirlemede [ICorDebug](icordebug-interface.md) arabirimi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="c9556-109">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="c9556-110">`pTargetPlatform`Değer, kullanımdaki gerçek donanımı belirtmek yerine, hedef için Öykünülen bir platforma başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="c9556-110">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="c9556-111">Örneğin, Windows işletim sisteminin 64 bitlik bir sürümündeki Windows 'da Windows (WOW) ortamında çalışan bir işlem `CORDB_PLATFORM_WINDOWS_X86` [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırması değerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9556-111">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="c9556-112">Bu yöntem başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c9556-112">This method must succeed.</span></span> <span data-ttu-id="c9556-113">Başarısız olursa, hedef platform kullanılamaz olur.</span><span class="sxs-lookup"><span data-stu-id="c9556-113">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="c9556-114">Yöntemi aşağıdaki nedenlerden dolayı başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="c9556-114">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="c9556-115">Hedef için Öykünülen platform kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="c9556-115">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="c9556-116">Hedef Platformdaki gerçek donanım kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c9556-116">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9556-117">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9556-117">Requirements</span></span>  

 <span data-ttu-id="c9556-118">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9556-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9556-119">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c9556-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9556-120">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c9556-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9556-121">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9556-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9556-122">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9556-122">See also</span></span>

- [<span data-ttu-id="c9556-123">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9556-123">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="c9556-124">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9556-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c9556-125">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c9556-125">Debugging</span></span>](index.md)
