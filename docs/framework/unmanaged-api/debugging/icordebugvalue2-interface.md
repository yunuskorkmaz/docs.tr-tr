---
title: ICorDebugValue2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue2
helpviewer_keywords:
- ICorDebugValue2 interface [.NET Framework debugging]
ms.assetid: 3ff2ad2a-da5a-461b-8627-1a8eba49df9c
topic_type:
- apiref
ms.openlocfilehash: d036ddf353aa3a622ade05e1e2daa7f170d28f63
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396773"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="8f682-102">ICorDebugValue2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f682-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="8f682-103">"ICorDebugType" nesnelerine yönelik destek sağlamak için "ICorDebugValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="8f682-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8f682-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="8f682-104">Methods</span></span>  
  
|<span data-ttu-id="8f682-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="8f682-105">Method</span></span>|<span data-ttu-id="8f682-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f682-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8f682-107">GetExactType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f682-107">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="8f682-108">`ICorDebugType`Bu değerin değerini temsil eden bir nesne için bir arabirim işaretçisi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="8f682-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8f682-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f682-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8f682-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="8f682-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f682-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f682-111">Requirements</span></span>  
 <span data-ttu-id="8f682-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f682-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f682-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f682-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f682-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f682-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f682-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f682-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f682-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f682-116">See also</span></span>

- [<span data-ttu-id="8f682-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8f682-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="8f682-118">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f682-118">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
