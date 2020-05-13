---
title: 'Icordebugınstancefieldsymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 0f1b648f494a2f2676374cfd13db46b70f1f195c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83210000"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="b0b67-102">Icordebugınstancefieldsymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0b67-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="b0b67-103">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="b0b67-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0b67-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0b67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0b67-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="b0b67-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="b0b67-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b0b67-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="b0b67-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b0b67-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="b0b67-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0b67-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0b67-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b0b67-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="b0b67-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0b67-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0b67-111">Requirements</span></span>  
 <span data-ttu-id="b0b67-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0b67-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0b67-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b0b67-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0b67-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0b67-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0b67-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0b67-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b67-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0b67-116">See also</span></span>

- [<span data-ttu-id="b0b67-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0b67-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b0b67-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="b0b67-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
