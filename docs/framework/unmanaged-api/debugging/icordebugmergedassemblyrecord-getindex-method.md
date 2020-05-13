---
title: 'Icordebugmergedassemblyrecord:: GetIndex yöntemi'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: b13e589e32b3317b567a4a89a5b48fc1299a1a84
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206947"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="eb99e-102">Icordebugmergedassemblyrecord:: GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="eb99e-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="eb99e-103">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="eb99e-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb99e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eb99e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eb99e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eb99e-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="eb99e-106">dışı Ön ek dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eb99e-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eb99e-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eb99e-107">Remarks</span></span>  
 <span data-ttu-id="eb99e-108">Ön ek dizini, birleştirilmiş meta veri türü adlarında ad çakışmalarını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="eb99e-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="eb99e-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="eb99e-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb99e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eb99e-110">Requirements</span></span>  
 <span data-ttu-id="eb99e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb99e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb99e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="eb99e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eb99e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="eb99e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eb99e-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb99e-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb99e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb99e-115">See also</span></span>

- [<span data-ttu-id="eb99e-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="eb99e-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="eb99e-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eb99e-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
