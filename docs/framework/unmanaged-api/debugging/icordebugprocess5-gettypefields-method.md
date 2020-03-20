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
ms.openlocfilehash: 29006eba3d3a523fd24a461207ab12222a639782
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178598"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="a98dd-102">ICorDebugProcess5::GetTypeFields Metodu</span><span class="sxs-lookup"><span data-stu-id="a98dd-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="a98dd-103">Bir türe ait alanlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="a98dd-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a98dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a98dd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a98dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a98dd-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="a98dd-106">[içinde] Alan bilgileri alınan türün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="a98dd-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="a98dd-107">[içinde] Alan bilgileri alınacak [olan COR_FIELD](cor-field-structure.md) nesnesayısı.</span><span class="sxs-lookup"><span data-stu-id="a98dd-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="a98dd-108">[çıkış] Türe ait alanlar hakkında bilgi sağlayan [COR_FIELD](cor-field-structure.md) nesneler dizisi.</span><span class="sxs-lookup"><span data-stu-id="a98dd-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="a98dd-109">[çıkış] 'de `fields`dahil COR_FIELD [nesne](cor-field-structure.md) sayısına işaretçi</span><span class="sxs-lookup"><span data-stu-id="a98dd-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a98dd-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a98dd-110">Remarks</span></span>  
 <span data-ttu-id="a98dd-111">Yöntemin `celt` doldurmak için kullandığı alan bilgilerinin sayısını belirten `fields`parametre, `COR_TYPE_LAYOUT::numFields` alanın değerine karşılık vermelidir.</span><span class="sxs-lookup"><span data-stu-id="a98dd-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a98dd-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a98dd-112">Requirements</span></span>  
 <span data-ttu-id="a98dd-113">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a98dd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a98dd-114">**Üstbilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a98dd-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a98dd-115">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a98dd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a98dd-116">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a98dd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a98dd-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a98dd-117">See also</span></span>

- [<span data-ttu-id="a98dd-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a98dd-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a98dd-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a98dd-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
