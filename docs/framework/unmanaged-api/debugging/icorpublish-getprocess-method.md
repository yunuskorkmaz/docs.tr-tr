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
ms.openlocfilehash: 0368349e6c6a566cb569738bf3bda40eb9f5de96
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790741"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="43ade-102">ICorPublish::GetProcess Yöntemi</span><span class="sxs-lookup"><span data-stu-id="43ade-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="43ade-103">Belirtilen tanımlayıcıya sahip işlemi temsil eden bir [ICorPublishProcess](icorpublishprocess-interface.md) örneğini alır.</span><span class="sxs-lookup"><span data-stu-id="43ade-103">Gets an [ICorPublishProcess](icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ade-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43ade-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43ade-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43ade-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="43ade-106">'ndaki İşlemin tanımlayıcısı.</span><span class="sxs-lookup"><span data-stu-id="43ade-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="43ade-107">dışı İşlemi temsil eden bir `ICorPublishProcess` örneğinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="43ade-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43ade-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43ade-108">Remarks</span></span>  
 <span data-ttu-id="43ade-109">işlem yoksa `GetProcess` başarısız olur veya geçerli kullanıcı tarafından hata ayıklanabilecek yönetilen bir işlem değildir.</span><span class="sxs-lookup"><span data-stu-id="43ade-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ade-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43ade-110">Requirements</span></span>  
 <span data-ttu-id="43ade-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ade-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ade-112">**Üst bilgi:** CorPub. IDL, CorPub. h</span><span class="sxs-lookup"><span data-stu-id="43ade-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="43ade-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="43ade-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43ade-114">**.NET Framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ade-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ade-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43ade-115">See also</span></span>

- [<span data-ttu-id="43ade-116">ICorPublish Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43ade-116">ICorPublish Interface</span></span>](icorpublish-interface.md)
