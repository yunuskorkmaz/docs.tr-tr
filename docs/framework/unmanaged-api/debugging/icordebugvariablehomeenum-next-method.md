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
ms.openlocfilehash: 480317a4ec0515411f1ca8156a5bc4d06aa3f38a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="5baa2-102">ICorDebugVariableHomeEnum::Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="5baa2-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="5baa2-103">Belirtilen sayıda alır [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişkenleri ve bir işlev bağımsız değişkenleri hakkında bilgi içeren örnekleri.</span><span class="sxs-lookup"><span data-stu-id="5baa2-103">Gets the specified number of [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5baa2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5baa2-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5baa2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5baa2-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="5baa2-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="5baa2-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="5baa2-107">Her biri işaret işaretçileri, bir dizi bir [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) yerel değişken ya da işlevin bağımsız değişkeninin hakkında bilgi sağlayan nesne.</span><span class="sxs-lookup"><span data-stu-id="5baa2-107">An array of pointers, each of which points to a [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5baa2-108">[out] Gerçekte nesneleri döndürülen örnek sayısı.</span><span class="sxs-lookup"><span data-stu-id="5baa2-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5baa2-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5baa2-109">Return Value</span></span>  
 <span data-ttu-id="5baa2-110">Bu yöntem, aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="5baa2-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="5baa2-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5baa2-111">HRESULT</span></span>|<span data-ttu-id="5baa2-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5baa2-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="5baa2-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="5baa2-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="5baa2-114">Gerçek örneklerinin sayısını alınan, yansıtılan `pceltFetched`, istenen örneklerinin sayısını'dan küçük.</span><span class="sxs-lookup"><span data-stu-id="5baa2-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5baa2-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5baa2-115">Remarks</span></span>  
 <span data-ttu-id="5baa2-116">[ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) yöntemi alır en fazla `celt` Numaralayıcı geçerli konumdan başlayarak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="5baa2-116">The [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="5baa2-117">Yöntem döndüğünde `pceltFetched` alınan nesneler gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="5baa2-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5baa2-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5baa2-118">Requirements</span></span>  
 <span data-ttu-id="5baa2-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5baa2-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5baa2-120">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5baa2-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5baa2-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5baa2-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5baa2-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5baa2-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5baa2-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5baa2-123">See Also</span></span>  
 [<span data-ttu-id="5baa2-124">ICorDebugVariableHomeEnum arabirimi</span><span class="sxs-lookup"><span data-stu-id="5baa2-124">ICorDebugVariableHomeEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [<span data-ttu-id="5baa2-125">ICorDebugVariableHome arabirimi</span><span class="sxs-lookup"><span data-stu-id="5baa2-125">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
