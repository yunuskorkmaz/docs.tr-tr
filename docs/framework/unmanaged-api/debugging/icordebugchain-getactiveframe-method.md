---
description: ': Icordebugzincirine:: GetActiveFrame metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: d46906d9d6c671880d9446d889cdf9f83f3b4366
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661430"
---
# <a name="icordebugchaingetactiveframe-method"></a><span data-ttu-id="16b29-103">ICorDebugChain::GetActiveFrame Metodu</span><span class="sxs-lookup"><span data-stu-id="16b29-103">ICorDebugChain::GetActiveFrame Method</span></span>

<span data-ttu-id="16b29-104">Zincirdeki etkin (yani en son) çerçeveyi alır.</span><span class="sxs-lookup"><span data-stu-id="16b29-104">Gets the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16b29-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="16b29-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16b29-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="16b29-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="16b29-107">dışı Zincirdeki etkin (yani en son) kareyi temsil eden ICorDebugFrame nesnesinin adresine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="16b29-107">[out] A pointer to the address of an ICorDebugFrame object that represents the active (that is, most recent) frame on the chain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16b29-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="16b29-108">Remarks</span></span>  

 <span data-ttu-id="16b29-109">Kullanılabilir bir yönetilen yığın çerçevesi yoksa, `ppFrame` null olarak ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="16b29-109">If no managed stack frame is available, `ppFrame` is set to null.</span></span>  
  
 <span data-ttu-id="16b29-110">Etkin çerçeve kullanılabilir değilse, çağrı başarılı olur ve `ppFrame` null olur.</span><span class="sxs-lookup"><span data-stu-id="16b29-110">If the active frame is not available, the call will succeed and `ppFrame` will be null.</span></span> <span data-ttu-id="16b29-111">CHAIN_ENTER_UNMANAGED nedeniyle başlatılan zincirler için etkin çerçeveler kullanılamaz ve bazı zincirler CHAIN_CLASS_INIT nedeniyle başlatılmış olur.</span><span class="sxs-lookup"><span data-stu-id="16b29-111">Active frames will not be available for chains initiated due to CHAIN_ENTER_UNMANAGED, and for some chains initiated due to CHAIN_CLASS_INIT.</span></span> <span data-ttu-id="16b29-112">CorDebugChainReason numaralandırması bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="16b29-112">See the CorDebugChainReason enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16b29-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="16b29-113">Requirements</span></span>  

 <span data-ttu-id="16b29-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16b29-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16b29-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="16b29-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16b29-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="16b29-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16b29-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16b29-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
