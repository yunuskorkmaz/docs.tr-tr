---
title: 'ICorDebugStaticFieldSymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: e961ae064bd5bb2c97175b4506ddd8c0f17d3b32
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131790"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="3cb86-102">ICorDebugStaticFieldSymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cb86-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="3cb86-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="3cb86-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cb86-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cb86-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cb86-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3cb86-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="3cb86-106">'ndaki `szName` arabelleğindeki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="3cb86-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3cb86-107">dışı Gerçekten `szName` arabelleğine yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3cb86-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3cb86-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="3cb86-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cb86-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cb86-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cb86-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="3cb86-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cb86-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cb86-111">Requirements</span></span>  
 <span data-ttu-id="3cb86-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cb86-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cb86-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3cb86-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cb86-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3cb86-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cb86-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cb86-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cb86-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cb86-116">See also</span></span>

- [<span data-ttu-id="3cb86-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cb86-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="3cb86-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3cb86-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
