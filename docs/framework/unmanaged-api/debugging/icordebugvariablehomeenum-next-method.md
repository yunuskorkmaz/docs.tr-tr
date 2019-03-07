---
title: ICorDebugVariableHomeEnum::Next yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8dd2d188b273d857ba92914f490e3448ba01601c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492484"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="c81cb-102">ICorDebugVariableHomeEnum::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="c81cb-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="c81cb-103">Belirtilen sayıda alır [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) örnekleriyle yerel değişkenleri ve bir işlevdeki bağımsız değişkenler hakkındaki bilgileri içerir.</span><span class="sxs-lookup"><span data-stu-id="c81cb-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c81cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c81cb-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c81cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c81cb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c81cb-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="c81cb-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="c81cb-107">Bir dizi işaretçileri, her biri için işaret eden bir [Icordebugvariablehome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) bir yerel değişken veya işlev bağımsız değişken hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="c81cb-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="c81cb-108">[out] Aslında nesneler döndürüldü örneklerinin sayısı.</span><span class="sxs-lookup"><span data-stu-id="c81cb-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c81cb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c81cb-109">Return Value</span></span>  
 <span data-ttu-id="c81cb-110">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="c81cb-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="c81cb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c81cb-111">HRESULT</span></span>|<span data-ttu-id="c81cb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c81cb-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="c81cb-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="c81cb-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="c81cb-114">Örnek gerçek sayısını alınan açıklandığı `pceltFetched`, istenen örnek sayısı'dan küçük.</span><span class="sxs-lookup"><span data-stu-id="c81cb-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c81cb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c81cb-115">Remarks</span></span>  
 <span data-ttu-id="c81cb-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi alır. en fazla `celt` Numaralandırıcı geçerli konumunda başlayan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="c81cb-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="c81cb-117">Yöntem döndürüldüğünde `pceltFetched` alınan nesneler gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="c81cb-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c81cb-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c81cb-118">Requirements</span></span>  
 <span data-ttu-id="c81cb-119">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c81cb-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c81cb-120">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c81cb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c81cb-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c81cb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c81cb-122">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c81cb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c81cb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c81cb-123">See also</span></span>
- [<span data-ttu-id="c81cb-124">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c81cb-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="c81cb-125">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c81cb-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
