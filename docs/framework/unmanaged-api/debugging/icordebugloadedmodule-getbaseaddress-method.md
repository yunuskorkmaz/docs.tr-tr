---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 190c9114cffa537ba162b19abdf30d5a6aee87f8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788454"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="0bce2-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="0bce2-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="0bce2-103">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="0bce2-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bce2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0bce2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0bce2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0bce2-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="0bce2-106">dışı Yüklenen modülün temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0bce2-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bce2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0bce2-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0bce2-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0bce2-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bce2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0bce2-109">Requirements</span></span>  
 <span data-ttu-id="0bce2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bce2-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bce2-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0bce2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0bce2-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0bce2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bce2-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bce2-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bce2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bce2-114">See also</span></span>

- [<span data-ttu-id="0bce2-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0bce2-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="0bce2-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0bce2-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
