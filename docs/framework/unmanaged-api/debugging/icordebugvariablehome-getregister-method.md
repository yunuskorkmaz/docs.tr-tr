---
description: ': Icordebugvariablehome:: GetRegister yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: c394d455048cf7451b8320ed72a6aa7adfb3518e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790665"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="8f0a2-103">Icordebugvariablehome:: GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f0a2-103">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="8f0a2-104">Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="8f0a2-104">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f0a2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f0a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8f0a2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f0a2-106">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="8f0a2-107">dışı Konum türü olan bir değişken için kaydolmayı belirten CorDebugRegister numaralandırma değeri `VLT_REGISTER` ve konum türü olan bir değişken için temel kayıt `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="8f0a2-107">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8f0a2-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8f0a2-108">Return Value</span></span>  

 <span data-ttu-id="8f0a2-109">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="8f0a2-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="8f0a2-110">Değer</span><span class="sxs-lookup"><span data-stu-id="8f0a2-110">Value</span></span>|<span data-ttu-id="8f0a2-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8f0a2-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="8f0a2-112">Değişken, bağımsız değişkeni tarafından belirtilen kasada bulunur `pRegister` .</span><span class="sxs-lookup"><span data-stu-id="8f0a2-112">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="8f0a2-113">Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.</span><span class="sxs-lookup"><span data-stu-id="8f0a2-113">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8f0a2-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f0a2-114">Requirements</span></span>  

 <span data-ttu-id="8f0a2-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f0a2-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f0a2-116">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8f0a2-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8f0a2-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8f0a2-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8f0a2-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f0a2-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f0a2-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f0a2-119">See also</span></span>

- [<span data-ttu-id="8f0a2-120">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="8f0a2-120">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="8f0a2-121">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f0a2-121">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
