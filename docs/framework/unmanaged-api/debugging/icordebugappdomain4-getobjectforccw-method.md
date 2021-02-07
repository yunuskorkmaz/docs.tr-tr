---
description: 'Daha fazla bilgi edinin: ICorDebugAppDomain4:: GetObjectForCCW yöntemi'
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 5ba4923c933d02f5d6ad5c1fd8c4d0e2ddb410d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754140"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="8f95a-103">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="8f95a-103">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>

<span data-ttu-id="8f95a-104">COM çağrılabilir sarmalayıcı (CCW) işaretçisinden yönetilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="8f95a-104">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f95a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f95a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f95a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f95a-106">Parameters</span></span>  

 `ccwPointer`  
 <span data-ttu-id="8f95a-107">'ndaki COM çağrılabilir sarmalayıcı (CCW) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="8f95a-107">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="8f95a-108">dışı Verilen CCW işaretçisine karşılık gelen yönetilen nesneyi temsil eden "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8f95a-108">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f95a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f95a-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f95a-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f95a-110">Requirements</span></span>  

 <span data-ttu-id="8f95a-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f95a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f95a-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f95a-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f95a-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f95a-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f95a-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f95a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f95a-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f95a-115">See also</span></span>

- [<span data-ttu-id="8f95a-116">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f95a-116">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="8f95a-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8f95a-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
