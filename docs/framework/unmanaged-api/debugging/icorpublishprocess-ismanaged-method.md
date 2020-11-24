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
ms.openlocfilehash: dfe247bda75c3695c7c09b85729b4e057c13c62d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95692637"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="70182-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70182-102">ICorPublishProcess::IsManaged Method</span></span>

<span data-ttu-id="70182-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md) tarafından başvurulan işlemin yönetilen koda sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="70182-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70182-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="70182-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70182-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="70182-105">Parameters</span></span>  

 `pbManaged`  
 <span data-ttu-id="70182-106">dışı İşlemin yönetilen koda sahip olup olmadığını gösteren bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="70182-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="70182-107">Değer, `true` işlemin yönetilen kodu varsa, aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="70182-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70182-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70182-108">Remarks</span></span>  

 <span data-ttu-id="70182-109">Geçerli sürümü `ICorPublishProcess` yalnızca yönetilen koda sahip işlemlere erişime izin verdiğinden, her zaman ' i `IsManaged` döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="70182-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70182-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70182-110">Requirements</span></span>  

 <span data-ttu-id="70182-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70182-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70182-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="70182-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="70182-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="70182-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="70182-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70182-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70182-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70182-115">See also</span></span>

- [<span data-ttu-id="70182-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70182-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
