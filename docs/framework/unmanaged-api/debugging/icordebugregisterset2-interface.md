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
ms.openlocfilehash: da2759219901a4f49808300ea3b038b10ce2d032
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61782843"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="68403-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68403-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="68403-103">Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64'den fazla kayda sahip donanım platformları için arabirim.</span><span class="sxs-lookup"><span data-stu-id="68403-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="68403-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="68403-104">Methods</span></span>  
  
|<span data-ttu-id="68403-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="68403-105">Method</span></span>|<span data-ttu-id="68403-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="68403-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="68403-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68403-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="68403-108">Her kaydın değerini alır (şu anda kod yürüttüğünü bilgisayarda) bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="68403-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="68403-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68403-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="68403-110">Bir bit eşlem kullanılabilir kayıtlara sağlayan bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="68403-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="68403-111">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68403-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="68403-112">.NET Framework 2.0 sürümünde uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="68403-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68403-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68403-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="68403-114">Bu arabirim makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="68403-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68403-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68403-115">Requirements</span></span>  
 <span data-ttu-id="68403-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68403-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68403-117">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68403-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68403-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68403-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68403-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68403-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68403-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68403-120">See also</span></span>

- [<span data-ttu-id="68403-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="68403-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="68403-122">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68403-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
