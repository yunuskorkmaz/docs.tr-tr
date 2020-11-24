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
ms.openlocfilehash: b0defd0a9c4197cf91fde1625794ff0d77c83ea0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95693144"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="ace9c-102">ICorPublishProcess::GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ace9c-102">ICorPublishProcess::GetProcessID Method</span></span>

<span data-ttu-id="ace9c-103">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="ace9c-103">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ace9c-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ace9c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ace9c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ace9c-105">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="ace9c-106">dışı Bu [ICorPublishProcess](icorpublishprocess-interface.md) nesnesinin temsil ettiği işlemin tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ace9c-106">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ace9c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ace9c-107">Requirements</span></span>  

 <span data-ttu-id="ace9c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ace9c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ace9c-109">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="ace9c-109">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="ace9c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ace9c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ace9c-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ace9c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ace9c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ace9c-112">See also</span></span>

- [<span data-ttu-id="ace9c-113">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ace9c-113">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
