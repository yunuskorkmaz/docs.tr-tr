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
ms.openlocfilehash: 3eec84624866b2be7068d7875cd650828c283fd2
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421104"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="d36e4-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d36e4-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="d36e4-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md) tarafından başvurulan işlemin yönetilen koda sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d36e4-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d36e4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d36e4-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d36e4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d36e4-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="d36e4-106">dışı İşlemin yönetilen koda sahip olup olmadığını gösteren bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d36e4-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="d36e4-107">Değer, `true` işlemin yönetilen kodu varsa, aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="d36e4-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d36e4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d36e4-108">Remarks</span></span>  
 <span data-ttu-id="d36e4-109">Geçerli sürümü `ICorPublishProcess` yalnızca yönetilen koda sahip işlemlere erişime izin verdiğinden, her zaman ' i `IsManaged` döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="d36e4-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d36e4-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d36e4-110">Requirements</span></span>  
 <span data-ttu-id="d36e4-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d36e4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d36e4-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d36e4-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d36e4-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d36e4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d36e4-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d36e4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d36e4-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d36e4-115">See also</span></span>

- [<span data-ttu-id="d36e4-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d36e4-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
