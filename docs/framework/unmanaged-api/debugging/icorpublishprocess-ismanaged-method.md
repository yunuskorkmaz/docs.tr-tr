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
ms.openlocfilehash: b57a8bcc584ffd209def5a84a99b15daa7480ee6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534949"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="b2848-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2848-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="b2848-103">İşlem bu tarafından başvurulan olup olmadığını gösteren bir değer alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) yönetilen kod adı verilir.</span><span class="sxs-lookup"><span data-stu-id="b2848-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2848-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2848-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b2848-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2848-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="b2848-106">[out] İşlem yönetilen kod olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b2848-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="b2848-107">Değer `true` işlem kodu; yönetiliyorsa Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="b2848-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2848-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2848-108">Remarks</span></span>  
 <span data-ttu-id="b2848-109">Geçerli sürümü bu yana `ICorPublishProcess` erişimine yalnızca yönetilen kod, işlemleri izin veren `IsManaged` her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="b2848-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2848-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2848-110">Requirements</span></span>  
 <span data-ttu-id="b2848-111">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2848-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2848-112">**Üst bilgi:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="b2848-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="b2848-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2848-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2848-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2848-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2848-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2848-115">See also</span></span>
- [<span data-ttu-id="b2848-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2848-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
