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
ms.openlocfilehash: 7f912f4b13620b567f5aa097604e98112d85f02d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711760"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="b2eb4-102">Icordebugvariablehome:: GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2eb4-102">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="b2eb4-103">Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="b2eb4-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2eb4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b2eb4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2eb4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b2eb4-105">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="b2eb4-106">dışı Konum türü olan bir değişken için kaydolmayı belirten CorDebugRegister numaralandırma değeri `VLT_REGISTER` ve konum türü olan bir değişken için temel kayıt `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="b2eb4-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b2eb4-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b2eb4-107">Return Value</span></span>  

 <span data-ttu-id="b2eb4-108">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="b2eb4-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="b2eb4-109">Değer</span><span class="sxs-lookup"><span data-stu-id="b2eb4-109">Value</span></span>|<span data-ttu-id="b2eb4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b2eb4-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="b2eb4-111">Değişken, bağımsız değişkeni tarafından belirtilen kasada bulunur `pRegister` .</span><span class="sxs-lookup"><span data-stu-id="b2eb4-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="b2eb4-112">Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.</span><span class="sxs-lookup"><span data-stu-id="b2eb4-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b2eb4-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2eb4-113">Requirements</span></span>  

 <span data-ttu-id="b2eb4-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2eb4-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2eb4-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b2eb4-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2eb4-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b2eb4-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2eb4-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2eb4-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2eb4-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b2eb4-118">See also</span></span>

- [<span data-ttu-id="b2eb4-119">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="b2eb4-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="b2eb4-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2eb4-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
