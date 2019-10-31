---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 3f2f8a1721847b8f7b845c42aa3c91e032c2d474
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122638"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="74e59-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="74e59-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="74e59-103">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="74e59-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74e59-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74e59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74e59-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74e59-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="74e59-106">dışı Yüklenen modüldeki bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74e59-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74e59-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74e59-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74e59-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="74e59-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e59-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74e59-109">Requirements</span></span>  
 <span data-ttu-id="74e59-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e59-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e59-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74e59-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74e59-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="74e59-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74e59-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e59-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e59-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="74e59-114">See also</span></span>

- [<span data-ttu-id="74e59-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74e59-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="74e59-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="74e59-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
