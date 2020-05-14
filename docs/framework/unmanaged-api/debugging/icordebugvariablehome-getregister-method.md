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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396829"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="e45ec-102">Icordebugvariablehome:: GetRegister yöntemi</span><span class="sxs-lookup"><span data-stu-id="e45ec-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="e45ec-103">Konum türü olan bir değişken içeren kaydı `VLT_REGISTER` ve konum türü olan bir değişken için temel kaydı alır `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="e45ec-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e45ec-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e45ec-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e45ec-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e45ec-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="e45ec-106">dışı Konum türü olan bir değişken için kaydolmayı belirten CorDebugRegister numaralandırma değeri `VLT_REGISTER` ve konum türü olan bir değişken için temel kayıt `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="e45ec-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e45ec-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e45ec-107">Return Value</span></span>  
 <span data-ttu-id="e45ec-108">Yöntemi aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="e45ec-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="e45ec-109">Değer</span><span class="sxs-lookup"><span data-stu-id="e45ec-109">Value</span></span>|<span data-ttu-id="e45ec-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e45ec-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="e45ec-111">Değişken, bağımsız değişkeni tarafından belirtilen kasada bulunur `pRegister` .</span><span class="sxs-lookup"><span data-stu-id="e45ec-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="e45ec-112">Değişken, YAZMAÇ veya yazmaç ile ilişkili bir konumda değil.</span><span class="sxs-lookup"><span data-stu-id="e45ec-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e45ec-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e45ec-113">Requirements</span></span>  
 <span data-ttu-id="e45ec-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e45ec-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e45ec-115">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e45ec-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e45ec-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e45ec-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e45ec-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e45ec-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e45ec-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45ec-118">See also</span></span>

- [<span data-ttu-id="e45ec-119">VariableLocationType Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="e45ec-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="e45ec-120">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e45ec-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
