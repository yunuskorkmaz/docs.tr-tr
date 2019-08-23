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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0925cf217afafe57abf82cf51a77b1992bad5152
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966835"
---
# <a name="icordebugvalue2-interface"></a><span data-ttu-id="0dc70-102">ICorDebugValue2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dc70-102">ICorDebugValue2 Interface</span></span>
<span data-ttu-id="0dc70-103">"ICorDebugType" nesnelerine yönelik destek sağlamak için "ICorDebugValue" arabirimini genişletir.</span><span class="sxs-lookup"><span data-stu-id="0dc70-103">Extends the "ICorDebugValue" interface to provide support for "ICorDebugType" objects.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0dc70-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="0dc70-104">Methods</span></span>  
  
|<span data-ttu-id="0dc70-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="0dc70-105">Method</span></span>|<span data-ttu-id="0dc70-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0dc70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0dc70-107">GetExactType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0dc70-107">GetExactType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md)|<span data-ttu-id="0dc70-108">Bu değerin değerini <xref:System.Type> temsil eden bir `ICorDebugType` nesne için bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="0dc70-108">Gets an interface pointer to an `ICorDebugType` object that represents the <xref:System.Type> of this value.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dc70-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0dc70-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0dc70-110">Bu arabirim, çapraz makine ya da çapraz işlem için uzaktan çağrılmakta değil.</span><span class="sxs-lookup"><span data-stu-id="0dc70-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc70-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0dc70-111">Requirements</span></span>  
 <span data-ttu-id="0dc70-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0dc70-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0dc70-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0dc70-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0dc70-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0dc70-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0dc70-115">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0dc70-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc70-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0dc70-116">See also</span></span>

- [<span data-ttu-id="0dc70-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0dc70-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

- [<span data-ttu-id="0dc70-118">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0dc70-118">ICorDebugValue3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)
