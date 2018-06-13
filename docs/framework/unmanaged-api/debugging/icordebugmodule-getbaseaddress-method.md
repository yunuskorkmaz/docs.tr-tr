---
title: ICorDebugModule::GetBaseAddress Metodu
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10e7da7711cd63579589fda416d0d3a4f777eefe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412551"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="4a897-102">ICorDebugModule::GetBaseAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="4a897-102">ICorDebugModule::GetBaseAddress Method</span></span>
<span data-ttu-id="4a897-103">Modülün taban adresi alır.</span><span class="sxs-lookup"><span data-stu-id="4a897-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a897-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4a897-104">Syntax</span></span>  
  
```  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4a897-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4a897-105">Parameters</span></span>  
 `pAddress`  
 <span data-ttu-id="4a897-106">[out] A `CORDB_ADDRESS` modülü taban adresini belirtir.</span><span class="sxs-lookup"><span data-stu-id="4a897-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a897-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4a897-107">Remarks</span></span>  
 <span data-ttu-id="4a897-108">Bir yerel modül ise (diğer bir deyişle, modül NGen.exe yerel Görüntü Oluşturucu tarafından üretilmiş ise) görüntü, temel adresini sıfır olur.</span><span class="sxs-lookup"><span data-stu-id="4a897-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a897-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4a897-109">Requirements</span></span>  
 <span data-ttu-id="4a897-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a897-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a897-111">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a897-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a897-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a897-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a897-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a897-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a897-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4a897-114">See Also</span></span>  
    
 
