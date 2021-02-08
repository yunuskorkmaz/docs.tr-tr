---
description: ': ICorPublishProcess:: IsManaged yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 55f620a896efd87c2f154ac68ef2db1a1b0a1ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790509"
---
# <a name="icorpublishprocessismanaged-method"></a><span data-ttu-id="06d1c-103">ICorPublishProcess::IsManaged Yöntemi</span><span class="sxs-lookup"><span data-stu-id="06d1c-103">ICorPublishProcess::IsManaged Method</span></span>

<span data-ttu-id="06d1c-104">Bu [ICorPublishProcess](icorpublishprocess-interface.md) tarafından başvurulan işlemin yönetilen koda sahip olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="06d1c-104">Gets a value that indicates whether the process referenced by this [ICorPublishProcess](icorpublishprocess-interface.md) is known to have managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06d1c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="06d1c-105">Syntax</span></span>  
  
```cpp  
HRESULT IsManaged (  
    [out] BOOL   *pbManaged  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06d1c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="06d1c-106">Parameters</span></span>  

 `pbManaged`  
 <span data-ttu-id="06d1c-107">dışı İşlemin yönetilen koda sahip olup olmadığını gösteren bir Boole değeri işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="06d1c-107">[out] A pointer to a Boolean value that indicates whether the process has managed code.</span></span> <span data-ttu-id="06d1c-108">Değer, `true` işlemin yönetilen kodu varsa, aksi durumda, `false` .</span><span class="sxs-lookup"><span data-stu-id="06d1c-108">The value is `true` if the process has managed code; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06d1c-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="06d1c-109">Remarks</span></span>  

 <span data-ttu-id="06d1c-110">Geçerli sürümü `ICorPublishProcess` yalnızca yönetilen koda sahip işlemlere erişime izin verdiğinden, her zaman ' i `IsManaged` döndürür `true` .</span><span class="sxs-lookup"><span data-stu-id="06d1c-110">Since the current version of `ICorPublishProcess` allows access only to processes that have managed code, `IsManaged` always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06d1c-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="06d1c-111">Requirements</span></span>  

 <span data-ttu-id="06d1c-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06d1c-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06d1c-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="06d1c-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="06d1c-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="06d1c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06d1c-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06d1c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06d1c-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="06d1c-116">See also</span></span>

- [<span data-ttu-id="06d1c-117">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="06d1c-117">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
