---
title: "ICorDebugSymbolProvider::GetCodeRange yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c46fb62e5f1867e2b527404bd3d003ba884ebfbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="c11c2-102">ICorDebugSymbolProvider::GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="c11c2-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="c11c2-103">Yöntemi başlangıç adresi ve bir yöntem göreli sanal adres (RVA) verilen boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c11c2-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c11c2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c11c2-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c11c2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c11c2-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c11c2-106">[in] Bir yöntem göreli sanal adres (RAV).</span><span class="sxs-lookup"><span data-stu-id="c11c2-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="c11c2-107">[out] Yöntemi başlangıç adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c11c2-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="c11c2-108">Yöntem kod boyutu (yöntemin kodunun bayt sayısı) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c11c2-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c11c2-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c11c2-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c11c2-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c11c2-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c11c2-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c11c2-111">Requirements</span></span>  
 <span data-ttu-id="c11c2-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c11c2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c11c2-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c11c2-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c11c2-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c11c2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c11c2-115">**.NET framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c11c2-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c11c2-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c11c2-116">See Also</span></span>  
 [<span data-ttu-id="c11c2-117">ICorDebugSymbolProvider arabirimi</span><span class="sxs-lookup"><span data-stu-id="c11c2-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c11c2-118">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c11c2-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
