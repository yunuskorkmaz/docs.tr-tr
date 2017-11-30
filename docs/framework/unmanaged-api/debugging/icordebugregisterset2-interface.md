---
title: ICorDebugRegisterSet2 Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugRegisterSet2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugRegisterSet2
helpviewer_keywords: ICorDebugRegisterSet2 interface [.NET Framework debugging]
ms.assetid: d7fbccbf-3b6b-4db8-a96d-768e1cb6b1a6
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 26967f50ded62f935a705c25eed58314b77bedd8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="99a18-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99a18-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="99a18-103">Yeteneklerini genişletir [Icordebugregisterset](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) 64 taneden fazla kayıtları olan donanım platformları için arabirim.</span><span class="sxs-lookup"><span data-stu-id="99a18-103">Extends the capabilities of the [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99a18-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="99a18-104">Methods</span></span>  
  
|<span data-ttu-id="99a18-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="99a18-105">Method</span></span>|<span data-ttu-id="99a18-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99a18-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99a18-107">GetRegisters yöntemi</span><span class="sxs-lookup"><span data-stu-id="99a18-107">GetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="99a18-108">Her kayıt değerini (kod şu anda yürütülmekte bilgisayarda) alır bit maskesi kullanılarak belirtilir.</span><span class="sxs-lookup"><span data-stu-id="99a18-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="99a18-109">GetRegistersAvailable yöntemi</span><span class="sxs-lookup"><span data-stu-id="99a18-109">GetRegistersAvailable Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="99a18-110">Bir bit eşlem kullanılabilir yazmaçlar sağlayan bir bayt dizisi alır.</span><span class="sxs-lookup"><span data-stu-id="99a18-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="99a18-111">SetRegisters yöntemi</span><span class="sxs-lookup"><span data-stu-id="99a18-111">SetRegisters Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="99a18-112">.NET Framework sürüm 2.0 uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="99a18-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99a18-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="99a18-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99a18-114">Bu arabirim, makineler arası veya çapraz işlem uzaktan çağrılan desteklemez.</span><span class="sxs-lookup"><span data-stu-id="99a18-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99a18-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99a18-115">Requirements</span></span>  
 <span data-ttu-id="99a18-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99a18-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99a18-117">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99a18-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99a18-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99a18-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99a18-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99a18-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99a18-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99a18-120">See Also</span></span>  
 [<span data-ttu-id="99a18-121">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="99a18-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="99a18-122">Icordebugregisterset arabirimi</span><span class="sxs-lookup"><span data-stu-id="99a18-122">ICorDebugRegisterSet Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)
