---
title: "ICorDebugType2::GetTypeID yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugType2.GetTypeID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d18aa8210ea90736c0757e2587aab4ff143dcdad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="d6b97-102">ICorDebugType2::GetTypeID yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6b97-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="d6b97-103">Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.</span><span class="sxs-lookup"><span data-stu-id="d6b97-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6b97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6b97-104">Syntax</span></span>  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d6b97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6b97-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="d6b97-106">[out] Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu Icordebugtype için.</span><span class="sxs-lookup"><span data-stu-id="d6b97-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d6b97-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d6b97-107">Return Value</span></span>  
 <span data-ttu-id="d6b97-108">Dönüş değeri `S_OK` başarı veya hata `HRESULT` hata kodu.</span><span class="sxs-lookup"><span data-stu-id="d6b97-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="d6b97-109">`HRESULT` Kodları aşağıdakileri içerir:</span><span class="sxs-lookup"><span data-stu-id="d6b97-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="d6b97-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="d6b97-110">Return code</span></span>|<span data-ttu-id="d6b97-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d6b97-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="d6b97-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="d6b97-112">Method succeeded.</span></span> <span data-ttu-id="d6b97-113">Yöntemin geçerli bir aldığı [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="d6b97-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="d6b97-114">Türü yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="d6b97-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="d6b97-115">Türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="d6b97-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6b97-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d6b97-116">Remarks</span></span>  
 <span data-ttu-id="d6b97-117">Bu yöntem, çalışma zamanına kadar yüklenmedi veya bir türü temsil eden Icordebugtype bir eşleme sağlar bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), bir opak gören işleyen çalışma zamanına yüklenen bir türü tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d6b97-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="d6b97-118">Ne zaman Icordebugtype temsil eden tür henüz henüz yüklenirken, bu yöntem `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="d6b97-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="d6b97-119">Türü varsa desteklenmiyor, döndürür `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="d6b97-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6b97-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6b97-120">Requirements</span></span>  
 <span data-ttu-id="d6b97-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6b97-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6b97-122">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d6b97-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d6b97-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d6b97-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d6b97-124">**.NET framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6b97-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6b97-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6b97-125">See Also</span></span>  
 [<span data-ttu-id="d6b97-126">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6b97-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
