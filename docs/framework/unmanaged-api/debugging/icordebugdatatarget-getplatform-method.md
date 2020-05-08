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
ms.openlocfilehash: 3df35d52a4e5209b282ccef653b065bdcf1f8fe4
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976544"
---
# <a name="icordebugdatatargetgetplatform-method"></a><span data-ttu-id="88049-102">ICorDebugDataTarget::GetPlatform Metodu</span><span class="sxs-lookup"><span data-stu-id="88049-102">ICorDebugDataTarget::GetPlatform Method</span></span>
<span data-ttu-id="88049-103">Hedef işlemin çalıştığı işlemci mimarisi ve işletim sistemi dahil olmak üzere platform hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="88049-103">Provides information about the platform, including processor architecture and operating system, on which the target process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88049-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="88049-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPlatform([out] CorDebugPlatform * pTargetPlatform);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88049-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="88049-105">Parameters</span></span>  
 `pTargetPlatform`  
 <span data-ttu-id="88049-106">dışı Hedef platformu açıklayan [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırması için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="88049-106">[out] A pointer to a [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration that describes the target platform.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88049-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="88049-107">Remarks</span></span>  
 <span data-ttu-id="88049-108">`CorDebugPlatformEnum` Sabit listesi dönüş değeri, kendi işaretçi boyutu, adres alanı düzeni, kayıt kümesi, yönerge biçimi, bağlam düzeni ve çağırma kuralları gibi hedef işlemin ayrıntılarını belirlemede [ICorDebug](icordebug-interface.md) arabirimi tarafından kullanılır.</span><span class="sxs-lookup"><span data-stu-id="88049-108">The `CorDebugPlatformEnum` enumeration return value is used by the [ICorDebug](icordebug-interface.md) interface to determine details of the target process such as its pointer size, address space layout, register set, instruction format, context layout, and calling conventions.</span></span>  
  
 <span data-ttu-id="88049-109">`pTargetPlatform` Değer, kullanımdaki gerçek donanımı belirtmek yerine, hedef için Öykünülen bir platforma başvurabilir.</span><span class="sxs-lookup"><span data-stu-id="88049-109">The `pTargetPlatform` value may refer to a platform that is being emulated for the target instead of specifying the actual hardware in use.</span></span> <span data-ttu-id="88049-110">Örneğin, Windows işletim sisteminin 64 bitlik bir sürümündeki Windows 'da Windows (WOW) ortamında çalışan bir işlem `CORDB_PLATFORM_WINDOWS_X86` [CorDebugPlatformEnum](cordebugplatform-enumeration.md) numaralandırması değerini kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88049-110">For example, a process that is running in the Windows on Windows (WOW) environment on a 64-bit edition of the Windows operating system should use the `CORDB_PLATFORM_WINDOWS_X86` value of the [CorDebugPlatformEnum](cordebugplatform-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="88049-111">Bu yöntem başarılı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="88049-111">This method must succeed.</span></span> <span data-ttu-id="88049-112">Başarısız olursa, hedef platform kullanılamaz olur.</span><span class="sxs-lookup"><span data-stu-id="88049-112">If it fails, the target platform is unusable.</span></span> <span data-ttu-id="88049-113">Yöntemi aşağıdaki nedenlerden dolayı başarısız olabilir:</span><span class="sxs-lookup"><span data-stu-id="88049-113">The method may fail for the following reasons:</span></span>  
  
- <span data-ttu-id="88049-114">Hedef için Öykünülen platform kullanılamıyor.</span><span class="sxs-lookup"><span data-stu-id="88049-114">The platform that is being emulated for the target is unusable.</span></span>  
  
- <span data-ttu-id="88049-115">Hedef Platformdaki gerçek donanım kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="88049-115">The actual hardware on the target platform is unusable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88049-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="88049-116">Requirements</span></span>  
 <span data-ttu-id="88049-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88049-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88049-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="88049-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88049-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="88049-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88049-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88049-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88049-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="88049-121">See also</span></span>

- [<span data-ttu-id="88049-122">ICorDebugDataTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="88049-122">ICorDebugDataTarget Interface</span></span>](icordebugdatatarget-interface.md)
- [<span data-ttu-id="88049-123">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="88049-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="88049-124">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="88049-124">Debugging</span></span>](index.md)
