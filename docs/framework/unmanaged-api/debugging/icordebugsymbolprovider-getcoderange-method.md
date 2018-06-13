---
title: ICorDebugSymbolProvider::GetCodeRange yöntemi
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f60ba1c68e95363a59c5a1d217756664f63e5256
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420130"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="c9f1b-102">ICorDebugSymbolProvider::GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="c9f1b-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="c9f1b-103">Yöntemi başlangıç adresi ve bir yöntem göreli sanal adres (RVA) verilen boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="c9f1b-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9f1b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c9f1b-104">Syntax</span></span>  
  
```  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9f1b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c9f1b-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="c9f1b-106">[in] Bir yöntem göreli sanal adres (RAV).</span><span class="sxs-lookup"><span data-stu-id="c9f1b-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="c9f1b-107">[out] Yöntemi başlangıç adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9f1b-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="c9f1b-108">Yöntem kod boyutu (yöntemin kodunun bayt sayısı) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c9f1b-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9f1b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c9f1b-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9f1b-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="c9f1b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9f1b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c9f1b-111">Requirements</span></span>  
 <span data-ttu-id="c9f1b-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9f1b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9f1b-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9f1b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9f1b-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9f1b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9f1b-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9f1b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9f1b-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c9f1b-116">See Also</span></span>  
 [<span data-ttu-id="c9f1b-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c9f1b-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [<span data-ttu-id="c9f1b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c9f1b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
