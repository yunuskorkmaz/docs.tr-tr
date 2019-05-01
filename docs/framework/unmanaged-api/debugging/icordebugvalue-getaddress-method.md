---
title: ICorDebugValue::GetAddress Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugValue.GetAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ac550ee7b1d66612557b30d15c275c90cf09b8af
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986862"
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="c2cd4-102">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="c2cd4-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="c2cd4-103">Ayıklanan sürecinde olan "ICorDebugValue" nesnenin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="c2cd4-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2cd4-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c2cd4-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2cd4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c2cd4-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="c2cd4-106">[out] İşaretçi bir `CORDB_ADDRESS` bu değeri nesnenin adresini belirten bir nesne.</span><span class="sxs-lookup"><span data-stu-id="c2cd4-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2cd4-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c2cd4-107">Remarks</span></span>  
 <span data-ttu-id="c2cd4-108">Değer kullanılamıyor, 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="c2cd4-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="c2cd4-109">Bu değer, en azından kısmen kayıtlara ise meydana gelmiş olabilir ya da bir çöp toplayıcı tanıtıcısı depolanan (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="c2cd4-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2cd4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c2cd4-110">Requirements</span></span>  
 <span data-ttu-id="c2cd4-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2cd4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2cd4-112">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c2cd4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c2cd4-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c2cd4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c2cd4-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c2cd4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2cd4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c2cd4-115">See also</span></span>
