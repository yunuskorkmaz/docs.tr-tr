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
ms.openlocfilehash: 4f87065fc4a3d80a8363f3ae2fbb76c29f3d9b96
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138411"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="acc6f-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="acc6f-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="acc6f-103">Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="acc6f-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="acc6f-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="acc6f-104">Methods</span></span>  
  
|<span data-ttu-id="acc6f-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="acc6f-105">Method</span></span>|<span data-ttu-id="acc6f-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="acc6f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="acc6f-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acc6f-107">CreateRelocBreakpoint Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="acc6f-108">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="acc6f-108">Not implemented.</span></span>|  
|[<span data-ttu-id="acc6f-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="acc6f-109">IsValid Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="acc6f-110">Bu `ICorDebugHeapValue` tarafından temsil edilen nesnenin geçerli olup olmadığını veya çöp toplayıcı tarafından geri alındığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="acc6f-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="acc6f-111">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="acc6f-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acc6f-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="acc6f-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="acc6f-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="acc6f-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="acc6f-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="acc6f-114">Requirements</span></span>  
 <span data-ttu-id="acc6f-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="acc6f-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="acc6f-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="acc6f-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="acc6f-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="acc6f-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="acc6f-118">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="acc6f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc6f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="acc6f-119">See also</span></span>

- [<span data-ttu-id="acc6f-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="acc6f-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
