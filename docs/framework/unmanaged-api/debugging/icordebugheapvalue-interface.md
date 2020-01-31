---
title: ICorDebugHeapValue Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue
helpviewer_keywords:
- ICorDebugHeapValue interface [.NET Framework debugging]
ms.assetid: 1bca66db-0359-4ae8-846e-e35f7e547e8b
topic_type:
- apiref
ms.openlocfilehash: fa31b8a6cc96935319e9bef3e561790b65e33a87
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777584"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="3513c-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3513c-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="3513c-103">Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3513c-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3513c-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3513c-104">Methods</span></span>  
  
|<span data-ttu-id="3513c-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3513c-105">Method</span></span>|<span data-ttu-id="3513c-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3513c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3513c-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3513c-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="3513c-108">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3513c-108">Not implemented.</span></span>|  
|[<span data-ttu-id="3513c-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3513c-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="3513c-110">Bu `ICorDebugHeapValue` tarafından temsil edilen nesnenin geçerli olup olmadığını veya çöp toplayıcı tarafından geri alındığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3513c-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="3513c-111">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3513c-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3513c-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3513c-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3513c-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="3513c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3513c-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3513c-114">Requirements</span></span>  
 <span data-ttu-id="3513c-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3513c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3513c-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3513c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3513c-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3513c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3513c-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3513c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3513c-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3513c-119">See also</span></span>

- [<span data-ttu-id="3513c-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3513c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
