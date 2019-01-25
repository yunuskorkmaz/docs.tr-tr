---
title: ICorDebugVariableHome::GetRegister yöntemi
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7d678b6f52719287a1e8bbe88d178fa47b2893ca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563151"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="bca21-102">ICorDebugVariableHome::GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="bca21-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="bca21-103">Konum türünde bir değişken içeren bir kayıt alır `VLT_REGISTER`hem de konum türünde bir değişken için temel kaydı `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="bca21-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bca21-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bca21-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bca21-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bca21-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="bca21-106">[out] Konum türünde bir değişken için kayıt gösteren bir CorDebugRegister sabit listesi değeri `VLT_REGISTER`hem de konum türünde bir değişken için temel kaydı `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="bca21-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bca21-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bca21-107">Return Value</span></span>  
 <span data-ttu-id="bca21-108">Bu yöntem, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="bca21-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="bca21-109">Değer</span><span class="sxs-lookup"><span data-stu-id="bca21-109">Value</span></span>|<span data-ttu-id="bca21-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bca21-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="bca21-111">Değişkeni tarafından belirtilen kayıt defterinde olduğu `pRegister` bağımsız değişken.</span><span class="sxs-lookup"><span data-stu-id="bca21-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="bca21-112">Değişken, bir kayıt veya bir kayıt göreli konumu değil.</span><span class="sxs-lookup"><span data-stu-id="bca21-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="bca21-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bca21-113">Requirements</span></span>  
 <span data-ttu-id="bca21-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bca21-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bca21-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bca21-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bca21-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bca21-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bca21-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bca21-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bca21-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bca21-118">See also</span></span>
- [<span data-ttu-id="bca21-119">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="bca21-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="bca21-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bca21-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
