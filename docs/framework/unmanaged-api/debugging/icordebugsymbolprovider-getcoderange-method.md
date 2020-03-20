---
title: ICorDebugSymbolProvider::GetCodeRange Yöntemi
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 81babade2ba499ce9326c664e83fa582abbd216f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178474"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="dbe8d-102">ICorDebugSymbolProvider::GetCodeRange Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dbe8d-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="dbe8d-103">Yöntemde göreli sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="dbe8d-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe8d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dbe8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dbe8d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dbe8d-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="dbe8d-106">[içinde] Bir yöntemdeki göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="dbe8d-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="dbe8d-107">[çıkış] Yöntemin başlangıç adresine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dbe8d-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="dbe8d-108">Yöntem kodu boyutu (yöntem kodu bayt sayısı) için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dbe8d-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dbe8d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dbe8d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dbe8d-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dbe8d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbe8d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dbe8d-111">Requirements</span></span>  
 <span data-ttu-id="dbe8d-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbe8d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbe8d-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dbe8d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dbe8d-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dbe8d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dbe8d-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbe8d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbe8d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dbe8d-116">See also</span></span>

- [<span data-ttu-id="dbe8d-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dbe8d-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="dbe8d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dbe8d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
