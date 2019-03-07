---
title: ICorDebugSymbolProvider::GetCodeRange yöntemi
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 392f526df53474dd2926e631e24ec5449bd1b199
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498477"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="137c5-102">ICorDebugSymbolProvider::GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="137c5-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="137c5-103">Yöntemi başlangıç adresi ve bir yöntemde göreli sanal adres (RVA) verilen boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="137c5-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="137c5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="137c5-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="137c5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="137c5-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="137c5-106">[in] Bir yöntem in göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="137c5-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="137c5-107">[out] Yöntemi başlangıç adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="137c5-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="137c5-108">Yöntemi kod boyutu (yöntemin koduna bayt sayısı) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="137c5-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137c5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="137c5-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="137c5-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="137c5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="137c5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="137c5-111">Requirements</span></span>  
 <span data-ttu-id="137c5-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="137c5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="137c5-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="137c5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="137c5-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="137c5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="137c5-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="137c5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="137c5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="137c5-116">See also</span></span>
- [<span data-ttu-id="137c5-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="137c5-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="137c5-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="137c5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
