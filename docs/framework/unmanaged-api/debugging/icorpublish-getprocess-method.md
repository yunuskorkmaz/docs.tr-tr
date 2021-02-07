---
description: ': ICorPublish:: GetProcess metodu hakkında daha fazla bilgi edinin'
title: ICorPublish::GetProcess Yöntemi
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
ms.openlocfilehash: d288a772274618cc99b63a68b37e84e543957b44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99721989"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="6e232-103">ICorPublish::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e232-103">ICorPublish::GetProcess Method</span></span>

<span data-ttu-id="6e232-104">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="6e232-104">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e232-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e232-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e232-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e232-106">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="6e232-107">'ndaki İşlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="6e232-107">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="6e232-108">dışı İşlemi temsil eden bir örneğin adresine yönelik bir işaretçi `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="6e232-108">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e232-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e232-109">Remarks</span></span>  

 <span data-ttu-id="6e232-110">`GetProcess` işlem yoksa veya geçerli kullanıcı tarafından hata ayıklanabilecek yönetilen bir işlem değilse başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="6e232-110">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e232-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e232-111">Requirements</span></span>  

 <span data-ttu-id="6e232-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e232-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e232-113">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="6e232-113">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="6e232-114">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6e232-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e232-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e232-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e232-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e232-116">See also</span></span>

- [<span data-ttu-id="6e232-117">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e232-117">ICorPublish Interface</span></span>](icorpublish-interface.md)
