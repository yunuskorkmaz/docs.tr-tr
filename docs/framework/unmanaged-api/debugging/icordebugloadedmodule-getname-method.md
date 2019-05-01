---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9bf09c01d24315c3f239911326f1844a0b2cc101
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946269"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="d1107-102">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1107-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="d1107-103">Yüklenen bir modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="d1107-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1107-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1107-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1107-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d1107-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="d1107-106">[in] Karakter sayısı `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="d1107-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="d1107-107">[out] Gerçekte yazılan karakter sayısı için bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="d1107-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="d1107-108">[out] Yüklenen bir modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="d1107-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1107-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d1107-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1107-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="d1107-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1107-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1107-111">Requirements</span></span>  
 <span data-ttu-id="d1107-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1107-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1107-113">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1107-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1107-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1107-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1107-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1107-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1107-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1107-116">See also</span></span>

- [<span data-ttu-id="d1107-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1107-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="d1107-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d1107-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
