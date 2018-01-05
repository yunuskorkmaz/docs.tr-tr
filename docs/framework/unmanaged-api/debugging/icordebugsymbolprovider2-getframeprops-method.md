---
title: "ICorDebugSymbolProvider2::GetFrameProps yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f74ed8cdd7448d7ebeaa98108e84b42e86f428b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="1035e-102">ICorDebugSymbolProvider2::GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="1035e-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="1035e-103">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="1035e-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1035e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1035e-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1035e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1035e-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="1035e-106">[in] Bir kod göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="1035e-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="1035e-107">[out] Yöntemin başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1035e-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="1035e-108">[out] Çerçeve başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1035e-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1035e-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1035e-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1035e-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="1035e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1035e-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1035e-111">Requirements</span></span>  
 <span data-ttu-id="1035e-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1035e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1035e-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1035e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1035e-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1035e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1035e-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1035e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1035e-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1035e-116">See Also</span></span>  
 [<span data-ttu-id="1035e-117">ICorDebugSymbolProvider2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1035e-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="1035e-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1035e-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
