---
title: ICorDebugInstanceFieldSymbol::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: dd925cc213ed8a6c5d1def85b3e6335751c1b594
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178768"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="afbe7-102">ICorDebugInstanceFieldSymbol::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="afbe7-102">ICorDebugInstanceFieldSymbol::GetName Method</span></span>
<span data-ttu-id="afbe7-103">Örnek alanının adını alır.</span><span class="sxs-lookup"><span data-stu-id="afbe7-103">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afbe7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="afbe7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afbe7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="afbe7-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="afbe7-106">[içinde] `szName` Arabellekteki karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="afbe7-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="afbe7-107">[çıkış] Arabelleğe yazılan karakter sayısına `szName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="afbe7-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="afbe7-108">[çıkış] Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="afbe7-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afbe7-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="afbe7-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="afbe7-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="afbe7-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afbe7-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="afbe7-111">Requirements</span></span>  
 <span data-ttu-id="afbe7-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afbe7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afbe7-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afbe7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afbe7-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afbe7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afbe7-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afbe7-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afbe7-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="afbe7-116">See also</span></span>

- [<span data-ttu-id="afbe7-117">ICorDebugInstanceFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="afbe7-117">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="afbe7-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="afbe7-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
