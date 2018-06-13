---
title: ICorDebugFunction3 Arabirimi
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1945e678dd62f81c698807714d0e71053d6b378
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414791"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="c9b24-102">ICorDebugFunction3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9b24-102">ICorDebugFunction3 Interface</span></span>
<span data-ttu-id="c9b24-103">[.NET Framework 4.5.2 ve sonraki sürümlerinde desteklenen]</span><span class="sxs-lookup"><span data-stu-id="c9b24-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c9b24-104">Mantıksal bir ReJIT isteğinden koduna erişim sağlamak için ICorDebugFunction arabirimi genişletir.</span><span class="sxs-lookup"><span data-stu-id="c9b24-104">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c9b24-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="c9b24-105">Methods</span></span>  
  
|<span data-ttu-id="c9b24-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="c9b24-106">Method</span></span>|<span data-ttu-id="c9b24-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c9b24-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c9b24-108">GetActiveReJitRequestILCode Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9b24-108">GetActiveReJitRequestILCode Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="c9b24-109">Bir arabirim işaretçisi alır bir [Icordebugılcode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) etkin bir ReJIT istek IL içerir.</span><span class="sxs-lookup"><span data-stu-id="c9b24-109">Gets an interface pointer to an [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9b24-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9b24-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9b24-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9b24-111">Requirements</span></span>  
 <span data-ttu-id="c9b24-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9b24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9b24-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9b24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9b24-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9b24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9b24-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9b24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b24-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9b24-116">See Also</span></span>  
 [<span data-ttu-id="c9b24-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9b24-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="c9b24-118">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c9b24-118">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)  
 [<span data-ttu-id="c9b24-119">ReJIT: Nasıl yapılır Kılavuzu</span><span class="sxs-lookup"><span data-stu-id="c9b24-119">ReJIT: A How-To Guide</span></span>](http://blogs.msdn.com/b/davbr/archive/2011/10/12/rejit-a-how-to-guide.aspx)
