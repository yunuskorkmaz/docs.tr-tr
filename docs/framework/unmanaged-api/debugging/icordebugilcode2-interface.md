---
description: 'Daha fazla bilgi edinin: ICorDebugILCode2 Interface'
title: ICorDebugILCode2 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
ms.openlocfilehash: 52e47b8cbf8f9926797e193944fd7e97b2e4dbcd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791419"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="ebdb0-103">ICorDebugILCode2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebdb0-103">ICorDebugILCode2 Interface</span></span>

<span data-ttu-id="ebdb0-104">[.NET Framework 4.5.2 ve sonraki sürümlerde desteklenir]</span><span class="sxs-lookup"><span data-stu-id="ebdb0-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="ebdb0-105">Bir işlevin yerel değişken imzasının belirtecini döndüren ve bir profiler 'ın belgelenmiş ara dili (IL) orijinal Yöntem Il uzaklıklarına eşleyen Yöntemler sağlamak için [ICorDebugILCode](icordebugilcode-interface.md) arabirimini mantıksal olarak genişletir.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-105">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebdb0-106">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="ebdb0-106">Methods</span></span>  
  
|<span data-ttu-id="ebdb0-107">Yöntem</span><span class="sxs-lookup"><span data-stu-id="ebdb0-107">Method</span></span>|<span data-ttu-id="ebdb0-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ebdb0-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebdb0-109">GetInstrumentedILMap Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ebdb0-109">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="ebdb0-110">Bu örnek için, Oluşturucu tarafından işaretlenmiş Il uzaklıkları orijinal Yöntem Il uzaklıklarından bir harita döndürür.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-110">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="ebdb0-111">GetLocalVarSigToken Metodu</span><span class="sxs-lookup"><span data-stu-id="ebdb0-111">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="ebdb0-112">Bu örnek tarafından temsil edilen işlev için yerel değişken imzasının meta veri belirtecini alır.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-112">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebdb0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ebdb0-113">Requirements</span></span>  

 <span data-ttu-id="ebdb0-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebdb0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebdb0-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ebdb0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ebdb0-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ebdb0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ebdb0-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebdb0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdb0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ebdb0-118">See also</span></span>

- [<span data-ttu-id="ebdb0-119">ICorDebugILCode Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ebdb0-119">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="ebdb0-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ebdb0-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ebdb0-121">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="ebdb0-121">Debugging</span></span>](index.md)
