---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: f207cd1c612b6444a9512adaa356ac2d01de7b9f
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788457"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="7c464-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="7c464-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="7c464-103">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="7c464-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c464-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c464-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7c464-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7c464-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="7c464-106">dışı Yüklenen modüldeki bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7c464-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7c464-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7c464-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c464-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="7c464-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c464-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c464-109">Requirements</span></span>  
 <span data-ttu-id="7c464-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c464-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c464-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7c464-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c464-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="7c464-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c464-113">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c464-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c464-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7c464-114">See also</span></span>

- [<span data-ttu-id="7c464-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7c464-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="7c464-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7c464-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
