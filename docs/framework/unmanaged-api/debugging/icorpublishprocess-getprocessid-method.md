---
title: ICorPublishProcess::GetProcessID Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorPublishProcess.GetProcessID
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bb785c84436e2b0c6848c8af2540e8efada38e6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="29b2a-102">ICorPublishProcess::GetProcessID Metodu</span><span class="sxs-lookup"><span data-stu-id="29b2a-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="29b2a-103">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="29b2a-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b2a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29b2a-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29b2a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29b2a-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="29b2a-106">[out] Bu tarafından temsil edilen işlem tanıtıcısı gösteren bir işaretçi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesnesi.</span><span class="sxs-lookup"><span data-stu-id="29b2a-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b2a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29b2a-107">Requirements</span></span>  
 <span data-ttu-id="29b2a-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b2a-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b2a-109">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="29b2a-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="29b2a-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29b2a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29b2a-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b2a-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29b2a-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="29b2a-112">See Also</span></span>  
 [<span data-ttu-id="29b2a-113">Icorpublishprocess arabirimi</span><span class="sxs-lookup"><span data-stu-id="29b2a-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
