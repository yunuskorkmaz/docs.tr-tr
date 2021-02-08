---
description: ': Icordebugınstancefieldsymbol:: GetName Yöntemi hakkında daha fazla bilgi edinin'
title: 'Icordebugınstancefieldsymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 9cc2106d1527aa0b4d9e5c52115b703ffe55037f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791198"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="a2958-103">Icordebugınstancefieldsymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2958-103">ICorDebugInstanceFieldSymbol::GetName Method</span></span>

<span data-ttu-id="a2958-104">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="a2958-104">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2958-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2958-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2958-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2958-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="a2958-107">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="a2958-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="a2958-108">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="a2958-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="a2958-109">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="a2958-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2958-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2958-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a2958-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2958-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2958-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2958-112">Requirements</span></span>  

 <span data-ttu-id="a2958-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2958-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2958-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a2958-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2958-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2958-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2958-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2958-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2958-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2958-117">See also</span></span>

- [<span data-ttu-id="a2958-118">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2958-118">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="a2958-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a2958-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
