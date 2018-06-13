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
ms.openlocfilehash: f3fc25f76ef0f848fc29ffbed12b653d1c59c1f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33423890"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="74d3f-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="74d3f-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="74d3f-103">İşlemin bu tarafından başvurulan olup olmadığını belirten bir değer alır [Icorpublishprocess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) yönetilen kodu bilinmektedir.</span><span class="sxs-lookup"><span data-stu-id="74d3f-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74d3f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="74d3f-104">Syntax</span></span>  
  
```  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="74d3f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="74d3f-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="74d3f-106">[out] İşlem yönetilen kodu olup olmadığını gösteren bir Boole değeri için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="74d3f-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="74d3f-107">Değer `true` işlem kodu; yönetiliyorsa Aksi halde, `false`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74d3f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="74d3f-108">Remarks</span></span>  
 <span data-ttu-id="74d3f-109">Geçerli sürümü bu yana `ICorPublishProcess` yalnızca yönetilen kodu, işlemleri erişime `IsManaged` her zaman döndürür `true`.</span><span class="sxs-lookup"><span data-stu-id="74d3f-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74d3f-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="74d3f-110">Requirements</span></span>  
 <span data-ttu-id="74d3f-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74d3f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74d3f-112">**Başlık:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="74d3f-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="74d3f-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74d3f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74d3f-114">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74d3f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74d3f-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="74d3f-115">See Also</span></span>  
 [<span data-ttu-id="74d3f-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="74d3f-116">ICorPublishProcess Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)
