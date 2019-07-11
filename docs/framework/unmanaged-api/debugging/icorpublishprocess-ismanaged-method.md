---
title: ICorPublishProcess::IsManaged Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublishProcess.IsManaged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublishProcess::IsManaged
helpviewer_keywords:
- IsManaged method, ICorPublishProcess interface [.NET Framework debugging]
- ICorPublishProcess::IsManaged method [.NET Framework debugging]
ms.assetid: 06b1f7cc-acdf-47a6-9d53-d9dec2424152
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee3a0c27d350dec8e9f3e9448174d978c7d50e81
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775693"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="d8015-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d8015-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="d8015-103">İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="d8015-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8015-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d8015-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8015-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d8015-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="d8015-106">[out] İşlem yönetilen kod olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d8015-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="d8015-107">Değer `true` işlem kodu; yönetiliyorsa Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d8015-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8015-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d8015-108">Remarks</span></span>  
 <span data-ttu-id="d8015-109">Geçerli sürümü bu yana `ICorPublishProcess` erişimine yalnızca yönetilen kod, işlemleri izin veren `IsManaged` her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="d8015-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8015-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d8015-110">Requirements</span></span>  
 <span data-ttu-id="d8015-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8015-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8015-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="d8015-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d8015-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8015-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8015-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8015-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8015-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d8015-115">See also</span></span>

- [<span data-ttu-id="d8015-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d8015-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
