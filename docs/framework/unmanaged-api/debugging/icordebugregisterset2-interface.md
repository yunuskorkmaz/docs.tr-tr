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
ms.openlocfilehash: 161358fab9a4601e7b718321273d493bd84a3228
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792005"
---
# <a name="icordebugregisterset2-interface"></a><span data-ttu-id="7ff48-102">ICorDebugRegisterSet2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff48-102">ICorDebugRegisterSet2 Interface</span></span>
<span data-ttu-id="7ff48-103">64 ' den fazla kayda sahip donanım platformları için [ICorDebugRegisterSet](icordebugregisterset-interface.md) arabiriminin yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="7ff48-103">Extends the capabilities of the [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface for hardware platforms that have more than 64 registers.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ff48-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="7ff48-104">Methods</span></span>  
  
|<span data-ttu-id="7ff48-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="7ff48-105">Method</span></span>|<span data-ttu-id="7ff48-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7ff48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ff48-107">GetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ff48-107">GetRegisters Method</span></span>](icordebugregisterset2-getregisters-method.md)|<span data-ttu-id="7ff48-108">Bit maskesi tarafından belirtilen her kaydın (Şu anda kod yürüten bilgisayardaki) değerini alır.</span><span class="sxs-lookup"><span data-stu-id="7ff48-108">Gets the value of each register (on the computer that is currently executing code) that is specified by the bit mask.</span></span>|  
|[<span data-ttu-id="7ff48-109">GetRegistersAvailable Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ff48-109">GetRegistersAvailable Method</span></span>](icordebugregisterset2-getregistersavailable-method.md)|<span data-ttu-id="7ff48-110">Kullanılabilir yazmaçların bit eşlemini sağlayan bir bayt dizisini alır.</span><span class="sxs-lookup"><span data-stu-id="7ff48-110">Gets an array of bytes that provides a bitmap of the available registers.</span></span>|  
|[<span data-ttu-id="7ff48-111">SetRegisters Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7ff48-111">SetRegisters Method</span></span>](icordebugregisterset2-setregisters-method.md)|<span data-ttu-id="7ff48-112">.NET Framework sürüm 2,0 ' de uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="7ff48-112">Not implemented in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ff48-113">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7ff48-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7ff48-114">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="7ff48-114">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ff48-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7ff48-115">Requirements</span></span>  
 <span data-ttu-id="7ff48-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ff48-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ff48-117">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7ff48-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ff48-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7ff48-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ff48-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ff48-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ff48-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7ff48-120">See also</span></span>

- [<span data-ttu-id="7ff48-121">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7ff48-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7ff48-122">ICorDebugRegisterSet Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7ff48-122">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
