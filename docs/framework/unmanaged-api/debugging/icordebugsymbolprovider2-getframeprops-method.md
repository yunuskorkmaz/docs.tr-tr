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
ms.openlocfilehash: 3892b8da3286132709792513f055d6ce75bd3fce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="dce12-102">ICorDebugSymbolProvider2::GetFrameProps yöntemi</span><span class="sxs-lookup"><span data-stu-id="dce12-102">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>
<span data-ttu-id="dce12-103">Bir yöntem ve bir kod göreli sanal adres verilen üst çerçeve göreli sanal adres başlatma yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="dce12-103">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dce12-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dce12-104">Syntax</span></span>  
  
```  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dce12-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dce12-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="dce12-106">[in] Bir kod göreli sanal adres.</span><span class="sxs-lookup"><span data-stu-id="dce12-106">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="dce12-107">[out] Yöntemin başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dce12-107">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="dce12-108">[out] Çerçeve başlangıç göreli sanal adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dce12-108">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dce12-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dce12-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dce12-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dce12-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce12-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dce12-111">Requirements</span></span>  
 <span data-ttu-id="dce12-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce12-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce12-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dce12-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dce12-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce12-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce12-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce12-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce12-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dce12-116">See Also</span></span>  
 [<span data-ttu-id="dce12-117">ICorDebugSymbolProvider2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="dce12-117">ICorDebugSymbolProvider2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 [<span data-ttu-id="dce12-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dce12-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
