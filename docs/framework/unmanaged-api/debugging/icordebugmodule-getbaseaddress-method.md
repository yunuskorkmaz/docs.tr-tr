---
title: ICorDebugModule::GetBaseAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
ms.openlocfilehash: 4562318c87b79fba5f3d99860ee438c0144e9aae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710252"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="d5b58-102">ICorDebugModule::GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d5b58-102">ICorDebugModule::GetBaseAddress Method</span></span>

<span data-ttu-id="d5b58-103">Modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="d5b58-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5b58-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d5b58-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5b58-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d5b58-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="d5b58-106">dışı `CORDB_ADDRESS` Modülün temel adresini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d5b58-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5b58-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d5b58-107">Remarks</span></span>  

 <span data-ttu-id="d5b58-108">Modül yerel bir görüntüdür (yani, modül yerel görüntü Oluşturucu, NGen.exe) tarafından üretildiyse, taban adresi sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d5b58-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5b58-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d5b58-109">Requirements</span></span>  

 <span data-ttu-id="d5b58-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5b58-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5b58-111">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5b58-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5b58-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d5b58-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5b58-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5b58-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5b58-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d5b58-114">See also</span></span>
