---
description: 'Şu konuda daha fazla bilgi edinin: ıcordebugvariablehomeenum:: Next yöntemi'
title: 'Icordebugvariablehomeenum:: Next yöntemi'
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
ms.openlocfilehash: 0aa0174e67bceaa724ddfeadc2560d12e112b859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790613"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="298dd-103">Icordebugvariablehomeenum:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="298dd-103">ICorDebugVariableHomeEnum::Next Method</span></span>

<span data-ttu-id="298dd-104">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="298dd-104">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="298dd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="298dd-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="298dd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="298dd-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="298dd-107">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="298dd-107">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="298dd-108">Her biri bir işlevin yerel değişkeni veya bağımsız değişkeni hakkında bilgi sağlayan [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="298dd-108">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="298dd-109">dışı Gerçekte nesnelerde döndürülen örneklerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="298dd-109">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="298dd-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="298dd-110">Return Value</span></span>  

 <span data-ttu-id="298dd-111">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="298dd-111">The method returns the following values.</span></span>  
  
|<span data-ttu-id="298dd-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="298dd-112">HRESULT</span></span>|<span data-ttu-id="298dd-113">Description</span><span class="sxs-lookup"><span data-stu-id="298dd-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="298dd-114">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="298dd-114">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="298dd-115">İçinde yansıtıldıkça alınan örneklerin gerçek sayısı `pceltFetched` , istenen örnek sayısından daha az.</span><span class="sxs-lookup"><span data-stu-id="298dd-115">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="298dd-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="298dd-116">Remarks</span></span>  

 <span data-ttu-id="298dd-117">[Icordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi, `celt` Numaralandırıcının geçerli konumundan başlayarak en fazla nesne alır.</span><span class="sxs-lookup"><span data-stu-id="298dd-117">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="298dd-118">Yöntemi döndürüldüğünde, `pceltFetched` alınan nesnelerin gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="298dd-118">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="298dd-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="298dd-119">Requirements</span></span>  

 <span data-ttu-id="298dd-120">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="298dd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="298dd-121">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="298dd-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="298dd-122">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="298dd-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="298dd-123">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="298dd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="298dd-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="298dd-124">See also</span></span>

- [<span data-ttu-id="298dd-125">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="298dd-125">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="298dd-126">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="298dd-126">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
