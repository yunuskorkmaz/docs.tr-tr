---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 4cf2c5c099de3d66878f09ff702a1cad6ddb8f57
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122632"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="cf4e7-102">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf4e7-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="cf4e7-103">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf4e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf4e7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf4e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf4e7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cf4e7-106">'ndaki `szName` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cf4e7-107">dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cf4e7-108">dışı Yüklenen modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf4e7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf4e7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cf4e7-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf4e7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf4e7-111">Requirements</span></span>  
 <span data-ttu-id="cf4e7-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf4e7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf4e7-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cf4e7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf4e7-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cf4e7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf4e7-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf4e7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4e7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf4e7-116">See also</span></span>

- [<span data-ttu-id="cf4e7-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf4e7-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="cf4e7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cf4e7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
