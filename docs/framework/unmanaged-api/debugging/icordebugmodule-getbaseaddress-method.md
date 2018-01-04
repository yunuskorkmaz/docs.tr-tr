---
title: ICorDebugModule::GetBaseAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule.GetBaseAddress
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aca93086e5425d7579b1394f72b039938f519ca9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="08717-102">ICorDebugModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="08717-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="08717-103">Modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="08717-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08717-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="08717-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="08717-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08717-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="08717-106">[out] A `CORDB_ADDRESS` modülü taban adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="08717-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08717-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08717-107">Remarks</span></span>  
 <span data-ttu-id="08717-108">Bir yerel modül ise (diğer bir deyişle, modül NGen.exe yerel Görüntü Oluşturucu tarafından üretilmiş ise) görüntü, temel adresini sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="08717-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08717-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08717-109">Requirements</span></span>  
 <span data-ttu-id="08717-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08717-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08717-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="08717-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="08717-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08717-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08717-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08717-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08717-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="08717-114">See Also</span></span>  
    
 
