---
title: 'Icordebugınstancefieldsymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b1b3cc489c504942806b043fa2e3b76d5415d84
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936943"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="98946-102">Icordebugınstancefieldsymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98946-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="98946-103">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="98946-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98946-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98946-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,   
   [out] ULONG32 *pcchName,   
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98946-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="98946-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="98946-106">'ndaki `szName` Arabellekteki karakterlerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="98946-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="98946-107">dışı Gerçekte `szName` arabelleğe yazılan karakter sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="98946-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="98946-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="98946-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98946-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="98946-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="98946-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="98946-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98946-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98946-111">Requirements</span></span>  
 <span data-ttu-id="98946-112">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98946-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98946-113">**Üst bilgi** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="98946-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98946-114">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="98946-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98946-115">**.NET Framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98946-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98946-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98946-116">See also</span></span>

- [<span data-ttu-id="98946-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98946-117">ICorDebugInstanceFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="98946-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98946-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
