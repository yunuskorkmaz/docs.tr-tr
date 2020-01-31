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
ms.openlocfilehash: 5fa042223e47961dad0a6799ab8ca999ef76e285
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791087"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="9b1d5-102">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b1d5-102">ICorDebugValue3 Interface</span></span>
<span data-ttu-id="9b1d5-103">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-103">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9b1d5-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="9b1d5-104">Methods</span></span>  
  
|<span data-ttu-id="9b1d5-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="9b1d5-105">Method</span></span>|<span data-ttu-id="9b1d5-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b1d5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9b1d5-107">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b1d5-107">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="9b1d5-108">Bu `ICorDebugValue3` nesnesinin bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-108">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b1d5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b1d5-109">Remarks</span></span>  
 <span data-ttu-id="9b1d5-110">[ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) yöntemi, 0 ile 2.147.483.647 bayt arasında değişen bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-110">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="9b1d5-111">.NET Framework 4,5 ' de, dizilerin boyutu 2 GB 'ı aşabilirler.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-111">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="9b1d5-112">`ICorDebugValue3` arabirimi bu dizilerin boyutunu belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-112">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b1d5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b1d5-113">Requirements</span></span>  
 <span data-ttu-id="9b1d5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b1d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b1d5-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b1d5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b1d5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b1d5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b1d5-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b1d5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b1d5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b1d5-118">See also</span></span>

- [<span data-ttu-id="9b1d5-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9b1d5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="9b1d5-120">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9b1d5-120">Debugging</span></span>](index.md)
