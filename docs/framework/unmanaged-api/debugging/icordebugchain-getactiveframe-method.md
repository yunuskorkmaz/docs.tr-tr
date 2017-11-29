---
title: ICorDebugChain::GetActiveFrame Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain.GetActiveFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain::GetActiveFrame
helpviewer_keywords:
- ICorDebugChain::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: 36887017-670b-4f21-b406-8fab956f84a3
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b5de327c1579d05f6ae4a440fc76a3fb9ee99b13
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="52f7d-102">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="52f7d-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="52f7d-103">Etkin alır (yani, en son) zinciri çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="52f7d-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52f7d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="52f7d-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52f7d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="52f7d-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="52f7d-106">[out] Bir işaretçi etkin temsil eden Icordebugframe nesne adresine (diğer bir deyişle, en son) zinciri çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="52f7d-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52f7d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="52f7d-107">Remarks</span></span>  
 <span data-ttu-id="52f7d-108">Yönetilen yığın çerçeve olup olmadığını `ppFrame` ayarlanmış null.</span><span class="sxs-lookup"><span data-stu-id="52f7d-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="52f7d-109">Etkin çerçeveyi kullanılabilir durumda değilse, çağrı başarılı olur ve `ppFrame` null olur.</span><span class="sxs-lookup"><span data-stu-id="52f7d-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="52f7d-110">Etkin çerçeve CHAIN_CLASS_INIT nedeniyle başlatılan bazı zincirlerini ve CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="52f7d-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="52f7d-111">CorDebugChainReason numaralandırması bakın.</span><span class="sxs-lookup"><span data-stu-id="52f7d-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52f7d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="52f7d-112">Requirements</span></span>  
 <span data-ttu-id="52f7d-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52f7d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52f7d-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="52f7d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="52f7d-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="52f7d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52f7d-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52f7d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
