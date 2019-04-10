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
ms.openlocfilehash: 864cb893511bceabd61ce0064065b3866ce01dfe
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212602"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="ba5a6-102">ICorDebugVariableHome::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba5a6-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="ba5a6-103">Uzaklık, bir değişken için temel kasadan alır.</span><span class="sxs-lookup"><span data-stu-id="ba5a6-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5a6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba5a6-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5a6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba5a6-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="ba5a6-106">[out] Temel kayıt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="ba5a6-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba5a6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba5a6-107">Return Value</span></span>  
 <span data-ttu-id="ba5a6-108">Bu yöntem, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="ba5a6-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="ba5a6-109">Değer</span><span class="sxs-lookup"><span data-stu-id="ba5a6-109">Value</span></span>|<span data-ttu-id="ba5a6-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba5a6-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="ba5a6-111">Register-göreli bellek konumunda değişkendir.</span><span class="sxs-lookup"><span data-stu-id="ba5a6-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="ba5a6-112">Değişken bir kayıt göreli bellek konumda değil.</span><span class="sxs-lookup"><span data-stu-id="ba5a6-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ba5a6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba5a6-113">Requirements</span></span>  
 <span data-ttu-id="ba5a6-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba5a6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5a6-115">**Üst bilgi:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba5a6-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba5a6-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba5a6-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ba5a6-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="ba5a6-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba5a6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba5a6-118">See also</span></span>

- [<span data-ttu-id="ba5a6-119">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba5a6-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
