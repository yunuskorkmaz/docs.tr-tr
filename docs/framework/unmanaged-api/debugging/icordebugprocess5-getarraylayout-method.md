---
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
ms.openlocfilehash: ea7630efedb7b667dc58174eda0cb98d9f382cfc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792385"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="c8fb0-102">ICorDebugProcess5::GetArrayLayout Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8fb0-102">ICorDebugProcess5::GetArrayLayout Method</span></span>
<span data-ttu-id="c8fb0-103">Dizi türlerinin yerleşimi hakkında bilgi sağlar.</span><span class="sxs-lookup"><span data-stu-id="c8fb0-103">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fb0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8fb0-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c8fb0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c8fb0-105">Parameters</span></span>  
 `id`  
 <span data-ttu-id="c8fb0-106">'ndaki Düzeni istenen diziyi belirten [COR_TYPEID](cor-typeid-structure.md) belirteç.</span><span class="sxs-lookup"><span data-stu-id="c8fb0-106">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="c8fb0-107">dışı Dizinin, bellekteki düzeni hakkında bilgi içeren [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) yapısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c8fb0-107">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c8fb0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8fb0-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8fb0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8fb0-109">Requirements</span></span>  
 <span data-ttu-id="c8fb0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8fb0-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fb0-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c8fb0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c8fb0-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c8fb0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8fb0-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fb0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fb0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8fb0-114">See also</span></span>

- [<span data-ttu-id="c8fb0-115">ICorDebugProcess5 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8fb0-115">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="c8fb0-116">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c8fb0-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
