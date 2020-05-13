---
title: 'Icordebugınstancefieldsymbol:: GetOffset Yöntemi'
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 7d553c1a446e06f34c20da18c0edfe6773cfb597
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209987"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="b09d3-102">Icordebugınstancefieldsymbol:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b09d3-102">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>
<span data-ttu-id="b09d3-103">Üst sınıfındaki bu örnek alanının bayt cinsinden konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="b09d3-103">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b09d3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b09d3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b09d3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b09d3-105">Parameters</span></span>  
 `pcbOffset`  
 <span data-ttu-id="b09d3-106">Bu örnek alanın üst sınıfında kaydırılacağı bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b09d3-106">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b09d3-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b09d3-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b09d3-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b09d3-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b09d3-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b09d3-109">Requirements</span></span>  
 <span data-ttu-id="b09d3-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b09d3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b09d3-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b09d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b09d3-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b09d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b09d3-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b09d3-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b09d3-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b09d3-114">See also</span></span>

- [<span data-ttu-id="b09d3-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b09d3-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b09d3-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b09d3-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
