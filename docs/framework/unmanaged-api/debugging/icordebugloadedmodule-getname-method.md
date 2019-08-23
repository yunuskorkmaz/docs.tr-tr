---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63341bcd6079688ed1a8e18ec8c422bca1427c72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69910073"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="a49c6-102">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a49c6-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="a49c6-103">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="a49c6-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a49c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a49c6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a49c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a49c6-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="a49c6-106">'ndaki `szName` Arabellekteki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="a49c6-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a49c6-107">dışı Gerçekte `szName` arabelleğe yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a49c6-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a49c6-108">dışı Yüklenen modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="a49c6-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a49c6-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a49c6-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a49c6-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a49c6-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a49c6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a49c6-111">Requirements</span></span>  
 <span data-ttu-id="a49c6-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a49c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a49c6-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a49c6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a49c6-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a49c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a49c6-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a49c6-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a49c6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a49c6-116">See also</span></span>

- [<span data-ttu-id="a49c6-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a49c6-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)
- [<span data-ttu-id="a49c6-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a49c6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
