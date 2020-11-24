---
title: 'ICorDebugStaticFieldSymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 6284a27921e0ba5bd3cedf07ef9f62348460ad06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677243"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="9dc3a-102">ICorDebugStaticFieldSymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dc3a-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>

<span data-ttu-id="9dc3a-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="9dc3a-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dc3a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9dc3a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9dc3a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9dc3a-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="9dc3a-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="9dc3a-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="9dc3a-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="9dc3a-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="9dc3a-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="9dc3a-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9dc3a-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9dc3a-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9dc3a-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9dc3a-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9dc3a-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dc3a-111">Requirements</span></span>  

 <span data-ttu-id="9dc3a-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dc3a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dc3a-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9dc3a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9dc3a-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9dc3a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dc3a-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9dc3a-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dc3a-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dc3a-116">See also</span></span>

- [<span data-ttu-id="9dc3a-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dc3a-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="9dc3a-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9dc3a-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
