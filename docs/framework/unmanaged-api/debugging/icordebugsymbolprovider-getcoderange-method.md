---
title: 'ICorDebugSymbolProvider:: GetCodeRange yöntemi'
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: dbe042641cadae182efac30502a70631be359bbe
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791648"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="71f90-102">ICorDebugSymbolProvider:: GetCodeRange yöntemi</span><span class="sxs-lookup"><span data-stu-id="71f90-102">ICorDebugSymbolProvider::GetCodeRange Method</span></span>
<span data-ttu-id="71f90-103">Bir yöntemde göreli bir sanal adres (RVA) verilen yöntem başlangıç adresini ve boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="71f90-103">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71f90-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71f90-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,   
   [out] ULONG32* pCodeStartAddress,   
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71f90-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71f90-105">Parameters</span></span>  
 `codeRva`  
 <span data-ttu-id="71f90-106">'ndaki Bir yöntemde göreli sanal adres (RVA).</span><span class="sxs-lookup"><span data-stu-id="71f90-106">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="71f90-107">dışı Metodun başlangıç adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="71f90-107">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="71f90-108">Yöntem kodu boyutuna yönelik bir işaretçi (yöntemin kodunun bayt sayısı).</span><span class="sxs-lookup"><span data-stu-id="71f90-108">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71f90-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71f90-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71f90-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="71f90-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71f90-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71f90-111">Requirements</span></span>  
 <span data-ttu-id="71f90-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71f90-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71f90-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="71f90-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="71f90-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="71f90-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="71f90-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71f90-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71f90-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71f90-116">See also</span></span>

- [<span data-ttu-id="71f90-117">ICorDebugSymbolProvider Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71f90-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="71f90-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71f90-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
