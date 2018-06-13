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
ms.openlocfilehash: 9a2ea7273fec62654c168d6786d3644b184ff7f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419575"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="c5114-102">ICorDebugVariableHome::GetOffset yöntemi</span><span class="sxs-lookup"><span data-stu-id="c5114-102">ICorDebugVariableHome::GetOffset Method</span></span>
<span data-ttu-id="c5114-103">Uzaklık bir değişken için temel kasadan alır.</span><span class="sxs-lookup"><span data-stu-id="c5114-103">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5114-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c5114-104">Syntax</span></span>  
  
```  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c5114-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c5114-105">Parameters</span></span>  
 `pOffset`  
 <span data-ttu-id="c5114-106">[out] Taban kayıt uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="c5114-106">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c5114-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c5114-107">Return Value</span></span>  
 <span data-ttu-id="c5114-108">Yöntemi, aşağıdaki değerleri döndürür:</span><span class="sxs-lookup"><span data-stu-id="c5114-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="c5114-109">Değer</span><span class="sxs-lookup"><span data-stu-id="c5114-109">Value</span></span>|<span data-ttu-id="c5114-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c5114-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="c5114-111">Bir kayıt göreli bellek konumda değişkenidir.</span><span class="sxs-lookup"><span data-stu-id="c5114-111">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="c5114-112">Değişken bir kayıt göreli bellek konumda değil.</span><span class="sxs-lookup"><span data-stu-id="c5114-112">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c5114-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c5114-113">Requirements</span></span>  
 <span data-ttu-id="c5114-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c5114-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c5114-115">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c5114-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c5114-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c5114-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c5114-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c5114-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5114-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c5114-118">See Also</span></span>  
 [<span data-ttu-id="c5114-119">ICorDebugVariableHome Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c5114-119">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
