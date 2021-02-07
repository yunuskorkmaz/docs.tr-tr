---
description: 'Daha fazla bilgi edinin: ICorDebugValue2 Interface'
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
ms.openlocfilehash: b408bb5d1732a60fc9aa8ffb93321d3542f2cab7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690268"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="69440-103">ICorDebugValue2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69440-103">ICorDebugValue2 Interface</span></span>

<span data-ttu-id="69440-104">"ICorDebugType" nesnelerine yönelik destek sağlamak için "ICorDebugValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="69440-104">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="69440-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="69440-105">Methods</span></span>  
  
|<span data-ttu-id="69440-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="69440-106">Method</span></span>|<span data-ttu-id="69440-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69440-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="69440-108">GetExactType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69440-108">GetExactType Method</span></span>](icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="69440-109">`ICorDebugType`Bu değerin değerini temsil eden bir nesne için bir arabirim işaretçisi alır <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="69440-109">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69440-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="69440-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="69440-111">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="69440-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69440-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69440-112">Requirements</span></span>  

 <span data-ttu-id="69440-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69440-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69440-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="69440-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="69440-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="69440-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69440-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69440-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69440-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="69440-117">See also</span></span>

- [<span data-ttu-id="69440-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="69440-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

- [<span data-ttu-id="69440-119">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69440-119">ICorDebugValue3 Interface</span></span>](icordebugvalue3-interface.md)
