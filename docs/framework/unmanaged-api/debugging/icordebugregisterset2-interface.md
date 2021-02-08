---
description: 'Daha fazla bilgi edinin: ICorDebugRegisterSet2 Interface'
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
ms.openlocfilehash: 3501325df188879f5687347ef329f490b487d9d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99803613"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="a2886-103">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2886-103">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="a2886-104">64 ' den fazla kayda sahip donanım platformları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabiriminin yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="a2886-104">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2886-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="a2886-105">Methods</span></span>  
  
|<span data-ttu-id="a2886-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="a2886-106">Method</span></span>|<span data-ttu-id="a2886-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a2886-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2886-108">GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="a2886-108">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="a2886-109">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="a2886-109">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="a2886-110">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2886-110">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="a2886-111">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="a2886-111">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="a2886-112">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2886-112">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="a2886-113">.NET Framework sürüm 2,0 ' de uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="a2886-113">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2886-114">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2886-114">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2886-115">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="a2886-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2886-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2886-116">Requirements</span></span>  

 <span data-ttu-id="a2886-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2886-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2886-118">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2886-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2886-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2886-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2886-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2886-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2886-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2886-121">See also</span></span>

- [<span data-ttu-id="a2886-122">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a2886-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="a2886-123">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2886-123">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
