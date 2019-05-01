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
ms.openlocfilehash: 29c5f96bab374d6e2d43424370bff2a4a2ab6df3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61986599"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="9c4d5-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9c4d5-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="9c4d5-103">İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="9c4d5-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c4d5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9c4d5-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c4d5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9c4d5-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="9c4d5-106">[out] İşlem yönetilen kod olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="9c4d5-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="9c4d5-107">Değer `true` işlem kodu; yönetiliyorsa Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="9c4d5-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9c4d5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9c4d5-108">Remarks</span></span>  
 <span data-ttu-id="9c4d5-109">Geçerli sürümü bu yana `ICorPublishProcess` erişimine yalnızca yönetilen kod, işlemleri izin veren `IsManaged` her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="9c4d5-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c4d5-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9c4d5-110">Requirements</span></span>  
 <span data-ttu-id="9c4d5-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9c4d5-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9c4d5-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="9c4d5-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="9c4d5-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9c4d5-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9c4d5-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9c4d5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c4d5-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9c4d5-115">See also</span></span>

- [<span data-ttu-id="9c4d5-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9c4d5-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
