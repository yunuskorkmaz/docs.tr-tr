---
title: ICorDebugType2::GetTypeID yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3098911bab2878876b93ee1ce23d9794d7e6cdbd
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67772460"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="7bf9e-102">ICorDebugType2::GetTypeID yöntemi</span><span class="sxs-lookup"><span data-stu-id="7bf9e-102">ICorDebugType2::GetTypeID Method</span></span>
<span data-ttu-id="7bf9e-103">Alır bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu tür.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-103">Gets a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bf9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7bf9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bf9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bf9e-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="7bf9e-106">[out] Bir işaretçi [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) bu Icordebugtype için.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-106">[out] A pointer to the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bf9e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7bf9e-107">Return Value</span></span>  
 <span data-ttu-id="7bf9e-108">Dönüş değeri `S_OK` başarı veya hata üzerinde `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-108">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="7bf9e-109">`HRESULT` Kodları şunlardır:</span><span class="sxs-lookup"><span data-stu-id="7bf9e-109">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="7bf9e-110">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="7bf9e-110">Return code</span></span>|<span data-ttu-id="7bf9e-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7bf9e-111">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="7bf9e-112">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-112">Method succeeded.</span></span> <span data-ttu-id="7bf9e-113">Yöntem, geçerli bir almıştır [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span><span class="sxs-lookup"><span data-stu-id="7bf9e-113">The method has retrieved a valid [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="7bf9e-114">Türü yüklü değil.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-114">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="7bf9e-115">Türü desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-115">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bf9e-116">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bf9e-116">Remarks</span></span>  
 <span data-ttu-id="7bf9e-117">Bu yöntem, çalışma zamanına kadar yüklenmiş olabilir değil veya bir türü temsil eden Icordebugtype bir eşleme sağlar. bir [cor_typeıd](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), bir opak gören işleyecek yüklenen çalışma zamanına tür tanımlar.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-117">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="7bf9e-118">Ne zaman Icordebugtype temsil eden tür sahip değildir ancak yüklenen, bu yöntemi döndürür `CORDBG_E_CLASS_NOT_LOADED`.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-118">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="7bf9e-119">Türü desteklenmiyor varsa, döndürür `CORDBG_E_UNSUPPORTED`.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-119">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7bf9e-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bf9e-120">Requirements</span></span>  
 <span data-ttu-id="7bf9e-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bf9e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bf9e-122">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7bf9e-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7bf9e-123">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7bf9e-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7bf9e-124">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bf9e-124">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf9e-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bf9e-125">See also</span></span>

- [<span data-ttu-id="7bf9e-126">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bf9e-126">ICorDebugType2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
