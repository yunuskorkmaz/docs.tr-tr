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
ms.openlocfilehash: e06c98067fea9368ac8f750d9187636d2ca9a8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420114"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="a6f75-102">ICorDebugVariableHome::GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6f75-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="a6f75-103">Konum türüne sahip bir değişken içeriyor kayıt alır `VLT_REGISTER`ve temel kaydetme konumu türüne sahip bir değişken için `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="a6f75-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6f75-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6f75-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6f75-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6f75-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="a6f75-106">[out] Konum türüne sahip bir değişken kaydolun gösteren bir CorDebugRegister numaralandırması değeri `VLT_REGISTER`ve temel kaydetme konumu türüne sahip bir değişken için `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="a6f75-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a6f75-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a6f75-107">Return Value</span></span>  
 <span data-ttu-id="a6f75-108">Yöntemi, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="a6f75-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a6f75-109">Değer</span><span class="sxs-lookup"><span data-stu-id="a6f75-109">Value</span></span>|<span data-ttu-id="a6f75-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a6f75-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a6f75-111">Tarafından gösterilen kaydındaki değişkenidir `pRegister` bağımsız değişkeni.</span><span class="sxs-lookup"><span data-stu-id="a6f75-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a6f75-112">Değişken, bir kayıt veya bir kayıt göreli konumu değil.</span><span class="sxs-lookup"><span data-stu-id="a6f75-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a6f75-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6f75-113">Requirements</span></span>  
 <span data-ttu-id="a6f75-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6f75-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6f75-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6f75-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6f75-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6f75-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6f75-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6f75-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6f75-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6f75-118">See Also</span></span>  
 [<span data-ttu-id="a6f75-119">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="a6f75-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="a6f75-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6f75-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
