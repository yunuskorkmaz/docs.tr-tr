---
title: ICorDebugProcess5::GetTypeFields Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeFields
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeFields
helpviewer_keywords:
- GetTypeFields method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::GetTypeFields method [.NET Framework debugging]
ms.assetid: 6a0ad3ee-dacb-47e9-abae-4536bcc4804b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f688993bfd8e6bef66451b075a49f31efe641cb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497111"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="dad84-102">ICorDebugProcess5::GetTypeFields Metodu</span><span class="sxs-lookup"><span data-stu-id="dad84-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="dad84-103">Bir türe ait alanları hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dad84-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad84-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dad84-104">Syntax</span></span>  
  
```  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dad84-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dad84-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="dad84-106">[in] Alan bilgilerini alınan tür tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="dad84-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="dad84-107">[in] Sayısını [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) olan alan bilgilerdir alınacak nesne.</span><span class="sxs-lookup"><span data-stu-id="dad84-107">[in] The number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="dad84-108">[out] Bir dizi [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) türe ait alanları hakkında bilgi sağlayan nesneleri.</span><span class="sxs-lookup"><span data-stu-id="dad84-108">[out] An array of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="dad84-109">[out] Bir işaretçi sayısına [cor_fıeld](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) bulunan nesneleri `fields`.</span><span class="sxs-lookup"><span data-stu-id="dad84-109">[out] A pointer to the number of [COR_FIELD](../../../../docs/framework/unmanaged-api/debugging/cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dad84-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dad84-110">Remarks</span></span>  
 <span data-ttu-id="dad84-111">`celt` Alan bilgilerini doldurmak için yöntemi kullanan alanların sayısını belirten bir parametre `fields`, değerine karşılık gelmelidir `COR_TYPE_LAYOUT::numFields` alan.</span><span class="sxs-lookup"><span data-stu-id="dad84-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad84-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dad84-112">Requirements</span></span>  
 <span data-ttu-id="dad84-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad84-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad84-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dad84-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dad84-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dad84-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dad84-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad84-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad84-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dad84-117">See also</span></span>
- [<span data-ttu-id="dad84-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dad84-118">ICorDebugProcess5 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)
- [<span data-ttu-id="dad84-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="dad84-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
