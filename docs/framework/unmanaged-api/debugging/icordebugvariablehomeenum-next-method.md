---
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
ms.openlocfilehash: 980f563d3b11fbfcce48b6d7c05275af520e14f1
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396500"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="9b6bb-102">Icordebugvariablehomeenum:: Next yöntemi</span><span class="sxs-lookup"><span data-stu-id="9b6bb-102">ICorDebugVariableHomeEnum::Next Method</span></span>
<span data-ttu-id="9b6bb-103">Bir işlevdeki yerel değişkenler ve bağımsız değişkenler hakkında bilgi içeren, belirtilen [ıcordebugvariablehome](icordebugvariablehome-interface.md) örneği sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-103">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9b6bb-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b6bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9b6bb-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="9b6bb-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-106">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="9b6bb-107">Her biri bir işlevin yerel değişkeni veya bağımsız değişkeni hakkında bilgi sağlayan [ıcordebugvariablehome](icordebugvariablehome-interface.md) nesnesine işaret eden bir işaretçiler dizisi.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-107">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9b6bb-108">dışı Gerçekte nesnelerde döndürülen örneklerin sayısı.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-108">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9b6bb-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9b6bb-109">Return Value</span></span>  
 <span data-ttu-id="9b6bb-110">Yöntemi aşağıdaki değerleri döndürür.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-110">The method returns the following values.</span></span>  
  
|<span data-ttu-id="9b6bb-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9b6bb-111">HRESULT</span></span>|<span data-ttu-id="9b6bb-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b6bb-112">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="9b6bb-113">Yöntem başarıyla tamamlandı.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-113">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="9b6bb-114">İçinde yansıtıldıkça alınan örneklerin gerçek sayısı `pceltFetched` , istenen örnek sayısından daha az.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-114">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9b6bb-115">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9b6bb-115">Remarks</span></span>  
 <span data-ttu-id="9b6bb-116">[Icordebugvariablehomeenum:: Next](icordebugvariablehomeenum-next-method.md) yöntemi, `celt` Numaralandırıcının geçerli konumundan başlayarak en fazla nesne alır.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-116">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="9b6bb-117">Yöntemi döndürüldüğünde, `pceltFetched` alınan nesnelerin gerçek sayısını içerir.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-117">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b6bb-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9b6bb-118">Requirements</span></span>  
 <span data-ttu-id="9b6bb-119">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b6bb-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b6bb-120">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9b6bb-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b6bb-121">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9b6bb-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b6bb-122">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b6bb-122">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b6bb-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b6bb-123">See also</span></span>

- [<span data-ttu-id="9b6bb-124">ICorDebugVariableHomeEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b6bb-124">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="9b6bb-125">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9b6bb-125">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
