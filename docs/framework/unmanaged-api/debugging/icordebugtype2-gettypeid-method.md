---
description: 'Daha fazla bilgi edinin: ICorDebugType2:: GetTypeId yöntemi'
title: 'ICorDebugType2:: GetTypeId metodu'
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
ms.openlocfilehash: 8143ede1a11ee5f73c49fc723920f53430339ed0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738110"
---
# <a name="icordebugtype2gettypeid-method"></a><span data-ttu-id="02baf-103">ICorDebugType2:: GetTypeId metodu</span><span class="sxs-lookup"><span data-stu-id="02baf-103">ICorDebugType2::GetTypeID Method</span></span>

<span data-ttu-id="02baf-104">Bu tür için bir [COR_TYPEID](cor-typeid-structure.md) alır.</span><span class="sxs-lookup"><span data-stu-id="02baf-104">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02baf-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="02baf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02baf-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="02baf-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="02baf-107">dışı Bu ICorDebugType için [COR_TYPEID](cor-typeid-structure.md) işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="02baf-107">[out] A pointer to the [COR_TYPEID](cor-typeid-structure.md) for this ICorDebugType.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02baf-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="02baf-108">Return Value</span></span>  

 <span data-ttu-id="02baf-109">Dönüş değeri `S_OK` başarılı veya hata durumunda hata `HRESULT` kodu.</span><span class="sxs-lookup"><span data-stu-id="02baf-109">The return value is `S_OK` on success, or a failure `HRESULT` code on failure.</span></span> <span data-ttu-id="02baf-110">`HRESULT`Kodlar şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="02baf-110">The `HRESULT` codes include the following:</span></span>  
  
|<span data-ttu-id="02baf-111">Dönüş kodu</span><span class="sxs-lookup"><span data-stu-id="02baf-111">Return code</span></span>|<span data-ttu-id="02baf-112">Description</span><span class="sxs-lookup"><span data-stu-id="02baf-112">Description</span></span>|  
|-----------------|-----------------|  
|`S_OK`|<span data-ttu-id="02baf-113">Yöntem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="02baf-113">Method succeeded.</span></span> <span data-ttu-id="02baf-114">Yöntem geçerli bir [COR_TYPEID](cor-typeid-structure.md)aldı.</span><span class="sxs-lookup"><span data-stu-id="02baf-114">The method has retrieved a valid [COR_TYPEID](cor-typeid-structure.md).</span></span>|  
|`CORDBG_E_CLASS_NOT_LOADED`|<span data-ttu-id="02baf-115">Tür yüklenmedi.</span><span class="sxs-lookup"><span data-stu-id="02baf-115">The type has not been loaded.</span></span>|  
|`CORDBG_E_UNSUPPORTED`|<span data-ttu-id="02baf-116">Tür desteklenmiyor.</span><span class="sxs-lookup"><span data-stu-id="02baf-116">The type is not supported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02baf-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="02baf-117">Remarks</span></span>  

 <span data-ttu-id="02baf-118">Bu yöntem, çalışma zamanına yüklenmiş olan [COR_TYPEID](cor-typeid-structure.md)veya bir tür çalışma zamanına yüklenmiş bir türü tanımlayan donuk bir tanıtıcı görevi gören ICorDebugType öğesinden bir eşleme sağlar.</span><span class="sxs-lookup"><span data-stu-id="02baf-118">This method provides a mapping from the ICorDebugType, which represents a type that may or may not have been loaded into the runtime, to a [COR_TYPEID](cor-typeid-structure.md), which serves as an opaque handle that identifies a type loaded into the runtime.</span></span>  
  
 <span data-ttu-id="02baf-119">ICorDebugType 'ın gösterdiği tür henüz yüklenmediyse, bu yöntem döndürür `CORDBG_E_CLASS_NOT_LOADED` .</span><span class="sxs-lookup"><span data-stu-id="02baf-119">When the type that the ICorDebugType represents has not yet been loaded, this method returns `CORDBG_E_CLASS_NOT_LOADED`.</span></span>  <span data-ttu-id="02baf-120">Tür desteklenmiyorsa, döndürür `CORDBG_E_UNSUPPORTED` .</span><span class="sxs-lookup"><span data-stu-id="02baf-120">If the type is not supported, it returns `CORDBG_E_UNSUPPORTED`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02baf-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="02baf-121">Requirements</span></span>  

 <span data-ttu-id="02baf-122">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02baf-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02baf-123">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="02baf-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02baf-124">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="02baf-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02baf-125">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02baf-125">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02baf-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="02baf-126">See also</span></span>

- [<span data-ttu-id="02baf-127">ICorDebugType2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="02baf-127">ICorDebugType2 Interface</span></span>](icordebugtype2-interface.md)
