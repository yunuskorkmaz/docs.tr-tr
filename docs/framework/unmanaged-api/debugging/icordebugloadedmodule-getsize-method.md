---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 2ed19cb4a190f2af7581a827e8bd11b748b3d4a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721328"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="18f75-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="18f75-102">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="18f75-103">Yüklenen modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="18f75-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f75-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="18f75-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18f75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18f75-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="18f75-106">dışı Yüklenen modüldeki bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18f75-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="18f75-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="18f75-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="18f75-108">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="18f75-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18f75-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18f75-109">Requirements</span></span>  

 <span data-ttu-id="18f75-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18f75-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18f75-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="18f75-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="18f75-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="18f75-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="18f75-113">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18f75-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f75-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18f75-114">See also</span></span>

- [<span data-ttu-id="18f75-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18f75-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="18f75-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="18f75-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
