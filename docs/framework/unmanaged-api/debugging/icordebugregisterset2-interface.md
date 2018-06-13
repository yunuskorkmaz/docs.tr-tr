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
ms.openlocfilehash: 6f4947a9b6c0e3fd87ee474111f143d273c1d7b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422801"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="8718f-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8718f-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="8718f-103">Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64 taneden fazla kayıtları olan donanım platformları için arabirim.</span><span class="sxs-lookup"><span data-stu-id="8718f-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8718f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8718f-104">Methods</span></span>  
  
|<span data-ttu-id="8718f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8718f-105">Method</span></span>|<span data-ttu-id="8718f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8718f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8718f-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8718f-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="8718f-108">Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="8718f-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="8718f-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8718f-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="8718f-110">Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="8718f-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="8718f-111">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8718f-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="8718f-112">.NET Framework sürüm 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="8718f-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8718f-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8718f-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8718f-114">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="8718f-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8718f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8718f-115">Requirements</span></span>  
 <span data-ttu-id="8718f-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8718f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8718f-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8718f-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8718f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8718f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8718f-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8718f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8718f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8718f-120">See Also</span></span>  
 [<span data-ttu-id="8718f-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8718f-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="8718f-122">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8718f-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
