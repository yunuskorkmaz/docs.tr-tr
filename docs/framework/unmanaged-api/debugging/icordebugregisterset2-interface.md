---
title: ICorDebugRegisterSet2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet2
helpviewer_keywords:
- ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 30cecaa1832ba9d45782b164ee65a2f39f28a8f8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605412"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="aaebb-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaebb-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="aaebb-103">Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64'den fazla kayda sahip donanım platformları için arabirim.</span><span class="sxs-lookup"><span data-stu-id="aaebb-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aaebb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aaebb-104">Methods</span></span>  
  
|<span data-ttu-id="aaebb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aaebb-105">Method</span></span>|<span data-ttu-id="aaebb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aaebb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aaebb-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaebb-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="aaebb-108">Her kaydın değerini alır (şu anda kod yürüttüğünü bilgisayarda) bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="aaebb-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="aaebb-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaebb-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="aaebb-110">Bir bit eşlem kullanılabilir kayıtlara sağlayan bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="aaebb-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="aaebb-111">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aaebb-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="aaebb-112">.NET Framework 2.0 sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="aaebb-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aaebb-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aaebb-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaebb-114">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="aaebb-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aaebb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aaebb-115">Requirements</span></span>  
 <span data-ttu-id="aaebb-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aaebb-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aaebb-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aaebb-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aaebb-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aaebb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aaebb-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aaebb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aaebb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aaebb-120">See also</span></span>
- [<span data-ttu-id="aaebb-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aaebb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="aaebb-122">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aaebb-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
