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
ms.openlocfilehash: 7018dcb41f46d5407549f5c3d3029716781014e3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugvaluegetaddress-method"></a><span data-ttu-id="cf486-102">ICorDebugValue::GetAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="cf486-102">ICorDebugValue::GetAddress Method</span></span>
<span data-ttu-id="cf486-103">Ayıklanacak sürecinde olduğundan "ICorDebugValue" nesnesinin adresini alır.</span><span class="sxs-lookup"><span data-stu-id="cf486-103">Gets the address of this "ICorDebugValue" object, which is in the process of being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf486-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf486-104">Syntax</span></span>  
  
```  
HRESULT GetAddress (  
    [out] CORDB_ADDRESS   *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cf486-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf486-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="cf486-106">[out] İşaretçi bir `CORDB_ADDRESS` nesne bu değer nesnesi adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="cf486-106">[out] Pointer to a `CORDB_ADDRESS` object that specifies the address of this value object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf486-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf486-107">Remarks</span></span>  
 <span data-ttu-id="cf486-108">Değer kullanılamıyorsa, 0 (sıfır) döndürülür.</span><span class="sxs-lookup"><span data-stu-id="cf486-108">If the value is unavailable, 0 (zero) is returned.</span></span> <span data-ttu-id="cf486-109">Bu değer en az kısmen Yazmaçları ise meydana gelmiş olabilir veya bir atık toplayıcı tanıtıcı depolanan (`GCHandle`).</span><span class="sxs-lookup"><span data-stu-id="cf486-109">This could happen if the value is at least partly in registers or stored in a garbage collector handle (`GCHandle`).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf486-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf486-110">Requirements</span></span>  
 <span data-ttu-id="cf486-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf486-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf486-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cf486-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cf486-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf486-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf486-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf486-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf486-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cf486-115">See Also</span></span>  
 
