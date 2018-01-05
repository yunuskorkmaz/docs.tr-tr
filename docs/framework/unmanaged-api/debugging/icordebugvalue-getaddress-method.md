---
title: ICorDebugValue::GetAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugValue.GetAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugValue::GetAddress
helpviewer_keywords:
- ICorDebugValue::GetAddress method [.NET Framework debugging]
- GetAddress method, ICorDebugValue interface [.NET Framework debugging]
ms.assetid: a247c792-45e1-4538-9e1f-b46acca4a463
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8aa5a0c3740b6cf97d2a5d855343a36b90fd538
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="74f97-102">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="74f97-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="74f97-103">Ayıklanacak sürecinde olduğundan "ICorDebugValue" nesnesinin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="74f97-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f97-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74f97-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74f97-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74f97-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="74f97-106">[out] İşaretçi bir `CORDB_ADDRESS` nesne bu değer nesnesi adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="74f97-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f97-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74f97-107">Remarks</span></span>  
 <span data-ttu-id="74f97-108">Değer kullanılamıyorsa, 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="74f97-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="74f97-109">Bu değer en az kısmen Yazmaçları ise meydana gelmiş olabilir veya bir atık toplayıcı tanıtıcı depolanan (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="74f97-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74f97-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74f97-110">Requirements</span></span>  
 <span data-ttu-id="74f97-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74f97-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74f97-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74f97-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74f97-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74f97-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74f97-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74f97-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74f97-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74f97-115">See Also</span></span>  
 
