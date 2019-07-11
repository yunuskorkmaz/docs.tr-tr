---
title: ICorDebugLoadedModule::GetSize Metodu
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 61bb5a019a8ba5450fa2859a851f4ac9425d45b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67759909"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="4bea6-102">ICorDebugLoadedModule::GetSize Metodu</span><span class="sxs-lookup"><span data-stu-id="4bea6-102">ICorDebugLoadedModule::GetSize Method</span></span>
<span data-ttu-id="4bea6-103">Yüklenen bir modülün bayt cinsinden boyutunu alır.</span><span class="sxs-lookup"><span data-stu-id="4bea6-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bea6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bea6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bea6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bea6-105">Parameters</span></span>  
 `pcBytes`  
 <span data-ttu-id="4bea6-106">[out] Yüklenen bir modülün bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4bea6-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bea6-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bea6-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4bea6-108">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4bea6-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bea6-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bea6-109">Requirements</span></span>  
 <span data-ttu-id="4bea6-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bea6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bea6-111">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bea6-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bea6-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bea6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bea6-113">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bea6-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bea6-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bea6-114">See also</span></span>

- [<span data-ttu-id="4bea6-115">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bea6-115">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="4bea6-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4bea6-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
