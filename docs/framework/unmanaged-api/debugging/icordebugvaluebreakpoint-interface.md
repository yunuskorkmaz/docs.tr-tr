---
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
ms.openlocfilehash: cf0a87afd1c0057c054205432fea7aa5844afb53
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684421"
---
# <a name="icordebugvaluebreakpoint-interface"></a><span data-ttu-id="4ade2-102">ICorDebugValueBreakpoint Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4ade2-102">ICorDebugValueBreakpoint Interface</span></span>

<span data-ttu-id="4ade2-103">Belirli değerlere erişim sağlamak için ICorDebugBreakpoint arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="4ade2-103">Extends the ICorDebugBreakpoint interface to provide access to specific values.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ade2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4ade2-104">Methods</span></span>  
  
|<span data-ttu-id="4ade2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4ade2-105">Method</span></span>|<span data-ttu-id="4ade2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4ade2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ade2-107">GetValue Metodu</span><span class="sxs-lookup"><span data-stu-id="4ade2-107">GetValue Method</span></span>](icordebugvaluebreakpoint-getvalue-method.md)|<span data-ttu-id="4ade2-108">Kesme noktasının ayarlandığı nesnenin değerini temsil eden ICorDebugValue nesnesine yönelik bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="4ade2-108">Gets an interface pointer to an ICorDebugValue object that represents the value of the object upon which the breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ade2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4ade2-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4ade2-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="4ade2-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ade2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4ade2-111">Requirements</span></span>  

 <span data-ttu-id="4ade2-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ade2-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ade2-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4ade2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ade2-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4ade2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ade2-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ade2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ade2-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4ade2-116">See also</span></span>

- [<span data-ttu-id="4ade2-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4ade2-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
