---
title: "ICorDebugVariableHomeEnum::Next yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHomeEnum.Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3bab158cbbe2eaf6e52ae0df6a0eed86d3d0b8ce
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="d9605-102">ICorDebugVariableHomeEnum::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="d9605-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="d9605-103">Belirtilen sayıda alır [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="d9605-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9605-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d9605-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d9605-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d9605-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d9605-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="d9605-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="d9605-107">Her biri işaret işaretçileri, bir dizi bir [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişken ya da işlevin bağımsız değişkeninin hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="d9605-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d9605-108">[out] Gerçekte nesneleri döndürülen örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="d9605-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d9605-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d9605-109">Return Value</span></span>  
 <span data-ttu-id="d9605-110">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="d9605-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="d9605-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d9605-111">HRESULT</span></span>|<span data-ttu-id="d9605-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d9605-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="d9605-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="d9605-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="d9605-114">Gerçek örneklerinin sayısını alınan, yansıtılan `pceltFetched`, istenen örneklerinin sayısını'dan küçük.</span><span class="sxs-lookup"><span data-stu-id="d9605-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9605-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d9605-115">Remarks</span></span>  
 <span data-ttu-id="d9605-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi alır en fazla `celt` Numaralayıcı geçerli konumdan başlayarak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="d9605-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="d9605-117">Yöntem döndüğünde `pceltFetched` alınan nesneler gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="d9605-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9605-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d9605-118">Requirements</span></span>  
 <span data-ttu-id="d9605-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9605-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9605-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9605-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9605-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9605-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9605-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9605-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9605-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d9605-123">See Also</span></span>  
 [<span data-ttu-id="d9605-124">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9605-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="d9605-125">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d9605-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
