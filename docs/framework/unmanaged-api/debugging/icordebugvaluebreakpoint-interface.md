---
description: ': ICorDebugValueBreakpoint arabirimi hakkında daha fazla bilgi edinin'
title: ICorDebugValueBreakpoint Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValueBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValueBreakpoint
helpviewer_keywords:
- ICorDebugValueBreakpoint interface [.NET Framework debugging]
ms.assetid: c02338fe-da6c-467f-9567-70ebb387e901
topic_type:
- apiref
ms.openlocfilehash: ff53b1f6e1557a3e98cc642f80eaaa2feaeac473
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790691"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="067c2-103">ICorDebugValueBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="067c2-103">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="067c2-104">Belirli değerlere erişim sağlamak için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="067c2-104">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="067c2-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="067c2-105">Methods</span></span>  
  
|<span data-ttu-id="067c2-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="067c2-106">Method</span></span>|<span data-ttu-id="067c2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="067c2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="067c2-108">GetValue Yöntemi</span><span class="sxs-lookup"><span data-stu-id="067c2-108">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="067c2-109">Kesme noktasının ayarlandığı nesnenin değerini temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="067c2-109">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="067c2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="067c2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="067c2-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="067c2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="067c2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="067c2-112">Requirements</span></span>  

 <span data-ttu-id="067c2-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="067c2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="067c2-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="067c2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="067c2-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="067c2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="067c2-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="067c2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="067c2-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="067c2-117">See also</span></span>

- [<span data-ttu-id="067c2-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="067c2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
