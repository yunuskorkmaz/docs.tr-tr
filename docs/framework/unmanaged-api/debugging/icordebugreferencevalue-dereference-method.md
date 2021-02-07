---
description: ': ICorDebugReferenceValue::D ereference yöntemi hakkında daha fazla bilgi edinin'
title: ICorDebugReferenceValue::Dereference Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: af225f746a9c67a90a7ad73046cd03401e4ba735
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691113"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="c5877-103">ICorDebugReferenceValue::Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5877-103">ICorDebugReferenceValue::Dereference Method</span></span>

<span data-ttu-id="c5877-104">Başvurulan nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="c5877-104">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5877-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5877-105">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c5877-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5877-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="c5877-107">dışı Bu ICorDebugReferenceValue nesnesinin işaret ettiği nesneyi temsil eden ICorDebugValue 'ın adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="c5877-107">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c5877-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c5877-108">Remarks</span></span>  

 <span data-ttu-id="c5877-109">`ICorDebugValue`Nesne yalnızca başvurusu henüz devre dışı bırakılmadıysa geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c5877-109">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5877-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5877-110">Requirements</span></span>  

 <span data-ttu-id="c5877-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5877-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5877-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="c5877-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5877-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c5877-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5877-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5877-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
