---
description: ': ICorDebugStaticFieldSymbol:: GetName metodu hakkında daha fazla bilgi edinin'
title: 'ICorDebugStaticFieldSymbol:: GetName Yöntemi'
ms.date: 03/30/2017
ms.assetid: e2be4af2-15d1-4e6a-8b68-1d78c93294a4
ms.openlocfilehash: c74de604f5880a69b77c89e56a82ae08517dd69c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794708"
---
# <a name="icordebugstaticfieldsymbolgetname-method"></a><span data-ttu-id="87bea-103">ICorDebugStaticFieldSymbol:: GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="87bea-103">ICorDebugStaticFieldSymbol::GetName Method</span></span>

<span data-ttu-id="87bea-104">Statik alanın adını alır.</span><span class="sxs-lookup"><span data-stu-id="87bea-104">Gets the name of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87bea-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="87bea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87bea-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="87bea-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="87bea-107">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="87bea-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="87bea-108">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="87bea-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="87bea-109">dışı Döndürülen adı depolayan bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="87bea-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87bea-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="87bea-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="87bea-111">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="87bea-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87bea-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="87bea-112">Requirements</span></span>  

 <span data-ttu-id="87bea-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87bea-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87bea-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="87bea-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="87bea-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="87bea-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87bea-116">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87bea-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87bea-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="87bea-117">See also</span></span>

- [<span data-ttu-id="87bea-118">ICorDebugStaticFieldSymbol Arabirimi</span><span class="sxs-lookup"><span data-stu-id="87bea-118">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="87bea-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="87bea-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
