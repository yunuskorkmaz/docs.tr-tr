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
ms.openlocfilehash: 36a485413490045ca49b99fca4fe5d43edc37114
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213016"
---
# <a name="icordebugheapvalue-interface"></a><span data-ttu-id="be3f6-102">ICorDebugHeapValue Arabirimi</span><span class="sxs-lookup"><span data-stu-id="be3f6-102">ICorDebugHeapValue Interface</span></span>

<span data-ttu-id="be3f6-103">Ortak dil çalışma zamanı (CLR) atık toplayıcısı tarafından toplanan bir nesneyi temsil eden "ICorDebugValue" öğesinin bir alt sınıfı.</span><span class="sxs-lookup"><span data-stu-id="be3f6-103">A subclass of "ICorDebugValue" that represents an object that has been collected by the common language runtime (CLR) garbage collector.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be3f6-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="be3f6-104">Methods</span></span>  
  
|<span data-ttu-id="be3f6-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="be3f6-105">Method</span></span>|<span data-ttu-id="be3f6-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="be3f6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be3f6-107">CreateRelocBreakpoint Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be3f6-107">CreateRelocBreakpoint Method</span></span>](icordebugheapvalue-createrelocbreakpoint-method.md)|<span data-ttu-id="be3f6-108">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="be3f6-108">Not implemented.</span></span>|  
|[<span data-ttu-id="be3f6-109">IsValid Yöntemi</span><span class="sxs-lookup"><span data-stu-id="be3f6-109">IsValid Method</span></span>](icordebugheapvalue-isvalid-method.md)|<span data-ttu-id="be3f6-110">Tarafından temsil edilen nesnenin geçerli olup olmadığını `ICorDebugHeapValue` veya çöp toplayıcı tarafından geri kazanıldığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="be3f6-110">Gets a value that indicates whether the object represented by this `ICorDebugHeapValue` is valid, or has been reclaimed by the garbage collector.</span></span> <span data-ttu-id="be3f6-111">Bu yöntem 2,0 .NET Framework sürümünde kullanımdan kaldırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="be3f6-111">This method has been deprecated in the .NET Framework version 2.0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be3f6-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="be3f6-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be3f6-113">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="be3f6-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be3f6-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="be3f6-114">Requirements</span></span>  
 <span data-ttu-id="be3f6-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be3f6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be3f6-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="be3f6-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be3f6-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="be3f6-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be3f6-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be3f6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be3f6-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="be3f6-119">See also</span></span>

- [<span data-ttu-id="be3f6-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="be3f6-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
