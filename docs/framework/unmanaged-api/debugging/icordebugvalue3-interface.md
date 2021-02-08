---
description: 'Daha fazla bilgi edinin: ICorDebugValue3 Interface'
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
ms.openlocfilehash: e5868b91d23426a2d8dd8fed87b13ec61fef95ef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794656"
---
# <a name="icordebugvalue3-interface"></a><span data-ttu-id="f6335-103">ICorDebugValue3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f6335-103">ICorDebugValue3 Interface</span></span>

<span data-ttu-id="f6335-104">2 GB 'den büyük diziler için destek sağlamak üzere "ICorDebugValue" ve "ICorDebugValue2" arabirimlerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="f6335-104">Extends the "ICorDebugValue" and "ICorDebugValue2" interfaces to provide support for arrays that are larger than 2 GB.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6335-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f6335-105">Methods</span></span>  
  
|<span data-ttu-id="f6335-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f6335-106">Method</span></span>|<span data-ttu-id="f6335-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f6335-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6335-108">GetSize64 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f6335-108">GetSize64 Method</span></span>](icordebugvalue3-getsize64-method.md)|<span data-ttu-id="f6335-109">Bu nesnenin boyutunu bayt cinsinden alır `ICorDebugValue3` .</span><span class="sxs-lookup"><span data-stu-id="f6335-109">Gets the size, in bytes, of this `ICorDebugValue3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6335-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f6335-110">Remarks</span></span>  

 <span data-ttu-id="f6335-111">[ICorDebugValue:: GetSize](icordebugvalue3-getsize64-method.md) yöntemi, 0 ile 2.147.483.647 bayt arasında değişen bir nesne boyutu döndürür.</span><span class="sxs-lookup"><span data-stu-id="f6335-111">The [ICorDebugValue::GetSize](icordebugvalue3-getsize64-method.md) method returns an object size that ranges from 0 to 2,147,483,647 bytes.</span></span> <span data-ttu-id="f6335-112">.NET Framework 4,5 ' de, dizilerin boyutu 2 GB 'ı aşabilirler.</span><span class="sxs-lookup"><span data-stu-id="f6335-112">In the .NET Framework 4.5, the size of arrays can exceed 2 GB.</span></span> <span data-ttu-id="f6335-113">`ICorDebugValue3`Arabirim, bu dizilerin boyutunu belirlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="f6335-113">The `ICorDebugValue3` interface enables you to determine the size of these arrays.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6335-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f6335-114">Requirements</span></span>  

 <span data-ttu-id="f6335-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6335-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6335-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f6335-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f6335-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f6335-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6335-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6335-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6335-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f6335-119">See also</span></span>

- [<span data-ttu-id="f6335-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f6335-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f6335-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="f6335-121">Debugging</span></span>](index.md)
