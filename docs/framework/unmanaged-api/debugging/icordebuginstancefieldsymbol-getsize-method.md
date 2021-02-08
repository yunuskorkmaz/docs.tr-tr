---
description: ': Icordebugınstancefieldsymbol:: GetSize yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugınstancefieldsymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: fa143620b57ec053ab26ff79b7ea2b2f386431e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791159"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="a9682-103">Icordebugınstancefieldsymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="a9682-103">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="a9682-104">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="a9682-104">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a9682-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a9682-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a9682-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a9682-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="a9682-107">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a9682-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a9682-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a9682-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a9682-109">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a9682-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a9682-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a9682-110">Requirements</span></span>  

 <span data-ttu-id="a9682-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a9682-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a9682-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a9682-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a9682-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a9682-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a9682-114">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a9682-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9682-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a9682-115">See also</span></span>

- [<span data-ttu-id="a9682-116">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a9682-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="a9682-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a9682-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
