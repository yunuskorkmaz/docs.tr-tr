---
title: ICorPublishProcess::GetProcessID Yöntemi
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
ms.openlocfilehash: 29427bab938437c40d0edb5676a2f8f76cbb6691
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764864"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="44fde-102">ICorPublishProcess::GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="44fde-102">ICorPublishProcess::GetProcessID Method</span></span>
<span data-ttu-id="44fde-103">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="44fde-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44fde-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="44fde-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44fde-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="44fde-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="44fde-106">[out] Bu tarafından temsil edilen işlem tanıtıcısı işaretçisi [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) nesne.</span><span class="sxs-lookup"><span data-stu-id="44fde-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44fde-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="44fde-107">Requirements</span></span>  
 <span data-ttu-id="44fde-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44fde-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44fde-109">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="44fde-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="44fde-110">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="44fde-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44fde-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44fde-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44fde-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="44fde-112">See also</span></span>

- [<span data-ttu-id="44fde-113">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="44fde-113">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
