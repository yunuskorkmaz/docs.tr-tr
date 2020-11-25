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
ms.openlocfilehash: daecd216b4d7e9c23336b8956c13735549be901b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730142"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="b487a-102">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="b487a-102">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="b487a-103">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="b487a-103">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b487a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b487a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b487a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b487a-105">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="b487a-106">dışı Zincirdeki etkin (yani en son) kareyi temsil eden ICorDebugFrame nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b487a-106">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b487a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b487a-107">Remarks</span></span>  

 <span data-ttu-id="b487a-108">Kullanılabilir bir yönetilen yığın çerçevesi yoksa, `ppFrame` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="b487a-108">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="b487a-109">Etkin çerçeve kullanılabilir değilse, çağrı başarılı olur ve `ppFrame` null olur.</span><span class="sxs-lookup"><span data-stu-id="b487a-109">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="b487a-110">CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirler için etkin çerçeveler kullanılamaz ve bazı zincirler CHAIN_CLASS_INIT nedeniyle başlatılmış olur.</span><span class="sxs-lookup"><span data-stu-id="b487a-110">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="b487a-111">CorDebugChainReason numaralandırması bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="b487a-111">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b487a-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b487a-112">Requirements</span></span>  

 <span data-ttu-id="b487a-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b487a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b487a-114">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b487a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b487a-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b487a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b487a-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b487a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
