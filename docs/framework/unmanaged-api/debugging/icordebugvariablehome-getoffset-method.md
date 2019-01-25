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
ms.openlocfilehash: 687c3bb441c2a12529c873b4fa5f9283b9326a40
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659075"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="1b759-102">ICorDebugVariableHome::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="1b759-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="1b759-103">Uzaklık, bir değişken için temel kasadan alır.</span><span class="sxs-lookup"><span data-stu-id="1b759-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b759-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b759-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1b759-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1b759-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="1b759-106">[out] Temel kayıt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="1b759-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1b759-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1b759-107">Return Value</span></span>  
 <span data-ttu-id="1b759-108">Bu yöntem, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="1b759-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="1b759-109">Değer</span><span class="sxs-lookup"><span data-stu-id="1b759-109">Value</span></span>|<span data-ttu-id="1b759-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b759-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="1b759-111">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="1b759-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="1b759-112">Değişken bir kayıt göreli bellek konumda değil.</span><span class="sxs-lookup"><span data-stu-id="1b759-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1b759-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1b759-113">Requirements</span></span>  
 <span data-ttu-id="1b759-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b759-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b759-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b759-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b759-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b759-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1b759-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1b759-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b759-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b759-118">See also</span></span>
- [<span data-ttu-id="1b759-119">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1b759-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
