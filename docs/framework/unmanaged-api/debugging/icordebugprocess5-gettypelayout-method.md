---
title: ICorDebugProcess5::GetTypeLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetTypeLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetTypeLayout
helpviewer_keywords:
- ICorDebugProcess5::GetTypeLayout method [.NET Framework debugging]
- GetTypeLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: bd62f5d1-e874-41f1-81e5-a29a7572c15d
topic_type:
- apiref
ms.openlocfilehash: 32277e8adcd4bb08c8d0480eb3b4e7e4b5949479
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723135"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="3118c-102">ICorDebugProcess5::GetTypeLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3118c-102">ICorDebugProcess5::GetTypeLayout Method</span></span>

<span data-ttu-id="3118c-103">Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="3118c-103">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3118c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3118c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3118c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3118c-105">Parameters</span></span>  

 `id`  
 <span data-ttu-id="3118c-106">'ndaki Düzeni istenen türü belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.</span><span class="sxs-lookup"><span data-stu-id="3118c-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="3118c-107">dışı Bellekteki nesnenin düzeni hakkında bilgi içeren [cor_type_layout](cor-type-layout-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3118c-107">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3118c-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3118c-108">Remarks</span></span>  

 <span data-ttu-id="3118c-109">`ICorDebugProcess5::GetTypeLayout`Yöntemi, bir dizi diğer [ICorDebugProcess5](icordebugprocess5-interface.md) yöntemi tarafından döndürülen [COR_TYPEID](cor-typeid-structure.md)temel alınarak bir nesne hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3118c-109">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="3118c-110">Bilgiler, yöntemi tarafından doldurulan bir [cor_type_layout](cor-type-layout-structure.md) yapısı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="3118c-110">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3118c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3118c-111">Requirements</span></span>  

 <span data-ttu-id="3118c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3118c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3118c-113">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3118c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3118c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3118c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3118c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3118c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3118c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3118c-116">See also</span></span>

- [<span data-ttu-id="3118c-117">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="3118c-117">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="3118c-118">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3118c-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="3118c-119">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3118c-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
