---
title: ICorDebugStaticFieldSymbol::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: b1f5ca266f51df730dfb840c7bf003c47f31ece9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178520"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="8635b-102">ICorDebugStaticFieldSymbol::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8635b-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="8635b-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="8635b-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8635b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8635b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8635b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8635b-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="8635b-106">[içinde] `szName` Arabellekteki karakter sayısı.</span><span class="sxs-lookup"><span data-stu-id="8635b-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="8635b-107">[çıkış] Arabelleğe yazılan karakter sayısına `szName` işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8635b-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="8635b-108">[çıkış] Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="8635b-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8635b-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8635b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8635b-110">Bu yöntem yalnızca .NET Native ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="8635b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8635b-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8635b-111">Requirements</span></span>  
 <span data-ttu-id="8635b-112">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8635b-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8635b-113">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8635b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8635b-114">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8635b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8635b-115">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8635b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8635b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8635b-116">See also</span></span>

- [<span data-ttu-id="8635b-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8635b-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="8635b-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8635b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
