---
description: ': ICorDebugSymbolProvider:: GetCodeRange yöntemi hakkında daha fazla bilgi edinin'
title: 'ICorDebugSymbolProvider:: GetCodeRange yöntemi'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 98b228be7483e6365815f6b783167b20fb3bcc48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659913"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="705a7-103">ICorDebugSymbolProvider:: GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="705a7-103">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="705a7-104">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="705a7-104">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="705a7-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="705a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="705a7-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="705a7-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="705a7-107">'ndaki Bir yöntemde göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="705a7-107">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="705a7-108">dışı Metodun başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="705a7-108">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="705a7-109">Yöntem kodu boyutuna yönelik bir işaretçi (yöntemin kodunun bayt sayısı).</span><span class="sxs-lookup"><span data-stu-id="705a7-109">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="705a7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="705a7-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="705a7-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="705a7-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="705a7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="705a7-112">Requirements</span></span>  

 <span data-ttu-id="705a7-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="705a7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="705a7-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="705a7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="705a7-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="705a7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="705a7-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="705a7-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="705a7-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="705a7-117">See also</span></span>

- [<span data-ttu-id="705a7-118">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="705a7-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="705a7-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="705a7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
