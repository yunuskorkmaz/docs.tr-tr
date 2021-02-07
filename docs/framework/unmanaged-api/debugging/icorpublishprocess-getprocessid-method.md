---
description: ': ICorPublishProcess:: GetProcessID Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: f959a49330e0ef4ade2a878acfd287657b5086ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728827"
---
# <a name="icorpublishprocessgetprocessid-method"></a><span data-ttu-id="1e5f9-103">ICorPublishProcess::GetProcessID Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e5f9-103">ICorPublishProcess::GetProcessID Method</span></span>

<span data-ttu-id="1e5f9-104">Bu işlem için işletim sistemi tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="1e5f9-104">Gets the operating system identifier for this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5f9-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e5f9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcessID (  
    [out] unsigned   *pid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e5f9-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e5f9-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="1e5f9-107">dışı Bu [ICorPublishProcess](icorpublishprocess-interface.md) nesnesinin temsil ettiği işlemin tanımlayıcısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e5f9-107">[out] A pointer to the identifier of the process represented by this [ICorPublishProcess](icorpublishprocess-interface.md) object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e5f9-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e5f9-108">Requirements</span></span>  

 <span data-ttu-id="1e5f9-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e5f9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5f9-110">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="1e5f9-110">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="1e5f9-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e5f9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e5f9-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5f9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5f9-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e5f9-113">See also</span></span>

- [<span data-ttu-id="1e5f9-114">ICorPublishProcess Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e5f9-114">ICorPublishProcess Interface</span></span>](icorpublishprocess-interface.md)
