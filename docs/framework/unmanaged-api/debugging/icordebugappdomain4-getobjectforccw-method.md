---
title: ICorDebugAppDomain4::GetObjectForCCW Metodu
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 50f46394c809321f0bd256e4c8d75b76fc7c2c70
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784857"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="945ce-102">ICorDebugAppDomain4::GetObjectForCCW Metodu</span><span class="sxs-lookup"><span data-stu-id="945ce-102">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>
<span data-ttu-id="945ce-103">COM çağrılabilir sarmalayıcı (CCW) işaretçisinden yönetilen bir nesne alır.</span><span class="sxs-lookup"><span data-stu-id="945ce-103">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="945ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="945ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,   
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="945ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="945ce-105">Parameters</span></span>  
 `ccwPointer`  
 <span data-ttu-id="945ce-106">'ndaki COM çağrılabilir sarmalayıcı (CCW) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="945ce-106">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="945ce-107">dışı Verilen CCW işaretçisine karşılık gelen yönetilen nesneyi temsil eden "ICorDebugValue" nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="945ce-107">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="945ce-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="945ce-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="945ce-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="945ce-109">Requirements</span></span>  
 <span data-ttu-id="945ce-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="945ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="945ce-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="945ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="945ce-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="945ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="945ce-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="945ce-113">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="945ce-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="945ce-114">See also</span></span>

- [<span data-ttu-id="945ce-115">ICorDebugAppDomain4 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="945ce-115">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="945ce-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="945ce-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
