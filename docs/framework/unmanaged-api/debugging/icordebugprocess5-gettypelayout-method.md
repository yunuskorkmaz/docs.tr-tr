---
title: ICorDebugProcess5::GetTypeLayout Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.GetTypeLayout
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f36b78558f8a8005735166436ad3dead28992e3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="3c2c6-102">ICorDebugProcess5::GetTypeLayout Metodu</span><span class="sxs-lookup"><span data-stu-id="3c2c6-102">ICorDebugProcess5::GetTypeLayout Method</span></span>
<span data-ttu-id="3c2c6-103">Kendi türü tanımlayıcısına göre bellekte bir nesnenin düzeni hakkındaki bilgileri alır.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c2c6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3c2c6-104">Syntax</span></span>  
  
```  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3c2c6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3c2c6-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="3c2c6-106">[in] A [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) belirteci düzeni istenen türünü belirtir.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-106">[in] A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="3c2c6-107">[out] Bir işaretçi bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) bellekte nesnesi düzeni hakkındaki bilgileri içeren yapısı.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-107">[out] A pointer to a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c2c6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3c2c6-108">Remarks</span></span>  
 <span data-ttu-id="3c2c6-109">`ICorDebugProcess5::GetTypeLayout` Yöntemi göre bir nesne hakkında bilgi sağlar, [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), bir dizi diğer tarafından döndürülen [Icordebugprocess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="3c2c6-110">Bilgileri tarafından sağlanan bir [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) yöntemiyle doldurulan yapısı.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-110">The information is provided by a [COR_TYPE_LAYOUT](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c2c6-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3c2c6-111">Requirements</span></span>  
 <span data-ttu-id="3c2c6-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c2c6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c2c6-113">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c2c6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c2c6-114">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c2c6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c2c6-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c2c6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c2c6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c2c6-116">See Also</span></span>  
 [<span data-ttu-id="3c2c6-117">COR_TYPE_LAYOUT yapısı</span><span class="sxs-lookup"><span data-stu-id="3c2c6-117">COR_TYPE_LAYOUT Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/cor-type-layout-structure.md)  
 [<span data-ttu-id="3c2c6-118">Icordebugprocess5 arabirimi</span><span class="sxs-lookup"><span data-stu-id="3c2c6-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 [<span data-ttu-id="3c2c6-119">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3c2c6-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
