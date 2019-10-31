---
title: 'Icordebugvariablehome:: GetOffset Yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 3af8c925b80b9fd4ed0a46d2bd50fe37a6f3154a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125092"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="fc612-102">Icordebugvariablehome:: GetOffset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc612-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="fc612-103">Bir değişken için temel kaydın konumunu alır.</span><span class="sxs-lookup"><span data-stu-id="fc612-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc612-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc612-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc612-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fc612-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="fc612-106">dışı Temel kayıttaki fark.</span><span class="sxs-lookup"><span data-stu-id="fc612-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc612-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fc612-107">Return Value</span></span>  
 <span data-ttu-id="fc612-108">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="fc612-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="fc612-109">Değer</span><span class="sxs-lookup"><span data-stu-id="fc612-109">Value</span></span>|<span data-ttu-id="fc612-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fc612-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="fc612-111">Değişken, YAZMAÇ göreli bir bellek konumudur.</span><span class="sxs-lookup"><span data-stu-id="fc612-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="fc612-112">Değişken, YAZMAÇ göreli bir bellek konumunda değil.</span><span class="sxs-lookup"><span data-stu-id="fc612-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc612-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc612-113">Requirements</span></span>  
 <span data-ttu-id="fc612-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc612-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc612-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="fc612-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc612-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fc612-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc612-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc612-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc612-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc612-118">See also</span></span>

- [<span data-ttu-id="fc612-119">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc612-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
