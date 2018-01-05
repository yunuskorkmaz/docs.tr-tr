---
title: ICorDebugProcess2::GetVersion Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess2.GetVersion
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 nterface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae9c80a65908d6ec1514ce64845217bd7b5c7805
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="b6058-102">ICorDebugProcess2::GetVersion Metodu</span><span class="sxs-lookup"><span data-stu-id="b6058-102">ICorDebugProcess2::GetVersion Method</span></span>
<span data-ttu-id="b6058-103">Bu işlemde çalışan ortak dil çalışma zamanı (CLR) sürüm numarasını alır.</span><span class="sxs-lookup"><span data-stu-id="b6058-103">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6058-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b6058-104">Syntax</span></span>  
  
```  
HRESULT GetVersion (  
    [out] COR_VERSION     *version  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b6058-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b6058-105">Parameters</span></span>  
 `version`  
 <span data-ttu-id="b6058-106">[out] Çalışma zamanı sürüm numarasını depolar cor_versıon yapısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b6058-106">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6058-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b6058-107">Remarks</span></span>  
 <span data-ttu-id="b6058-108">`GetVersion` Yöntemi, hiçbir çalışma zamanı işleminde yüklerse bir hata kodu döndürür.</span><span class="sxs-lookup"><span data-stu-id="b6058-108">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6058-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b6058-109">Requirements</span></span>  
 <span data-ttu-id="b6058-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6058-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6058-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b6058-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b6058-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b6058-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b6058-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6058-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
