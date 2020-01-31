---
title: 'Icordebugmergedassemblyrecord:: GetIndex yöntemi'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: c8fb5ace27fbf7fbebdaca5822af99cd6673e8cf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793133"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="5c44a-102">Icordebugmergedassemblyrecord:: GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="5c44a-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="5c44a-103">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="5c44a-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c44a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5c44a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5c44a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5c44a-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="5c44a-106">dışı Ön ek dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="5c44a-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5c44a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5c44a-107">Remarks</span></span>  
 <span data-ttu-id="5c44a-108">Ön ek dizini, birleştirilmiş meta veri türü adlarında ad çakışmalarını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5c44a-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5c44a-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="5c44a-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c44a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5c44a-110">Requirements</span></span>  
 <span data-ttu-id="5c44a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c44a-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c44a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5c44a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5c44a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5c44a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c44a-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c44a-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c44a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c44a-115">See also</span></span>

- [<span data-ttu-id="5c44a-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5c44a-116">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="5c44a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="5c44a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
