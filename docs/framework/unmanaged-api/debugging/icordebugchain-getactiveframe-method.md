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
ms.openlocfilehash: 2f67188539d5ad5523c255fbc663e990e1b8245f
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894677"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="3884d-102">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="3884d-102">ICorDebugChain::GetActiveFrame Method</span></span>
<span data-ttu-id="3884d-103">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="3884d-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3884d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3884d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3884d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3884d-105">Parameters</span></span>  
 `ppFrame`  
 <span data-ttu-id="3884d-106">dışı Zincirdeki etkin (yani en son) kareyi temsil eden ICorDebugFrame nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3884d-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3884d-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3884d-107">Remarks</span></span>  
 <span data-ttu-id="3884d-108">Kullanılabilir bir yönetilen yığın çerçevesi yoksa, `ppFrame` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="3884d-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="3884d-109">Etkin çerçeve kullanılabilir değilse, çağrı başarılı olur ve `ppFrame` null olur.</span><span class="sxs-lookup"><span data-stu-id="3884d-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="3884d-110">CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirler için etkin çerçeveler kullanılamaz ve bazı zincirler CHAIN_CLASS_INIT nedeniyle başlatılmış olur.</span><span class="sxs-lookup"><span data-stu-id="3884d-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="3884d-111">CorDebugChainReason numaralandırması bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="3884d-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3884d-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3884d-112">Requirements</span></span>  
 <span data-ttu-id="3884d-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3884d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3884d-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3884d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3884d-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3884d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3884d-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3884d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
