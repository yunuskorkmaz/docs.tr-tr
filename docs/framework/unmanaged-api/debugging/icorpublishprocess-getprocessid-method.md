---
title: ICorPublishProcess::GetProcessID Metodu
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.GetProcessID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::GetProcessID
helpviewer_keywords:
- ICorPublishProcess::GetProcessID method [.NET Framework debugging]
- GetProcessID method [.NET Framework debugging]
ms.assetid: f31185e0-f01d-463a-b392-42163e39bfe9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39382b73a0fcd73282dbc69508b15dbfff240463
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669717"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="570cd-102">ICorPublishProcess::GetProcessID Metodu</span><span class="sxs-lookup"><span data-stu-id="570cd-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="570cd-103">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="570cd-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570cd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="570cd-104">Syntax</span></span>  
  
```  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="570cd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="570cd-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="570cd-106">[out] Bu tarafından temsil edilen işlem tanıtıcısı işaretçisi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="570cd-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="570cd-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="570cd-107">Requirements</span></span>  
 <span data-ttu-id="570cd-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="570cd-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="570cd-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="570cd-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="570cd-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="570cd-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="570cd-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="570cd-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="570cd-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="570cd-112">See also</span></span>
- [<span data-ttu-id="570cd-113">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="570cd-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
