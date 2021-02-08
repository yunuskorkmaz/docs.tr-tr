---
description: ': ICorDebugModule:: GetBaseAddress metodu hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bdfa4aeac3a9c06f666d56f1ee08ec503626ce7d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790821"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="d504e-103">ICorDebugModule::GetBaseAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d504e-103">ICorDebugModule::GetBaseAddress Method</span></span>

<span data-ttu-id="d504e-104">Modülün temel adresini alır.</span><span class="sxs-lookup"><span data-stu-id="d504e-104">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d504e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d504e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d504e-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d504e-106">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="d504e-107">dışı `CORDB_ADDRESS` Modülün temel adresini belirten bir.</span><span class="sxs-lookup"><span data-stu-id="d504e-107">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d504e-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d504e-108">Remarks</span></span>  

 <span data-ttu-id="d504e-109">Modül yerel bir görüntüdür (yani, modül yerel görüntü Oluşturucu, NGen.exe) tarafından üretildiyse, taban adresi sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="d504e-109">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d504e-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d504e-110">Requirements</span></span>  

 <span data-ttu-id="d504e-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d504e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d504e-112">**Üst bilgi:** CorDebug. IDL, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d504e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d504e-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d504e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d504e-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d504e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d504e-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d504e-115">See also</span></span>
