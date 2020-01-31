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
ms.openlocfilehash: 68931ba16ea1f8f61176c6d6ed8300e762b61690
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790534"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="d2f91-102">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d2f91-102">ICorPublishProcess::IsManaged Method</span></span>
<span data-ttu-id="d2f91-103">Bu [ICorPublishProcess](icorpublishprocess-interface.md) tarafından başvurulan işlemin yönetilen koda sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="d2f91-103">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2f91-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2f91-104">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2f91-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d2f91-105">Parameters</span></span>  
 `pbManaged`  
 <span data-ttu-id="d2f91-106">dışı İşlemin yönetilen koda sahip olup olmadığını gösteren bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d2f91-106">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="d2f91-107">İşlemin yönetilen kodu varsa değer `true`. Aksi takdirde, `false`.</span><span class="sxs-lookup"><span data-stu-id="d2f91-107">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d2f91-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d2f91-108">Remarks</span></span>  
 <span data-ttu-id="d2f91-109">Geçerli `ICorPublishProcess` sürümü yalnızca yönetilen koda sahip işlemlere erişime izin verdiğinden, `IsManaged` her zaman `true`döndürür.</span><span class="sxs-lookup"><span data-stu-id="d2f91-109">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2f91-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d2f91-110">Requirements</span></span>  
 <span data-ttu-id="d2f91-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2f91-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2f91-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="d2f91-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="d2f91-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d2f91-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2f91-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2f91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2f91-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2f91-115">See also</span></span>

- [<span data-ttu-id="d2f91-116">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d2f91-116">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
