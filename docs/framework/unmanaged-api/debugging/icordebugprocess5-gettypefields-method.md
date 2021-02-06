---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeFields yöntemi'
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
ms.openlocfilehash: bdbb0be76400262d83876b9fc37cc4f00eb34e43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649825"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="32ca1-103">ICorDebugProcess5::GetTypeFields Metodu</span><span class="sxs-lookup"><span data-stu-id="32ca1-103">ICorDebugProcess5::GetTypeFields Method</span></span>

<span data-ttu-id="32ca1-104">Bir türe ait alanlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="32ca1-104">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32ca1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="32ca1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32ca1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="32ca1-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="32ca1-107">'ndaki Alan bilgilerinin alındığı türün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="32ca1-107">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="32ca1-108">'ndaki Alan bilgileri alınacak olan [COR_FIELD](cor-field-structure.md) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="32ca1-108">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="32ca1-109">dışı Türe ait alanlar hakkında bilgi sağlayan [COR_FIELD](cor-field-structure.md) nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="32ca1-109">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="32ca1-110">dışı İçinde bulunan [COR_FIELD](cor-field-structure.md) nesne sayısı için bir işaretçi `fields` .</span><span class="sxs-lookup"><span data-stu-id="32ca1-110">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32ca1-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="32ca1-111">Remarks</span></span>  

 <span data-ttu-id="32ca1-112">`celt`Alan bilgilerinin doldurmak için kullandığı alan sayısını belirten parametresi, `fields` alanın değerine karşılık gelmelidir `COR_TYPE_LAYOUT::numFields` .</span><span class="sxs-lookup"><span data-stu-id="32ca1-112">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32ca1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="32ca1-113">Requirements</span></span>  

 <span data-ttu-id="32ca1-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32ca1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32ca1-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="32ca1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32ca1-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="32ca1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32ca1-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32ca1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32ca1-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="32ca1-118">See also</span></span>

- [<span data-ttu-id="32ca1-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="32ca1-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="32ca1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="32ca1-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
