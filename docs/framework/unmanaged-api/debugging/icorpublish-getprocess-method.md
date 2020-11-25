---
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
ms.openlocfilehash: a45f613b7547e2e80abdbd8ac85cb0b2b6a499e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716895"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="f15f1-102">ICorPublish::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f15f1-102">ICorPublish::GetProcess Method</span></span>

<span data-ttu-id="f15f1-103">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="f15f1-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15f1-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="f15f1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f15f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f15f1-105">Parameters</span></span>  

 `pid`  
 <span data-ttu-id="f15f1-106">'ndaki İşlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="f15f1-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f15f1-107">dışı İşlemi temsil eden bir örneğin adresine yönelik bir işaretçi `ICorPublishProcess` .</span><span class="sxs-lookup"><span data-stu-id="f15f1-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f15f1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f15f1-108">Remarks</span></span>  

 <span data-ttu-id="f15f1-109">`GetProcess` işlem yoksa veya geçerli kullanıcı tarafından hata ayıklanabilecek yönetilen bir işlem değilse başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="f15f1-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f15f1-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f15f1-110">Requirements</span></span>  

 <span data-ttu-id="f15f1-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f15f1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f15f1-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="f15f1-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f15f1-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f15f1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f15f1-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f15f1-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f15f1-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f15f1-115">See also</span></span>

- [<span data-ttu-id="f15f1-116">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f15f1-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
