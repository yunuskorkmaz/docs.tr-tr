---
title: 'ICorDebugStaticFieldSymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: 75f5324296f9b42406157d06351f7e680a749444
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378746"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="4bf4d-102">ICorDebugStaticFieldSymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bf4d-102">ICorDebugStaticFieldSymbol::GetName Method</span></span>
<span data-ttu-id="4bf4d-103">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-103">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bf4d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bf4d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bf4d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bf4d-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="4bf4d-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="4bf4d-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="4bf4d-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="4bf4d-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="4bf4d-108">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-108">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bf4d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bf4d-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bf4d-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bf4d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bf4d-111">Requirements</span></span>  
 <span data-ttu-id="4bf4d-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bf4d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bf4d-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4bf4d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bf4d-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="4bf4d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bf4d-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bf4d-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf4d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-116">See also</span></span>

- [<span data-ttu-id="4bf4d-117">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bf4d-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="4bf4d-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4bf4d-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
