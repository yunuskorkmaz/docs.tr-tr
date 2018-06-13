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
ms.openlocfilehash: a104d4d3cc74a6c1cb343818c9b0b3e8978b97df
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402805"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="29242-102">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="29242-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="29242-103">Etkin alır (yani, en son) zinciri çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="29242-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29242-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="29242-104">Syntax</span></span>  
  
```  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29242-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="29242-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="29242-106">[out] Bir işaretçi etkin temsil eden Icordebugframe nesne adresine (diğer bir deyişle, en son) zinciri çerçevesi.</span><span class="sxs-lookup"><span data-stu-id="29242-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29242-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="29242-107">Remarks</span></span>  
 <span data-ttu-id="29242-108">Yönetilen yığın çerçeve olup olmadığını `ppFrame` ayarlanmış null.</span><span class="sxs-lookup"><span data-stu-id="29242-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="29242-109">Etkin çerçeveyi kullanılabilir durumda değilse, çağrı başarılı olur ve `ppFrame` null olur.</span><span class="sxs-lookup"><span data-stu-id="29242-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="29242-110">Etkin çerçeve CHAIN_CLASS_INIT nedeniyle başlatılan bazı zincirlerini ve CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirleri için kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="29242-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="29242-111">CorDebugChainReason numaralandırması bakın.</span><span class="sxs-lookup"><span data-stu-id="29242-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29242-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="29242-112">Requirements</span></span>  
 <span data-ttu-id="29242-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29242-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29242-114">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29242-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29242-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29242-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29242-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29242-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
