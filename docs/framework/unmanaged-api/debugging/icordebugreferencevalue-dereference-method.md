---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2a0fd1981e7da5af19cf3a422c6008d373e9ac92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416599"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="f2d67-102">ICorDebugReferenceValue::Dereference Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f2d67-102">ICorDebugReferenceValue::Dereference Method</span></span>
<span data-ttu-id="f2d67-103">Başvurulan nesnesini alır.</span><span class="sxs-lookup"><span data-stu-id="f2d67-103">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2d67-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2d67-104">Syntax</span></span>  
  
```  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2d67-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f2d67-105">Parameters</span></span>  
 `ppValue`  
 <span data-ttu-id="f2d67-106">[out] Bu Icordebugreferencevalue nesne işaret ettiği nesneyi temsil eden bir Icordebugvalue adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f2d67-106">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2d67-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f2d67-107">Remarks</span></span>  
 <span data-ttu-id="f2d67-108">`ICorDebugValue` Nesne, yalnızca kendi başvuru olmayan henüz devre dışı bırakılmış ederken geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="f2d67-108">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2d67-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f2d67-109">Requirements</span></span>  
 <span data-ttu-id="f2d67-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2d67-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2d67-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f2d67-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f2d67-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2d67-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2d67-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2d67-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
