---
title: 'ICorDebugStaticFieldSymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2187a205b41388d191ad4f06db6d6caa86971e13
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913409"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="b8dd5-102">ICorDebugStaticFieldSymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b8dd5-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="b8dd5-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8dd5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b8dd5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8dd5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b8dd5-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b8dd5-106">'ndaki `szName` Arabellekteki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b8dd5-107">dışı Gerçekte `szName` arabelleğe yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b8dd5-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8dd5-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b8dd5-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8dd5-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8dd5-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b8dd5-111">Requirements</span></span>  
 <span data-ttu-id="b8dd5-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8dd5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8dd5-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b8dd5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8dd5-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b8dd5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8dd5-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8dd5-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8dd5-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b8dd5-116">See also</span></span>

- [<span data-ttu-id="b8dd5-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b8dd5-117">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="b8dd5-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b8dd5-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
