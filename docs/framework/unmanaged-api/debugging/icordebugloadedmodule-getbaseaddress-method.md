---
title: ICorDebugLoadedModule::GetBaseAddress Metodu
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 8af814ff2eaaf3ae6dae9031c13bf37ea0c1236b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122652"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="26728-102">ICorDebugLoadedModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="26728-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>
<span data-ttu-id="26728-103">Yüklenen modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="26728-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26728-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="26728-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26728-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="26728-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="26728-106">dışı Yüklenen modülün temel adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="26728-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26728-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="26728-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="26728-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="26728-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26728-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="26728-109">Requirements</span></span>  
 <span data-ttu-id="26728-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26728-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26728-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="26728-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="26728-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="26728-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26728-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26728-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26728-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="26728-114">See also</span></span>

- [<span data-ttu-id="26728-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="26728-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="26728-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="26728-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
