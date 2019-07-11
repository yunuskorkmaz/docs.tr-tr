---
title: ICorDebugVariableHome::GetOffset yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0fdab81d499fe1508493cb0bf05a1787974a9d01
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774533"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="3674d-102">ICorDebugVariableHome::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="3674d-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="3674d-103">Uzaklık, bir değişken için temel kasadan alır.</span><span class="sxs-lookup"><span data-stu-id="3674d-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3674d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3674d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3674d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3674d-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="3674d-106">[out] Temel kayıt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="3674d-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3674d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3674d-107">Return Value</span></span>  
 <span data-ttu-id="3674d-108">Bu yöntem, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="3674d-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="3674d-109">Değer</span><span class="sxs-lookup"><span data-stu-id="3674d-109">Value</span></span>|<span data-ttu-id="3674d-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3674d-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="3674d-111">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="3674d-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="3674d-112">Değişken bir kayıt göreli bellek konumda değil.</span><span class="sxs-lookup"><span data-stu-id="3674d-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3674d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3674d-113">Requirements</span></span>  
 <span data-ttu-id="3674d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3674d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3674d-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3674d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3674d-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3674d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3674d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3674d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3674d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3674d-118">See also</span></span>

- [<span data-ttu-id="3674d-119">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3674d-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
