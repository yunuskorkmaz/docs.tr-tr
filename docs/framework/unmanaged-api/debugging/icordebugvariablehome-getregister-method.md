---
title: 'Icordebugvariablehome:: GetRegister yöntemi'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125069"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="1a7b6-102">Icordebugvariablehome:: GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="1a7b6-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="1a7b6-103">`VLT_REGISTER`konum türüne sahip bir değişken içeren kaydı alır ve `VLT_REGISTER_RELATIVE`konum türü olan bir değişken için temel kayıt olur.</span><span class="sxs-lookup"><span data-stu-id="1a7b6-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a7b6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a7b6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a7b6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1a7b6-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="1a7b6-106">dışı Bir CorDebugRegister numaralandırma değeri, konum türü `VLT_REGISTER`olan bir değişken için kaydolmayı ve `VLT_REGISTER_RELATIVE`konum türü olan bir değişken için temel kayıt olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="1a7b6-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a7b6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1a7b6-107">Return Value</span></span>  
 <span data-ttu-id="1a7b6-108">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="1a7b6-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="1a7b6-109">Değer</span><span class="sxs-lookup"><span data-stu-id="1a7b6-109">Value</span></span>|<span data-ttu-id="1a7b6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a7b6-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1a7b6-111">Değişken `pRegister` bağımsız değişkeni tarafından belirtilen yazmaç içinde.</span><span class="sxs-lookup"><span data-stu-id="1a7b6-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1a7b6-112">Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.</span><span class="sxs-lookup"><span data-stu-id="1a7b6-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1a7b6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1a7b6-113">Requirements</span></span>  
 <span data-ttu-id="1a7b6-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a7b6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a7b6-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1a7b6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a7b6-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1a7b6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a7b6-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a7b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a7b6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a7b6-118">See also</span></span>

- [<span data-ttu-id="1a7b6-119">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="1a7b6-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="1a7b6-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1a7b6-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
