---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 628f85f3045533ead7ace47b11573a0b1a46df46
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782047"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="cbf43-102">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cbf43-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="cbf43-103">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="cbf43-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cbf43-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cbf43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cbf43-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cbf43-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="cbf43-106">'ndaki `szName` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="cbf43-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="cbf43-107">dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cbf43-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="cbf43-108">dışı Yüklenen modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="cbf43-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cbf43-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cbf43-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cbf43-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="cbf43-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cbf43-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cbf43-111">Requirements</span></span>  
 <span data-ttu-id="cbf43-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cbf43-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cbf43-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cbf43-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cbf43-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cbf43-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cbf43-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cbf43-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cbf43-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cbf43-116">See also</span></span>

- [<span data-ttu-id="cbf43-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cbf43-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="cbf43-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cbf43-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
