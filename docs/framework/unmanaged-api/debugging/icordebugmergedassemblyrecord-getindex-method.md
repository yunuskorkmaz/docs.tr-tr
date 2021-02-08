---
description: ': Icordebugmergedassemblyrecord:: GetIndex yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugmergedassemblyrecord:: GetIndex yöntemi'
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: f3a51c5ed5edacc9678c965ac385d0969e2ee8a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801117"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="e28a0-103">Icordebugmergedassemblyrecord:: GetIndex yöntemi</span><span class="sxs-lookup"><span data-stu-id="e28a0-103">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>

<span data-ttu-id="e28a0-104">Derlemenin önek dizinini alır.</span><span class="sxs-lookup"><span data-stu-id="e28a0-104">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28a0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e28a0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e28a0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e28a0-106">Parameters</span></span>  

 `pIndex`  
 <span data-ttu-id="e28a0-107">dışı Ön ek dizinine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e28a0-107">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e28a0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e28a0-108">Remarks</span></span>  

 <span data-ttu-id="e28a0-109">Ön ek dizini, birleştirilmiş meta veri türü adlarında ad çakışmalarını engellemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e28a0-109">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e28a0-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e28a0-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e28a0-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e28a0-111">Requirements</span></span>  

 <span data-ttu-id="e28a0-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e28a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e28a0-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e28a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e28a0-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e28a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e28a0-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e28a0-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28a0-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e28a0-116">See also</span></span>

- [<span data-ttu-id="e28a0-117">ICorDebugMergedAssemblyRecord Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e28a0-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="e28a0-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e28a0-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
