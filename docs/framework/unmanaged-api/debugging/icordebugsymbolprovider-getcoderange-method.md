---
title: 'ICorDebugSymbolProvider:: GetCodeRange yöntemi'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: f61a98dbd5a65207a46e033d54f9d5f60adac201
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709134"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="e8e88-102">ICorDebugSymbolProvider:: GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="e8e88-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="e8e88-103">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="e8e88-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8e88-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e8e88-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e8e88-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e8e88-105">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="e8e88-106">'ndaki Bir yöntemde göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="e8e88-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="e8e88-107">dışı Metodun başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e8e88-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="e8e88-108">Yöntem kodu boyutuna yönelik bir işaretçi (yöntemin kodunun bayt sayısı).</span><span class="sxs-lookup"><span data-stu-id="e8e88-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8e88-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e8e88-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8e88-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e8e88-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8e88-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e8e88-111">Requirements</span></span>  

 <span data-ttu-id="e8e88-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8e88-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8e88-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8e88-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8e88-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e8e88-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8e88-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8e88-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8e88-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e8e88-116">See also</span></span>

- [<span data-ttu-id="e8e88-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e8e88-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="e8e88-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e8e88-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
