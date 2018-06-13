---
title: ICorDebugLoadedModule::GetName Metodu
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bfdf8e43258d14e7298119ce4d7136ea5de54c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415047"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="65abd-102">ICorDebugLoadedModule::GetName Metodu</span><span class="sxs-lookup"><span data-stu-id="65abd-102">ICorDebugLoadedModule::GetName Method</span></span>
<span data-ttu-id="65abd-103">Yüklenen modül adını alır.</span><span class="sxs-lookup"><span data-stu-id="65abd-103">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65abd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65abd-104">Syntax</span></span>  
  
```  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65abd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65abd-105">Parameters</span></span>  
 `cchName`  
 <span data-ttu-id="65abd-106">[in] Karakter sayısını `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="65abd-106">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="65abd-107">[out] Gerçekte yazılan karakter sayısını gösteren bir işaretçi `szName` arabellek.</span><span class="sxs-lookup"><span data-stu-id="65abd-107">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="65abd-108">[out] Yüklenen modülünün adını içeren karakter dizisi.</span><span class="sxs-lookup"><span data-stu-id="65abd-108">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65abd-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="65abd-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65abd-110">Bu yöntem yalnızca .NET yerel ile kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="65abd-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65abd-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65abd-111">Requirements</span></span>  
 <span data-ttu-id="65abd-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65abd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65abd-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="65abd-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="65abd-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65abd-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65abd-115">**.NET framework sürümleri:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65abd-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65abd-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65abd-116">See Also</span></span>  
 [<span data-ttu-id="65abd-117">ICorDebugLoadedModule Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65abd-117">ICorDebugLoadedModule Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 [<span data-ttu-id="65abd-118">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="65abd-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
