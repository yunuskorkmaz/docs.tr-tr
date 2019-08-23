---
title: 'Icordebugmergedassemblyrecord:: GetIndex yöntemi'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca304b90cee291ef86e225c2b0691631833e53a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917940"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="dfa0f-102">Icordebugmergedassemblyrecord:: GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="dfa0f-102">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>
<span data-ttu-id="dfa0f-103">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="dfa0f-103">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfa0f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dfa0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dfa0f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dfa0f-105">Parameters</span></span>  
 `pIndex`  
 <span data-ttu-id="dfa0f-106">dışı Ön ek dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="dfa0f-106">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dfa0f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dfa0f-107">Remarks</span></span>  
 <span data-ttu-id="dfa0f-108">Ön ek dizini, birleştirilmiş meta veri türü adlarında ad çakışmalarını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="dfa0f-108">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dfa0f-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="dfa0f-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfa0f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dfa0f-110">Requirements</span></span>  
 <span data-ttu-id="dfa0f-111">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfa0f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfa0f-112">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="dfa0f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dfa0f-113">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="dfa0f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dfa0f-114">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfa0f-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfa0f-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dfa0f-115">See also</span></span>

- [<span data-ttu-id="dfa0f-116">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dfa0f-116">ICorDebugMergedAssemblyRecord Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="dfa0f-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dfa0f-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
