---
title: ICorDebugChain::GetActiveFrame Metodu
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c14b48a29993a65a0a0ab9fcb63bcb1e0d882042
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494083"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="d49ce-102">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="d49ce-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="d49ce-103">Etkin alır (yani, en son) zincirindeki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="d49ce-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d49ce-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d49ce-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d49ce-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d49ce-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="d49ce-106">[out] Etkin temsil eden Icordebugframe nesnenin adresini bir işaretçiye (diğer bir deyişle, en son) zincirindeki çerçeve.</span><span class="sxs-lookup"><span data-stu-id="d49ce-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d49ce-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d49ce-107">Remarks</span></span>  
 <span data-ttu-id="d49ce-108">Yönetilen yığın çerçeve varsa `ppFrame` ayarlanır null.</span><span class="sxs-lookup"><span data-stu-id="d49ce-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="d49ce-109">Etkin çerçeveye kullanılabilir durumda değilse, çağrı başarılı olacaktır ve `ppFrame` null olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d49ce-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="d49ce-110">Etkin çerçeve CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirleri için ve başlatılan CHAIN_CLASS_INIT nedeniyle bazı zincirleri için kullanılabilir olmayacak.</span><span class="sxs-lookup"><span data-stu-id="d49ce-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="d49ce-111">CorDebugChainReason numaralandırması bakın.</span><span class="sxs-lookup"><span data-stu-id="d49ce-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d49ce-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d49ce-112">Requirements</span></span>  
 <span data-ttu-id="d49ce-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d49ce-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d49ce-114">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d49ce-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d49ce-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d49ce-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d49ce-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d49ce-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
