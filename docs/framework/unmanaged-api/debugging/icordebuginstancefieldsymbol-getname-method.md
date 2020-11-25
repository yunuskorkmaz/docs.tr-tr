---
title: 'Icordebugınstancefieldsymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: e466a62761cc6dd1f1fc0a54f05d54f85c190d07
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724942"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="ba835-102">Icordebugınstancefieldsymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba835-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>

<span data-ttu-id="ba835-103">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="ba835-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba835-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ba835-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba835-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba835-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ba835-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="ba835-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ba835-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="ba835-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ba835-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="ba835-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ba835-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba835-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ba835-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ba835-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba835-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba835-111">Requirements</span></span>  

 <span data-ttu-id="ba835-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba835-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba835-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ba835-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba835-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ba835-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba835-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba835-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba835-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba835-116">See also</span></span>

- [<span data-ttu-id="ba835-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba835-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="ba835-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ba835-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
