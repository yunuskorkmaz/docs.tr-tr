---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetTypeLayout yöntemi'
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
ms.openlocfilehash: d4496fa832b048dfc0bbe792aeb8fdcd460f5158
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746288"
---
# <a name="icordebugprocess5gettypelayout-method"></a><span data-ttu-id="a15a1-103">ICorDebugProcess5::GetTypeLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a15a1-103">ICorDebugProcess5::GetTypeLayout Method</span></span>

<span data-ttu-id="a15a1-104">Bir nesnenin tür tanımlayıcısına göre bellek içindeki düzeni hakkında bilgi alır.</span><span class="sxs-lookup"><span data-stu-id="a15a1-104">Gets information about the layout of an object in memory based on its type identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a15a1-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a15a1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeLayout(    [in] COR_TYPEID id,     [out] COR_TYPE_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a15a1-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a15a1-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="a15a1-107">'ndaki Düzeni istenen türü belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.</span><span class="sxs-lookup"><span data-stu-id="a15a1-107">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the type whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="a15a1-108">dışı Bellekteki nesnenin düzeni hakkında bilgi içeren [cor_type_layout](cor-type-layout-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a15a1-108">[out] A pointer to a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that contains information about the layout of the object in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a15a1-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a15a1-109">Remarks</span></span>  

 <span data-ttu-id="a15a1-110">`ICorDebugProcess5::GetTypeLayout`Yöntemi, bir dizi diğer [ICorDebugProcess5](icordebugprocess5-interface.md) yöntemi tarafından döndürülen [COR_TYPEID](cor-typeid-structure.md)temel alınarak bir nesne hakkında bilgiler sağlar.</span><span class="sxs-lookup"><span data-stu-id="a15a1-110">The `ICorDebugProcess5::GetTypeLayout` method provides information about an object based on its [COR_TYPEID](cor-typeid-structure.md), which is returned by a number of other [ICorDebugProcess5](icordebugprocess5-interface.md) methods.</span></span> <span data-ttu-id="a15a1-111">Bilgiler, yöntemi tarafından doldurulan bir [cor_type_layout](cor-type-layout-structure.md) yapısı tarafından sağlanır.</span><span class="sxs-lookup"><span data-stu-id="a15a1-111">The information is provided by a [COR_TYPE_LAYOUT](cor-type-layout-structure.md) structure that is populated by the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a15a1-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a15a1-112">Requirements</span></span>  

 <span data-ttu-id="a15a1-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a15a1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a15a1-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a15a1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a15a1-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a15a1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a15a1-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a15a1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a15a1-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a15a1-117">See also</span></span>

- [<span data-ttu-id="a15a1-118">COR_TYPE_LAYOUT Yapısı</span><span class="sxs-lookup"><span data-stu-id="a15a1-118">COR_TYPE_LAYOUT Structure</span></span>](cor-type-layout-structure.md)
- [<span data-ttu-id="a15a1-119">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a15a1-119">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a15a1-120">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a15a1-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
