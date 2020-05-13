---
title: 'Icordebugınstancefieldsymbol:: GetSize yöntemi'
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: 3d3c6881ecd54fc48be92e5ea0dc74a5cfdabd8f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209959"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="31869-102">Icordebugınstancefieldsymbol:: GetSize yöntemi</span><span class="sxs-lookup"><span data-stu-id="31869-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="31869-103">Örnek alanının bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="31869-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31869-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31869-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31869-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31869-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="31869-106">dışı Alanın uzunluğuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="31869-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="31869-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31869-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31869-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="31869-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31869-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31869-109">Requirements</span></span>  
 <span data-ttu-id="31869-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31869-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31869-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="31869-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="31869-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31869-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31869-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31869-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31869-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31869-114">See also</span></span>

- [<span data-ttu-id="31869-115">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31869-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="31869-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="31869-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
