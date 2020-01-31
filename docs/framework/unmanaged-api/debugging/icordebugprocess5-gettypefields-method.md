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
ms.openlocfilehash: 644b5ed751caaf1809250244b37badc8037b0f57
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792348"
---
# <a name="icordebugprocess5gettypefields-method"></a><span data-ttu-id="aa6b5-102">ICorDebugProcess5::GetTypeFields Metodu</span><span class="sxs-lookup"><span data-stu-id="aa6b5-102">ICorDebugProcess5::GetTypeFields Method</span></span>
<span data-ttu-id="aa6b5-103">Bir türe ait alanlar hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-103">Provides information about the fields that belong to a type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa6b5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa6b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeFields(  
    [in] COR_TYPEID id,  
    [in] ULONG32 celt,  
    [out] COR_FIELD fields[],   
    [out] ULONG32 *pceltNeeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa6b5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="aa6b5-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="aa6b5-106">'ndaki Alan bilgilerinin alındığı türün tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-106">[in] The identifier of the type whose field information is retrieved.</span></span>  
  
 `celt`  
 <span data-ttu-id="aa6b5-107">'ndaki Alan bilgileri alınacak olan [COR_FIELD](cor-field-structure.md) nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-107">[in] The number of [COR_FIELD](cor-field-structure.md) objects whose field information is to be retrieved.</span></span>  
  
 `fields`  
 <span data-ttu-id="aa6b5-108">dışı Türe ait alanlar hakkında bilgi sağlayan [COR_FIELD](cor-field-structure.md) nesneleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-108">[out] An array of [COR_FIELD](cor-field-structure.md) objects that provide information about the fields that belong to the type.</span></span>  
  
 `pceltNeeded`  
 <span data-ttu-id="aa6b5-109">dışı `fields`eklenen [COR_FIELD](cor-field-structure.md) nesnelerinin sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-109">[out] A pointer to the number of [COR_FIELD](cor-field-structure.md) objects included in `fields`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aa6b5-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa6b5-110">Remarks</span></span>  
 <span data-ttu-id="aa6b5-111">Alan bilgilerini yöntemin `fields`doldurmak için kullandığı alan sayısını belirten `celt` parametresi, `COR_TYPE_LAYOUT::numFields` alanının değerine karşılık gelmelidir.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-111">The `celt` parameter, which specifies the number of fields whose field information the method uses to populate `fields`, should correspond to the value of the `COR_TYPE_LAYOUT::numFields` field.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa6b5-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa6b5-112">Requirements</span></span>  
 <span data-ttu-id="aa6b5-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa6b5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa6b5-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="aa6b5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa6b5-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="aa6b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa6b5-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa6b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa6b5-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa6b5-117">See also</span></span>

- [<span data-ttu-id="aa6b5-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa6b5-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="aa6b5-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aa6b5-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
