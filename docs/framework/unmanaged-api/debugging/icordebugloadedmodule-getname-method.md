---
title: ICorDebugLoadedModule::GetName Yöntemi
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: c18af45184f5a9485e13b9d4789bff2c570834cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731858"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="ca94f-102">ICorDebugLoadedModule::GetName Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ca94f-102">ICorDebugLoadedModule::GetName Method</span></span>

<span data-ttu-id="ca94f-103">Yüklenen modülün adını alır.</span><span class="sxs-lookup"><span data-stu-id="ca94f-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca94f-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ca94f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ca94f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ca94f-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ca94f-106">'ndaki Arabellekteki karakterlerin sayısı `szName` .</span><span class="sxs-lookup"><span data-stu-id="ca94f-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ca94f-107">dışı Gerçekte arabelleğe yazılan karakter sayısına yönelik bir işaretçi `szName` .</span><span class="sxs-lookup"><span data-stu-id="ca94f-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ca94f-108">dışı Yüklenen modülün adını içeren bir karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="ca94f-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ca94f-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ca94f-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ca94f-110">Bu yöntem yalnızca .NET Native kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="ca94f-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca94f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ca94f-111">Requirements</span></span>  

 <span data-ttu-id="ca94f-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca94f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca94f-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ca94f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ca94f-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ca94f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ca94f-115">**.NET Framework sürümleri:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca94f-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca94f-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ca94f-116">See also</span></span>

- [<span data-ttu-id="ca94f-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ca94f-117">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ca94f-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ca94f-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
