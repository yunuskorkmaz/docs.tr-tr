---
title: ICorDebugValue3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue3
helpviewer_keywords:
- ICorDebugValue3 interface [.NET Framework debugging]
ms.assetid: 7d5385d3-f4a5-47c4-8478-a3513b5e9406
topic_type:
- apiref
ms.openlocfilehash: 1f46866a1b975455acd294221e38ef3b4c358660
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140209"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="6a3c2-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a3c2-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="6a3c2-103">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6a3c2-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6a3c2-104">Methods</span></span>  
  
|<span data-ttu-id="6a3c2-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6a3c2-105">Method</span></span>|<span data-ttu-id="6a3c2-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6a3c2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6a3c2-107">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a3c2-107">GetSize64 Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md)|<span data-ttu-id="6a3c2-108">Bu `ICorDebugValue3` nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a3c2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6a3c2-109">Remarks</span></span>  
 <span data-ttu-id="6a3c2-110">[ICorDebugValue:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) yöntemi, 0 ile 2.147.483.647 bayt arasında değişen bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-110">The [ICorDebugValue::GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="6a3c2-111">.NET Framework 4,5 ' de, dizilerin boyutu 2 GB 'ı aşabilirler.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="6a3c2-112">`ICorDebugValue3` arabirimi bu dizilerin boyutunu belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6a3c2-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a3c2-113">Requirements</span></span>  
 <span data-ttu-id="6a3c2-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a3c2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a3c2-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6a3c2-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6a3c2-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6a3c2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6a3c2-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a3c2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a3c2-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a3c2-118">See also</span></span>

- [<span data-ttu-id="6a3c2-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6a3c2-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="6a3c2-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="6a3c2-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
