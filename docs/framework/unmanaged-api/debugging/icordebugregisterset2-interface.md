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
ms.openlocfilehash: c04bb3a7584fcb783af929e87713dbec67ad705f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712332"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="fb90a-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb90a-102">ICorDebugRegisterSet2 Interface</span></span>

<span data-ttu-id="fb90a-103">64 ' den fazla kayda sahip donanım platformları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabiriminin yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="fb90a-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fb90a-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="fb90a-104">Methods</span></span>  
  
|<span data-ttu-id="fb90a-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="fb90a-105">Method</span></span>|<span data-ttu-id="fb90a-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fb90a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fb90a-107">GetRegisters Metodu</span><span class="sxs-lookup"><span data-stu-id="fb90a-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="fb90a-108">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="fb90a-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="fb90a-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb90a-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="fb90a-110">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="fb90a-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="fb90a-111">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb90a-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="fb90a-112">.NET Framework sürüm 2,0 ' de uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="fb90a-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fb90a-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb90a-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fb90a-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="fb90a-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb90a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb90a-115">Requirements</span></span>  

 <span data-ttu-id="fb90a-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb90a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb90a-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fb90a-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fb90a-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fb90a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fb90a-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb90a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb90a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb90a-120">See also</span></span>

- [<span data-ttu-id="fb90a-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fb90a-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="fb90a-122">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb90a-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
