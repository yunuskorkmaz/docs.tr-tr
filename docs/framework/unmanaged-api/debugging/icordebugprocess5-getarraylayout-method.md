---
description: 'Daha fazla bilgi edinin: ICorDebugProcess5:: GetArrayLayout yöntemi'
title: ICorDebugProcess5::GetArrayLayout Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: c82b296da3a367f5307240225a560af67a56c866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746405"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="08634-103">ICorDebugProcess5::GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08634-103">ICorDebugProcess5::GetArrayLayout Method</span></span>

<span data-ttu-id="08634-104">Dizi türlerinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="08634-104">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08634-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08634-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08634-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08634-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="08634-107">'ndaki Düzeni istenen diziyi belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.</span><span class="sxs-lookup"><span data-stu-id="08634-107">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="08634-108">dışı Dizinin, bellekteki düzeni hakkında bilgi içeren [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="08634-108">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08634-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08634-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08634-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08634-110">Requirements</span></span>  

 <span data-ttu-id="08634-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08634-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08634-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="08634-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08634-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="08634-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08634-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08634-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08634-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08634-115">See also</span></span>

- [<span data-ttu-id="08634-116">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08634-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="08634-117">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="08634-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
