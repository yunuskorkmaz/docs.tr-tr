---
title: 'ICorDebugSymbolProvider:: GetCodeRange yöntemi'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18fd8fdf9bcfa20b686ad1f04cd8dcc3b1c26de2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964636"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="40f9b-102">ICorDebugSymbolProvider:: GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="40f9b-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="40f9b-103">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="40f9b-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f9b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="40f9b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f9b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="40f9b-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="40f9b-106">'ndaki Bir yöntemde göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="40f9b-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="40f9b-107">dışı Metodun başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="40f9b-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="40f9b-108">Yöntem kodu boyutuna yönelik bir işaretçi (yöntemin kodunun bayt sayısı).</span><span class="sxs-lookup"><span data-stu-id="40f9b-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="40f9b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40f9b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40f9b-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="40f9b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f9b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40f9b-111">Requirements</span></span>  
 <span data-ttu-id="40f9b-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f9b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f9b-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40f9b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40f9b-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="40f9b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40f9b-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f9b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f9b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40f9b-116">See also</span></span>

- [<span data-ttu-id="40f9b-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40f9b-117">ICorDebugSymbolProvider Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="40f9b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40f9b-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
